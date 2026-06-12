---
title: "What should I do?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by deadlychicken22 on 2006-10-28
I have been using ubuntu for almost a year now, but I still don't really know much about how it works (hence posting in beginner talk). Over the summer, I went crazy with trying out fancy graphics and other things on my ubuntu desktop. I tried out many things, including glx and compiz. Now, for whatever reason, the programs no longer work properly (I disabled the startup scripts) and my desktop is left in a very messy state (frequent problems). 

I would like to get my graphics back to how they were originally when I installed ubuntu and get rid of all of this other stuff (for now). I considered simply reinstalling ubuntu, but the problem with that is that I remember it taking me hours and hours to get my wireless network working (connecting through a netgear wg111) and to get my networked printer to work. It also took me quite awhile to get my graphics card properly detected and configured (a geforce 7600 gt). I'm sure there were other problems with the install, but I can't remember what they were.

What should I do? Is there a way to get rid of all of this crap without destroying my other settings? Basically, I would like it to be like a new install except that I need my wireless network, printer, and my graphics card to work.

Thank you,
-Ben

---

### Post by TheWizzard on 2006-10-28
the general problem of ubuntu is that it is so easy. ubuntu doesn't force you to learn the details of linux. i noticed that my knowledge of linux decreased since i'm using ubuntu. on the other hand i don't spend hours and hours solving problems 8) 


i can only give you advice for the next time you install:
- make installation notes! this is always useful. even my fedora installation notes were helpful when i migrated to ubuntu because they deal with my hardware.
- use the command line as much as possible, not the gui installer (synaptic). and use sudo for every command instead of performing several root tasks with "sudo -i". now you can use the history command 
```
history > history.txt
```
this gives you a record of how you configured your box. you can easily copy/pas commands. 

for the moment: 
- backup the /etc folder. all your settings are inhere and can help you to configure after a clean install. 
- i think a clean install is the best for you at the moment. 
- backup as much as you can on an external usb-disk if possible. your global settings are all in /etc and your personal settings are in hidden folders in your home folder. 
- use 
```
dpkg --get-selections | grep -v deinstall > installed-software.log
``` to get a list of the packages you installed. you can install all packages at once with the command 
```
# dpkg --set-selections < /backup/installed-software.log
``` but be carefull because this may install orphan rubish you don't want.

---

### Post by deadlychicken22 on 2006-10-28
Thanks for the helpful answer. I think that what you are suggesting is my best course of action, I'm just afraid I won't be able to get everything working again... I remember many headaches trying to get my wireless network and graphics card to work. Has support for wireless usb network devices increased? Is the geforce 7600 gt fully detected now? I think I will download edgy and try it out next weekend (this week is my last week of the quarter, I have a lot of tests :( ).

EDIT: The biggest problem is my wireless internet. To get my wireless adaptor to work, I had to get it setup with ndiswrapper. Unfortunately, I didn't know how to set it up and while I was in ubuntu I couldn't check for help online because it wouldn't connect to the internet.

Also, I have an AMD athlon 64 3200+ processor. I am currently running on the regular x86 version, should I switch to the 64-bit version? What are the advantages/disadvantages?

Thanks!

---

### Post by TheWizzard on 2006-10-29
> **deadlychicken22 said:**
> Thanks for the helpful answer. I think that what you are suggesting is my best course of action, I'm just afraid I won't be able to get everything working again... I remember many headaches trying to get my wireless network and graphics card to work. Has support for wireless usb network devices increased? Is the geforce 7600 gt fully detected now? I think I will download edgy and try it out next weekend (this week is my last week of the quarter, I have a lot of tests :( ).

EDIT: The biggest problem is my wireless internet. To get my wireless adaptor to work, I had to get it setup with ndiswrapper. Unfortunately, I didn't know how to set it up and while I was in ubuntu I couldn't check for help online because it wouldn't connect to the internet.

Also, I have an AMD athlon 64 3200+ processor. I am currently running on the regular x86 version, should I switch to the 64-bit version? What are the advantages/disadvantages?

Thanks!

networking can be a headache in linux if you start from windows. however, as you learn more about linux, you'll notice networking is actually more clear in linux. but you have to learn first... 
on my laptop i installed dual boot with windows (i need that sometimes) and getting my wifi to work was much easier in linux :-D 


for an amd64 i'd advice you to install the 386 version and then move to the k7 kernel (for 32 bit amd).

---

### Post by willy1234x1 on 2006-10-29
wizzard is right I have an amd64 but I use the I386 there are more programs made for that then the amd64 version but I may have had a different experience than him since I think I've actually learned more about linux using ubuntu it's easy but it can go really in depth as well

---

