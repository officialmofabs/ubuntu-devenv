# Multi VNC Ubuntu GUI with Docker 🖥️

A powerful Docker solution for running multiple Ubuntu GUI instances with VNC access. Launch up to 10 parallel Ubuntu desktop environments, each with its own XFCE4 GUI and persistent storage. Perfect for virtual labs, parallel testing, development environments, and training sessions.

## Features

- 10 independent Ubuntu desktop environments
- VNC access to each container
- Persistent storage for each container
- XFCE4 desktop environment
- Automatic container restart on failure
- Easy deployment with Docker Compose

## Prerequisites

- Docker
- Docker Compose
- VNC Viewer (like RealVNC, TigerVNC, or any VNC client)

## Project Structure

```
.
├── Dockerfile
├── docker-compose.yml
├── start-vnc.sh
├── README.md
└── data/
    ├── vnc1/
    ├── vnc2/
    ├── ...
    └── vnc10/
```

## Quick Start

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. Create the required data directories:
   ```bash
   mkdir -p data/vnc{1..10}
   ```

3. Build and start the containers:
   ```bash
   docker-compose up -d
   ```

4. Connect to any container using a VNC viewer:
   - Container 1: `localhost:5901`
   - Container 2: `localhost:5902`
   - ...
   - Container 10: `localhost:5910`

   Default VNC password: `password`

## Container Details

Each container runs:
- Ubuntu (latest)
- XFCE4 desktop environment
- TightVNC Server
- Resolution: 1920x1080 (configurable in Dockerfile)

## Port Mapping

| Container    | Port  |
|-------------|-------|
| vnc_ubuntu1 | 5901  |
| vnc_ubuntu2 | 5902  |
| vnc_ubuntu3 | 5903  |
| vnc_ubuntu4 | 5904  |
| vnc_ubuntu5 | 5905  |
| vnc_ubuntu6 | 5906  |
| vnc_ubuntu7 | 5907  |
| vnc_ubuntu8 | 5908  |
| vnc_ubuntu9 | 5909  |
| vnc_ubuntu10| 5910  |

## Persistent Storage

Each container has its own persistent storage in the `data` directory:
- Container 1: `./data/vnc1`
- Container 2: `./data/vnc2`
- ...and so on

## Management Commands

Start all containers:
```bash
docker-compose up -d
```

Stop all containers:
```bash
docker-compose down
```

View container logs:
```bash
docker-compose logs [container_name]
```

Restart a specific container:
```bash
docker-compose restart vnc1  # Replace vnc1 with desired container name
```

## Security Considerations

- The default VNC password is set to "password". It's recommended to change this in the Dockerfile for production use.
- VNC traffic is not encrypted by default. For production use, consider using SSH tunneling or VPN.

## Customization

- Resolution can be modified in the Dockerfile (ENV RESOLUTION=1920x1080)
- Additional packages can be added to the Dockerfile
- Desktop environment settings can be modified through XFCE4 settings

## Troubleshooting

1. If you can't connect to VNC:
   - Ensure the ports are not being used by other applications
   - Check container logs: `docker-compose logs vnc1`
   - Verify the container is running: `docker-compose ps`

2. If the container keeps restarting:
   - Check logs for errors: `docker-compose logs vnc1`
   - Ensure sufficient system resources are available

## License

[Add your license information here]

## Contributing

[Add contribution guidelines if applicable]
