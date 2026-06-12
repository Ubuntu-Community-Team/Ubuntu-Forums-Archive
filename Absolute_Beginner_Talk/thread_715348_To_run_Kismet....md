---
title: "To run Kismet..."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by krowii on 2008-03-04
Hello everyone...my question: What do I need to do to run kismet in ubuntu? We are putting together a project in my networking class and I have to use ubuntu for my part...so I am trying to get kismet to work...

my system is a toshiba laptop: 
Intel Core 2 Duo T5500 @ 1.66GHz w/ 2.0GB RAM
Mobile Intel 945GM Express Chipset Family

I am running ubuntu in a virtual environment (VPC) and I supposedly just installed Kismet using Synaptic (it says status: installed when i search for Kismet) but when i try to run kismet in the terminal, i get this output:

[COLOR="Blue"]krowii@Raccoon:~$ kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}[/COLOR]


Can someone please take some time to help me with this? I would really appreciate it!! ^^

---

### Post by Origin415 on 2008-03-04
You need to setup kismet manually first by editing its configuration file, /usr/local/etc/kismet.conf
There is unfortunately no "easy" way to do this yet (that I know of :/)

There is more information about this here:[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml) (or in the man pages for kismet)

---

### Post by krowii on 2008-03-05
OK~ Thanks for the info~~ I'll just have to struggle through this I guess! ^^

I wish someone could post a step-by-step guide to getting kismet to work in Ubuntu. It seems like theres a hundred threads about kismet, but no single complete walk through. :(

---

### Post by shivam.seth on 2008-03-23
you need to edit the configuration file of kismet named Kismet.conf

In the configuration file, you need to change the **Source** to whatever drivers you are using for your wireless card. There will be three dummy entries against your** source** in the configuration file... Change those! The entries need to be changed according to your wLan card. Which wLan card do you use and what are the drivers you are using for the same? I will see if I can help!!!

---

### Post by shivam.seth on 2008-03-23
For a good tutorial, you can check out this link .... [http://kerneltrap.org/node/5414]("http://kerneltrap.org/node/5414")

If still you need help, please come back!

---

