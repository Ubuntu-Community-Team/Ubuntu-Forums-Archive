---
title: "Suggestions for an email only OS?"
date: 2012-12-31
forum: Any Other OS
---

### Post by MasterRolfe on 2012-12-31
I'm trying to setup a computer for my Gran, who as you might guess, is not very tech savvy.  She struggles to send text messages from her Nokia 3330.

I've got an AcerAspire One, which  I no longer use this netbook, so I want to format it and install an OS that can only do the very basics.

All my Gran used her old computer (now broken) for was email.  I would like to setup a very simple to use OS that can do little more than email.

Ideally, if I could get the netbook to boot straight into an email client, and setup a connection to her dial-up Internet, that would be best.  The less extras the better.

If you know of anything out there that fulfils those specs, or something close, please let me know.

Thanks!

---

### Post by mamamia88 on 2012-12-31
> **MasterRolfe said:**
> I'm trying to setup a computer for my Gran, who as you might guess, is not very tech savvy.  She struggles to send text messages from her Nokia 3330.

I've got an AcerAspire One, which  I no longer use this netbook, so I want to format it and install an OS that can only do the very basics.

All my Gran used her old computer (now broken) for was email.  I would like to setup a very simple to use OS that can do little more than email.

Ideally, if I could get the netbook to boot straight into an email client, and setup a connection to her dial-up Internet, that would be best.  The less extras the better.

If you know of anything out there that fulfils those specs, or something close, please let me know.

Thanks! Literally Any OS. I'd probably give her xubuntu and then put Icons on the desktop and rename them to what the task is.  For example rename thunderbird to email.    Then take menulibre or any other menu editor and remove anything that she'll never use from the menu.  There you go a grandma proof os.  Maybe use debian stable for her with xfce instead since you won't have to deal with as many possible bugs. Also you can add thunderbird to the startup apps really easily

---

### Post by ibjsb4 on 2012-12-31
Check out Puppy Linux

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by handsheldhigh on 2012-12-31
Have you considered Chrome or Chromium OS? You can get premade builds from  chromeos.hexxeh.net or build one yourself from chromium.org/chromium-os.

---

### Post by lykwydchykyn on 2012-12-31
Is it webmail or POP3?

You could just do openbox and have it launch email from the autostart script, or actually build a custom environment in the .xsession script so that the session actually logs out when the email client is closed.

But you're probably best off sticking with a conventional desktop interface with a big "email" icon.  You never know if she might want to do some other things on it.  

I'll second the recommendation for xubuntu (LTS) or debian stable with XFCE.  I've set this up for non-computer-savvy folks with great success.  You could also try LXDE and maybe use the lxlauncher, which is a full-screen tabbed launcher like on the original eeePC.

If you want to build a really simple interface, I have a project called [KiLauncher](http://github.com/alandmoore/KiLauncher) which is a configurable full-screen launcher meant for Kiosks.  I use it as an interface on a laptop for my two youngest boys and it works quite well.  Big buttons, no fuss.

---

### Post by UltimateCat on 2012-12-31
Hi! [MasterRolfe]("http://ubuntuforums.org/member.php?u=1771309"):

I have been using Debian 6.5.0 Squeeze Stable for about 7 months now and have had zero problems.

I recommend Debian because it runs very smooth and is a stable distribution. 
[http://www.debian.org/](http://www.debian.org/)

[http://www.debian.org/CD/](http://www.debian.org/CD/)

With Debian you would use 'su' to execute updates, upgrades and etc.

I'd stay away from Fedora because it has to be re-installed every 3-6 months or
'pre-upgraded' ....

Puppy is very nice; I heard; from an old Linux friend of mine ;)

Best Regards

---

### Post by mips on 2013-01-02
I would go Debian + xfce and just add the email client to the startup apps.

---

### Post by fdrake on 2013-01-02
Linux Mint

---

### Post by MasterRolfe on 2013-01-02
Thanks!  I'll check these options out!

---

### Post by s1wood on 2013-01-04
Look at Eldy - specifically designed for the older user. Installs on top of existing system.

Susan

---

### Post by ugm6hr on 2013-01-05
> **s1wood said:**
> Look at Eldy - specifically designed for the older user. Installs on top of existing system.

Susan

I have never tried it, but I have seen it on the BBC.
It sounds perfect for your needs. The email client is very basic though.
[http://www.eldy.eu/video-tour/](http://www.eldy.eu/video-tour/)

---

