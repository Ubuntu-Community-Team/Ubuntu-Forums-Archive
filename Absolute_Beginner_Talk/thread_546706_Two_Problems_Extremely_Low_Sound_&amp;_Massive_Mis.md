---
title: "Two Problems: Extremely Low Sound &amp; Massive Missing Data"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Overquoted on 2007-09-09
I am **extremely** blonde. But first thing's first.

I bought a new motherboard to replace the one that died in April (finally). It's an ASRock P4i65G with onboard sound. The chip is ICH5. Now, with Master Volume, PCM and Speaker Volume up all the way, I have incredibly low sound. I'm using it with ALSA. Also, PCM is the only thing that really affects the sound. The motherboard is not hooked up to the audio plugs in the front of the case (I unplugged the case cable to make sure it wasn't a weird issue involving sound being halved). I would try to install the sound driver manually to see if it'd help, but the site seems to've disappeared (it redirects to Parent Directory). So I don't even know what driver it calls for to use modprobe snd-(driver) command.

Much bigger, dumber issue. When I reinstalled Ubuntu (the first time - I had to do it a second after updating/installing software made Ubuntu take 2-7 minutes loading apps), GRUB detected WIndows XP on my 80gb Western Digital. This was from April, before the motherboard fried. It asked me which OS I wanted to load, and because I'm an idiot and had time on my hands, I clicked XP. It flashed a blue screen for maybe a 10th of a second, then rebooted the computer.

GRUB popped up again...and this time I tried Safe Mode. Same result (not surprising). By now, I'm feeling just dandy. And when I'm feeling dandy, I get reaaal dumb. So when GRUB asks me again, I click on the option "Boot from last known restore" or whatever the option is. Same result, so I just decide to boot Ubuntu and reinstall XP later.

Now I've reinstalled Ubuntu (second time in one day). So I go to test a .mkv file (after installing codecs) that was on my 80GB hard drive. ...and everything is missing. The WIndows folder is still there, Program files and folders are as they were in April, but most of the specific user info under Documents and Settings is gone (Dektop folder missing) and two extremely size-heavy folders containing music and fansubs are gone (they used to be in the C:// directory back when the HD was C - ie, C/Anime). Ubuntu reports that 68 gigs are free...and I had at least 30-40GBs of anime on there.

The hard drive is not wiped. XP has not tried to reinstall itself (judging by the programs and other misc. files in the Windows folder) and I doubt it really had time to delete over fifty gigs of files in that tiny, TINY amount of time. However, when I run testdisk, it sees nothing to recover. When I run ntfsundelete, it sees 0 files for possible recovery. Except for stupidly enabling write with NTFS Config Tool, I've not done anything to the hard drive.

I really want to recover at least a LIST of what I had, if not the files themselves. Not to mention knowing why Windows (evil thing that it is) deleted those specific files and folders (and not everything). The only personal file I've found (outside of the program folders) was a vlc snapshot under Documents and Settings/Owner (my profile from XP)/My Documents/My Pictures. But I know that I had more misc. files in Documents and Settings.

Oh, and GRUB no longer lists XP as a possible OS. Just the various Ubuntu options.


I'm currently running a program called foremost, scanning for .avi. It's been scanning for at least thirty minutes. The Output folder has on empty text file in it (well, a text file of 0 bytes) and an empty folder. So I'm guessing no results yet. Meanwhile, a friend suggested grabbing a '98 install disk and accessing fdisk through the DOS tool. Or something along those lines. :) I might try it before I go to bed, but I'm pretty tired. Been at this for at least thirteen hours. *twitch*

---

### Post by swoll1980 on 2007-09-09
try putting the headphone volume up see what happens if this works you have to right click the sound thingy in the taskbar go to preferences and switch the wanna be master to headphones

---

### Post by Overquoted on 2007-09-09
I'm not seeing a 'Headphone' control under ALSA or OSS.

---

### Post by swoll1980 on 2007-09-09
try going to preferences and adding one, or try typing  the command   alsaconf   into a terminal

---

### Post by Overquoted on 2007-09-09
'Command not found.'

---

### Post by Overquoted on 2007-09-09
I have just recalled something. During the first install, I accessed the 80GB drive (the one with missing data) and attempted to play a .mkv file from it. It gave me a "need codecs" message, which is why I remember now. So the data was there after my silly attempts to load XP (even though I knew better).

So trying to boot the thing up wasn't the cause, as far as I can tell. It must've happened during the second install (and I didn't partition the 80gb) or during the mounting process. So, is the data still there?


Though...I guess it could've happened when I installed some software from the Package Manager and updated everything. I think I attempted to enable write support after that. Maybe whatever caused the extreme slowness in app loading caused the missing data? I don't know. :S I have a few things left to try, but if anyone has any ideas, let me know.  :confused:

~~~When I switch to OSS, none of the volume controls affect the sound. Only PCM under ALSA affects the sound at all.

---

### Post by Overquoted on 2007-09-24
...Still no relevant progress. And no help. I don't have the money atm to buy another HD to install a Windows OS onto to see if I'm able to recover my missing data that way.

The sound problem I gave up on. I fished out some old (powerful) speakers. Basically, still really low sound controlled only by PCM, but I can hear it with my speakers. It just crackles sometimes like the sound is too high.

Now I've discovered a video problem. On Windows XP, even running under Style XP and running a number of programs, I never had a problem with video. But under Ubuntu, I can't seem to play .mkv files. A handful will crash the app 
(Totem or VLC) entirely, while others will skip scenes or skip frames (the latter giving the video a jerky appearance). VLC gets the skipped scenes, while Totem gets the jerkiness, along with a weird bright neon green in the background.


I'm half tempted at this point to wipe the drive Ubuntu is on and just install Windows on it. But if I do that, I know I won't have the patience to reinstall any Linux system again...ergo, no dual-booting.

---

### Post by Overquoted on 2007-09-24
Forgot to add that when I play .mkv files, Ubuntu acts like I'm maxing out my CPU. But if that's true, then Ubuntu makes XP look very resource-friendly.

---

