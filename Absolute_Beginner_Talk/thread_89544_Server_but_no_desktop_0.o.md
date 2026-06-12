---
title: "Server but no desktop? 0.o"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by dwalker on 2005-11-12
I must say, I do have an odd problem. I've had Ubuntu for a couple months now, but didn't have a server/PC I wanted to use it on until a few days ago. I tried installingit, but it wouldn't install. Not even the Live CD (And I know what's supposed to happen, as I've used the Live CD on this PC before). 

It's 5.04. I've been able to install Server mode, but that's it. Right around the time of installing it, the screen goes black and it looks as if it shuts off. I've tried moving my mouse and hitting keys, but nothing works. The only way to get a response from it is to just hit the power button, but of course that shuts it down. I know Ubuntu is a nice, simple OS, and I'd really like a chance to actually use it. Does anyone know what could be causing this? I've asked friends online who use it, and they're baffled. As far as I know, the hardware meets all the necessary specs. The only thing that ever gets a [[COLOR="Red"]Fail[/COLOR]] during installation is a network card, because I don't have it hooked up to anything yet.

Any help would be more than appreciated. :)

---

### Post by grim918 on 2005-11-12
that is strange the only thing that i can think of is that something went wrong with the cd. if thats the case you should just get another copy by downloading it or requesting to get one by mail. another thing that might be the problem is to check your cd-rom. if its going bad and you have been having problems with it then that could be a problem. you should try  to run the live distro on another computer. if it boots up then you might be having a hardware problem with your box. if it doesnt boot up then its most likely a faulty disc and should be replaced. i hope this info can help you out. i am also new to ubuntu and linux for that matter

---

### Post by dwalker on 2005-11-12
I have a total of 10 x86 discs. Tried a couple. I seriously doubt it's my CD-ROM drive, as I've said that Ubuntu boots/installs fine in Server mode. So it's obviously running. And it ran XP Pro, as well.

I've used the Live CD on another PC. If it keeps failing, I suppose I'll just try all of the disks until I go crazy and throw the PC/server out of my second-story room. :P No resolve, but it'll temporarily make me feel better.

---

### Post by grim918 on 2005-11-12
im sorry but i dont know what could be causing the problem. that is a strange situation.

---

### Post by jasay on 2005-11-12
If you can boot and log in in server mode you ought to be able to install everything else from the cd or online repos using apt. You may have to enable universe and multiverse repos first.  The first part of [this link]("http://www.ubuntuforums.org/showthread.php?t=75971&highlight=server+desktop") will show you how to edit the sources.list file using the command line.  Then install ubuntu-desktop instead of xubuntu.```
sudo apt-get install ubuntu-desktop
```  I think that's all you need to do to turn a server into a desktop, but I've never actually tried, so I'm not sure.

---

### Post by Kapre on 2005-11-12
dwalker - I would say that it is the CD. If you can download a new ISO and burn it on a  slower speed (4x), you can try installing from it. You can also try Jasay's approach (after logging in terminal type the command he specified above). 

K

---

### Post by dwalker on 2005-11-13
Tried both methods. Got the same result... nothing. I guess you really do get what you pay for.

---

