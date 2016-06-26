---
layout: post
title: Ubuntu Installation Guide!
---

# Ubuntu Software Setup Instructions
### Common Guide Lines
1. Install any softwares

   ```
   sudo apt-get install <pacakge_name>
            (or)
   Download the package from relevant site and extract and install
            (or)
   Using dpkg / Ubuntu Software Center / Synaptic Tool
   ```
2. Uninstall any softwares

   ```
   sudo apt-get autoremove
   sudo apt-get remove <pacakge_name> (will remove the binaries)
           (or)
   sudo apt-get purge <pacakge_name>  (will remove everything)
   ```
3. List All existing installed Packages

   ```
   dpkg-query -l
   ```

### Setup Useful Packages

* [Ubuntu Build Essentials](http://packages.ubuntu.com/precise/build-essential)

  ```
  sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) main universe
  sudo apt-get update
  sudo apt-get install build-essential
  ```
* [SSH](https://www.maketecheasier.com/secure-ssh-server-ubuntu/)

  ```
  $ sudo apt-get update
  $ sudo apt-get install openssh
  ```
* Telnet/FTP

  ```
  $ sudo apt-get install xinetd telnetd
  $ sudo /etc/init.d/xinetd restart
  **FTP**
  $ sudo apt-get update
  $ sudo apt-get install vsftpd
  $ sudo service vsftpd restart
  ```
* LAMP

  ```
  $ sudo apt-get install apache2
  $ sudo apt-get install mysql-server
  $ sudo apt-get -y install php7.0 libapache2-mod-php7.0
  $ sudo /etc/init.d/apache2 restart (or) systemctl restart apache2
  **Test**
  $ php -r 'echo "\n\nYour PHP installation is working fine.\n\n\n";' (or)
  $ vi /var/www/html/info.php
    <?php
       phpinfo();
    ?>
  $ sudo chown www-data:www-data /var/www/html/info.php
  - Accessing file in browser `http://localhost/info.php` 

  **Enable the SSL website in apache**
  $ sudo a2enmod ssl
  $ sudo a2ensite default-ssl
  **phpmyadmin**
  $ sudo apt-get -y install phpmyadmin
  ```
  #### Ref: 
  - [Apache](http://httpd.apache.org/)
  - [PHP](http://www.php.net/)
  - [MySQL](http://www.mysql.com/)
  - [MariaDB](https://mariadb.com/)
  - [Ubuntu](http://www.ubuntu.com/)
  - [phpMyAdmin](http://www.phpmyadmin.net/)


* [python](http://chrisstrelioff.ws/sandbox/2014/06/04/install_and_setup_python_and_packages_on_ubuntu_14_04.html)

* [Browsers:Firefox/Chrome](https://www.mozilla.org/en-US/firefox/new/)

  ```
  **Firefox**
  $ cd /usr/local
  $ wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/46.0.1/linux-x86_64/en-US/firefox-46.0.1.tar.bz2
  $ tar xvjf firefox-46.0.1.tar.bz2
  $ sudo ln -s /usr/local/firefox/firefox /usr/bin/firefox
  $ firefox &
  **Chrome**
  $ wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
  $ sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
  $ sudo apt-get update
  $ sudo apt-get install google-chrome
  ```
* [TeamViewer](https://www.teamviewer.com/hi/download/windows/)
  
  ```
  $ wget http://download.teamviewer.com/download/teamviewer_linux.deb
  $ sudo dpkg --add-architecture i686
  $ sudo apt-get update
  $ sudo dpkg -i teamviewer_linux.deb
  $ sudo apt-get -f install
  $ sudo dpkg -i teamviewer_linux.deb
  ```
* [Skype](https://www.skype.com/en/download-skype/skype-for-computer/)

  ```
  $ sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
  $ sudo apt-get update
  $ sudo apt-get install skype
  ```
* [Sublime](https://www.sublimetext.com/2)
  
  ```
  $ sudo add-apt-repository -y ppa:webupd8team/sublime-text-2
  $ sudo apt-get update
  $ sudo apt-get install sublime-text
  ```

* [Git](https://git-scm.com/)

  ```
  $ sudo apt-get update
  $ sudo apt-get install git-core
  $ git --version
  $ git config --global user.name "username"
  $ git config --global user.email "user@email.com"
  $ git config --list
  ```

* [Atom](http://atom.io/)

  ```
  $ sudo add-apt-repository ppa:webupd8team/atom
  $ sudo apt-get update
  $ sudo apt-get install atom
  $ atom -version (version checking)

  Note: CTRL+, -> Settings
  ```

* [Nginx](http://nginx.com)
  
  ```
  $ sudo apt-get install nginx
  $ sudo /etc/init.d/nginx start
  $ htop (checking)
  $ sudo vi /etc/nginx/nginx.conf (configuration file)
  $ sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000 (redirection)
  ```
* [Java](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html)

  ```
  $ sudo apt-add-repository ppa:webupd8team/java
  $ sudo apt-get update
  $ sudo apt-get install oracle-java8-installer
  $ java -version (Versification)

  Setting Path:
  -----------
   ~/.bashrc :
    export JAVA_HOME=`pwd`
    export PATH=$JAVA_HOME/bin:$PATH
  ```

* [Node.js](https://nodejs.org/en/download/)

  ```
  $ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
  $ sudo apt-get install -y nodejs
  $ node --version
  ---------------------------------------------------------------
  [nvm](http://www.liquidweb.com/kb/how-to-install-nvm-node-version-manager-for-node-js-on-ubuntu-14-04-lts/)
  [npm](https://docs.npmjs.com/getting-started/installing-node)
  [grunt](http://gruntjs.com/installing-grunt)
  [gulp](https://github.com/gulpjs/gulp/tree/master/docs)
  ```

* [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

  ```
  $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
  $ echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list 
  $ sudo apt-get update
  $ sudo apt-get install -y mongodb-org
  $ sudo service mongod status/start/stop (check status)
  $ mongostat ( summary stats)
  $ mongo (shell)
  ```

* [DropBox](https://www.dropbox.com/business)

  ```
  $ sudo apt-get install nautilus-dropbox
  $ dropbox
  ```
### Common Errors && Solutions

-  Disable IPv6

   ```
   $ echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
   ```

-  Disable Firewall

   ```
   $ sudo ufw disable
   ```

-  To enable ssh root access

   ```
   $ sudo vi /etc/ssh/sshd_config
   @ PermitRootLogin without-password to @PermitRootLogin yes
   $ sudo service ssh restart
   ```

-  [Enable root user](http://www.bictor.com/2015/10/07/enabling-root-user-in-ubuntu-14-04-3/)


### Some useful References
- [Adding Users in linux](http://www.tecmint.com/add-users-in-linux/)
