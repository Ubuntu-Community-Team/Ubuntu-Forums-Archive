---
title: "noob: unable to install packages"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by badperson on 2007-10-30
Hi,

I did a lamp install of ubuntu 7.10 server edition last night. 

I created a directory, and created a *.java file that just prints a line out on the console. I tried to compile the file, and got a message saying that javac was available in several packages and that I should install one of them. I tried to do so by typing:

sudo apt-get install sun-java6-jdk

It then says it can't find the package. Do I need to be in a certain directory when installing packages? The server guide documentation doesn't say that you do. 

thanks. 
bp

---

### Post by Steve1961 on 2007-10-30
Just type sudo nano /etc/apt/sources.list and make sure the universe and multiverse repos are uncommented

---

### Post by badperson on 2007-10-30
thanks, 

I tried that, and uncommented everything having something to do with universe and multiverse...btw, in nano, to savet he file you hit ctl + O for Write Out, right? 

still had the same problem, 
it says it's reading package list\building dependency tree\reading state information\couldn't find package. 

thanks, 
bp

---

### Post by taurus on 2007-10-30
Did you remember to update the list first?

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```
Otherwise, post you /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by Steve1961 on 2007-10-30
Ctrl O does save - but make sure it's the letter O and not zero.

Try sudo apt-cache search sun-java6-jdk

This is what I get:

sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)

Looks like it's in the multiverse repo

---

### Post by badperson on 2007-10-30
thanks, 
I'll try posting the sources.list later tonight, if I can connect the ubuntu machine to the internet. 

I'm totally new to ubuntu; I booted up with an ethernet cable attached, but am not sure if I can get on the internet. When I did sudo apt-get update, I got a lot of errors; unable to connect, unable to find this or that. 

I'm also going totally off the command line, I was hoping to instally a gui environment; I think sudo apt-get install ubuntu-desktop is the solution for that, right? 

thanks again. 
bp

---

### Post by Steve1961 on 2007-10-30
sudo apt-get install ubuntu-desktop should get you a gui environment

---

### Post by badperson on 2007-11-01
Hi,

by typing sudo apt-get updagte, I get a whole bunch of "failed to fetch" errors...I'm guessing the machine isn't hooked up to the internet. 

I booted up with an ethernet cable attached...which program do I configure the connection with my isp? 

thanks, 
bp

---

### Post by Steve1961 on 2007-11-01
Use the ifconfig command to whatt interfaces Ubuntu recognizes.  If you use dhcp you could then try and get a connection by typing something similar to:

sudo dhclient eth0

---

### Post by badperson on 2007-11-01
hi,

thanks. that gives me

no dhcpoffers recieved
no working leases in persistent database.

I'm wondering if it wouldn't be better to download the desktop edition of ubuntu and play with that for awhile before playing with the server. 

Can the desktop edition have some server functionality; other machines connecting to it, sharing files, virtual desktop, that kind of thing? 
bp

---

### Post by Steve1961 on 2007-11-01
The desktop version can do everything teh server version can, so probably a good idea to download the live cd and check everything works properly from that

---

