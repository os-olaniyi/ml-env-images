FROM tensorflow/tensorflow:2.8.0-python3.9

# Set working directory to /app
WORKDIR /app

# Install additional dependencies
RUN pip install --no-cache-dir keras opencv-python torch torchvision tensorboard scikit-learn

# Install VSCode server
RUN apt-get update && apt-get install -y curl wget && \
    wget -q https://code-server.dev/install.sh && sh install.sh && \
    rm -rf /var/lib/apt/lists/*

# Install Jupyter
RUN pip install --no-cache-dir jupyter

# Install VSCode extensions
RUN code-server --install-extension streetsidesoftware.code-spell-checker && \
    code-server --install-extension ms-python.python && \
    code-server --install-extension ms-toolsai.jupyter && \
    code-server --install-extension visualstudioexptteam.vscodeintellicode-apiutils
    

# Expose the port for VSCode
EXPOSE 8080

# Create a volume for code and resources
VOLUME /app/code

# Run VSCode when the container starts
CMD ["code-server", "--bind-addr", "0.0.0.0:8080"]