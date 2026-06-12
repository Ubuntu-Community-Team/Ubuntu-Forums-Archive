---
title: "Desklets not installing"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by redtag on 2007-11-21
Anybody else having a problem installing gDesklets?

I've gone into terminal and typed in sudo apt-get install gdesklets and I get this error:
E: Couldn't find package gdesklets

I've tried this too:
System>Administration>Synaptic Package Manager> Search for and install gDesklets.

and nothing shows up.

I've tried installing screenlets as well and no luck.  I've been searching all over google and ubuntu forums and every tutorial that I find leads me no where.

Does anybody have any ideas to what the problem could be?

I'm running ubuntu 7.10

Thanks ahead for any and all help!

---

### Post by TidusBlade on 2007-11-21
I am not exactly sure the problem is, but could it be that you have no repos installed or something? Because I am perfectly sure I saw gdesklets on the Gutsy Add/Remove programs...

---

### Post by redtag on 2007-11-21
Do you know where I can find more information about repos?

Thanks!

---

### Post by stchman on 2007-11-21
> **redtag said:**
> Anybody else having a problem installing gDesklets?

I've gone into terminal and typed in sudo apt-get install gdesklets and I get this error:
E: Couldn't find package gdesklets

I've tried this too:
System>Administration>Synaptic Package Manager> Search for and install gDesklets.

and nothing shows up.

I've tried installing screenlets as well and no luck.  I've been searching all over google and ubuntu forums and every tutorial that I find leads me no where.

Does anybody have any ideas to what the problem could be?

I'm running ubuntu 7.10

Thanks ahead for any and all help!

The package gdesklets is in the universe repository for Edgy, Feisty, and Gutsy.

Make sure to have you have the main, universe, multiverse, and restricted repositories enabled.  

You can enable these by going to System--->Administration---> Software Sources and checking all the boxes under the Ubuntu Software tab.

Now since you are a beginner I have to ask a silly question.  When you are trying to install packages is your PC hooked up to the internet?

Do the following then in a terminal:

```

sudo apt-get update
sudo apt-get -y install gdesklets
```

Hope this helps.

---

### Post by redtag on 2007-11-21
Thanks!

That worked great!

---

### Post by redtag on 2007-11-23
Any idea where to find a desklet that looks like 
[http://www.prashanthellina.com/images/awn_dock.png](http://www.prashanthellina.com/images/awn_dock.png)

?

---

### Post by westyonfire on 2008-01-05
hi, I'm a linux beginner but I know the link you posted isnt a desklet. its called avant windows navigator.

---

### Post by fmartinez on 2008-01-05
> **redtag said:**
> Any idea where to find a desklet that looks like 
[http://www.prashanthellina.com/images/awn_dock.png](http://www.prashanthellina.com/images/awn_dock.png)

?

I found a lot of great themes here for: AWN, Icons, backgrounds, compiz, etc.... 
[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

