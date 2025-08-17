# Comprehensive Setup and Configuration Guide for Nginx and Jenkins on Ubuntu

Step 1: Installing Nginx
Update your server’s package lists to ensure you have the most recent repository information. Install Nginx using the package manager, which also installs necessary dependencies. Configure the firewall (ufw) to allow HTTP and HTTPS traffic by enabling appropriate Nginx profiles. Verify Nginx is running by checking its service status and accessing the default web page. This sets up a robust, efficient web server capable of handling multiple connections and serving as a reverse proxy or load balancer.

Step 2: Installing Jenkins
Add the Jenkins repository and key to your system to access the latest Jenkins packages. Install Jenkins via the package manager. Start and enable Jenkins service to run automatically on system boot. Open firewall ports needed by Jenkins (default port 8080, and others if required). Complete the Jenkins initial setup by retrieving the administrator password and configuring it via the web interface. Jenkins is now ready to automate building, testing, and deploying your applications.

Step 3: Initial Nginx Configuration with IPv6 Reverse Proxy
Configured Nginx to listen on your server’s IPv6 address. Set up reverse proxying to forward incoming requests to your Jenkins or application backend running on localhost (port 8080). Added headers to preserve client IP and protocol info, essential for logging and security. Supported WebSocket connections for Jenkins or other apps that require it.

Step 4: Configure DNS with IPv6 on Namecheap
Created an AAAA record in your DNS management console pointing your domain to your IPv6 address (without brackets). Used DNS propagation tools to verify the new AAAA record is active worldwide before proceeding.

Step 5: Enable HTTPS with Let's Encrypt and Certbot
Installed Certbot and Nginx plugin to manage SSL certificates automatically. Obtained SSL certificates for your domain using Certbot’s automatic configuration. Configured Nginx to listen on both IPv4 and IPv6 port 443 with SSL enabled. Tested configuration integrity and reloaded Nginx to apply SSL settings. Ensured Certbot’s auto-renewal mechanism is in place to keep certificates valid.

Step 6: Configure HTTP to HTTPS Redirection
Set up Nginx server blocks to listen on HTTP ports for both IPv4 and IPv6. Configured these blocks to redirect all HTTP traffic to the HTTPS secure endpoint. This ensures secure connections by default.

Step 7: Implement Load Balancing with Upstream Servers
Defined upstream blocks in Nginx for your application backends (multiple instances on different ports). Configured proxy_pass directives to distribute incoming requests evenly among the backend servers. This enhances application scalability and availability.

Step 8: Configure Path-Based Routing for Multiple Applications
Set up Nginx location blocks to route requests based on URL path prefixes (/app1/, /app2/) to respective backend upstream groups. Included proxy headers and WebSocket support in each location block. Configured the root path (/) to route to the primary application backend.

Step 9: Testing and Validation
Used nginx -t to confirm configuration syntax correctness after each edit. Reloaded the Nginx service to apply configuration changes. Verified HTTPS is working with valid SSL certificates. Confirmed HTTP traffic redirects to HTTPS properly. Tested IPv6 and IPv4 connectivity to the site. Validated load balancing by observing traffic distribution and failover behavior. Confirmed path-based routing serves correct backend applications based on request URL.


<img width="1181" height="464" alt="Screenshot from 2025-08-17 15-44-18" src="https://github.com/user-attachments/assets/e2106df3-472a-4a1e-93aa-e168674d6c52" />
<img width="1049" height="455" alt="Screenshot from 2025-08-17 15-53-03" src="https://github.com/user-attachments/assets/6b44f174-85fc-449f-8606-63f70467ba71" />
<img width="1049" height="455" alt="Screenshot from 2025-08-17 15-53-03" src="https://github.com/user-attachments/assets/81cb73a3-8ee1-408d-aa4f-d8186081aa0c" />
<img width="1472" height="757" alt="Screenshot from 2025-08-17 16-01-00" src="https://github.com/user-attachments/assets/d98124f0-4e9f-4fbb-95ca-98c4b39d71e2" />
<img width="1185" height="995" alt="Screenshot from 2025-08-17 16-09-03" src="https://github.com/user-attachments/assets/37aca779-387b-4a0f-9fb3-a5fd065f489b" />
<img width="1533" height="800" alt="Screenshot from 2025-08-17 16-12-46" src="https://github.com/user-attachments/assets/fdb20fec-3246-441a-9ad9-748813707a8e" />
<img width="1533" height="800" alt="Screenshot from 2025-08-17 16-12-57" src="https://github.com/user-attachments/assets/46555c37-f30f-4988-9bc0-ab84f9bcc584" />






