---
title: "Installing stuff..."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by Miakehl on 2006-03-04
Since I have yet to get my modem working, I have (actually am as I type) downloaded Mplayer and XMMS. XMMS is a .tar.gz file and Mplayer is a .deb file. I have absolutley no idea on how to install these. If anyone has instruction or links on how to install, it would be greatly appreciated.

Thnx,
_Mia

---

### Post by WackToMack on 2006-03-04
To install the Mplayer .deb, go to Applications>Accessories>Terminal.  Be sure to put the Mplayer .deb in the Home folder.  Now, in the terminal type :

```
sudo dpkg -i (filename).deb
```

(Don't use the parenthesis when typing the command.)

I'm not sure how to install the other one because I'm a noob too. Good Luck. :D

---

### Post by engla on 2006-03-04
What you should know is that while that way of installing those packages perfectly works (the .deb is easier than the .tgz is a hint), it's far from the easiest way to do it.

The preferred/easiest way is this:
Launch Synaptic!
System > Administration > Synaptic Package Manager.
Here you can search for packages and mark for install .. these will be downloaded from the net and all those listed are specifically prepared for ubuntu and just works.
You are so lucky so both mplayer and xmms are available in synaptic
(And the tip is; if something is available in synaptic, use that, it's easier and more likely to work (rather, synaptic-installed software work 98% of the time))

---

### Post by Sef on 2006-03-04
> Mplayer and XMMS

For those programs just do this:  Applications ---> Add Applications ----> Enter Password ------> Click on Sound and Video  -----> click on more programs ----> click on the programs you want and click on apply.....follow the directions and they will install automatically.

---

### Post by Qrk on 2006-03-04
Be sure to add the extra repositories...

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by aysiu on 2006-03-04
I think some people missed the beginning of the post: [QUOTE=Miakehl]Since I have yet to get my modem working[/QUOTE]

---

