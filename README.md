# Reverse-Proxy-Configuration
 "Belajar Jaringan Komputer untuk Pemula" - Build web server and Configuring NGINX &amp; Apache2 as Reverse Proxy Server

## Node.JS Web Server

In this section, we will set up a web server. Ready? Let's go straight to the steps.

1. Clone this repository

    ```bash
    $ git clone https://github.com/nurmuhimawann/reverse-proxy-configuration.git
    ```

2. Open Project Folder in Linux Terminal

    ```bash
    $ cd a387-jarkom-labs
    ```

3. Install Node.js Locally with Linux Node Version Manager (nvm)

    To install linux nvm, please run the following command.

    ```bash
    $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
    ```

    Urge! For nvm to work, please exit terminal with the following command.

    ```bash
    $ exit
    ```

    Open terminal again. Then, install Node.js with the following command.

    ```bash
    $ nvm install v14.15.4
    ```

4. Install all dependencies in package.json

    ```bash
    $ npm install
    ```

5. Run web server (Node.js)

    ```bash
    $ npm run start
    ```

6. Open URL referencing LocalHost in your browser

    Open **http://localhost:8000/** in your browser. And, Yeaay Congratulations. The web app is successfully running on the local server 😉

## NGINX Configuration

To configure NGINX as a reverse proxy, follow these steps.

1. Installing Nginx

    ```bash
    $ sudo apt update
    $ sudo apt-get install nginx -y
    ```

2. Verify Nginx is running

    Now you can verify that Nginx is running:

    ```bash
    $ sudo service nginx status
    ```

    If Nginx is not already running, you can run and check again that Nginx is running using the following command.

    ```bash
    $ sudo service nginx start
    $ sudo service nginx status
    ```

    NGINX server runs on port 80, which is the default port for the HTTP protocol. To access it, run **http://localhost:80/**

3. Configure NGINX as a Reverse Proxy Server

    a. view configuration files `default`

    ```bash
    $ cat /etc/nginx/sites-available/default
    ```

    b. edit configuration files `default`

    ```bash
    $ sudo nano /etc/nginx/sites-available/default
    ```

    - Changed the NGINX port from 80 to 3000 (not the Node.js web server port)
    - Changed the rate limit configuration to 6 requests per minute, alias one request every 10 seconds.

    c. Save file changes by pressing CTRL+X, then Y, and Enter.

4. Restart Nginx

    ```bash
    $ sudo service nginx restart
    ```

5. Run web server (Node.js)

    ```bash
    $ npm run start
    ```

6. Open URL referencing LocalHost in your browser

    Open your web browser and navigate to the localhost you set up with Nginx **http://localhost:3000/**.

    🎉🎉 Yeaay, Congrats. The web server is successfully running. You have successfully installed and configured Nginx reverse proxy on your Linux system 😉.

</br>

## Apache2 Configuration

To configure Apache2 as a reverse proxy, follow these steps.

1. Installing Apache2

    ```bash
    $ sudo apt update
    $ sudo apt-get install apache2 -y
    ```

2. Verify Apache2 is running

    Now you can verify that Apache2 is running:

    ```bash
    $ sudo service apache2 status
    ```

    If Apache2 is not already running, you can run and check again that Apache2 is running using the following command.

    ```bash
    $ sudo service apache2 start
    $ sudo service apache2 status
    ```

    Apache2 server runs on port 80, which is the default port for the HTTP protocol. To access it, run **http://localhost:80/**

3. Configure Apache2 as a Reverse Proxy Server

    a. view configuration files `000-default.conf`

    ```bash
    $ cat /etc/apache2/sites-available/000-default.conf
    ```

    b. edit configuration files `000-default.conf`

    ```bash
    $ sudo nano /etc/apache2/sites-available/000-default.conf
    ```

    - Changed the Apache2 port from 80 to 5000 (not the Node.js web server port)

    c. Save file changes by pressing CTRL+X, then Y, and Enter.

    d. view configuration files `ports.conf`

    ```bash
    $ cat /etc/apache2/ports.conf
    ```

    e. edit configuration files `ports.conf`

    ```bash
    $ sudo nano /etc/apache2/ports.conf
    ```

    - Changed the default port to 5000

    f. Save file changes by pressing CTRL+X, then Y, and Enter.

4. Enable Apache Modules for Reverse Proxy

    ```bash
    $ sudo a2enmod proxy
    $ sudo a2enmod proxy_http
    $ sudo a2enmod proxy_balancer
    $ sudo a2enmod lbmethod_byrequests
    ```

5. Restart Apache2

    ```bash
    $ sudo service apache2 restart
    ```

6. Run web server (Node.js)

    ```bash
    $ npm run start
    ```

7. Open URL referencing LocalHost in your browser

    Open your web browser and navigate to the localhost you set up with Nginx **http://localhost:5000/**.

    🎉🎉 Yeaay, Congrats. The web server (reverse proxy) is successfully running. You have successfully installed and configured Nginx reverse proxy on your Linux system 😉.
