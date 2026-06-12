---
title: "Working G4 Cube xorg.conf for Hardy 8.04"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by avtolle on 2008-04-28
After reading several threads and proposed solutions to the blank screen problem with Xubuntu 8.04, and deciding that nothing ventured, nothing gained, I adapted the suggestions of rhythminmind on another thread to the xorg.conf file. I have a G4 Cube, with an ATI Rage 128 video device. The operative parts of my xorg.conf file are below.
```

Section "Monitor"
Identifier "Configured Monitor"
[COLOR=Blue]Horizsync[/COLOR] [COLOR=Blue]28-51[/COLOR]
[COLOR=Blue]Vertrefresh 43-60[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[COLOR=Blue]SubSection "Display"
Modes "1024x768"
EndSubSection[/COLOR]
EndSection

<snip>[COLOR=Blue]
Section "DRI"
Mode 0666
EndSection[/COLOR]

```Those [COLOR=Blue]items[/COLOR] are those I manually added to the xorg.conf file, the precise nature of such taken from the xorg.conf file under 7.10, modified as suggested in the post of rhythminmind in the thread entitled "Working G3 imac xorg.conf for Hardy 8.04".

I also adopted the suggestion of stream303 in several threads to modify my [COLOR=Blue]/etc/yaboot.conf[/COLOR] flle by changing the append line to read "nosplash" in lieu of "quiet splash" at the end of that part of the image=/boot/vmlinux and image=/boot/vmlinux.old sections of said file, making the change known to openfirmware as:
```

sudo ybin -v -C /etc/yaboot.conf 
```which allows me to see what is happening rather than looking at a blank screen as the system boots.

Hope this helps someone.

---

### Post by stream303 on 2008-04-28
That's fantastic!  Thanks for sharing.

So other than using nosplash in either the second-stage boot prompt, or making it permanent in /etc/yaboot.conf with ybin, did you have to use any other video kernel parameters?

If not that's great news for ATI Rage owners..

---

### Post by avtolle on 2008-04-28
> **stream303 said:**
> That's fantastic!  Thanks for sharing.

So other than using nosplash in either the second-stage boot prompt, or making it permanent in /etc/yaboot.conf with ybin, did you have to use any other video kernel parameters?

If not that's great news for ATI Rage owners..

No, didn't have to use any other video kernel parameters. It (nosplash) didn't work from the second stage boot prompt, thus I made it permanent in /etc/yaboot.conf with ybin. Technically, I could have left /etc/yaboot.conf alone, as after the blank screen sits there a while, the "spinner" shows, and I'm into the sign in screen. Since I like to see what's going on, I enabled the nosplash permanently.

BTW, forgot to add to my initial post, my display is the 15" Apple Studio display that came with the Cube. Thus, if one is using another monitor, the rates in Horizsync and Vertrefresh may well be different, and may be obtained by looking at the /etc/X11/xorg.conf file under 7.10 or earlier install. Same story with the entry in "Modes" subsection under the Section "Screen", and the entry under the added Section "DRI" in the manually edited xorg.conf file, the portions which I set out in the initial post.

---

### Post by shgadwa on 2008-04-28
I am sorry but you are speaking Chineese and I cannot understand it. How to you get to that page to edit the sorg file??? I read it was sudo dpkg-reconfigure xserver-xorg but someone else said that it is old. That did not work though because I get some kind of errot later on that says its important into or whatever and it mentioned backup...nothing else.

Oh well, I gave up and went to Gentoo. I tried installing that and so far, ran into problems installing the filesystem. There are a lot of errors on hda4 for some reason. Also it had problems installing the superdrives...oh well. I jsut need a linux to get these computers working and to sell them.

---

### Post by avtolle on 2008-04-28
To edit one's /etc/X11/xorg.conf file; once the system is up, and one is looking at the blank screen, set to a terminal (I used Alt+Ctrl+F2), then after signing on with username and password, at the prompt type (without the quotes, of course) "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" to make a backup of the original file. Once this is done, then at the prompt (and without the quotes) "sudo nano /etc/X11/xorg.conf", find the section(s) to edit, make the edits, when finished making the edits, ^o to write, then "Enter" or "Return" to save to the file name provided, then ^x to exit. 

