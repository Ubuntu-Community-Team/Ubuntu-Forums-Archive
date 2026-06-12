---
title: "Failed to start the X server. HELP PLEASE"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by fulio on 2007-08-06
when i boot up my laptop it says "Failed to start the X server (your graphical interface). then it asks yes or no. what do i do?? somone please help me, im new to this.

---

### Post by Ek0nomik on 2007-08-06
The yes or no is simply asking if you want to view the error report.

It's more than likely a problem with your video card and the drivers to support it.

If you hit No, can you get back to the command line screen?  Are you able to log in or type out commands?  If it seems frozen, try hitting 'Control + Alt + F1', it may allow you to login to your system.

Do you know what kind of video card you have?

If not (and you are able to get to a command prompt), run this command and post the output:

```
lspci
```

---

### Post by fulio on 2007-08-06
yes im able to  go to the command line screen. and im able to longin.
i have a Nvidia geforce 6150. i also typed in lspci but how do i copy all that command and show it?and also i have been having this problem "bcm43xx_microcode5.fw" not available or load failed

---

### Post by Ek0nomik on 2007-08-06
> **fulio said:**
> yes im able to  go to the command line screen. and im able to longin.
i have a Nvidia geforce 6150. i also typed in lspci but how do i copy all that command and show it?and also i have been having this problem "bcm43xx_microcode5.fw" not available or load failed

As long as you know the video card model you should be fine.

Try running this at the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

Select 'nv' as your video card, and just keep hitting 'Ok' to the rest of the stuff.  It will ask you a lot of questions and want to auto detect a lot as well.  Just let the reconfigure do its thing.

You can use tab to move around items, enter to select.  This should hopefully allow you to at least boot into Ubuntu graphically and then allow you to install better drivers so it won't be as sluggish.

Let me know how it works.

---

### Post by fulio on 2007-08-06
yea i have done that now. Now its freezing up on my during the boot.
also it freezes up in recovery mode. any help agn.

---

### Post by Ek0nomik on 2007-08-07
> **fulio said:**
> yea i have done that now. Now its freezing up on my during the boot.
also it freezes up in recovery mode. any help agn.

You really need to be a little more specific.  Where in the loading process are you "freezing"?  Are you getting any errors?  If so, what exactly do they say?

---

