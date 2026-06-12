---
title: "firefox problem"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by marks321 on 2007-07-08
Firefox crashes going back to start up scripts and asking for password again when i go to radiotimes website and press the whats on now button this also happens with other web sites. Is there a known bug between UBUNTU and FIREFOX ?

---

### Post by starcraft.man on 2007-07-08
> **marks321 said:**
> Firefox crashes going back to start up scripts and asking for password again when i go to radiotimes website and press the whats on now button this also happens with other web sites. Is there a known bug between UBUNTU and FIREFOX ?

Works fine for me. I just looked around the site.[ You mean this one?]("http://www.radiotimes.com/ListingsServlet?event=13&broadcastType=2&jspGridLocation=/jsp/radio_listings_grid.jsp&jspListLocation=/jsp/radio_listings_single.jsp&jspError=/jsp/error.jsp")

It's got some flash on it, did you install flash for firefox? If not, open a terminal (after closing firefox) and put this in please.

```
sudo aptitude install flashplugin-nonfree
```

Short of missing flash, I don't see another reason for it to crash.

---

### Post by greg_g on 2007-07-08
Some more information (and punctuation) might be helpful.

I just went to radiotimes.com and clicked on the "now" link under both TV and Radio.  It did what it was supposed to do and nothing more.

What version of Ubuntu are you running?  What extensions do you have installed with Firefox?  What other sites do this (specificially)?

When this happens does it completely reboot the computer (you see the BIOS startup screen) or just the desktop (it only goes back to the Gnome login screen)?

Lets figure this out,

greg

---

### Post by kiolb on 2007-08-02
Hello.

Same problem. Flash is installed, as I can view. eg [www.formula1.com](www.formula1.com). 
It goes back to command screen, as if loading modules, but login prompt comes back to quickly for me to see what is happening. This happend twice now. The second time, only firefox closed. I was browsing [www.prophecy.co.za](www.prophecy.co.za) both times. This has also happend randomly on other sites. (cannot remeber which). Running 2.0.0.6 with Blue Ice 1.2.4 theme.

I tried "sudo aptitude install flashplugin-nonfree", which did install. But I could view flash content before this ???????.

Unless flash needs to be installed after each update of firefox!!!!!

Any ideas.
Thanks.

---

### Post by daktari on 2007-08-02
This could help some, and might confuse others, but some of the same ground has been covered in a very recent thread:

[http://ubuntuforums.org/showthread.php?t=504284&highlight=firefox+update](http://ubuntuforums.org/showthread.php?t=504284&highlight=firefox+update)

---

