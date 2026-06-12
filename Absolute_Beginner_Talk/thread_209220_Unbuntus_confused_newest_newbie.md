---
title: "Unbuntus confused newest newbie"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by fuji9991 on 2006-07-04
Hello.  I am looking to ween myself off of windows and set up my first web server at the same time.  I heard Linux is the way to go and Ubuntu is a great tool.

I downloaded Ubuntu server 6.06 from the Ubuntu site and performed a LAMP installation on my computer.

When I boot I get a text prompt "user@user:~$" in what looks like a DOS window.  I am confused after seeing all the GUI screenshots all over the web and I can not find  documentation that tells me what I am supposed to do next.

Can anyone give me a general explination of where to go from here and provide a link to a start-up guide?  Thanks.:eek:

---

### Post by T700 on 2006-07-04
By default, Ubuntu server install does not have a GUI; it is administered via the command line. You can install a GUI by typing at the command line:
 
 ```
sudo aptitude install gnome-desktop-environment
``` 
and press enter.  When next you log in, you will have a GUI.  I'm sure some others will provide you with additional information.  Setting up a server is easy.  Setting up a secure and well functioning server is a little more tricky.
[SIZE=1] 
[/SIZE]  Paul 

*Edited to add the forgotten "sudo"!  :-)*
[SIZE=1] [/SIZE]

---

### Post by MetalMusicAddict on 2006-07-04
[QUOTE=fuji9991]Hello.  I am looking to ween myself off of windows and set up my first web server at the same time.  I heard Linux is the way to go and Ubuntu is a great tool.

I downloaded Ubuntu server 6.06 from the Ubuntu site and performed a LAMP installation on my computer.

When I boot I get a text prompt "user@user:~$" in what looks like a DOS window.  I am confused after seeing all the GUI screenshots all over the web and I can not find  documentation that tells me what I am supposed to do next.

Can anyone give me a general explination of where to go from here and provide a link to a start-up guide?  Thanks.:eek:[/QUOTE]
This isnt ment to sound mean or be a huge dererent but the jump you trying to make is a huge one. I would get comfortable with Ubuntu or linux in general first. Many things are gonna be a shock for you especially with a server install which has no gui. If you want a GUI from where you are now, from your user promt you mentioned you can type a couple of things to get a desktop environment.

Others please feel free to add.

From the prompt:

For a Gnome desktop- **sudo apt-get install ubuntu-desktop**
For a KDE desktop- **sudo apt-get install kubuntu-desktop**
For a XFCE desktop- **sudo apt-get install xubuntu-desktop** <- This will be a little more lightweight and what I use on my server.

These will give the same install as if you installed from their own disks.

---

### Post by fuji9991 on 2006-07-04
Thanks guys.  I understand a vinilla Unbuntu server is a text driven OS aye?  I tried to install "sudo apt-get install ubuntu-desktop" but I get Temporary failure resolving 'security.unbuntu.com'.  I am pretty sure it is a networking issue seeing as I just plugged in DSL and never did a config.  Can you guys point me in the direction as to how to config the internet connection.

P.S. don;t worry about me,  I know what I am getting into.  I will be an anchor for a few weeks but I'll be posting tips in no time.  I won;t be serving anything sensitive and if the server got hacked and abused I would just start over from scratch.

---

### Post by nalmeth on 2006-07-04
Try restarting networking with
sudo /etc/init.d/networking restart

also, it is a good idea to use aptitude rather than apt-get when installing a meta-package that brings along a whole bag of packages, like the kubuntu / ubuntu / xubuntu, because it makes them much easier to uninstall.

Sound like you know what you're doing, just thought I'd add the tip

have fun!

---

### Post by MetalMusicAddict on 2006-07-04
Welcome sir. I wish you all the luck. The work is worth it. Did the installer configure your NIC for DHCP on install? If not Im not sure how to do it from commandline. Id try the [Xubuntu]("http://www.xubuntu.org/") Install. Id get the alternate install. Might be a little better to start with.

---

### Post by Tarvok on 2006-07-04
Sounds to me like you've got an ADSL modem. I wonder why most people, when they hear "DSL", start giving LAN advice?

Anyway, if you have an ADSL moem (like, you got the free package from SBC or something), [go here]("https://help.ubuntu.com/community/ADSLPPPoE").

---

### Post by MaximB on 2006-07-04
for adsl config just type :
sudo pppoeconf
then enter YOUR password
and the config will begin

---

