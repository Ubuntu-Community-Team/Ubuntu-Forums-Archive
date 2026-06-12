---
title: "Just downloaded Ubuntu 7.10 &amp; now have a black screen"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by D.K. on 2007-10-27
Hi,

I have no picture on my monitor but there is a message saying "44KHz/55Hz Out of Range".
I presume the resolution has changed...the sort of thing I may have sorted on "Safe Mode" with Windows but I haven't a clue how to do it with Ubuntu.
Could someone please help?

Thanks,
D.

---

### Post by ed-koala on 2007-10-27
You probably need to edit your xorg.conf file.  Here is a guide you can follow to see what to do - [http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by llamakc on 2007-10-27
Press the keys ctrl-alt-F2. You'll be at a login prompt. Login as your user and type:

```

sudo dpkg-reconfigure xserver-xorg

```

Also, what sort of video card do you have? If you have an NVidia choose the "nv" driver during that reconfigure prompt, "radeon" if you have ATI. Then after that is done, type:

```

sudo /etc/init.d/gdm restart

```

Post any errors or issues back here.

---

### Post by sad_iq on 2007-10-27
Is this before the install or after?? If it's before there is a VGA (F4 I think) option when you boot, choose one that you're monitor supports. If it's after you can google the specs of your monitor theb when you boot and get to that error press Alt+Ctrl+F1 to login to a command line then do this: ```
sudo /etc/init.d/gdm stop
 sudo nano /etc/X11/Xorg.conf
``` then find the Section "Monitor" line and replace the refresh rates there are with the ones you googled. Press Ctrl+x when finished to save and folow the instructions!!!
 Here is my section "Monitor" as reference: 

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

---

### Post by D.K. on 2007-10-27
Many thanks ed-koala but I don't get a login prompt...just nothing after it has booted

---

### Post by llamakc on 2007-10-27
YOU have to make it go to the login prompt.

Press CTRL-ALT-F2 and login.

---

### Post by D.K. on 2007-10-27
> **llamakc said:**
> Press the keys ctrl-alt-F2. You'll be at a login prompt. Login as your user and type:

```

sudo dpkg-reconfigure xserver-xorg

```

Also, what sort of video card do you have? If you have an NVidia choose the "nv" driver during that reconfigure prompt, "radeon" if you have ATI. Then after that is done, type:

```

sudo /etc/init.d/gdm restart

```

Post any errors or issues back here.


 Llamakc...Just tried your advice and everything now appears to work..thank you very much and thanks also to everyone else for being so prompt and helpful.

D.

---

