---
title: "failed installation of realplayer with synaptic"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by lila on 2005-12-08
Hello,
a couple of days ago I tried to get my DVD palyer to play DVDs, by first enabling DMA, then downloading libdvd...whatever it was called, then coming across "Easy Ubuntu" in the customisation forum, tried that, it did things, including downloading codecs, but I still can't read DVDs.  
Thought maybe it's just Totem, so downloaded Realplayer with synaptic, at the breathtaking speed of, on average, 1600 bytes (1.6kB) per second.  It tried to install itself, going through various screens where I clicked ok, and then asked or told me something to do with root that I didn't get (linguistically - I tried to read the sentence and I just didn't get it) but I clicked ok anyway.  Some files failed to download properly (it said so during the download), and now I have the icon in the menu but nothing happens when I click on it.  And when I look for any files related to realplayer, I can't find them.  I don't know where it downloaded them to.
Any hints on what I can do?
:???: Lila

---

### Post by Estariel on 2005-12-08
To figure out why realplayer isn't starting, open a Terminal and type
```
realplayer
```
It will most likely output an error; please post it here.

The problem with Totem and DVD's could be because of the gstreamer backend of totem, which has never worked well for me (and it is known for having problems with DVDs).
Just install the xine backend (the package is totem-xine I think) and it might work.

Also, please start a terminal and do the following:
```
ls /usr/lib/libdvd*
```
and paste the output in here.

edit: typo

---

### Post by lila on 2005-12-08
[QUOTE=Estariel]To figure out why realplayer isn't starting, open a Terminal and type
```
realplayer
```
It will most likely output an error; please post it here.

The problem with Totem and DVD's could be because of the gstreamer backend of totem, which has never worked well for me (and it is known for having problems with DVDs).
Just install the xine backend (the package is totem-xine I think) and it might work.

Also, please start a terminal and do the following:
```
ls /usr/lib/libdvd*
```
and paste the output in here.

edit: typo[/QUOTE]

Typing realplayer in terminal gives me this:
 realplayer
/usr/bin/realplayer: line 5: /usr/lib/RealPlayer8/realplay: No such file or directory
/usr/bin/realplayer: line 5: exec: /usr/lib/RealPlayer8/realplay: cannot execute: No such file or directory

The ls /usr/lib/libdvd* bit gives me my first ever colour output in terminal:
/usr/lib/libdvdcss.so.2      /usr/lib/libdvdnav.so.4.0.0
/usr/lib/libdvdcss.so.2.0.4  /usr/lib/libdvdread.so.3
/usr/lib/libdvdnav.so.4      /usr/lib/libdvdread.so.3.0.0

with the first half of the first and last line, and the last half of the second line in *_turquoise_*!  
I have looked for the -xine version before, but I'll check again, last time I couldn't find it but I have since added more repositories.
Will do that now.
CHeers,
Lila:smile:

---

### Post by Estariel on 2005-12-08
The realplayer error means that the installation program couldn't copy the executables to the places where they are supposed to be (which was to be expected, since the installer didn't have root privileges).

This is a far shot, but it might have installed something in a hidden directory in your home directory (this is where most stuff goes that cannot be installed system wide.)
You might even have a non hidden directory...

Is there a directory called "realplayer" in your home directory?

If not, please execute

```
ls -a .real*
```

in your home directory. This will list all hidden directories that start with ".real".
A dot in front of a directories hides it.

To see hidden directories with a normal ls command, add the option -a

Your previous ls output shows us that you have all libraries necessary to play DVDs.


Thus, installing totem-xine is the best option, I think.

---

### Post by lila on 2005-12-08
[QUOTE=Estariel]The realplayer error means that the installation program couldn't copy the executables to the places where they are supposed to be (which was to be expected, since the installer didn't have root privileges).

This is a far shot, but it might have installed something in a hidden directory in your home directory (this is where most stuff goes that cannot be installed system wide.)
You might even have a non hidden directory...

Is there a directory called "realplayer" in your home directory?

If not, please execute

```
ls -a .real*
```

in your home directory. This will list all hidden directories that start with ".real".
A dot in front of a directories hides it.

To see hidden directories with a normal ls command, add the option -a

Your previous ls output shows us that you have all libraries necessary to play DVDs.


Thus, installing totem-xine is the best option, I think.[/QUOTE]

Right.  This is what I get when I do the command in Terminal:  
ls: .real*: No such file or directory
I'm not sure what you mean by doing the command in the home directory (which I assume to be the same thing as home file?)  There is no non-hidden directory in that either, all checked, everything there is something I know about.

Can't find totem -xine in either synaptic or add application.  The only thing xine-based I can find there is Kaffeine.  Is that any good? or how can I find totem-xine?

I must say, I'm impressed, you are very efficient....  Thanks for your help!
Lila:smile:

---

### Post by Estariel on 2005-12-08
kaffeine is KDEs media player, and I prefer it over totem (but that is also because I use KDE instead of GNOME).
But I fear a KDE application would look rather ugly on your GNOME desktop, and I would try to get totem-xine instead.

