---
title: "Jetty startup script?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by redline6561 on 2007-06-06
Hi lazyweb,

I've been trying to get an install of jetty on ubuntu that will load during boot up and I've run update-rc.d jetty defaults but it's not working. What am I doing wrong?
Jetty Install Process:
Install JDK 6u1 from Sun:
Grab the bin file and run:
sudo chmod +x *.bin
sudo sh ./jdk*.bin
sudo mv jdk1.6.0_01 Java6u1
sudo mv Java6u1 /usr/lib
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
sudo update-alternatives --config java
Select whichever number corresponds to /usr/lib/Java6u1/bin/java

Grab latest jetty from website and run:
sudo mkdir /opt/jetty
sudo chown $USER /opt/jetty
Unzip to /opt/jetty
Throw timekeeper in /opt/jetty/webapps via sudo cp -R timekeeper /opt/jetty/webapps
sudo chown -R jetty /opt/jetty
sudo chmod -R ugo+rw /opt/jetty
sudo cp /opt/jetty/bin/jetty.sh /etc/init.d/jetty
sudo touch /etc/init.d/jetty
set JETTY_HOME=/opt/jetty and JAVA_HOME=/usr/lib/Java6u1 in /opt/jetty/bin/jetty.sh
set Log location in /opt/jetty/etc/jetty.xml to /opt/jetty/logs
sudo ln -s /opt/jetty/bin/jetty.sh /etc/init.d/jetty
sudo update-rc.d jetty defaults

HALP?

Thanks.

---

