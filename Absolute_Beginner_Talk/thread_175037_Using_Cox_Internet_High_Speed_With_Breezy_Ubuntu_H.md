---
title: "Using Cox Internet High Speed With Breezy Ubuntu How To Get Working"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by dreamerwand on 2006-05-12
Hello I've been running Breezy Ubuntu for several months using dial-up just fine. Now I have switched to Cox High Speed Internet and when I boot into Ubuntu it does not go online automatically (whereas in Windows it does).

Long ago when I installed Ubuntu I didn't configure the networking and now I see I need to do so for my network card. When I type ifconfig it says nothing.

How do I enable my networking card so I can use the internet in Ubuntu? I know  it has to do with DHCP somehow, right? Please help, the modem is a high speed cable modem connected with an ethernet cable. What do I need to do, thanks.

---

### Post by johnc4510 on 2006-05-12
System>Administration>Networking and configure eth0
Now, this is in dapper, but Networking is in Breezy too, but it might be in a different place, I don't remember for sure. Like Applications>Internet, I just don't remember.

---

### Post by dreamerwand on 2006-05-12
[QUOTE=johnc4510]System>Administration>Networking and configure eth0
Now, this is in dapper, but Networking is in Breezy too, but it might be in a different place, I don't remember for sure. Like Applications>Internet, I just don't remember.[/QUOTE]

Hi I tried this in Breezy's KDE and went into administrator mode to configure the eth0 device and it crashed throwing up a logo with a crash message. Does this work in Gnome better than it does in KDE? After following the instructions you provide should the device and internet just work when I try it in Gnome?

---

### Post by johnc4510 on 2006-05-12
yes, I have cox too, for about 3 months, and this is what I did to connect. Now everytime I login, I'm online

---

### Post by johnc4510 on 2006-05-12
[QUOTE=johnc4510]yes, I have cox too, for about 3 months, and this is what I did to connect. Now everytime I login, I'm online[/QUOTE]I use Gnome.

---

### Post by dreamerwand on 2006-05-12
[QUOTE=johnc4510]yes, I have cox too, for about 3 months, and this is what I did to connect. Now everytime I login, I'm online[/QUOTE]

Great to hear about your experience thank you. Thank you for your help I will try your suggestion within the Gnome desktop for setting up the networking. Because of the crash in KDE when configuring I'll not use KDE unless there is a simple work around for this crash. Thank you for your help

---

### Post by dreamerwand on 2006-05-12
Hi it now works, thank you! **BUT** when I run sudo I receive the following error:

```
sudo: unable to lookup myhostname via gethostbyname()
```

Where myhostname was a generic name I entered when originally installing Breezy Ubuntu

How do I fix this so I can use sudo again? It appears it modified my /etc/hosts file and removed my hostname information and inserted its own. How do I reclaim my use of sudo and how do I edit the hosts file when I can't use sudo now?

---

### Post by dreamerwand on 2006-05-12
In addition to now not being able to use sudo due to the new hosts file error of my host name disappearing from it, now when I login to Gnome it gives me a warning and I can't use sudo to edit the hosts file to insert my hostname again. I can't use sudo in a terminal in Gnome and I tried to login with "Failsafe" but sudo didn't work there either.

How do I fix this problem and will I experience this problem in the future or was it just a temporary auto-edit done when I configured/activated my network card in networking?

---

### Post by dreamerwand on 2006-05-12
On this hostname problem I will attempt to follow these suggestions:

[http://ubuntuforums.org/showthread.php?t=173330&highlight=sudo+hostname](http://ubuntuforums.org/showthread.php?t=173330&highlight=sudo+hostname)

I'll see if those suggestions resolve this problem

---

### Post by dreamerwand on 2006-05-12
Problem solved! Thanks johnc4510 for your help, within minutes you responded and enabled me to use my high speed internet on Breezy Ubuntu with Gnome and the Search feature on the forums enabled me to solve a related issue within minutes too! Thank you

---

