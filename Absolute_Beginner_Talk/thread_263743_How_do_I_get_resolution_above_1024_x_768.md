---
title: "How do I get resolution above 1024 x 768"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by EmmDoubleEw on 2006-09-23
I have an ATI card, how do I change my resolution beyond the Gnome and KDE restrictions?

---

### Post by haxer on 2006-09-23
system - settings then screen resolution ?

---

### Post by bulldog on 2006-09-23
First install the drivers for your ATI-card.

Then look in your /etc/X11/xorg.conf  if the desired resolution is present.
If so set it to default with dept 24 if possible.

You can't choose a resolution which not is in your xorg.conf.

---

### Post by EmmDoubleEw on 2006-09-23
> **bulldog said:**
> First install the drivers for your ATI-card.

Then look in your /etc/X11/xorg.conf  if the desired resolution is present.
If so set it to default with dept 24 if possible.

You can't choose a resolution which not is in your xorg.conf.

It doesn't go above 1024 x 768 in the xorg.conf, so I can't change it? That's ridiculous, I thought Linux was famous for being customizable, yet I can't even get my monitor's native widescreen resolution? :confused:

---

### Post by jd65pl on 2006-09-23
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Have a go at adjusting your monitors resolution with that command.

J

---

### Post by alienexplorers on 2006-09-23
when I use this command (sudo dpkg-reconfigure -phigh xserver-xorg) on my old ATI All In Wonder 7200 I am unable to boot into X. I must manually reconfigure xorg.conf to get it to boot correctly.  Then I must add ModeLine commands for each video mode I want to use.

---

### Post by shakumafu on 2006-09-23
> **EmmDoubleEw said:**
> It doesn't go above 1024 x 768 in the xorg.conf, so I can't change it? That's ridiculous, I thought Linux was famous for being customizable, yet I can't even get my monitor's native widescreen resolution? :confused:

you have to install the driver first. the vesa driver can only go so far. once you install the driver, you can add higher resolutions

---

### Post by lonce on 2006-09-23
all you do, is look at how your xorg.conf file is setup and add a line with the resolution you want to use to it.  make it look like the other lines that show resolution.  Save it.  Restart and it will add that option to your resolution menu.  Thats how I did it and it worked like a charm. Very easy.

---

### Post by arkangel on 2006-09-23
with ati cards  you have to install the driver [first]("ati.com/support/driver.html") as  shakumafu  said 
then edit your xorg.conf

there is a nice [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") 
I recommend method 2

---

### Post by EmmDoubleEw on 2006-09-24
Thanks for all the replies guys.

I actually did install the drivers and it didn't do anything, and actually the instructions on the ATI website aren't consistent with what's happening on my computer. (it asks me to modify files that don't exist) I thought it had something to do with it only supposed to work on redhat and SUSE.

I'll give it all a try again.

---

### Post by arkangel on 2006-09-24
maybe your problem is simpler to solve , coudl you post  which ati card you have and on which  computer 

in a console type 
#fglrxinfo
and post your output

---

