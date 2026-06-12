---
title: "Beryl problems with scroll and Xine movie play on Edgy"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-26
Hello, I am still new at xubuntu and I tried to install Beryl on my xubuntu 6.10 Edgy.

I have an Intel media accelerator 900 graphics card and I installed it with the directions off of this Beryl wiki page: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Then the window manager wouldn't let me click onto the Beryl option after writing beryl-manager in terminal.

So I read Pricechilds page, but it wasn't for intel or xubuntu, so I found this ubuntu forum: [http://www.ubuntuforums.org/showthread.php?t=269767&highlight=xubuntu+beryl](http://www.ubuntuforums.org/showthread.php?t=269767&highlight=xubuntu+beryl)

then I configure it like tutorial #2 off of this beryl forum: [http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

I used the original edgy installs from the first edgy/beryl wiki page and configured it like page 2 with Jeeves Bond's comment about xfce4-session: [http://www.ubuntuforums.org/showthread.php?t=269767&page=2&highlight=xubuntu+beryl](http://www.ubuntuforums.org/showthread.php?t=269767&page=2&highlight=xubuntu+beryl)

so I now have my self logged in as xgl, and the window themes and effects work, but the scroll function of my xubuntu has turned from a fast and smooth scroll to a shakey and slow scroll that is very difficult. I also had terrible movie problems with my xine (with the full screen) and I have been running a xine-check but it did not really help.

I'm wondering if I did something wrong, or if this is common with Beryl/Intel/xubuntu/and Edgy?

I would love some help, and if it is un-fixable, I would love some help on removing it from my brand new edgy.

Thanks,
-c.

I also am really just wanting the "glass" theme and don't really care about all of the special effects, all though if I could get it working as fast and smooth as xubuntu has been, then that would be really cool.

---

### Post by DSn0wMan on 2006-10-26
Sounds like your video card is having a hard time keepig up.

---

### Post by crimesaucer on 2006-10-26
Yeh, I got an error from xine saying that there was maybe an overload to my system, would that be the case?

...and Marvin the manic depressant robot rules.

---

### Post by crimesaucer on 2006-10-26
Is there a way to wave window borders as clean looking as the themes in Beryl, but without all of the special effects that might of "overloaded" my system?

Would fluxbox work with xfce4.4 xubuntu?

---

### Post by DSn0wMan on 2006-10-27
just go grab a cheap nvidia card. My 6 year old nvidia GForce2 (32MB) seems to handle compiz pretty well. I am guessing you could grab a 128MB - 256MB video card for under $40.

[http://www.pricewatch.com/video%5Fcards/](http://www.pricewatch.com/video%5Fcards/)

---

### Post by d3v1ant_0n3 on 2006-10-27
Open up Beryl settings manager (If you're having trouble doing it from the icon, there should be a menu entry too) and uncheck all the options apart from 'general options' (which can't be turned off AFAIK)- That'll turn off all the plugins, but should still allow you to run Emerald themes.. I think.

---

### Post by crimesaucer on 2006-10-27
Thanks, I messed around with the settings and turned everything off, and then turned the general window themes back on, but my xine was still having problems, and then I had a weird thing happen with my Firefox running without showing and not being able to shut off because a small portion of it was stuck in the corner, and then the cpu was stuck at 100%. 

So I removed beryl and all of the packages, and removed it from my start up programs and then I still had problems with my gdm (I think that's the name).

I think that one of the settings and a certain terminal command that one of the tutorials had said to do got my system stuck on not showing the windows and the panels correctly.

I tried to fix it and ruined everything, and a -f install and re-install of my desktop and upgrades/dist-upgrades wouldn't help a bit and finally it became such a problem that I just wiped it and and am installing everything from scratch again. Then, I'll read through the forums that I had followed and find out what I did that ruined me, I'm thinking it was a "chomd" code pointing to start xgl, but I'm not sure. 

I should of just went to my Windows Xp partiton to ask how to change it back (since I couldn't get a firefox page to show), but I tried to fix it without asking and ended up ruining everything.

As for the nvidia graphics card, thanks, I'll look into that for my notebook.

---

### Post by d3v1ant_0n3 on 2006-10-27
Unless you have one of a small range of Alienwares that support it, you can't upgrade graphics in a notebook AFAIK. Sorry.

---

### Post by crimesaucer on 2006-10-28
So all I have is a media accelerator 900 Intel embedded graphics card, so that isn't good enough of a graphics card to run the new beryl for edgy?

Do you know of a good window theme for xubuntu edgy that is a vista like "glass" window theme?

---

