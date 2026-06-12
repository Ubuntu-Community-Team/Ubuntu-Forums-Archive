---
title: "Screen quality"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by marcos33br on 2007-04-16
Hi there

I have decided to gradually get rid of windows OS and installed Ubuntu in my computer. Things are going fairly well so far, but I would like to have a better screen resolution. Although Ubuntu allows me to have a screen resolution of 1024x768, the quality of the image is much poorer than windows. My graphic card is a intel 82852/82855 GM/GME and I had a look at intel website and they say there is specific drivers for Linux (does not specify which ones though). I tried to "upgrade" using the repository thing they give and I also downloaded the package for the drivers but I am still not very used to the package thing Linux uses for installing things, I am also unsure if that would solve my problem or bring others. How do I get my screen in the same level I have with windows? is it possible?
Any help appreciated, thanks

---

### Post by freebird54 on 2007-04-16
To know what the problem is I guess we would need to know in what way 'quality' is defined in this instance.  Are the fonts less clear?  Are things fuzzy?  Are the icons just too big?  Most visuals on a Linux system are very configurable - which means of course that they can be further from what you want/expect than on a system with few choices...

We'll be glad to help when we know what to help with!

Welcome to Ubuntu.

---

### Post by marcos33br on 2007-04-16
It is mostly fuzzy, just as an example, I opened the same website in windows and linux and the windows one was much clearer and easy to see. I tried to make the letter bigger with linux (mozilla, view, text size, increase) but it didn't help, it just got the words disorganized.
Thanks for your help

---

### Post by Feba on 2007-04-16
Could you take a screenshot for us? Just press Print Screen ( PRT SCR) on your keyboard, and it should automatically bring up the program. Then just upload it to imageshack.us or the like.

Also, [http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/) might be of help.

---

### Post by Rinzwind on 2007-04-16
> **marcos33br said:**
> It is mostly fuzzy, just as an example, I opened the same website in windows and linux and the windows one was much clearer and easy to see. I tried to make the letter bigger with linux (mozilla, view, text size, increase) but it didn't help, it just got the words disorganized.
Thanks for your help

Could you try to find out what font is used in each environment? 
Maybe all you need are the msttcorefonts. 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts)

---

### Post by freebird54 on 2007-04-16
Can you point me to the website?  It sounds vry strange behaviour indeed - unless the particular website is 'optimized' for IE and that is what you used on Windows.

I find them equally sharp on my system - in fact it is a little painfui to go back to the Windows look now (which doesn't help your problem at all, I realize).

One thing you could do, for general information to work from, is to open an Applications->Accessories->Terminal and enter this code into it:

```
cat /etc/X11/xorg.conf
```

This will dump a file into your terminal.  If you highlight it, and paste it into your reply, it will tell us a fair bit about how your graphics are set up.  BTW, once it is on your reply, highlight it and press the # in the command bar above you to put it in a box!  Also - there is no reason not to paste the command I gave you in to the terminal window either- you don't have to type it in!

EDIT:  Yes - the fonts are a likely possibility.  Forgot they aren't in by default!

---

### Post by marcos33br on 2007-04-16
Thanks for all your help, I though that maybe there would be a quicker solution for it, I am at work right now, so will have to try all proposed solutions after work.
Thanks

---

### Post by freebird54 on 2007-04-16
Start with the fonts - and maybe the screenshot or website.  Good likelihood there.

Good luck!

---

### Post by marcos33br on 2007-04-16
I tried the fonts, not sure if I did everything I could, but it did not help? should I restart the system?
I will try the screenshot now.
One more thing. I noticed that the icons are ok, but wherever there are words (not just for mozilla) the fuzziness is there.
Cheers

---

### Post by freebird54 on 2007-04-16
What kind of screen are you using?  If it is an LCD, have you turned on the subpixel smoothing in System->Preferences->Font ?  There are a few little things in there that can make a difference.  I don't recall installing the fonts to be difficult, and they seemed to be available right away.  If not, a <ctr><alt><backspace> will restart the GUI without having to restart the whole computer.

Waiting further info :)

---

### Post by marcos33br on 2007-04-16
[http://img455.imageshack.us/my.php?image=screenshotmh2.png]](http://img455.imageshack.us/my.php?image=screenshotmh2.png])[IMG]http://img455.imageshack.us/img455/9418/screenshotmh2.th.png[/IMG][/URL]
here is the screenshot, lets see if it helps.
Just tried the system fonts, it certainly helped, but did not solve the issue

---

### Post by Feba on 2007-04-16
That picture looks fine to me... Seems to me it's a problem with your monitor.

Have you tried using another monitor? Keep in mind, if you're running a large (1900x1200, maybe) monitor on a lower resoulution, it might look fuzzy.

EDIT: Try running > **sudo dpkg**-reconfigure xserver-**xorg** Give the most accurate replies you can, if your monitor supports higher resolutions, use them.

---

### Post by RedSquirrel on 2007-04-16
Are you using an LCD monitor? Sometimes it's just a matter of adjusting the "Fine Tune" setting on the monitor itself. Sometimes it's set rather low and the fonts look awful. I know on my monitor I see a huge difference in font quality if I put the Fine Tune up high.

You might also try some different font settings in:

```
sudo dpkg-reconfigure fontconfig-config
```

Try both "Native" and "Autohinter" and see which one looks best to you. The second screen in that config program is for hinting; you'll want that for an LCD monitor. And probably say "no" to the third question.

To make your fontconfig changes take effect, you have to restart X: Logout. At the login screen, press Ctrl-Alt-Backspace. Login again.

---

