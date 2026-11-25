# Homelab-setup
For this setup; I'm repurposing an old Dell Desktop into a Debian server that'll host Proxmox VE.

Proxmox VE is a free, open-source platform that can run and manage Virtual Machines (VMs) and Containers. You can access it via Web-browser, so I can build from my home computer. For my project, I'm planning to use VMs to simulate a small-scale network for Cybersecurity testing. Additionally, I'll use a container to host tailscale so I can SSH into my machine if I'm away from home.

## Proxmox-setup
After installing Debian onto my host machine, I'll be referring to Proxmox documentation for setup: https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_13_Trixie
Luckily the setup is straightforward, you can just copy and paste the commands into your terminal.

The first step is to change my host machine's loopback address. Here I've replaced 127.0.1.1 with the IP address of my host machine.
![Step one](images/proxmox1.png)

Next, we have to add the repository sources, then check it's correctly configured with:

nano /etc/apt/sources.list.d/pve-install-repo.sources
![Step two](images/proxmox2.png)
![Step three](images/proxmox3.png)

Everything looks okay, so next we add the repo key as a root user.
![Step four](images/proxmox4.png)

Next, I've issued the 'apt modernize-sources' command to migrate pre-existing repositories into the deb822 format. 

Once it's migrated, the 'apt update && apt full-upgrade' will refresh the list of available packages and update them.
![Step five](images/proxmox5.png) 
##### Note: This isn't necessary as the old entries still work for now, but still considered good practice.