I had a look at packages.ubuntu.org/breezy/gnome
and found the following:
```
totem-xine (1.2.0-0ubuntu3) [universe] 
A simple media player for the Gnome desktop based on xine
```

So it _should_ be there.

Are you sure you have universe enabled?

---

### Post by lila on 2005-12-08
[QUOTE=Estariel]kaffeine is KDEs media player, and I prefer it over totem (but that is also because I use KDE instead of GNOME).
But I fear a KDE application would look rather ugly on your GNOME desktop, and I would try to get totem-xine instead.

I had a look at packages.ubuntu.org/breezy/gnome
and found the following:
```
totem-xine (1.2.0-0ubuntu3) [universe] 
A simple media player for the Gnome desktop based on xine
```

So it _should_ be there.

Are you sure you have universe enabled?[/QUOTE]

...sorry for the delay... I do have universe, and on looking through again, not by section but by "not installed" (status) I found it and installed it, hence the delay.  Now I have put a DVD in, and I get the copyright warning plus the extra add-ons (about the making of...), but not the actual film.  It is a perfectly legal DVD, which I have watched before, so it's not the disk.
Anyway, thanks again for your help, but I'm going to have to leave this till tomorrow now, it's half past midnight and I need to work tomorrow...
Good night,
Lila (is there a sleepy smiley?)

---

### Post by doitashimashite on 2005-12-08
A RealPlayer installation procedure that worked for me:

Download RealPlayer from [http://www.real.com/linux/](http://www.real.com/linux/)

$ cd browse_to_your_download_folder
$ chmod 700 RealPlayer10GOLD.bin
$ sudo ./RealPlayer10GOLD.bin

Enter the complete path to the directory where you want RealPlayer to be installed.  You must specify the full pathname of the directory and have write privileges to the chosen directory.

Directory:  [/home/chua/RealPlayer]: /opt/RealPlayer

You have selected the following RealPlayer configuration:
Destination:            /opt/RealPlayer
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y

enter the prefix for symbolic links [/usr]: /usr

Hit Enter and that's done.

---

### Post by Estariel on 2005-12-08
[QUOTE=lila]...sorry for the delay... I do have universe, and on looking through again, not by section but by "not installed" (status) I found it and installed it, hence the delay.  Now I have put a DVD in, and I get the copyright warning plus the extra add-ons (about the making of...), but not the actual film.  It is a perfectly legal DVD, which I have watched before, so it's not the disk.
Anyway, thanks again for your help, but I'm going to have to leave this till tomorrow now, it's half past midnight and I need to work tomorrow...
Good night,
Lila (is there a sleepy smiley?)[/QUOTE]

That is very weird.
Can you try right-clicking in the video area of the player and chose "DVD Menu" in the menu that should show up? (The menu shows up in Kaffeine, and since both of them are just frontends for xine, Totem shouldn't behave any different...)
If that doesn't work, please try a different DVD to test whether it is the DVDs fault (for not supporting standards, etc.) or a setup problem.

I have for example a problem with the 4th season of the show "Alias".. None of the DVDs will play if I run Kaffeine with my normal user account, but it works if I run it as root. All my other DVDs work... I have no idea why that is the case...
I didn't have that problem with my gentoo installation though. (But i got rid of it :) )

---

### Post by lila on 2005-12-09
[QUOTE=Estariel]That is very weird.
Can you try right-clicking in the video area of the player and chose "DVD Menu" in the menu that should show up? (The menu shows up in Kaffeine, and since both of them are just frontends for xine, Totem shouldn't behave any different...)
If that doesn't work, please try a different DVD to test whether it is the DVDs fault (for not supporting standards, etc.) or a setup problem.

I have for example a problem with the 4th season of the show "Alias".. None of the DVDs will play if I run Kaffeine with my normal user account, but it works if I run it as root. All my other DVDs work... I have no idea why that is the case...
I didn't have that problem with my gentoo installation though. (But i got rid of it :) )[/QUOTE]

I have just put it in again, and I get Totem firing up and then fairly immediately a new window on top that is called "select files", giving me these files:
AUDIO_TS
images
VIDEO_TS
Belleville.htm;?    (Belleville is part of the movie title, the ;? is an exact copy of waht it says).
When I click on Video, a new list of bits of film comes up, only some of which (as said) work.  The the ones that work are all marked .VOB, the others are marked .IFO or .BUP and have the Gnome foot on them.
If I close the whole lot, including Totem, and restart Totem, I can rightclick the video area, but it comes up not active (all the lines in grey).  If I click on play the DVD in the menu again, it starts the other window again....  So I don't know what it would do if I could rightclick it.
Can I try another DVD? not without difficulty.  I have one other one, but that doesn't get recognised at all (it was a freebie with the paper a couple of weeks ago, will try it in the DVD player at work to see if it's ok).  Apart from that, I haven't got any.  We're a not very technological household, we don't have a TV, and so far always had computers way too old to cope with DVDs... so I guess I'm going to have to go and rent or buy one?  I'll see what I can do tomorrow...
Lila

---

