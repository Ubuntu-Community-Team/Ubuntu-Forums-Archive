---
title: "[SOLVED] Problems installing on Powermac G4"
date: 2008-05-15
forum: Apple Hardware Users
---

### Post by a_L_p on 2008-05-15
Hello, 

I have been working to install Ubuntu on my Powerbook G4 and have completed all neccesary steps (that I can see) 

1. Downloaded the latest release Hardy 8.04 for Mac (PowerPC) and IBM-PPC (POWER5) desktop here: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

2. Using OSX Disk utility I burned it to CD

3. Using the OSX install CD I partitioned My hard drive into 2 partitions one formated for OSX and the other as Free Space

4. OSX installation complete, I put in the Ubuntu CD and started from it. 

4a. Some text comes on the screen saying to press enter or if that doesn't work type 'live video=ofonly'. Pressing enter didn't work, it brought up the endless white screen. So, I typed the 'live video=ofonly' and then pressed enter. It says 'Please wait loading Kernel' then I get two identical messages something like 'cannot allocate resources... then it says loading... then the screen goes to black with a small white _ in the top left, I can hear the CD being read, and it sounds like something is happening, but then the screen just goes to black after a minute or so... 

I have tried this last step a number of times now, and get the same result every time.

Does anyone out there have any solutions for me?

Thanks,
Andy Price

---

### Post by avtolle on 2008-05-15
Hmm, are you using the Live (Desktop) iso? The reason for the question is that you're having the same problems I had on my Cubes with same. If you are, then I suggest downloading the alternate iso, with the text based installer, as that is what I did to install. Thereafter, there was some editing of the /etc/X11/xorg.conf file needed, but we can approach that later, assuming that you get an installation.

---

### Post by stream303 on 2008-05-15
I'd definitely recommend the "alternate" installer rather than the live-cd.

With the live-cd you could try this at the second-stage boot: prompt
```
live-nosplash-powerpc
or
live-nosplash-powerpc video=ofonly
``` 

The splash screen is troublesome.  With Hardy, *after installation with the alternate cd*, I still had to do this at the second-stage boot prompt:

```
Linux nosplash
```

Try the alternate install, and if that works, try this command at the second stage boot prompt (halt the countdown with -tab- so you can type it in).

If this works you can make it permanent in /etc/yaboot.conf, but let's try this first..

---

### Post by mchladek on 2008-05-15
I got Hardy installed on my iBook G4 with the alternate iso.  I agree with avtolle that that's the way to go.

Also, once I did get it installed, I had to use "Linux nosplash video=ofonly" on the second boot prompt to actually get Hardy to boot.  If all that works for you, you'll want to configure your yaboot to make the previous command permanent.  I'm pretty sure there are instructions on how to do that on the [PowerPC Wiki]("https://wiki.ubuntu.com/PowerPCFAQ").

Edit:  And stream beat me to it!

---

### Post by a_L_p on 2008-05-15
Thank you all for the replies, 

I am very new to this all, and I am totally open to trying what ever will get this installed. 

Is there a good place to see the instructions for doing the alternate install? 

Thanks. 
Andy

---

### Post by avtolle on 2008-05-15
The "instructions" appear on the screen as each step in the process is reached. To install from the alternate CD, once md5sum of the iso download is verified, and after the burn (I use 4x) to a CD-R (use "name brand" ones). boot from the CD, and "You're off". I've done this so many times, I don't recall if or when I looked at any sources prior to beginning the install. Not trying to be snarky here, just relating my experiences. :-)

---

### Post by crapple on 2008-05-15
I am having trouble with installing 8.4 to can someone tell me how to edit the x 11 config file.

---

### Post by avtolle on 2008-05-15
> **crapple said:**
> I am having trouble with installing 8.4 to can someone tell me how to edit the x 11 config file.
Do you have a copy of the /etc/X11/xorg.conf file from an earlier installation on this particular computer? If so, that will come in very handy.

To edit the file, no particular specs available, one does from the terminal:```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak #Make a backup, just in case.
sudo nano /etc/X11/xorg.conf #Opens file for editing
```
Then, when one is in the file, go to the part labeled [COLOR=DeepSkyBlue]Section "Monitor"[COLOR=Black]which will likely read something like Identifier "Configured Monitor" the EndSection. After "Configured Monitor", hit Enter on your keyboard, and type [COLOR=DeepSkyBlue]Horizsync xx-xx[COLOR=Black], where the values of xx-xx are from your information about your monitor. After typing this in, again hit Enter to get a new line, then type in [COLOR=DeepSkyBlue]Vertrefresh yy-yy[COLOR=Black], again with the values of yy-yy from your information about your monitor.

Then proceed to the next sction, [COLOR=DeepSkyBlue]"Screen"[COLOR=Black], and after that part labeled [COLOR=DeepSkyBlue]Device "Configured Video Device", [COLOR=Black]again hit enter to get a blank line and type in [COLOR=DeepSkyBlue]Subsection "Display"[COLOR=Black] (again, hit Enter for a new line), then type on the new line [COLOR=DeepSkyBlue]Modes "aaaaxbbbb"[COLOR=Black], again from the information you have about your monitor. There may be several, just type them all in on the same line. Then, after hitting enter again to get a blank line, type [COLOR=DeepSkyBlue]EndSubSection[COLOR=Black]. 

Then, if there is a Section on your existing information that does not appear in the existing file, you need to add it. For example, in my particular case, with a G4 Cube, ATI Rage 128, 15" Studio display, my additional section reads:> [COLOR=DeepSkyBlue]Section "DRI"
Mode 0666
EndSection[COLOR=Black].

Once it is edited to your satisfaction, ctl O to write, Enter to save to the name given, and ctrl X to exit Nano. Then restart your computer to see if it works.

I would remind anyone reading this that s/he needs to get her/his specs for the entries given above from (hopefully) a copy of a prior install xorg.conf file. If there isn't one, then a search on the capabilities of the video card and monitor in question needs to be performed to obtain this information.

I've posted on an earlier thread the details of the pertinent parts of my /etc/X11/xorg.conf file as edited, which worked for me. There is at least one other post about a working configuration for a G3 on this forum.

Good luck.


[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by a_L_p on 2008-05-16
> **stream303 said:**
> I'd definitely recommend the "alternate" installer rather than the live-cd.

With the live-cd you could try this at the second-stage boot: prompt
```
live-nosplash-powerpc
or
live-nosplash-powerpc video=ofonly
``` 

The splash screen is troublesome.  With Hardy, *after installation with the alternate cd*, I still had to do this at the second-stage boot prompt:

```
Linux nosplash
```

Try the alternate install, and if that works, try this command at the second stage boot prompt (halt the countdown with -tab- so you can type it in).

If this works you can make it permanent in /etc/yaboot.conf, but let's try this first..

I got the live Cd to work with live-nosplash-powerpc video=ofonly

Thanks,
:-) Andy

---

### Post by stream303 on 2008-05-16
Allright!!

Now to make it permanent, you can edit your /etc/yaboot.conf file and add it to the append= line: (sudo nano /etc/yaboot.conf will do)

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        **append="nosplash video=ofonly"**

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        **append="nosplash video=ofonly"**
```

After saving it, or writing it out, let the system know about the change:

```
sudo ybin -v -C /etc/yaboot.conf
```

Note the capital C.

Enjoy!

---

