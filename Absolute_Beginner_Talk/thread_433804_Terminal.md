---
title: "Terminal ?????"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by ABCgang on 2007-05-05
I'm new to Ubuntu and have been researching how to download the libmp3lame.so driver for Audacity to convert MP3's.   I've got audacity downloaded and I can record/playback music with it.     

Now for the "absolute beginner talk" question coming from a Windows XP user.  Where do I find a terminal and how do I open it?  Maybe it's just a terminalogy problem I'm having, but I don't know where to type these various codes (sudo slocate -u & locate libmp3) to look in /usr/lib for the lame info.   Can anybody help out the totally lost trying to make the switch to linux?  Thanks

---

### Post by fickendichdu on 2007-05-05
Fairly new myself but the terminal is under Applications then accesories.

---

### Post by taurus on 2007-05-05
Applications -> Accessories -> Terminal

---

### Post by Najand on 2007-05-05
Terminal is under Application -> Accressories -> Terminal

---

### Post by ABCgang on 2007-05-05
Thanks fickendichdu, taurus and najand for responding to my plea for help.  I found the "terminal" right where you said it was.

Now, do you just hit enter after you typed the code in or is there something else required?  I typed in those two codes mentioned in my first question and hit the enter button, but nothing happend.  I was expecting to be taken to where the libmp3 file was at.  

Instead, I keep getting:    ubuntu@ubunti-desktop:~$   Is this normal?

---

### Post by Najand on 2007-05-06
Probably it has not been installed.&#12288;You may need to install the suitable package before that.

---

### Post by teddybairs1 on 2007-05-06
What engine does Audacity run? Go to Synaptic (System-->Administration-->Synaptic Package Manager) and search for LAME. You can also try audacity and lame together. There should be a .deb plugin package straight from the repos to allow it to work with mp3s. You shouldn't have to bother with the .so stuff yourself.

---

### Post by jyba on 2007-05-06
> **ABCgang said:**
>  I typed in those two codes mentioned in my first question and hit the enter button, but nothing happend.  I was expecting to be taken to where the libmp3 file was at.  

Instead, I keep getting:    ubuntu@ubunti-desktop:~$   Is this normal?

The locate database probably needs updating before your newly installed files show up. Type:

```
sudo updatedb
```

...give it your password and then sit back for a couple of minutes whilst the database is rebuilt. Then try again: 

```
sudo slocate -u & locate libmp3
```

*****************************************************************

EDIT: Sorry, ignore this answer - I should have read the man page before writing it...:)

---

### Post by ABCgang on 2007-05-06
Well thanks guys for trying to help, but it just doesn't look like it's going to work.  For some reason, I can't locate the LAME files to download to ubuntu.  I've even been to the Audacity forum with no luck.  I've had Audacity and LAME on Windows XP before and it was easy to load and use.  

Although ubuntu looks like a powerful OS, it doesn't appear to be user friendly and I'm probably going to dump it to reload Windows XP.  Thanks for trying and good luck out there.  Wes

---

### Post by jfinkels on 2007-05-06
Perhaps you may have a typo in your command. The way you wrote it:
```

sudo slocate -u & locate libmp3

```

Means something quite different from this:
```

sudo slocate -u && locate libmp3

```

So be careful.

Also, you may want to check out the package manager, Synaptic (Under "System > Administration") and search for lame or liblame which will install libraries for you.

Perhaps you could tell us what you are trying to do and we can tell you how to go about getting it done.

EDIT:

ps. when I run that command, it looks something like this:
```

jeff@jeff-laptop:~$ sudo slocate -u && locate libmp3
Password:
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0

```

---

### Post by zvacet on 2007-05-06
If you have all repos open you will find lame and Audacity in synaptic.When you find and install Audacity right click on it and you will see what is recommended for installation with it.

---

### Post by ubuntu27 on 2007-05-06
@ABCgang: First install some codecs following this guide:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ABCgang on 2007-05-06
jfinkels,

***Also, you may want to check out the package manager, Synaptic (Under "System > Administration") and search for lame or liblame which will install libraries for you.***

I tried this and it appears to have worked.  I can now convert recorded music with Audacity to MP3's.  Thank you very much for your suggestion as I was ready to give up on Ubuntu.

---

### Post by ubnewbie2 on 2007-05-06
> **jfinkels said:**
> Perhaps you may have a typo in your command. The way you wrote it:
```

sudo slocate -u & locate libmp3

```

Means something quite different from this:
```

sudo slocate -u && locate libmp3

```

So be careful.

Also, you may want to check out the package manager, Synaptic (Under "System > Administration") and search for lame or liblame which will install libraries for you.

Perhaps you could tell us what you are trying to do and we can tell you how to go about getting it done.

EDIT:

ps. when I run that command, it looks something like this:
```

jeff@jeff-laptop:~$ sudo slocate -u && locate libmp3
Password:
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0

```

I pointed mine to /usr/lib/libmp3lame.so.0 and it seems to be happy now.

---

### Post by ABCgang on 2007-05-06
ubnewbie2,

By pointed to, do you mean you typed /usr/lib/libmp3lame.so.0 in a terminal and hit the enter button?

---

### Post by ubnewbie2 on 2007-05-06
> **ABCgang said:**
> ubnewbie2,

