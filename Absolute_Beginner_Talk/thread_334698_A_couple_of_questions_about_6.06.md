---
title: "A couple of questions about 6.06"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by mavix on 2007-01-09
Question #1: how do i go about setting up a dial up internet connection in ubuntu 6.06? It doesn't appear to recognise my internal modem and when i connect an external modem it keeps on deactivating it. Question #2: if i download the wine package will it install without having to download other packages?

---

### Post by Jussi Kukkonen on 2007-01-09
You'll probably get an answer to #2 if you run ***sudo apt-get --simulate install wine***

---

### Post by ieee488 on 2007-01-09
I use dial-up on Ubuntu 6.06.

I always use **sudo wvdialconf** to see if modems I have are compatible.

When you execute that command in a terminal window, you'll see Ubuntu trying
to find a modem.

It will definitely find your external modem.

Then you will need to check with your ISP to see what it needs from you to log in.
In Windows, all that was "hidden" from us, but with Linux you will need to know what is really happening.

---

### Post by tagginannie on 2007-01-10
> **mavix said:**
> Question #1: how do i go about setting up a dial up internet connection in ubuntu 6.06? It doesn't appear to recognise my internal modem and when i connect an external modem it keeps on deactivating it. Question #2: if i download the wine package will it install without having to download other packages?

Your internal modem is probably a win modem witch means you can only use it for windows. As for dialup first go /etc/ppp/ and right click on the "Options" file and go to actions->edit as root. Look for the word "auth" and put a "#" befor it so it will look like this "#auth" now save.Now go to your home folder and right clck and choose "creat new->text file and save it as a blank file and name it "resolv.conf", open the terminal witch you can find in system tools of the menu and type "sudo cp resolv.conf /etc/resolv.conf.Now start 
the gnome network config or KPPP and enter the name of your ISP and access number. 
Now click on modem and enter your modem name and change the speed to 57600. Dont 
bother with querying the modem because Ubuntu will not detect it, that only works after 
you have connected to your ISP. Close the boxes, now enter your user name and 
password and click connect


Suzy

---

### Post by Sef on 2007-01-10
Read [Linmodems]("http://linmodems.org").   They can help you get your modem up and running.

---

### Post by maddog39 on 2007-01-10
By the way, if you run:
```

sudo apt-get install wine

```
it will work no matter what, the installer handles all the depdency packages and is pretty much gaurenteed to work. I've never had a problem with a program not working after I installed it with apt-get.

---

