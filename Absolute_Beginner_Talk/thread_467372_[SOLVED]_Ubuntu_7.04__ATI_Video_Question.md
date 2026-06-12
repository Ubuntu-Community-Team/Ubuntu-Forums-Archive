---
title: "[SOLVED] Ubuntu 7.04 / ATI Video Question"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by crjackson on 2007-06-07
I just installed 7.04 32bit Ubuntu.  It boots, it runs, all seems to work except that my video refresh is at 60Hz and can't be changed.  I have an ATI x800 256mb video card, and a ViewSonic CRT that will refresh at 150mhz.

Normally under Winxp, I run at 1024x768 x 100Mhz - If I want higher resolution, it goes ungodly high on this card / montior combination.

I went into the restricted driver section of ubuntu and installed the ATI restricted driver but it did nothing except all lower resolutions at the same 60Hz refresh rate.

I see that ATI has a Linux driver on there web site and I have downloaded it.  Is this the same as the restricted driver?

If not, can some one walk me through putting that driver on my install (unless it won't help me get some resolution and refresh rate relief)?

I have looked over the install documents provided by ATI but they do not list ubuntu as a supported distro, and they do list many requirements that I'm unsure how to detirmine if ubuntu has or needs.

Can some one please walk this dummy through the process?

Thanks...

---

### Post by Ek0nomik on 2007-06-07
You can manually add the refresh rate and resolutions in your xorg.conf file.

```
gksudo gedit /etc/X11/xorg.conf
```

There are thousands of threads about it on the forum, you should be able to find one.  ;)

---

### Post by crjackson on 2007-06-07
Great! And thank you for helping me.  I'll try this tomorrow.  I realize there are many posts but the answers I found seemed numours and confusing.  I told you I was a dummy and needed someone to hold my hand on this.

Thank you for helping in spite of the other posts.

---

### Post by crjackson on 2007-06-07
> **Ek0nomik said:**
> You can manually add the refresh rate and resolutions in your xorg.conf file.

```
gksudo gedit /etc/X11/xorg.conf
```

There are thousands of threads about it on the forum, you should be able to find one.  ;)

Almost forgot - Do I need that driver from ATI's website to enable anything?  Does it add something or is it the same driver or what?

---

### Post by Ek0nomik on 2007-06-07
Here is an excellent site for getting ATI drivers working on Ubuntu.  The link I am providing you is for 7.04 (Feisty Fawn).  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)  If you need instructions for another distribution of Ubuntu, or even a non Ubuntu distribution, it's all on that site.

You don't want to change your resolution, correct?  You said you have 1024x768, and that is all you want?  If you just want your refresh rate changed, it should be quite simple.  :)

This HOW TO might help you.  I know it looks like it is quite outdated, but I believe the original posted has since edited it to work on all Ubuntu versions.  (Or so I would only hope)

If you have more questions feel free to ask.

---

### Post by crjackson on 2007-06-07
> **Ek0nomik said:**
> Here is an excellent site for getting ATI drivers working on Ubuntu.  The link I am providing you is for 7.04 (Feisty Fawn).  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)  If you need instructions for another distribution of Ubuntu, or even a non Ubuntu distribution, it's all on that site.

You don't want to change your resolution, correct?  You said you have 1024x768, and that is all you want?  If you just want your refresh rate changed, it should be quite simple.  :)

This HOW TO might help you.  I know it looks like it is quite outdated, but I believe the original posted has since edited it to work on all Ubuntu versions.  (Or so I would only hope)

If you have more questions feel free to ask.

Great.  I book marked it, and when I get home I'll turn this into a PDF file.

I would like to have the option of a higher resolution but it's not critical right at this moment.  However, the refresh rate **IS** a problem right now so It's my primary issue.

This is like learing an forgin language to me and very confusing.  Hopefully after a month or so I'll start catching on to this stuff.  Thanks for your help.:D

---

### Post by Ek0nomik on 2007-06-07
> **crjackson said:**
> Great.  I book marked it, and when I get home I'll turn this into a PDF file.

I would like to have the option of a higher resolution but it's not critical right at this moment.  However, the refresh rate **IS** a problem right now so It's my primary issue.

This is like learing an forgin language to me and very confusing.  Hopefully after a month or so I'll start catching on to this stuff.  Thanks for your help.:D

Once you start to get over a few hurdles, you will understand it much better.  I myself am new to Linux (roughly 4 months or something), but there comes a point where things kinda start to click, and you know how to do a lot of stuff just by some basic knowledge.  Then if you get stuck, just search the web or come directly to the forums.  :)

---

### Post by crjackson on 2007-06-09
Okay, so I'm doing something wrong.  I cut and pasted the text into the terminal.  It opened up the xorg.conf file.  I found a refresh rate entry that said 43-60.  I changed the 60 to 100.  I saved the file. I did the ctrl-alt-bksp.

I looked at the refresh settings available, and nothing has changed.  It still says 60.  What did I do wrong?:(

---

### Post by crjackson on 2007-06-19
I just wanted to report back with my progress...

After a fresh install of A64 ubuntu, I downloaded the driver from the AMD/ATI website.  I followed their instructions without much luck.  Then I right clicked on the downloaded file and made it launchable.  Bang!  The drive installation interface poped up.  It installed FLAWLESSLY and even gave me the Catalyst Control Center (working perfectly).  I now have ALL the resolutions and refresh rates that my hardware supports.:D

---

