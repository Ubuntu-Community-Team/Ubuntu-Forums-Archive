---
title: "What happened to my x-server!?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-06-18
Hi,

I didn't start ubuntu for a couple weeks since I was mainly working on university stuff (on word). Now I wanted to go back to ubuntu again to work on my website stuff (which I have in ubuntu). But When I start it, it says that the x-server can't start because of some problem. But I didn't change anything.

How can I get it right again??

---

### Post by Jimmyfj on 2007-06-18
> **kramer65 said:**
> Hi,

I didn't start ubuntu for a couple weeks since I was mainly working on university stuff (on word). Now I wanted to go back to ubuntu again to work on my website stuff (which I have in ubuntu). But When I start it, it says that the x-sevrer can't start because of some problem. But I didn't change anything.

How can I get it right again??

dpkg-reconfigure xserver-xorg

---

### Post by Crafty Kisses on 2007-06-18
> **kramer65 said:**
> Hi,

I didn't start ubuntu for a couple weeks since I was mainly working on university stuff (on word). Now I wanted to go back to ubuntu again to work on my website stuff (which I have in ubuntu). But When I start it, it says that the x-sevrer can't start because of some problem. But I didn't change anything.

How can I get it right again??

First reconfigure your X server, you can do this by entering the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

Then after you get back into Ubuntu you should back the current X server file up, you can do this by entering the following command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

You also can then recover this X server backup if anything goes wrong, you can do this by entering the following command:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Hope this helps. :p

---

### Post by kramer65 on 2007-06-18
thanks for the tips. I have a slight problem though. I never get to any command line. It just says:

Timidity is not yet configured
Enable alsa sequencer first by editing /etc/default/timidity.

And then only black. I can type something, but it doesn't do anything when hitting enter, only showing another black line.

Any ideas..?

---

### Post by kramer65 on 2007-06-18
Nobody knows??

---

### Post by speirint on 2007-08-18
I just now got the same problem when I was trying to restart my computer to select a different kernal after already being taken to the gdm.  I however, have been using this computer under ubuntu consistently for quite some time now (several months).

  Try running ubuntu off of a different (older) kernal until we figure it out.  I'm completely new to ubuntu, so I'm still trying to figure out how to edit anything with /etc ...

Here's what I got:
A list of things are being checked-the last two lines say:
Checking battery        [OK]
Running local boot scripts (/etc/rc.local)           [OK]
Timidity is not yet configured.            [OK]
Enable Alsa Sequencer first by editing /etc/default/timidity.

By the way, have you been having any problems with sound on your system?  I've been trying to get alsa to work for a while and having seen this makes me think that it may have something to do with why I'm hearing sound sporadically if at all.  I'm also using Fiesty Fawn 7.04 as well.

---

### Post by DM was on fire! on 2007-08-18
XD
I didn't even have to ask. I was installing my ATI drivers and when I rebooted, I got the blue screen of death from xserver.
I think I'll try this stuff, though. Thanks! :o

---

### Post by slimdog360 on 2007-08-18
at boot go the safe mode or what ever its called option. That will get you to a command line.

---

### Post by DM was on fire! on 2007-08-18
> **slimdog360 said:**
> at boot go the safe mode or what ever its called option. That will get you to a command line.

Recovery mode, I believe? 
Since GDM is disabled when booting up without x-server, it gives you a command line there.

Unfortunately, I'm a #$%#%# idiot who doesn't know all that stuff, so I'm going to have to have Ubuntu reinstalled.
That's what I get for messing around with something I shouldn't. Unfortunately, I don't remember if I backed up x-server or not.

...I think I'm gonna go see. D:

EDIT - Noes. D:

---

### Post by speirint on 2007-08-18
I believe you can make the selection during the boot up before it ever tries to get to the gdm-am I correct?  The gdm is the login screen where the drum strike sound effect (assuming your sound works) plays?  If so, then you can select the version by kernal and safe mode.

---

