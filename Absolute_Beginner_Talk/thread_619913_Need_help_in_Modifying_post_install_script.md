---
title: "Need help in Modifying post install script"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by raxz on 2007-11-22
Hi 
I have a shell script that I copied from a co-worker which I usually use after installing Ubuntu and I would like some help in modifying the Eclipse part and the resources part for Gutsy Gibbon because they don't seem to work. I had to use the package manager to install Eclipse when I was using Feisty any suggestions would also be appreciated.

BTW, what is LDAP for?

Thanks

```


#!/bin/bash

######The out of date resources path how should I update this for gutsy######



#echo -n 'Updating APT cache data... '
#cat << DONE > ${APT_SOURCES_PATH}
#deb http://ph.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#deb-src http://ph.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#deb http://ph.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
#deb-src http://ph.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#deb http://ph.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb-src http://ph.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb http://packages.freecontrib.org/plf dapper free non-free
#deb-src http://packages.freecontrib.org/plf dapper free non-free
#deb http://archive.canonical.com/ubuntu dapper-commercial main
#DONE
#apt-get -qq update 
#echo 'Done'

#echo -n 'Installing LDAP authentication packages... '
#apt-get install -y --force-yes nfs-common portmap libpam-modules libpam-ldap libnss-ldap ldap-utils 
#echo 'Done'

#echo -n 'Reconfiguring LDAP authentication modules... '
#dpkg-reconfigure libpam-ldap 
#dpkg-reconfigure libnss-ldap 
#echo 'Done'



######The out of date resources path how should I update this for gutsy######






#echo -n 'Installing base software... '
#apt-get install -y --force-yes \
    linux-686 \
    linux-headers-686 \
    build-essential \
    openssh-server \
    subversion \
    zip \
    unzip \
    rar \
    unrar \
    bzip2 
#echo 'Done'

echo -n 'Installing additional software... '
apt-get install -y --force-yes \
    apache2-mpm-prefork \
    libapache2-mod-php5 \
    php5-curl \
    php5-ldap \
    php5-mysql \
    php5-mysqli \
    php5-gd \
    php5-imap \
    php5-xmlrpc \
    mysql-server-5.0 \
    mysql-admin \
    mysql-query-browser \
    phpmyadmin
mysql_tzinfo_to_sql ${TIMEZONE_PATH} | mysql -u root mysql
echo 'Done'

echo -n 'Installing desktop software... '
apt-get install -y --force-yes \
    gdesklets \
    gstreamer0.10-plugins-good \
    gstreamer0.10-plugins-bad \
    gstreamer0.10-plugins-ugly \
    totem-xine \
    w32codecs \
    bittornado-gui \
    mozilla-thunderbird 
echo 'Done'

echo -n 'Installing Emacs stuff... '
apt-get install -y --force-yes \
    emacs21 \
    emacs21-el \
    emacs-goodies-el \
    gnus \
    bbdb \
    eudc \
    php-elisp \
    ruby-elisp \
    python-mode
echo 'Done'

apt-get install -y --force-yes \
    sun-java5-jre \
    sun-java5-plugin
update-alternatives --config java 

#tar xzf installers/easyeclipse-php-1.0.2.tar.gz -C /opt
#ln -s /opt/php-1.0.2 /opt/easyeclipse
#echo -e '#!/bin/bash\n\n/opt/easyeclipse/eclipse' > /usr/local/bin/eclipse
#chmod a+x /usr/local/bin/eclipse

apt-get install -y --force-yes \
    gsfonts-x11 \
    flashplugin-nonfree

apt-get install -y --force-yes \
    cabextract \
    msttcorefonts \
    wine
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz -O - | tar xvzf - -C /opt

reboot



```

---

### Post by jfinkels on 2007-11-22
> **raxz said:**
> Hi 
I have a shell script that I copied from a co-worker which I usually use after installing Ubuntu and I would like some help in modifying the Eclipse part and the resources part for Gutsy Gibbon because they don't seem to work. I had to use the package manager to install Eclipse when I was using Feisty any suggestions would also be appreciated.

BTW, what is LDAP for?

LDAP is "Lightweight Directory Access Protocol", it's a protocol for managing users and computers across a network.

```

#echo -n 'Updating APT cache data... '
#cat << DONE > ${APT_SOURCES_PATH}
#deb http://ph.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#deb-src http://ph.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#deb http://ph.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
#deb-src http://ph.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#deb http://ph.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb-src http://ph.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb http://packages.freecontrib.org/plf dapper free non-free
#deb-src http://packages.freecontrib.org/plf dapper free non-free
#deb http://archive.canonical.com/ubuntu dapper-commercial main
#DONE
#apt-get -qq update 
#echo 'Done'

```

