---
title: "Failed to start X Server - have blue screen and no GDM in Feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-04-20
Hi.

I've been using Edgy since it came out with no problems. I upgraded to Feisty with no problems. 

**_On the first run of Feisty everything worked_**, then I got a update message about driver notification. I ticked the Ati box to enable it then restarted.

Now I have on reboot a blue screen with the message:

Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem.

When I click 'No' it takes me to a text base command line, so I can type things.

If I click 'Yes' I get the message:

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.23

then other bumf ending with: Using config file: "/etc/X11/xorg.conf"

So I have no GDM.

Is there anyway to roll back this ATI driver update I did, as Feisty was working fine before I stupidly tried to upgrade the driver.

Thank you.

Tweed.

---

### Post by freebird54 on 2007-04-20
There are a couple of ways.  First question - did you make a backup of the xorg.conf before beginning?  If not then do this

```
sudo dpkg-reconfigure xserver-xorg
```

You may find it helpful to follow along with this guide:

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

as you do it.  Return your video deiver choice to ATI  - and if that doesn't work then choose vesa the next time :)  Should get you in, then we try a slower approach for the upgrade in drivers...

---

### Post by Mizled on 2007-04-20
Mostly the ATI driver you installed borked your Xorg.conf file. I would suggest running the command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you get to the driver portion check the "VESA" driver and that will get you the default config which will get Gnome to boot but you will have no Graphics driver acceleration. Hope this helps.

---

### Post by Tweedicus on 2007-04-20
Phew. Thank you.

I typed in that command. Then followed the autodect settings all the way through, and it's all working again.

I don't know why I chose to upgrade the the ATI chipset when I'm running an S3 Super Savage card.
Curiosity killed the cat I guess.

Thanks once again.

Tweed

---

### Post by freebird54 on 2007-04-20
Nah - that's barely a flesh wound this time :)  Glad you got going again...

---

