---
title: "First questions concerning apt-upgrade and boot"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by theaustrian on 2007-08-24
Hi Everyone

I am new to the Ubuntu and the Linux community. I have never really worked with Linux. I am now trying. I have spent the last 2 days working on the server installation of ubuntu feisty fawn. I am only working on the terminal. Thinking that I will learn most there. My ultimate goal is to have a website running with mysql and php behind it. I have already accomplished most of it with the comprehensive tutorials and documentations you have here.

My first question is concerning the apt-get upgrade future. Which I ran straight after the installation. It is saying that it is keeping back linux-image-server and linux-server. Why is that and what should I do.

The second question is if it is possible to post my syslog of my last restart, so you guys could have a look at it and tell me whats going on/wrong. I most interested if all drivers are working. Just a quick look to check if there is any security problem would be sufficient.

Thank you very much and may ubuntu be with you

Greetings from Costa Rica

Ferdinand

---

### Post by Hobo Joe on 2007-08-24
As far as drivers go, the command 'glxinfo' will help.

---

### Post by theaustrian on 2007-08-24
I installed mesa-utils but now when I start glxinfo it says can't open display (null). Is that because I don't have a window system. When installing mesa-utils it also installed x11 common. Would I need to configure x11? (I actually just want to work on terminal; is it a security risk for a server?)

What about the other question concerning apt-get upgrade any clues there.

Thank you for the answer

---

### Post by bjarneh on 2007-08-24
sudo glxinfo

don't become root first, then you will not be allowed to open a display

---

### Post by Bachstelze on 2007-08-24
glxinfo is for graphics drivers, it won't be of much use for a server...

The linux-image package contains your image of the Linux kernel. It wasn't updated to the lastest version because updating it would require to install new packages (the packages containing the new kernel). To update it, do

```
sudo apt-get dist-upgrade
```

Running a X server is not a security risk but if you don't need/want it, why bother ?

---

### Post by az on 2007-08-24
INstall mc (midnight commander).  It's a file manager.  

sudo apt-get install mc

It is in the universe repo.  Run it and hit F9 to get into the menu.  Enable lynx-like motion and that will allow you to use the cursor keys to zip around your filesystem.

Use it to view your logs in /var/log

Midnight Commander will transparently view gzped logs without you having to unpack them yourself...

---

### Post by theaustrian on 2007-08-24
So updating the dist is no problem at all and doesn't change anything besides the kernel.

Thank you all for your quick responses.

---

### Post by bjarneh on 2007-08-24
sorry didn't read your entire question

---

### Post by theaustrian on 2007-08-24
no worries bjarneh. thank you.

Right now I am also working on the system via putty. I installed openssh-server and wanted access the server via a key but I just had to type in the password. How can I change that. I looked in the ssh documentation here on the ubuntu page but I could not find any. 

If I am asking to many questions just tell me :)

---

