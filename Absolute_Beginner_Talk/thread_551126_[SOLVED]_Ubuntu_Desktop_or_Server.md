---
title: "[SOLVED] Ubuntu Desktop or Server?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-09-14
What is the difference between Ubuntu 7.04 Desktop and Ubuntu 7.04 Server editions?  I currently have the desktop version installed but I wanted to encrypt my entire OS and found, what seems like a good, how to at [https://help.ubuntu.com/community/EncryptedFilesystemHowto8?highlight=%28encryptedfilesystem%29](https://help.ubuntu.com/community/EncryptedFilesystemHowto8?highlight=%28encryptedfilesystem%29).  This website says to download and run the server edition but that a desktop version is going to be installed.  Will the server edition run the same as the desktop?

---

### Post by jay4e on 2007-09-14
basically the desktop edition install the gui and common home and office apps.  server edition installs some additional file management and networking as well as apache, mysql, php if you choose the lamp option.  

The kernel and core system are the same, its just the apps that are installed that makes the difference.  further its just the defailt install that is really different as all the apps are available on both.  thus you can install the desktop and then install all the needed server apps or vice verse.

Case in point, on my laptop im running the desktop edition with the lamp apps to do web testing.

---

### Post by slughappy1 on 2007-09-14
I see, so you say that it's just the applications that are installed that makes the difference? Awesome, thanks

---

### Post by sfong15 on 2007-09-18
> **jay4e said:**
> basically the desktop edition install the gui and common home and office apps.  server edition installs some additional file management and networking as well as apache, mysql, php if you choose the lamp option.  

The kernel and core system are the same, its just the apps that are installed that makes the difference.  further its just the defailt install that is really different as all the apps are available on both.  thus you can install the desktop and then install all the needed server apps or vice verse.

Case in point, on my laptop im running the desktop edition with the lamp apps to do web testing.

I have exactly the same question, i.e. just installed desktop LTS but not sure if I should rub it off and install server version, what I really need is get LAMP running.

Where do I find applications download for LAMP to turn my desktop to server?   I would also need ftp server in that machine as well.

Thanks in advance

---

### Post by CaptainInsaneO on 2007-09-18
Keep in mind that server edition doesn't have a gui. You'd have to do

```
sudo apt-get install gnome-desktop
```

to get the gui working so you don't have just a command line all the time.

---

### Post by mhilliard on 2007-09-18
Herman,
Is the Gnome Desktop preferable to other desktops for the Ubuntu server? Is is it smaller or does it take less resources?

This is a newby question, but I thought the KDE desktop was the default. Thanks for any info you can send my way!

Mark

---

### Post by atria on 2007-09-18
Gnome is the default setup for Ubuntu (the desktop version anyway)

As for the server edition you have to install a desktop environment by yourself if you need it.
Gnome is not exactly light on resources but other window managers like fluxbox and xfce are.

You can actually install the other window managers with apt-get.

---

