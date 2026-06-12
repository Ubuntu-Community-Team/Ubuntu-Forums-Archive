---
title: "Software Installation"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by dan.erasmus on 2006-10-03
Hi All

I have recently switched over to Ubuntu. I am currently running it dual boot with XP on my Acer Travelmate 4100. Ubuntu has been running as my primary dektop OS for the last 2 - 3 weeks.

I just have one small problem with it, why is it so difficult to install software in Ubuntu? I am specifically referring to software that is not sitting in the Synaptic. Some software is really easy, just double-click it and there you go (Skype), but then you get things like installing a package that will allow you to play MP3's and you have to do 10 things (*** exaggeration ***) just to get it going. 

**[SIZE="4"]There seems to be no standardised format for software and software installation in Linux. [/SIZE]**

I am aware of the fact that there are many different distros of Linux, but would it not be handy for one of you clever Linux programmers to write some, sort of program that can compile a package that is easily installable on any distro (i.e. double-click the file and follow the prompts)? 

Just a comparison, lets say you have Windows 98, Windows 2000 and Windows XP. I know 2000 and XP are basically the same, but the point is that 95% of exe's from a third party vendors are able to install on any of the three platforms without having to download any additional software or having to do anything special. 

If there is a good reason for Linux not having a facility like this, then please inform me and I will learn to live with the shortcomings, but if not, can someone tell me why?

Thanks,

Dan

---

### Post by xyz on 2006-10-03
Try this link for starters. Good luck, patience and a little work will do the trick.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by risbac on 2006-10-03
To install without the repositories is clearly not the typical way to do it. The setup.exe philosophy is a Windows one and can't be easily applied here. Why? Good question, I think it's first because there is more difference between two Linux distribution than between Windows 2000 and XP. Please correct me if I'm wrong, but when you install a Linux software, you make the maximum use of libraries already installed. For Windows, I think there are much more libraries included in each softwares and doing the same thing as others. The duplication allows you to install without caring much what is already installed or not on the computer. Linux just uses another philosophy, which allow you to update your whole system in a few clicks when it needs to work almost software by software on Windows. Also, by using the repos and only the repos, you know that everything will be installed at the right place in your system: config in /etc/..., etc.. etc... With Windows, each software installs its stuffs according to its own logic. 

So the idea is more: stick to the repos, or add new trusted ones. 
Otherwise you have to compile most of the time, and its not an easy process. Softwares which are not in the repos are more or less not supported by the OS in a way, even if you can always compile.

---

### Post by risbac on 2006-10-03
And also, looking at your examples, you talk about proprietary softwares. I'm not sure, but I think that Easy Ubuntu proposes to install them. And otherwise they are probably in the Canonical repositories, that's how I would install them. I try as much as possible to stick to the repos, or compile. I don't like to use installers, you don't really know where they put the stuffs.

---

### Post by risbac on 2006-10-03
Third answer, seems that I can summarize my thoughts easily... Looking at what you say, I don't think it's impossible to simplify the compile job. Two versions ago in Ubuntu, you had to use command line to install a .deb package. Now it's automatic. So I don't really see why it would not be possible to do a small program running the "configure" then installing the missing package and compiling. Maybe i'm just day dreaming.

---

### Post by andiii on 2006-10-03
The package management is a great advantage over manually downloading software. It can't be easier to keep a system (and all applications) up to date.

---

### Post by aysiu on 2006-10-03
There are "clever" Linux developers already trying to do what you propose.

[Autopackage](http://autopackage.org/)
[Klik](http://klik.atekon.de/)

Thing is--just as with a setup.exe for Windows--usually, it's up to the software developers to create a package for the operating system. And, on some sites, you will see that: an RPM for SuSE, an RPM for Fedora, a DEB for Debian, a DEB for Ubuntu, etc.

---