By pointed to, do you mean you typed /usr/lib/libmp3lame.so.0 in a terminal and hit the enter button?

No, Audacity asks you to locate the lame library when you first try to use it.  Or you can go into preferences, under the file formats tab, click on the find library button, change the option at the bottom of the popup dialog  to extended libraries, and then navigate to, and select the desired library file.

---

### Post by jfinkels on 2007-05-06
> **ABCgang said:**
> jfinkels,

***Also, you may want to check out the package manager, Synaptic (Under "System > Administration") and search for lame or liblame which will install libraries for you.***

I tried this and it appears to have worked.  I can now convert recorded music with Audacity to MP3's.  Thank you very much for your suggestion as I was ready to give up on Ubuntu.

Excellent!

Take a look here for more info on installing in Ubuntu [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

And here for, well, anything: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

### Post by ABCgang on 2007-05-06
Thanks jfinkels and ubnewbiw2 for the information and ubuntu sites.  I'm sure it'll come in handy.

Another question about Audacity on Ubuntu.

When I go to Edit>Preferences to change specifications about the recording process, I can't see the bottom of the Audacity Preferences box to click the "OK" button to apply any changes.  I can change the size horizontally, but can't do anything with it vertically.  I've looked into Ubuntu and tried to move/size/change the box to no avail.  Have either of you got any suggestions?

PS:  I downloaded Audacity to my Windows XP computer and the preference box is centered where I can view the "OK" button.

---

### Post by ubnewbie2 on 2007-05-07
> **ABCgang said:**
> Thanks jfinkels and ubnewbiw2 for the information and ubuntu sites.  I'm sure it'll come in handy.

Another question about Audacity on Ubuntu.

When I go to Edit>Preferences to change specifications about the recording process, I can't see the bottom of the Audacity Preferences box to click the "OK" button to apply any changes.  I can change the size horizontally, but can't do anything with it vertically.  I've looked into Ubuntu and tried to move/size/change the box to no avail.  Have either of you got any suggestions?

PS:  I downloaded Audacity to my Windows XP computer and the preference box is centered where I can view the "OK" button.

My OK button is visible.   However, try right clicking on the title bar of the dialog box, and choose resize or move.

---

### Post by ABCgang on 2007-05-07
I already tried that prior to posting ubnewbie2 and it wouldn't do anything?  

Good suggestion though as I thought that would have done the trick initially.

---

### Post by ubnewbie2 on 2007-05-07
Ah, I just played around with resize, and it seems to have a minimum size.  I can only make it bigger.  What screen resolution are you using?  Mine is 1280x1024, and that dialog takes up about 2/3 of the screen height. So if you are using 800x600 for example, it might have trouble fitting.

---

### Post by jfinkels on 2007-05-07
You can move a window by holding <Alt> and clicking and dragging any part of the window (not just the title bar) if necessary.

---

### Post by ABCgang on 2007-05-07
jfinkels,
 
I tried the holding the alt button and dragging the preference box, but it won't move upward to reveal the Cance//OK button.  


ubnewbie2,

My screen resolution only has 800x600 and 600x600 for choices.  How do I get a better resolution like yours?

---

### Post by jfinkels on 2007-05-07
> **ABCgang said:**
> jfinkels,
 
I tried the holding the alt button and dragging the preference box, but it won't move upward to reveal the Cance//OK button.  


ubnewbie2,

My screen resolution only has 800x600 and 600x600 for choices.  How do I get a better resolution like yours?

You're going to have to edit your xorg.conf file, which controls the entire GUI system. Of course, this will only work if your monitor and graphics card allow high resolutions...

1. Backup your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

2. Open your xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```

3. Find the section that starts like this:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Radeon Mobility M300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
[...]

```
(This is what mine looks like.) If you want to add a different resolution (let's say 1280x800), edit every line that starts with "Modes" so that it has the resolution you want, like this:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Radeon Mobility M300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1440x900"
        EndSubSection
[...]

```
4. Save and see if you can change resolutions now. If not, restart your X session by saving whatever you're working on and pressing <Ctrl>+<Alt>+<Backspace>. (This will log you out). Log in again and see if you can change the resolution. If not, you may need to look into drivers, so search the forums and start a new thread if necessary.

---

### Post by ABCgang on 2007-05-08
jfinkels (and the others that posted here too),

I was able to change my resolution by typing "sudo dpkg-reconfigure xserver-xorg" in a terminal and making the appropriate changes to the resolution (with the spacebar).  What I was hanging up on and you did mention it, was to re-boot with ctrl+alt+backspace.  Once I re-booted this way, the changes applied and now I can see all of the dropdown boxes.  

Once again, thanks everyone for your help.

---

### Post by jfinkels on 2007-05-08
> **ABCgang said:**
> jfinkels (and the others that posted here too),

I was able to change my resolution by typing "sudo dpkg-reconfigure xserver-xorg" in a terminal and making the appropriate changes to the resolution (with the spacebar).  What I was hanging up on and you did mention it, was to re-boot with ctrl+alt+backspace.  Once I re-booted this way, the changes applied and now I can see all of the dropdown boxes.  

Once again, thanks everyone for your help.

Excellent!

Pressing <Ctrl>+<Alt>+<Delete> restarts your X server (the program which ultimately controls all graphical programs).

---