After this, at the prompt, type "sudo poweroff" (again, no quotes) to shut the system down (if one types "sudo shutdown now", the system goes to a recovery screen, which, if one is not careful in the selection, undoes all the editing). Once it shuts down, then hit the power button to start, and, in my case, success was at hand. HTH.

---

### Post by stream303 on 2008-04-28
> **shgadwa said:**
> I am sorry but you are speaking Chineese and I cannot understand it. How to you get to that page to edit the sorg file??? I read it was sudo dpkg-reconfigure xserver-xorg but someone else said that it is old.

In all honesty, while I applaud your efforts to re-use these machines, each and every one of them is going to need specialized care.  You have no idea what has been done to them by previous owners, and the "quick fix" distro isn't realistic.

I suggest getting more involved with your own machine first, and Linux in general, before trying to sell those boxes.  We're here to help, but it might require some dedication and interest on your part other than trying to do just a quick turnaround.

Actually, you may be better off just offering them up for sale as-is, and let the end-user decide what to do with it.

---

### Post by stream303 on 2008-04-28
> **avtolle said:**
> Thus, if one is using another monitor, the rates in Horizsync and Vertrefresh may well be different, and may be obtained by looking at the /etc/X11/xorg.conf file under 7.10 or earlier install.

Good point - in fact, maybe your techniques could be used for **Emac** owners, with their 1280x960 displays, and changing

Horizsync 71-73
Vertrefresh 70-140

and their modes
Modes "1280x960"

like you did in your example.  It is unclear if they might have to add

Option  "UseFBDev"  "true"

in their device section as well.  Maybe not...

Again, thanks to OswaldKelso and his great emac tips...

---

### Post by shgadwa on 2008-04-29
ok...I got into the file to edit it...but do i just type everything just as you said it????

I mean, its all text, do I use the quotes or not?

---

### Post by shgadwa on 2008-04-30
I tried to edit the file typing in the text exactly like it was shown above....when trying to write the changes, it says that there is no such file or directory as /etc/x11/xorg.conf. It said the same thing when trying to back up /etc/x11/xorg.conf....

Sooooo, I wrote the changes to xserver-xorg, if that will work.

Still seems to not work though.....it loads and gets such on something, I forget what it says...

---

### Post by avtolle on 2008-04-30
> **shgadwa said:**
> I tried to edit the file typing in the text exactly like it was shown above....when trying to write the changes, it says that there is no such file or directory as /etc/x11/xorg.conf. It said the same thing when trying to back up /etc/x11/xorg.conf....

Sooooo, I wrote the changes to xserver-xorg, if that will work.

Still seems to not work though.....it loads and gets such on something, I forget what it says...
Remember that Linux is case sensitive. The correct path to the file is /etc/X11/xorg.conf (note the uppercase X). No, the quotes should not be used.

---

### Post by shgadwa on 2008-04-30
OK...I removed the quoted and it still did not do anything.

I am reinstalling the OS now and I hope it fixes it.

---

### Post by avtolle on 2008-04-30
> **shgadwa said:**
> OK...I removed the quoted and it still did not do anything.

I am reinstalling the OS now and I hope it fixes it.
When you finish with your reinstall, and IF it doesn't fix the problem, try [http://ubuntuforums.org/showthread.php?t=770033](http://ubuntuforums.org/showthread.php?t=770033)
to edit the /etc/X11/xorg.conf file. HTH.

---

### Post by shgadwa on 2008-04-30
hmmmmmmmmmmmmmmmmmmmmmmm:-k


I think 8.4 must not be fore this computer or something....editing the file does nothing at all, it seems.

I did it for the G3 one...I still get the same no resume image...doing normal boot......? What do I do??

The date is set right and I did the sudo apt-get update and upgrade commands which upgraded it...still same problem.

---

### Post by shgadwa on 2008-04-30
What now?

---

### Post by stream303 on 2008-04-30
> **shgadwa said:**
> I think 8.4 must not be fore this computer or something....editing the file does nothing at all, it seems.

> I did it for the G3 one...I still get the same no resume image...doing normal boot......? What do I do??

Don't worry about that.  There is only a resume-image if you had hibernated the machine.  Since you haven't, the system will look for it, not find it, and continue on...

