---
title: "Just installed Server, can i get a GUI?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by jamesr316 on 2006-08-28
I must have read over the part that said the server doesnt come with a GUI interface. I was able to install the OS no problem, and grub starts up fine. I am a newby and I want to learn linux, but I do not want the desktop environment as I want to run a webserver and basically compare this server to my 2k3 server. Is there any way to install a desktop environment? I downloaded the 64-bit PC (AMD64) server install CD. Thanks in advance.

---

### Post by bodhi.zazen on 2006-08-28
Yes, which one do you want?

---

### Post by aysiu on 2006-08-28
```
sudo aptitude update
sudo aptitude install ubuntu-desktop linux-amd64-generic
sudo /etc/init.d/gdm start
``` You can substitute *kubuntu-desktop* or *xubuntu-desktop* for *ubuntu-desktop*.

There are also *linux-amd64-k8* and *linux-amd64-k8-smp* instead of *linux-amd64-generic*.

---

### Post by ciscosurfer on 2006-08-28
I'm confused.  You say you do not want the desktop environment as you run a webserver, but that you want to install a desktop environment.  

If you want to install a desktop environment, install ubuntu-desktop, but *keep in mind* it will install many dependencies, i.e., a lot of files that you may not want if you are running a server (hence, the reason the server edition, and almost every other distro that runs as a server edition, has no GUI by default (reasons include, but not limited to: you want it slim, there's generally no need for a GUI, security)```
sudo aptitude update && sudo aptitude install ubuntu-desktop linux-amd64-generic
sudo /etc/init.d/gdm start
```

---

### Post by aysiu on 2006-08-28
Wow, you're right, ciscosurfer. I totally missed that.

Yeah, if you just want a GUI but not a desktop environment, just do ```
sudo aptitude update
sudo aptitude install x-window-system-core icewm
startx
``` You can substitute *fluxbox* or *blackbox* for *icewm* if you prefer those.

---

### Post by jamesr316 on 2006-08-28
which one would you reccomend? im not familiar with either?

aysiu, that doesnt work for me. my ethernet isnt configured correctly (wireless card) and the first line fails to resolve the "us.archive.ubuntu.com" 

The next line told me couldnt find any package whos name or description matched "ubuntu-desktop"...listed some other packages to install, asked me yes or no, chose yes, it did its thing and finished, then i tried your 3rd line and it gave me:
"sudo: /etc/init.d/gdm: command not found"

---

### Post by aysiu on 2006-08-28
You have a server... but your ethernet isn't configured correctly...? I'm not sure I understand you. What does your server do?

In any case, you should probably straighten out what's going on with your internet connection before you try installing stuff through online repositories.

Or... if you have a Ubuntu **Alternate CD** handy, you could use that as a local repository (instead of using online repositories).

---

### Post by jamesr316 on 2006-08-28
let me try to explain a little better. I want to run the server version and not the desktop version. Among exploring, i would like to try to use this as a local webserver to try to test some php scripts. I do need a desktop environment as I will obviously need it first because I am not proficient in linux yet. What I would like to do eventually is be able to remote into it, almost like microsoft terminal services or a vnc connection. But as of right now, i just want to explore the server version through a desktop environment. This is just for my education, this will not be a live server.

---

### Post by bodhi.zazen on 2006-08-28
> **jamesr316 said:**
> which one would you reccomend? im not familiar with either?

aysiu, that doesnt work for me. my ethernet isnt configured correctly (wireless card) and the first line fails to resolve the "us.archive.ubuntu.com" 

The next line told me couldnt find any package whos name or description matched "ubuntu-desktop"...listed some other packages to install, asked me yes or no, chose yes, it did its thing and finished, then i tried your 3rd line and it gave me:
"sudo: /etc/init.d/gdm: command not found"

You will obviously need to fix your Internet connectivity.

If I recall correctly, ubuntu-desktop is not in the repositories but is only available on the Ubuntu cd's, in which case you will need to install from the CD, which may be helpful.

If you can connect to the Internet, I would second the suggestion of icewm. It is light, has less dependencies, and is a little more newbie friendly then blackbox/Fluxbox/openbox.

Edit: Just saw your last post. If you are new to Linux I suggest you start with the standard Ubuntu install. Once you know what and how you want your server, start with the server install.

FYI: I run Fluxbox on a server install without KDE/Gnome/XFCE and it is light and fast.

---

### Post by aysiu on 2006-08-28
You're not recalling correctly--*ubuntu-desktop* is in both the online repositories and the **Alternate CDs**.

---

### Post by jamesr316 on 2006-08-28
Ok, i did not realize that you need to connect to the internet to install packages. I just learned something :)

---

### Post by aysiu on 2006-08-28
> **jamesr316 said:**
> Ok, i did not realize that you need to connect to the internet to install packages. I just learned something :)
Well, the other option is to install from the **Alternate CD**.

The **Desktop CD** and **Server CD** will not have the packages you need for a GUI.

---

### Post by jamesr316 on 2006-08-28
i reinstalled, configged my card correctly, currently installing what you told me to.

---

### Post by aysiu on 2006-08-28
> **jamesr316 said:**
> i reinstalled, configged my card correctly, currently installing what you told me to.
Which? *icewm* or *ubuntu-desktop*?

---

### Post by jamesr316 on 2006-08-28
ubuntu-desktop...still installing.

---

### Post by jason.b.c on 2006-08-28
Hey , Not to step on anyone's toes here but , Can the kubuntu desktop be installed from a CD...??

I've got the kubuntu , Ubuntu , Edubuntu , etc CD's here ...., I have gnome in breezy right now , Can i also have KDE...???   Wil that cause problems..??

---

### Post by aysiu on 2006-08-28
> **jason.b.c said:**
> Hey , Not to step on anyone's toes here but , Can the kubuntu desktop be installed from a CD...??

I've got the kubuntu , Ubuntu , Edubuntu , etc CD's here ...., I have gnome in breezy right now , Can i also have KDE...???   Wil that cause problems..??
You can also have KDE, but to install it from CD, you need the **Alternate CD**. You cannot add Kubuntu from the **Desktop CD**.

Of course, if you have the patience to wait for the download, you can install it from the online repositories:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by jason.b.c on 2006-08-28
> **aysiu said:**
> You can also have KDE, but to install it from CD, you need the **Alternate CD**. You cannot add Kubuntu from the **Desktop CD**.

Of course, if you have the patience to wait for the download, you can install it from the online repositories:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

You mean it can't be installed from the kubuntu v6.06 live/install CD i got from Ship-it..??  There's no way i could ever download it...No way..

You mean you can't "cd" (change directory) to the CD (compact disk)...?

---

### Post by jamesr316 on 2006-08-28
Thanks for all of the help. I have learned 2 things from this post already. You get packages from the internet, and there is an alternate cd. 

I have the desktop environment running right now, I will play around with it and I'm sure you will see me ask more questions here. Thanks for the quick responses everyone, this support community rocks. I hope to be able to contribute to it one day.

---

### Post by aysiu on 2006-08-28
> **jason.b.c said:**
> You mean it can't be installed from the kubuntu v6.06 live/install CD i got from Ship-it..??  There's no way i could ever download it...No way..

You mean you can't "cd" (change directory) to the CD (compact disk)...? I mean that you can install anew (as in *overwrite* your current installation) from the **Desktop CD**, but you cannot use it as a way to *add* a new desktop environment to your existing installation. For that, you need the **Alternate CD** or the online repositories.

I'm not talking about changing directories. I'm talking about using *aptitude*, *apt-get*, Adept, or Synaptic to install Kubuntu, Ubuntu, or Xubuntu on top of Ubuntu, Xubuntu, or Kubuntu.

> **jamesr316 said:**
> 
I have the desktop environment running right now, I will play around with it You must have a super-fast internet connection to have downloaded and installed it that quickly. > and I'm sure you will see me ask more questions here. Thanks for the quick responses everyone, this support community rocks. I hope to be able to contribute to it one day. Sounds good.

---

