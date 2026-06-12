---
title: "Installing MythTv on Ubuntu 6.10  (OFFLINE) how?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by EzEe on 2007-04-26
Hi I don't have a internet connection for my pc in which ubuntu is installed. I want to install mythtv offline by downloading its .deb file and other dependencies. But the problem is I am unable to get all its dependencies. Can anybody help me with it. I need a list of all the file that mythtv needs to install. 

     Also plz tell if the guide for online installation is also applicable to offline installation or not.

---

### Post by NICU on 2007-04-27
Hi, using MythTV without an internet connection won't make you very happy.  You use your internet connection to download the program guides.  You can watch individual channels, but you won't be able to look at program guide, and you'll probably have a hard time scheduling recordings.  

The best MythTV install guide can be found here - [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)  It does require an internet connection however.  There are quite a few distrobutions out there that are centered around MythTV, like Knoppmyth - [http://mysettopbox.tv/](http://mysettopbox.tv/) Its not Ubuntu, but it will let you install MythTV without an internet connection.

---

### Post by superm1 on 2007-04-27
> **EzEe said:**
> Hi I don't have a internet connection for my pc in which ubuntu is installed. I want to install mythtv offline by downloading its .deb file and other dependencies. But the problem is I am unable to get all its dependencies. Can anybody help me with it. I need a list of all the file that mythtv needs to install. 

     Also plz tell if the guide for online installation is also applicable to offline installation or not.

Hi,
Actually there is a very convenient method of using synaptic to generate a list of of required files to download on another machine.  You'll need a GUI install of ubuntu to do this.

1) Open up Synaptic Package Manager.
2) Mark all apps that you want installed.
3) Click on the first menu and choose to generate package download script.
4) Save this script somewhere.
5) Run the script on another linux machine with wget. 
6) The result will be all debs that you need for dependencies and applications
7) Move these files to /var/cache/apt/archives on your 6.10 machine.

-
Question though, why 6.10 rather than 7.04?  I can tell you for sure that the ease of installation has improved immensely on 7.04.

Regardless, see the Ubuntu MythTV guides for more information on setting up whichever release you opt to use, [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by EzEe on 2007-04-29
> **superm1 said:**
> Hi,

-
Question though, why 6.10 rather than 7.04?  I can tell you for sure that the ease of installation has improved immensely on 7.04.
, [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

Well I thought that 6.10 has official support till 2009 whereas 7.04 has support till 2008. Also I thought that 7.04 will have many bugs which will create trouble for me since I have recently started using linux so I am still a novice in handling problems related to Ubuntu.

---

### Post by superm1 on 2007-04-29
> **EzEe said:**
> Well I thought that 6.10 has official support till 2009 whereas 7.04 has support till 2008. Also I thought that 7.04 will have many bugs which will create trouble for me since I have recently started using linux so I am still a novice in handling problems related to Ubuntu.
You have a minor mixup here.  6.06 is the long term support release whereas 7.04 is supported up through next year.  Irregardless, you can use either for mythtv.

---

### Post by viciouslime on 2007-04-29
> **NICU said:**
> Hi, using MythTV without an internet connection won't make you very happy.  You use your internet connection to download the program guides.  You can watch individual channels, but you won't be able to look at program guide, and you'll probably have a hard time scheduling recordings.

Not true if you live in Europe.

---