For best results, perhaps start a new thread something along the lines of

[PPC] - G3 wont boot with video

or whatever your specific machine problem is, will get you results faster than jumping around..

What exact G3 model do you have, and how much memory is installed again?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Since these are pre-owned machines, you may want to start with a clean-slate and zap the pram:

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

---

### Post by shgadwa on 2008-04-30
I think it is this one...

[http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html](http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html)

It has a 20GB hard drive and 512MB of RAM and for eBay's sake and for the monies sake, I need to get it working.

---

### Post by stream303 on 2008-04-30
Cool.  Why not start a new thread something like

[PPC]- G3/400 DV won't boot with video

or something like that, and we can concentrate our efforts better.

---

### Post by DeltaBCooper on 2008-07-22
> **avtolle said:**
> After reading several threads and proposed solutions to the blank screen problem with Xubuntu 8.04, and deciding that nothing ventured, nothing gained, I adapted the suggestions of rhythminmind on another thread to the xorg.conf file. I have a G4 Cube, with an ATI Rage 128 video device. The operative parts of my xorg.conf file are below.
```

Section "Monitor"
Identifier "Configured Monitor"
[COLOR=Blue]Horizsync[/COLOR] [COLOR=Blue]28-51[/COLOR]
[COLOR=Blue]Vertrefresh 43-60[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[COLOR=Blue]SubSection "Display"
Modes "1024x768"
EndSubSection[/COLOR]
EndSection

<snip>[COLOR=Blue]
Section "DRI"
Mode 0666
EndSection[/COLOR]

```Those [COLOR=Blue]items[/COLOR] are those I manually added to the xorg.conf file, the precise nature of such taken from the xorg.conf file under 7.10, modified as suggested in the post of rhythminmind in the thread entitled "Working G3 imac xorg.conf for Hardy 8.04".

I also adopted the suggestion of stream303 in several threads to modify my [COLOR=Blue]/etc/yaboot.conf[/COLOR] flle by changing the append line to read "nosplash" in lieu of "quiet splash" at the end of that part of the image=/boot/vmlinux and image=/boot/vmlinux.old sections of said file, making the change known to openfirmware as:
```

sudo ybin -v -C /etc/yaboot.conf 
```which allows me to see what is happening rather than looking at a blank screen as the system boots.

Hope this helps someone.


I'm having a problem. I've been working on this screen resolution thing for a couple weeks now and I thought this thread was finally going to fix it.  Alas, it has only made it worse.  

For whatever reason, after applying both the changes that were suggested up there, I can only boot to command prompt.  HOw in the world do I get back into the GUI. It's not running as one of my sessions as ctrl+alt+F7 takes me to a blinking cursor. 

I tried reversing the changes and nothing happens, except now I can't watch my computer boot.

Also, if someone could give me an idea where to find Horizsync and
Vertrefresh values for my benqfp202w? I was not running 7.10 before.

---

### Post by DeltaBCooper on 2008-07-22
startx does nothing. says I have no display.

---

### Post by stream303 on 2008-07-22
Which machine do you have?  Is it a cube?  The output of
```
cat /proc/cpuinfo
```
will help determine it.

If so, the cubes came with either an ATI Rage 128 pro, an Nvidia Geforce2 MX, or ATI Radeon card.  You might want to take a look at the output of

**lspci**

to help you determine.

Your monitor's native resolution seems to be 1680x1050 widescreen.  Do a search or find the docs on what the horizontal and vertical freqs are.

After gathering this info, you can determine if you need to modify the xorg.conf file further by specifying the driver and the monitor specs.

---

### Post by DeltaBCooper on 2008-07-22
Yes. G4 Cube 450 mhz ATI rage 128 20" benq fp202w. I'll give it a shot.

---

### Post by stream303 on 2008-07-22
Not sure if those old cards supported 1680x1050, you'd have to check.  Depending on your requirements, you may be able to drop the default depth down from 24 to 16 as something else to play with.

It may feel like we're back in the 90's, but at least we have the capability of getting linux on it.  Apple could have easily chosen a lock-in.

---

### Post by DeltaBCooper on 2008-07-23
yeah it does support the resolution. maybe the community's driver's don't though.

---

