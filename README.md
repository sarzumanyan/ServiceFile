# ServiceFile
Service file for flask application
A unit configuration file whose name ends in `.service` encodes information about a process controlled and supervised by systemd. It helps your application run on background, without running it.
# Create the service structure
File should be situated in `/etc/systemd/system` directory.
#### Description:
- A description of your service.
#### After:
- Specifies the order in which services should be started. `network.target` ensures the network is available before starting your service.
#### User and Group:
- Specify the user and group under which your application should run. Preferably, use a non-privileged user.
#### ExecStart:
- Path to the executable of your application.
#### Restart:
- Defines the restart behavior of your service. `always` means it will be automatically restarted if it crashes.
#### WantedBy:
- Specifies which target this service should be started with.
# Reload systemd:
After creating and saving the service file, reload systemd to read the new service definition:

```bash
sudo systemctl daemon-reload
```
- To enable the service to start on boot:
```bash
sudo systemctl enable web_application.service
```
- To start the service:
```bash
sudo systemctl start web_application.service
```
- To stop the service:
```bash
sudo systemctl stop web_application.service
```
- To restart the service:
```bash
sudo systemctl restart web_application.service
```
- To disable the service from starting on boot:
```bash
sudo systemctl disable web_application.service
```

# View Service Status:

You can view the status of your service using:

```bash
sudo systemctl status web_application.service
```
