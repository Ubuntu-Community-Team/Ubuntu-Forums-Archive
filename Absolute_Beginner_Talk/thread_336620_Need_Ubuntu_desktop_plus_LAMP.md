---
title: "Need Ubuntu desktop plus LAMP"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by 4partee on 2007-01-11
I installed 6.06 desktop and hoped I could install the AMP of LAMP.  But no..., I hit a wall at Apache. I tried to install via Synaptic and I would like to include the screenshot of the error I received, but apparently that is not possible.  I am way too frustrated to type the message.  Perhaps you could try it and see that it happens to you as well. 

Interestingly, I go back to retrace my steps so I can get this post right and guess what, something totally different happens.  Instead of refusing to even start the install, I now get this message that I was luckily enough to be able to copy from the dialog box that popped up.

"E: apache: subprocess post-installation script returned error exit status 1"

I'm not a Linux novice and not a Wintard.  I am running a LAMP+desktop right now just fine on a Slackware based system.  I'm just exploring alternatives and Ubuntu seems to be highly regarded.  

The problem I forsee is that [whatever]buntu is divided between server and desktop and both is what I need on one system.  

I did some surfing on the forum and saw that ..buntu has a BIG problem with wireless laptops.  So in adddition to the above roadblock, I would need to use the built-in BC4318 wifi on my laptop. 

If anyone cares to respond, please understand that I might not be back by here to reply for a while.  As it stands, I would need a persuavive argument to migrate from a working Slackware solution.  

John

---

### Post by thewump on 2007-01-11
I did this yesterday:

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

( Then install ROROX and Rails )

You'll maybe get more than you wanted.. but was very straightfoward install of apache, mysql, and php.

Keith

---

### Post by 4partee on 2007-01-11
Thanks for that.  Fast too! 

However, the standard Slackware install already includes LAMP.  This does not argue well for the persuation to migrate to  ..buntu.  IOW, I don't need to go to Sourceforge to achieve LAMP.  I would be more impressed if ..AMP was at least available available via Synaptics.

John

---

### Post by Albi on 2007-01-11
4partree- the server installation CD includes LAMP as one of the optional defaults.  You can install ubuntu-desktop with apt (or xubuntu-desktop to save some resources) as an addon later.

---

### Post by 4partee on 2007-01-11
Thank You so much for the prompt reply.  

So, are you saying that if I do a new install of the server version I can add the desktop so I have a Ububtu+server version?

Could you please reply with the commands I would need to perform to add the desktop version to the server version? I ask this due to the sorry experience I have had so far.  

I have never installed the server version, and the server version specifically excludes XWindows, so explain how would I get to the point where I could be right back here.  That is, reading and replying to the forum.  I will need to install the server version right over this install as I am out of free partitions, so I could be out-of -pocket for a while.

John

John

---

### Post by rccharles on 2007-01-12
Try:

apt-get install gnome-desktop-environment

The apt-get command will find and download all dependencies. It should start up the GUI.

You would think that there would be a howto on this, but I do not know where to look.

Robert

---

### Post by 4partee on 2007-01-12
> **rccharles said:**
> Try:

apt-get install gnome-desktop-environment

Robert

That package was reported as not found.  I searched some more amd found this: 
[http://www.ubuntuforums.org/showthread.php?t=331840&highlight=lamp](http://www.ubuntuforums.org/showthread.php?t=331840&highlight=lamp)

Per message #8 I am running sudo apt-get install ubuntu-desktop right now.  Honestly, I don't know what to do next though.  How do I start the gui? Do I type a command or do I reboot?  

John

---

### Post by rccharles on 2007-01-12
> **4partee said:**
> That package was reported as not found.  I searched some more amd found this: 
[http://www.ubuntuforums.org/showthread.php?t=331840&highlight=lamp](http://www.ubuntuforums.org/showthread.php?t=331840&highlight=lamp)

Per message #8 I am running sudo apt-get install ubuntu-desktop right now.  Honestly, I don't know what to do next though.  How do I start the gui? Do I type a command or do I reboot?  

John

I should have mentioned ubuntu-desktop too.  Sorry about the confusion.

Robert

---

### Post by exp0zed on 2007-01-18
> **4partee said:**
> That package was reported as not found.  I searched some more amd found this: 
[http://www.ubuntuforums.org/showthread.php?t=331840&highlight=lamp](http://www.ubuntuforums.org/showthread.php?t=331840&highlight=lamp)

Per message #8 I am running sudo apt-get install ubuntu-desktop right now.  Honestly, I don't know what to do next though.  How do I start the gui? Do I type a command or do I reboot?  

John

sudo startx

---

### Post by davebgimp on 2007-01-18
For web development, i like to use [Xampp]("http://www.apachefriends.org/en/xampp.html"). Very easy to set up.

---

### Post by irish_flu on 2007-01-18
> **4partee said:**
> I installed 6.06 desktop and hoped I could install the AMP of LAMP.  But no..., I hit a wall at Apache. I tried to install via Synaptic and I would like to include the screenshot of the error I received, but apparently that is not possible.  I am way too frustrated to type the message.  Perhaps you could try it and see that it happens to you as well. 

Interestingly, I go back to retrace my steps so I can get this post right and guess what, something totally different happens.  Instead of refusing to even start the install, I now get this message that I was luckily enough to be able to copy from the dialog box that popped up.

"E: apache: subprocess post-installation script returned error exit status 1"

I'm not a Linux novice and not a Wintard.  I am running a LAMP+desktop right now just fine on a Slackware based system.  I'm just exploring alternatives and Ubuntu seems to be highly regarded.  

The problem I forsee is that [whatever]buntu is divided between server and desktop and both is what I need on one system.  

I did some surfing on the forum and saw that ..buntu has a BIG problem with wireless laptops.  So in adddition to the above roadblock, I would need to use the built-in BC4318 wifi on my laptop. 

If anyone cares to respond, please understand that I might not be back by here to reply for a while.  As it stands, I would need a persuavive argument to migrate from a working Slackware solution.  

John

I'm bummed that it gave you problems.  Normally, installing the "vanilla" ubuntu desktop CD, adding a couple of extra repositories (just by clicking on them in Synaptic's options) and then installing the packages works fine.  I wonder if there's not perhaps a larger issue afoot....

---

