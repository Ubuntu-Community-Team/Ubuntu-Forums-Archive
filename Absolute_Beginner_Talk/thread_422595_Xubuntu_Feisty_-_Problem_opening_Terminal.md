---
title: "Xubuntu Feisty - Problem opening Terminal"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-04-25
Hi

I have done a clean install of Xubuntu 7.04 and encountered a problem.
Whenever I try to open Terminal, the screen blacks out and the system throws me out - back to login screen!

Anyone else had this problem?
Suggested fixes?

Thanks

KiwiPete

---

### Post by Minker17 on 2007-04-25
This is happening to me as well.

---

### Post by KiwiPete on 2007-04-27
Has anyone else got ideas about this???

Because I cannot get into Terminal I cannot use sudo to get root access and change Xorg.conf or do any command line stuff.

Really need some help with this.

Kiwi Pete

---

### Post by johnny4north on 2007-04-27
i believe there is a bug with with one of intels chipsets causing this type if error.  i have not located the bug yet.   i came across it a few days ago.  i will repost here when i find it again.

---

### Post by silverdulcet on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/99927](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/99927) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I believe the bug is this one. I am having similar iissues with an i810 chipset. I have reconfigured Xorg a couple times and either it restarts the Xsession or it totally locks up the Xserver altogether. I can ssh into the machine from another one but the local screen totally locks up.

---

### Post by KiwiPete on 2007-04-27
The problem does seem to be to do with the Intel 810 chipset driver.
I have discovered that using the gnome-terminal is fine - just the kdc one crashes the system.
Also, if I edit the /etc/X11/xorg.conf file and change the video card driver from <i810> to <vesa> then the problem with Terminal crashing the system is fixed - but the screen display is very chunky low resolution.

So for now I am back to using the i810 driver in xorg, and avoiding the kdc Terminal.
But it would be nice if there is a fix for the driver problem.

KiwiPete

---

### Post by Fraser67 on 2007-04-27
I have this problem with Xubuntu 7.04 installed on an old  Dell Latitude CPt. This is my first dealing with Linux so this is some what frustrating.Forgive me if this is a daftr question but..

How do you open the gnome-terminal in the first place on a Xubuntu installation?

---

### Post by silverdulcet on 2007-04-27
Actually unless you already have a full Gnome install alongside your Xubuntu window manager your better off just using xterm until the bug is resolved.

```
xterm
```

Its already installed. gnome-terminal requires 226mb of additional packages to run on Xubuntu. Its probably much more overhead then you want.

---

### Post by Fraser67 on 2007-04-27
So how do you run xterm (if you can't open a terminal window in the first place?

---

### Post by silverdulcet on 2007-04-27
Press Alt-F2, type xterm, press enter.

You can also add a terminal panel button if you like. Right-click on your top panel. Choose Launcher. Type the name of it (Terminal or Xterm) and a description if you like. The Name and Description is just what appears upon mouse-over. Choose an icon and then type in the Command box "xterm". (without quotes) You are also able to move your new launcher wherever you like by Right-clicking it and selecting Move.

Editing the Xubuntu startmenu is a little trickier but if you search for some howto's you can also add to or edit the startmenu to run xterm instead. If later you want to switch it back to the xfce terminal the command is "xfce4-terminal".

Hope this helps.

---

### Post by Fraser67 on 2007-04-27
Thats great. Thanks for all the replies.

---

### Post by silverdulcet on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It seems that if you edit your xorg.conf file and change the DefaultDepth to 16 the problem of xfce4-terminal locking up or kicking you out to the login screen goes away. I've tested it myself and it works for my machine.

---

### Post by KiwiPete on 2007-05-01
Thanks Silverducet for that tip about changing Default Depth from 24 to 16 in xorg.conf.
It worked for me!

My only question is is this a proper fix or just a workaround for a bug that may have other negative effects down the track?

KiwiPete

---

### Post by silverdulcet on 2007-05-01
My advice is to keep a watch on the launchpad bug I linked above. For now its just a work-around since the bug seems to have something to do with having your display set to 24 bit color. When they do resolve that bug then you are free to change the DefaultDepth back to 24. The only negative is that until it is fixed you can't run your display with 24 bit color and use xfce4-terminal. You either use a different terminal or set your color depth to 16 bit. 

Credit goes to [https://launchpad.net/~theforkofjustice/]("https://launchpad.net/~theforkofjustice/") for finding the work-around.

---

