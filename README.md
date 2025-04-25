Docker Monitoring with Prometheus, Grafana, and cAdvisor
This project provides a setup for monitoring Docker containers using Prometheus, Grafana, and cAdvisor. The setup includes a Docker Compose configuration that spins up Prometheus, Grafana, and cAdvisor for monitoring NGINX (or any other container you choose).

🛠️ Project Setup
Prerequisites
Before you start, make sure you have the following tools installed:

* Docker - For container management.

* Docker Compose - For multi-container management.

* Git - For version control and cloning the repo.

1. Clone the Repository
First, clone this repository to your local machine:
https://github.com/saiusha30/nginx-monitoring-with-cadvisor-prometheus-grafana.git
2. Edit the Prometheus Configuration (prometheus.yml)
Open the prometheus.yml file to make sure the scrape configuration for cAdvisor and NGINX is set up properly.

3. Start the Docker Compose Stack
Run the following command to start Prometheus, Grafana, and cAdvisor using Docker Compose:

docker-compose up -d

This will start the services in detached mode:

* Prometheus will run on port 9090.

* Grafana will run on port 3000.

* cAdvisor will run on port 8080.
4. Run NGINX Container
Run your NGINX container with the following command:

docker run -d --name nginx-container -p 80:80 nginx4. 

This will start an NGINX container, and it will be monitored by cAdvisor and scraped by Prometheus.

5. Access the Services
Prometheus: Open your browser and go to http://localhost:9090 to access the Prometheus dashboard.

Grafana: Open your browser and go to http://localhost:3000 to access the Grafana dashboard. The default login is:

Username: admin

Password: admin (or whatever you've set).

6. Steps to Create a New Dashboard in Grafana:

Step A : Create a New Dashboard:

* Once logged in, on the left sidebar, click on the "+" (plus) icon to open the menu.

* Select "Dashboard" from the options.
Step B:
Add a Panel:

* After creating a new dashboard, Grafana will automatically present you with an empty panel.

* Click on the "Add Panel" button, or hover over the panel and click the "Add Panel" option.
Step C:
Choose Data Source:

* On the new panel that appears, select the Prometheus data source (or any other data source that you've already set up in Grafana).

* This data source is where Grafana will pull the metrics from (e.g., Prometheus for monitoring Docker containers).
Step D:
Write Your Query:

* After selecting the data source, you will see a query editor.

* Write your query to retrieve the metrics you want to visualize. For example, if you want to monitor NGINX container CPU usage, you can use a query like:
rate(container_cpu_usage_seconds_total{container_name="nginx-container"}[5m])

Step E:
Save the Panel:

* Once you're happy with the visualization, click on "Apply" in the top right corner of the panel to save it.

🧰 Project Structure
docker-compose.yml: Defines the services (Prometheus, Grafana, cAdvisor).

prometheus.yml: Prometheus configuration file with scrape targets.
README.md: This documentation.


🚀 Contributing
Feel free to fork this project and submit pull requests for any improvements or additional features you would like to add.

Issues
If you encounter any problems, please open an issue in the GitHub repository.

📚 References
Grafana Official Website

Prometheus Official Website

cAdvisor Official Website



