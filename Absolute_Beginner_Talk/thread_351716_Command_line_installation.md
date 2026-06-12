---
title: "Command line installation"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by amar2d4 on 2007-02-02
How do i make a command line installation of Ubuntu 6.06?

I don't get a X-windows option to install.I get only a command line.It seems I have problems with X-windows version.

:guitar:

---

### Post by mikewhatever on 2007-02-02
I am not sure, but do you mean text mode installation? If so, you can try choosing safe graphic with LiveCD, or downloading Alternate install CD. Hope it helps.

---

### Post by amar2d4 on 2007-02-02
> **mikewhatever said:**
> I am not sure, but do you mean text mode installation? If so, you can try choosing safe graphic with LiveCD, or downloading Alternate install CD. Hope it helps.

Tried safe graphics mode.

How do I do a text mode installation?

---

### Post by L14UX_1NS1D3 on 2007-02-02
ya I had the same problem with the 6.10 cd.
You might have a defective cd, jsut burn another one and see what happens. 
best of luck ! :wink:

---

### Post by amar2d4 on 2007-02-02
> **L14UX_1NS1D3 said:**
> ya I had the same problem with the 6.10 cd.
You might have a defective cd, jsut burn another one and see what happens. 
best of luck ! :wink:

I got this CD from UBUNTU.org.Does that add any credibility.:)

---

### Post by guysmiley25 on 2007-02-02
What you need is the server install CD. Instead of the Live CD.

```
ubuntu-6.10-server-i386.iso
```

not

```
ubuntu-6.10-desktop-i386.iso
```

---

### Post by guysmiley25 on 2007-02-02
You may want:

```
ubuntu-6.10-alternate-i386.iso
```

Boot that and select a command line system.



```
ubuntu-6.10-server-i386.iso
```

Lets you install a LAMP server.

---

### Post by lamego on 2007-02-02
Do you mean you did a standard install and didn't get the graphical login ?
That means you need to configure the xserver.
Login and then type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by raul_ on 2007-02-02
The server install wll install.....a server!

Just download the alternate install CD. If you choose to install the server you won't get many applications and you won't have a graphical environment...

---

### Post by steve.horsley on 2007-02-02
The "Alternate" inataller is the one you want. This is a full-featured installer (more options than the graphical installer, and more reliable). Although it's text mode, it's not really command line. It's like the old windows OS/2 installers. Use up/down arrows to select from lists, and enter to select. 

You don't want the server installer. It is assumed that servers are not desktops, and it doesn't install a GUI. That would leave you feeling rather strained, I imagine.

---

### Post by amar2d4 on 2007-02-02
Initially when trying to boot from Cd after selecting language as english my screen gets frozen.

I try starting ZUbuntu in safe graphics mode.It gets frozen again in when trying to detect my SATA drive.
I get the following material from the forum,
---------------------------------------------------------------------------------------------------------
At last, I can install Ubuntu in my PC and make it dual boot.
Thanx a lot guys, for helping me out. Very much appreciate

Let me explain what I did
1st I try put acpi=force irqpoll parameter at the end of the line like mr.wizrd told me.
But nothing happen still Ubuntu can't detect my SATA drive

Then I read thread [http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230) that mr.wizrd gave me and wallaa. I figure out that it work when I put the acpi=force irqpoll parameter in between 2nd and 3rd parameter of the line. After that both of my SATA drive appear.

I'm very happy with it.
Thanx again, if not maybe I'm not one of the Ubuntu user
--------------------------------------------------------------------------------------------------------

Now i get into command line mode,but, not into X-windows mode.

When trying to look for errors.

It says X-window system version 7.0.0.

X protocol version 11, revision 0, and release 7.0


I get a box which says start when configured properly and back to commandline mode.


The machine is a GX520 ,533MZ celeron,256 MB RAM,30 Gb HDD machine contributed by my company towards my Lab work.

Thats the whole story.please,suggest.

---

### Post by benson444 on 2007-02-02
So you've installed the OS but the graphics system won't start? Now try the command:

sudo dpkg-reconfigure xserver-xorg

Choose the default settings for everything except graphics drivers and resolutions. For graphics choose "vesa" from the list. Then choose whatever resolutions you want using the space bar. Hit tab when ready to continue. When back at the command enter:

startx

Hope it works.

---