If you are using Ubuntu 7.10 Gutsy Gibbon, these repositories won't work. You'll need to make sure that the repositories you want to add here are still available for Gutsy. You can try just replacing "dapper" with "gutsy".

As for the variable " ${APT_SOURCES_PATH}", the path should be the same in Gutsy as it is in Dapper. aptitude sources are in the file "/etc/apt/sources.list".

```

echo -n 'Installing additional software... '
apt-get install -y --force-yes \
    apache2-mpm-prefork \
    libapache2-mod-php5 \
    php5-curl \
    php5-ldap \
    php5-mysql \
    php5-mysqli \
    php5-gd \
    php5-imap \
    php5-xmlrpc \
    mysql-server-5.0 \
    mysql-admin \
    mysql-query-browser \
    phpmyadmin
mysql_tzinfo_to_sql ${TIMEZONE_PATH} | mysql -u root mysql
echo 'Done'

```
As for ${TIMEZONE_PATH}, you're probably looking for "/usr/share/zoneinfo", but I'm not sure.
```

#tar xzf installers/easyeclipse-php-1.0.2.tar.gz -C /opt
#ln -s /opt/php-1.0.2 /opt/easyeclipse
#echo -e '#!/bin/bash\n\n/opt/easyeclipse/eclipse' > /usr/local/bin/eclipse
#chmod a+x /usr/local/bin/eclipse

```
What is the problem you are having with this? This extracts the package located at "./installers/easyeclipse-php-1.0.2.tar.gz" to the "/opt" directory, makes a link to it, makes a script that runs it, and makes that script executable. Note that you need to have the "installers/" directory in the same directory as this script that we are discussing, and it must contain "easyeclipse-php-1.0.2.tar.gz". What errors are you getting when you run this script?

---

### Post by raxz on 2007-11-22
ok, so I think I'm not gonna be needing LDAP(?)....

I am using this guide [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources) for my package lists...

basically how I'm using the script is by cutting and pasting parts of it on the terminal till I get everything that I need. I'm afraid to just run it all as root as the last time I did that I meessed up my Ubuntu...

so far after trying this script on Gutsy it's giving me this...

```

 sudo apt-get install -y --force-yes \
>     apache2-mpm-prefork \
>     libapache2-mod-php5 \
>     php5-curl \
>     php5-ldap \
>     php5-mysql \
>     php5-mysqli \
>     php5-gd \
>     php5-imap \
>     php5-xmlrpc \
>     mysql-server-5.0 \
>     mysql-admin \
>     mysql-query-browser \
>     phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php5-mysqli is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  php5-mysql
E: Package php5-mysqli has no installation candidate

```

Could anyone just give me a modified version of the script for Gutsy: mrgreen:?

Fixed I just removed the  'php5-mysqli \'...still if anyone is kind enough to give a modified version with Eclipse+Ruby+Rails+PHP+C+JAVA..... I would appreciate it so my next install would be painless...

---

### Post by jfinkels on 2007-11-22
My advice to you is this: understand what your script is doing before trying to use it! The best thing for you to do is to determine what you need for your own particular installation, instead of taking a script written for some other system...

As for php5-mysql, as the error message says, the package "php5-mysqli" has been replaced by the package "php5-mysql", so just install that instead of trying to install "php5-mysqli".
 
> **raxz said:**
> if anyone is kind enough to give a modified version with Eclipse+Ruby+Rails+PHP+C+JAVA..... I would appreciate it so my next install would be painless...

To install Eclipse, just do:```
sudo aptitude install eclipse
```

To install Ruby, just do:```
sudo aptitude install ruby
```

To install PHP, just do:```
sudo aptitude install php5-mysql
```

GCC should be installed, but if you want some extra libraries, make, etc. do:```
sudo aptitude install build-essential
```

To install Java, just do:```
sudo aptitude install sun-java6-jre
``` If you want the Java Software Development Kit, do:```
sudo aptitude install sun-java6-jdk
```

Now just put them all together:```
sudo aptitude install eclipse ruby php5-mysql build-essential sun-java6-jdk
```

Try it out yourself: run that command on your system and see how it goes. If you're pleased with the results, just add the "-y" flag to aptitude so it won't ask you for confirmation, and put it in a script:```
#!/bin/bash
sudo aptitude -y install eclipse ruby php5-mysql build-essential sun-java6-jdk
```

---

### Post by raxz on 2007-12-10
thanks.

Problem is solved now.:lolflag:

---

