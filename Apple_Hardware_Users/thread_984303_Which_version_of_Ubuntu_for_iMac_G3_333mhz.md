---
title: "Which version of Ubuntu for iMac G3 333mhz?"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by dmanskiman on 2008-11-16
I have already installed intrepid with the ppc alternate cd on my iMac G3 333mhz.  I have been fiddling with xorg.conf forever, and still nothing works.  When I tried to boot my mac up the other day, after yet another failed attempt to correctly detect my screen and start Gnome the screen went black with an underscore in the top left.  Usually after gnome fails it shows a gui and allows me to edit xorg.conf, or go into low res mode (which worked but none of the programs worked).  I've given up trying to put ppc intrepid on this machine!!  

After reading I have found that even if the display works right ubuntu doesn't work well if at all with my type of imac.  So this begs the question, which version of ubuntu should I burn onto a cd and install?  Should I use the alternate cd again or go gui?  After that should I try doing a network upgrade to Hardy? 
Which versions of ubuntu have had the most success with my type of mac?


All help would be ever so greatly appreciated :-D

---

### Post by stream303 on 2008-11-16
Since there have been many changes to the X server in Hardy+ releases, as a first-time installer I might suggest Gutsy 7.10 since it is still getting updates.  Feisty used to be my favorite, but it EOL'ed recently.  You could even try Debian Etch'n-half 4.0r5.  The problem is that you are nearly guaranteed to have to edit the xorg.conf file because Apple hardware isn't Linux-friendly. :)

Using the alternate like you are doing is perfect, especially if you have low ram.  How much ram do you have?  Also, if you have replaced the original hard drive with something larger than 8gb, you'll have to do custom partitioning to keep the root partition under 8gb.

In any case, G3 owners will have to edit /etc/X11/xorg.conf as root like you are doing, being sure to see this faq:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

If you can't get to even a bad gui to do editing, you'll have to hit the commandline.  If you are fortunate, you can try a virtual terminal (CTRL-ALT-F2) and do your editing from there with vi or nano.

```
sudo nano /etc/X11/xorg.conf
```

or if a virtual terminal isn't working, you reboot into "rescue mode" or "single mode".  At the second stage boot: prompt, hit TAB to stop the countdown.  You should see some options presented such as

Linux rescue

or you can also try "Linux single video=ofonly nosplash"

The system will look like it is installing again, but eventually you will get the option to be dropped into a root shell, usually /dev/hda3 if you have used the whole disk just for Ubuntu.

In this mode, you are already root, so you can just do

```
vi /etc/X11/xorg.conf
```

I have not been able to get the easy editor, nano, to work in rescue mode, so you may have to resort to vi, so if you are determined, you may want to get a little practice with vi first on another machine.

If you are determined to use Intrepid, you may want to use the values listed in that faq listed above, but use the following as a template - it seems that Intrepid doesn't barf as long as you use all these sections:

[http://ubuntuforums.org/showthread.php?t=978303](http://ubuntuforums.org/showthread.php?t=978303)

Try to keep it fun. :)

---

