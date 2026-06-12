---
title: "VLC crashing, don't know how to solve it"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by nicknormal on 2006-08-04
Greetings.

I'm a new Linux and Ubuntu user.
on Windows i'm a big fan of VLC player.

i've managed to install VLC using Synaptic Package Manager and have .avi files (xvid, divx, etc. encoding) stored on local hard drive.

however when i open the file in VLC, the player will resize (like it's ready to play) and then quickly crash. i haven't seen a single frame of video yet.

in the System Monitor, under Processes, i noticed the process for VLC (wxvlc) will jump to about 30% CPU resource, and then disappear.

the player is crashing with standard .avi files! help! on an usb-connected drive i can't watch .mpg files either! this player is superb on Windows, and i don't want to install Windows on another machine! help me help ubuntu work! what am i doing wrong!??!?!!!

regards,
Nick

---

### Post by scxtt on 2006-08-04
run it from the command line, then you can see any crashing info ...

$:> vlc /path/to/video

---

### Post by nicknormal on 2006-08-04
i just did that, and it responded with:

X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 141 (XVideo)
Minor opcode of failed request: 19 ()
Serial number of failed request: 80
Current serial number in output stream: 81
pure virtual method called
terminate called without an active exception
Aborted

---

### Post by cantormath on 2006-08-04
> **nicknormal said:**
> Greetings.

I'm a new Linux and Ubuntu user.
on Windows i'm a big fan of VLC player.

i've managed to install VLC using Synaptic Package Manager and have .avi files (xvid, divx, etc. encoding) stored on local hard drive.

however when i open the file in VLC, the player will resize (like it's ready to play) and then quickly crash. i haven't seen a single frame of video yet.

in the System Monitor, under Processes, i noticed the process for VLC (wxvlc) will jump to about 30% CPU resource, and then disappear.

the player is crashing with standard .avi files! help! on an usb-connected drive i can't watch .mpg files either! this player is superb on Windows, and i don't want to install Windows on another machine! help me help ubuntu work! what am i doing wrong!??!?!!!

regards,
Nick

use this:
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by nicknormal on 2006-08-05
i used Automatix to install MPlayer, codecs, etc.

but still MPlayer crashes, VLC crashes, Totem crashes, whenever i open these .avi files!! these files played fine yesterday on my WinXP machine. and worse yet is in the Ubuntu file window, the file is given a PREVIEW thumbnail!!! as if something can read the file and pull an image from it! but these media players can't play them! help!

---

### Post by scxtt on 2006-08-05
the vlc output error is pretty cryptic (worthless) - but this line makes me wonder if you don't have sufficient space in memory:

X Error of failed request: BadAlloc (insufficient resources for operation)

what do you get if you just open vlc, not specifying a media file?

---

### Post by nicknormal on 2006-08-05
in terminal if i just type 'vlc' it opens VLC media player and returns this in terminal:
VLC media player 0.8.4 Janus

looks good. VLC just as is doesnt crash.

this machine has 256Mb of SDRAM. do you think i need more, or is there a way to allocate HDD space as virtual RAM? i know movie files are big (700Mb) but shouldn't it at least PLAY the files! not just crash immediately?!?

regards,
Nick

---

### Post by scxtt on 2006-08-05
yeah, it looks like your lack of RAM is biting you in the *** ... you should have *at least* another 256MB of swap defined also ... you can monitor your memory usage by typing top in a terminal or gnome system monitor ...

---

### Post by nicknormal on 2006-08-05
scxtt,
well it looks like i actually do have 721.6Mb of swap space allocated.
so i don't know where the problem is.

any other ideas?

---

### Post by kurniawands on 2006-08-05
hope this might help you...

about 90% of my "crashing application" problem on dapper is always solved by doing update and upgrade. mean... running sudo apt-get update and sudo apt-get upgrade from the terminal.

the rest is by looking for a broken applications in synaptic. worst, i remove them from the library and reinstall those application from the beginning. ;)

---

### Post by nicknormal on 2006-08-05
i've done all that.

i just did a complete fresh install of ubuntu. updated my packages, installed VLC clean with no other large installs. Totem and VLC both crash outright.

new install! i have swap space, system monitor shows the apps fine if i just launch them, then i open a movie file and bam, they crash, disappear.

i transfer the movie files to external HDD and move over to my XP box, they play fine, two minutes after they crash on Ubuntu.

i'll try to solve this, but if by this weekend i don't have a solution, i fear this machine will have to become another MS Windows box. really DONT want to do that :-( :-( :-(

---

### Post by nicknormal on 2006-08-05
ughhhhhhhhhhhh

sometimes the most obvious solution solves the problem:

i was curious, what if there was a native problem with the graphics card? the card that came with the box is a dual-vga Matrox card. device manager didn't read any problems with it, but the various players (Totem, VLC, MPlayer, all reliable!) were just crashing.

so i swapped out the Matrox for a GeForce3 that i still have installed in my WinXP box. reinstalled Ubuntu fresh. updated all packages, installed the necessary players, codecs, etc.

double-click a file and BAM it plays! all fine.

i'm playing files now from an external HDD fine. copying over locally to test them. but it's something on the Matrox card obviously, probably a conflict with the dual-VGA head that i didn't think of before.

so now i have to go out and buy a good but basic card. low-fi solution hi-fi results.

thanks y'all. pfft.

Nick

---

### Post by adds2one on 2006-08-31
The error you were experienceing is a known bug. You were right that it is about the BadAlloc line in the error output. Here is the report about it:

[https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/38939](https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/38939)

It has to do with how much RAM is on the video card.

Looks like I am going to have to either go back to Windows on my desktop or buy a new video card.

---

### Post by cian42 on 2006-10-30
i have the exact same problem.
so there is no fix to this except buying a new video card?:(

---

### Post by SolaceDisparaged on 2006-12-06
i have a geforce 600GT with 128MB onboard, why is it that I'M getting this error????
My video card should work just fine!!

---

### Post by DrMilo on 2006-12-19
VLC works fine for me if I close Firefox but I get this crash with Firefox open. Also Rhythmbox does something similar. I simply refuse to believe this is memory because I'm doing nothing different now compared to what I was doing before and everything worked then. I'm talking for months here. Anyway my system performance seems fine even when this problem happens so there's memory available.  Sometime around the upgrade to Firefox 2 and Flash 9, both were close together, my sound and video started having problems. It has something to do with running Flash in Firefox and then trying to run  any other application that uses audio. Untill I shut down Firefox the second application won't work. I've up and down graded Flash and that simply doesn't help. I'm reluctant to downgrade Firefox. How could a browser do this? I don't know.

---

### Post by rundgren on 2006-12-20
I also have an old Matrox G450 card, and I'm having problems with crashing videoplayers.. A lot of videos work fine, though.. For those that don't, my workaround is: Opening vlc (not by clicking on a video file, but by running vlc), open preferences and go to Video -> Output modules, switching on "advanced options" and changing "Output module" to "X11." Then all videos will play, but hardware acceleration of video zooming is not available. My workaround for getting smooth videoplayback is to simply set my screen resolution to the resolution of the video :-)
(Yes, I've realized I need to get rid of this 7 year old sh#$y card... Going for something cheap from NVIDI I think..)

PS: I've also experienced a crashing issue with vlc unrelated to this problem (I think), but deleting the file "/home/<username>/.vlc/vlcrc" (as suggested on vlc webpage) fixed this.

---

### Post by yefymenko on 2007-04-02
it seems that I am having the same type of problem, but the solutions that I have seen here don't seem to apply.  I have a nvidia 7600 oc graphics card with 256mb ram.  The latest drivers.  I have tried to uninstall vlc through synaptic package manager and reinstall, same issue.  I have a AMD 64 processor, I don't know if that matters.  I have been able to play all kinds of files before on the same machine with the same setup, but I had vlc crash in the firefox browser and now it will not play anything at all, not even .avi.  It seems that when I open a file with it it plays the first frame or so and then shuts down.  If I open the player with out playing a file it opens fine, but will not play anything that I try to open.

Any other suggestions.....

---

### Post by yefymenko on 2007-04-03
I seem to have answered my own question.  For some reason uninstalling mplayer codec, got my vlc to work fine again.

---

### Post by myddewji13 on 2008-02-07
I have the same prob as you..cant seem to fix it by geting rid of the mplayer codecs...so now what do i do?

---

