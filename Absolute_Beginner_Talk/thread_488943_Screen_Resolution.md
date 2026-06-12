---
title: "Screen Resolution"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by HamHamT on 2007-06-30
Is it possible to make the screen resolution bigger? My computer is normally at 1280xsomething, and the max here is 1028. Is there a mod or something that I can use to increase my resolution?

---

### Post by p_quarles on 2007-06-30
What kind of graphics controller do you have?

---

### Post by HamHamT on 2007-06-30
Not sure what that is, sorry, can you explain it to me? My graphics card is a Radeon 9200 Series.

I'm sure I have the ability to because I could do it fine on my Windows OS (Same computer)

---

### Post by p_quarles on 2007-06-30
Graphics controller/graphics card = same thing.

The Radeon series is manufactured by ATI. Look that up in these forums, and you'll find directions for getting it to work.

---

### Post by overdrank on 2007-06-30
> **HamHamT said:**
> Not sure what that is, sorry, can you explain it to me? My graphics card is a Radeon 9200 Series.

I'm sure I have the ability to because I could do it fine on my Windows OS (Same computer)

Hi are you using any desktop effects or beryl. If not then go to applications,accessories, terminal and enter the command
[PHP]sudo dpkg-reconfigure -phigh xserver-xorg[/PHP] 
You can copy and paste the command to terminal it will ask for your password then answer a few question and select the resolution there that you want to add.
Good luck!:popcorn:

---

### Post by HamHamT on 2007-06-30
Thanks overdrank, but if I am using desktop effects is it still possible?

+

I did what you said and it worked out all fine, it seemed like it worked and when the window closed this was in the terminal 

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070630185846

```

Am I supposed to reboot to see the effect? I don't have desktop effects on.

---

### Post by overdrank on 2007-06-30
> **HamHamT said:**
> Thanks overdrank, but if I am using desktop effects is it still possible?
Yes restart and hope it works!

Well yes and no. I cannot guarantee, but I did help someone this morning with the same card and it solved his issue got his beryl working, 
You can try to edit you xorg and add that resolution there.
[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]
enter the above command in the terminal this will open the xorg file and you can scroll down to the screen section and add the resolution that you want to each line. This can also cause you xorg to crash so back up you xorg. Which ever way you choose just be prepared to loose the effects or crash your xorg. Good luck!

---

### Post by HamHamT on 2007-06-30
Unfortunately, I've tried disabling my desktop effects and I've tried enabling them and doing the second method, but no luck. I've rebooted twice and no luck.

I'm going to search the way that p_quarles suggested. Thanks for the help both of y ou!

---

