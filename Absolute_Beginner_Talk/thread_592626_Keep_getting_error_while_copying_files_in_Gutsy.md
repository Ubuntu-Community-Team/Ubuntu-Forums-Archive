---
title: "Keep getting error while copying files in Gutsy"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-10-26
Error "Too many open files" while copying "/home/ahm...thing.mp3". Do you want to continue?
The same time this happens, totem stops playing the music and gives me an error 'location not found' and all the music files lose there pretty musical note icon which is replaced with a sheet of paper icon (not text) and they lose there association with any music playing app. Processor usage is spiking alot and at times just goes to 100%ish and stays there. I cant access any other folders.
Rebooting is the only cure thus far. 
Ahh reminds of windows 98
This never happened in feisty btw and only started today; I did a clean install a couple of days ago and am copying files over now
Any ideas anyone?:mad:

---

### Post by MegaJim on 2007-10-26
how are you copying the files?  If you're using Gnautilus try it in a terminal.

---

### Post by boyturtle on 2007-10-26
Really not practical to use terminal as have about 3000 musical files and I need to copy each individually and I need to inspect each of their properties and make adjustments as needed
When I checked system monitor, it was nautilus and gnome system monitor that were chomping away at the resources so I ended the nautilus process and it seems to have settled down and I can play the music again and all app associations have resumed. Nautilus is still showing as a sleeping process tho

---

### Post by MegaJim on 2007-10-26
Ah,

try starting nautilus from the command line

```
nautilus $HOME
```

when the error pops up, check the command window for any more deatiled info and post them here or google them.

You might also try

```
dmesg | tail 
``` just after the error occurs

---

### Post by boyturtle on 2007-10-26
It has done it again, although the processor usage hasnt gone thru the roof yet, it has started to misbehave with the music files. I sohould add at this point that I am copying music files from an ntfs drive and then deleting them

Ran dmesg | tail in terminal as soon as it happened and got
[INDENT]> [   39.643984] /dev/vmnet: hub 0 does not exist, allocating memory.
[   39.644125] /dev/vmnet: port on hub 0 successfully opened
[   39.644273] bridge-eth0: enabling the bridge
[   39.644389] bridge-eth0: up
[   39.644489] bridge-eth0: already up
[   39.644492] bridge-eth0: attached
[   40.270645] NET: Registered protocol family 17
[   43.551658] NET: Registered protocol family 10
[   43.551815] lo: Disabled Privacy Extensions
[   48.304845] eth0: no IPv6 routers present
[/INDENT]

---

### Post by MegaJim on 2007-10-26
that doesnt show anything, what about the terminal window, did it give you some errors when it crapped out?

---

### Post by boyturtle on 2007-10-26
Eek, this error was in terminal, waiting for me when I got back in
> Initializing gnome-mount extension
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-certified.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-certified.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-urgent.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-urgent.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-multimedia.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-multimedia.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-plan.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-plan.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-downloads.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-downloads.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-favorite.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-favorite.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-ohno.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-ohno.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-money.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-money.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-package.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-package.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-danger.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-danger.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-shared.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-shared.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-sound.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-sound.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-web.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-web.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-art.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-art.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-documents.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-documents.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-sales.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-sales.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-new.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-new.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-default.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-default.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/stock_mail-priority-high.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/stock_mail-priority-high.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-personal.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-personal.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-cool.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-cool.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-presentation.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-presentation.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-readonly.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-readonly.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-mail.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-mail.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-people.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-people.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-system.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-system.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-handshake.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-handshake.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-OK.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-OK.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-generic.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-generic.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-camera.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-camera.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-photos.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-photos.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-pictures.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-pictures.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-draft.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-draft.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-unreadable.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-unreadable.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-distinguished.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-distinguished.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/48x48/emblems/emblem-marketing.png into memory: Failed to open file '/usr/share/icons/gnome/48x48/emblems/emblem-marketing.png': Too many open files
** Message: Failed to load /usr/share/icons/gnome/32x32/emblems/emblem-important.png into memory: Failed to open file '/usr/share/icons/gnome/32x32/emblems/emblem-important.png': Too many open files
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
Unable to create TCP socket
 Dont know if any of that means anything to you, or anyone else?

---

### Post by boyturtle on 2007-10-26
the above was after I put in 
> nautilus $HOME in terminal

IUt didnt do anything for ages before I went out, and that was what awaited my return

---

### Post by MegaJim on 2007-10-26
Well, those files its having a problem with are the little overlays on your icons that tell you what the properties of the file are.

It seems like nautilus is running out of memory while trying to show all the files in your directories.

---

### Post by boyturtle on 2007-10-26
I'm running 1Gb of ram and 1.5 Gb swap file. Never had this problem with feisty. 
Could it be something to do with me accessing the ntfs partition? Could that be causing nautilus to go all flakey on me?

---

### Post by Boondock5 on 2007-10-27
> **boyturtle said:**
> Error "Too many open files" while copying "/home/ahm...thing.mp3". Do you want to continue?
The same time this happens, totem stops playing the music and gives me an error 'location not found' and all the music files lose there pretty musical note icon which is replaced with a sheet of paper icon (not text) and they lose there association with any music playing app. Processor usage is spiking alot and at times just goes to 100%ish and stays there. I cant access any other folders.
Rebooting is the only cure thus far. 
Ahh reminds of windows 98
This never happened in feisty btw and only started today; I did a clean install a couple of days ago and am copying files over now
Any ideas anyone?:mad:



I had the same thing happen to me. I was copying mp3 files to a flash drive,(w/only minimal trouble out of that damn windows based flash drive crap thing) after about 30 song transfers, I get the "Too many open files" thing and everything as far as apps went into slow motion.

So now, forward to today, everything running slightly slower than usual, (This thing screams with Ubuntu on it) and it doesn't want to play music( it will, but the video effects thing doesnt work from Movie player(Totem.)

I've been reading everywhere about this "too many open files" thing and no one seems to have a fix for it in Ubuntu. Am I just missing something? 

If, someone knows a fix for this, I'll need to be walked through the fix. As I am severely mouse impaired. I do have a permanent Command Prompt box  to use so I just need to know very specific instructions.

I managed to do the Gutsy Upgrade by myself so I'm not a complete dummy, just need to know where to start and what to type where.


Thanks in advance,  Matt

---

### Post by Boondock5 on 2007-10-27
bumpers,

---

### Post by boyturtle on 2007-10-27
'it went wild again and stopped reading the music files. I stopped nautilus as usual and got a dialog box saying> Nautilus can't be used now, due to an unexpected error.

Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

Any ideas anyone?

---

### Post by LaLeX on 2007-10-28
Hello!
Just happened to me too... I was trying to copy some files over an smb mount, and the error appeared....

Any ideas so far??

---

### Post by Boondock5 on 2007-10-28
Sounds like we all got the same problem. I managed to fix that part of mine, atleast patch through it by upping the limit of the number of files that can be open to 2048. but now something is running in the background slowing up the whole OS.

---

### Post by gate on 2007-10-29
I am having the same problem, copying files from a big fat32 USB drive. One detail I have noticed from the other posts: most or all were copying mp3 files, as I was. could it be file type specific? unlikely, in my mind, but possible.

EDIT: Forgot: yes, its a gutsy clean install on a celeron M with 1 GB ram.

---

### Post by gate on 2007-10-29
I filed a bug report.
 [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/158248](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/158248)

---

### Post by boyturtle on 2007-10-29
It seems like this problem isnt restricted to copying music files between drives/partitions. I copied all the music files en masse to the ubuntu partition and that worked ok; the fun began when I started to copy individual files between folders
Only seems to do it with music files tho, all other formats I have tried have worked ok:confused:

---

### Post by philinux on 2007-10-29
I would use the sudo cp xxx xxx  command from terminal

[http://www.linuxcommand.org/lts0050.php#cp](http://www.linuxcommand.org/lts0050.php#cp)

---

### Post by Scratches on 2007-10-30
Add my wife and I to the list of Gutsy users having the same problem on two different computers none of which are running a duel boot. Our computers are not sharing anything but the router.  We are randomly getting...

The folder contents could not be displayed. 
Sorry, couldn't display all the contents of "folder name".

and ...

Too many files open errors.

We don't have many files nor folders open at one time, just reorganizing a lot of individual .mp3s from folder to folder.   So I can't explain either of these errors.

Stopping the Nautilus Process and letting it automatically restart fixes it until it happens again.

Hope this gets fixed soon, thanks.

Tom

---

### Post by Kanji_Man on 2007-10-31
I was also encountering this problem when reorganizing large numbers of sound files. I disabled the nautilus preview for audio files:
Edit> Preferences> Preview> "Preview sound files:" - Never

I dont think this really resolves the bug, which I expect has something to do with trying to generate large numbers of audio previews in a short period of time, but atleast I avoid the problem.

---

### Post by iggee85 on 2007-10-31
I'm also getting this error playing/copying/deleting .flac files off an external USB hard drive (ext3).
Ending nautilus fixes it until the error pops up again.

---

### Post by Scratches on 2007-10-31
> **Kanji_Man said:**
> I was also encountering this problem when reorganizing large numbers of sound files. I disabled the nautilus preview for audio files:
Edit> Preferences> Preview> "Preview sound files:" - Never

I dont think this really resolves the bug, which I expect has something to do with trying to generate large numbers of audio previews in a short period of time, but atleast I avoid the problem.

I just tried this and unfortunately it doesn't solve the problem.  I even changed the setting and rebooted the computer and the copy files / folder display bug pops its ugly head again.

Tom

---

### Post by Boondock5 on 2007-11-06
I'm still waiting on a fix for this, It got so bad I ended up wiping the drive and starting oveer about a week ago.

---

### Post by NoSuchNick on 2007-11-07
I saw this problem here, too. Seems like hovering over a MP3 causes nautilus to open several pipes which get never closed.

Turning of previews for audio solved the problem for me.

You can use the following command to show the number open FIFOs to see if you have the same problem::

```
lsof -c nautilus | awk '{ print $5; }' |sort | uniq -c | grep FIFO
```

This number was steadily increasing on my machine before i turned of audio previews.

---

### Post by Boondock5 on 2007-11-07
At the risk of sounding llike a total n00b, (which I am to ubuntu.) could you supply the exact command and how-to to make this happen (turning off previews), My terminal window and I together = bad news

---

### Post by NoSuchNick on 2007-11-07
> **Boondock5 said:**
> At the risk of sounding llike a total n00b, (which I am to ubuntu.) could you supply the exact command and how-to to make this happen (turning off previews), My terminal window and I together = bad news

Kanji_Man described it in the post above (#21).

---

### Post by Boondock5 on 2007-11-07
> **NoSuchNick said:**
> Kanji_Man described it in the post above (#21).

Thanks just did that now to see if it works...

---

### Post by Boondock5 on 2007-11-07
I just copied an assload of files to my flash drive. NO MORE "TOO MANY OPEN FILES"!


YEEEEEHAAAWWW! Thanks guys!

---

### Post by hanzomon4 on 2007-11-30
It's not just copying files, it happens with anything. Randomly my system will refuse to launch applications or do anything. When I try to launch a command from the terminal I get the error. I have to logout to get my system back.

---

### Post by gobbluth on 2007-11-30
> Edit> Preferences> Preview> "Preview sound files:" - Never

This worked! I couldn't believe how easy the fix to this problem was after I had been Googling this error for so long. 

This thread should be stickied or this bug should be fixed soon because this has been a huge issue for me when I copy files to my mp3 player, to my external hard drive, and around on my computer.

Thank you!

---

### Post by Cryptic1911 on 2007-12-08
Sweet. I think the disabling of audio previews will fix my issue too. I did the lsof command and it seemed to stop at 1012 for some reason, but if i restarted nautilus it was at 10 until I hovered over some mp3s.. then it jumped to 50 really quick. After I disabled the previews it never went above 10. What's odd is that although my audio previews were "on", it never previewed anything (which was the way I wanted it). If it had, I would have immediately turned the option off


:guitar:

---

### Post by rlyounker on 2007-12-19
I am having the same problem. I am running Gutsy as well. I am organizing my music/mp3's/albumArt/etc. I am not so much copying files (other than making a copy of "cover.jpg" and renaming it "AlbumArtSmall.jpg") as much as I am moving them from one folder to another. I heard someone say they  submitted a bug report.... how do I put my name on that? How do I fill out my own?

Thanks for the help.

YonK

---

### Post by Abboudi on 2007-12-25
"YEEEEEHAAAWWW! Thanks guys!"

mind me wanting to know how to flush/clear the mem used by naut,? (without having to restart it)

---

### Post by DarkDancer on 2007-12-31
Disabling previews isn't a fix it's a patch a real fix needs to come along... ;)

I have the problem and my previews were never on. I got around it by using Gnome Commander. Works brilliantly.

---

### Post by jondecker76 on 2008-01-10
I've noticed this problem on several computers (all running Gutsy) - all while trying to copy songs onto an MP3 player.. This seriously needs fixed

---

### Post by emeriste on 2008-02-19
> **hanzomon4 said:**
> It's not just copying files, it happens with anything. Randomly my system will refuse to launch applications or do anything. When I try to launch a command from the terminal I get the error. I have to logout to get my system back.

I seem to have this same problem. You probably don't have to logout in order to fix it. I am able to fix it (temporarily) by opening a terminal and typing "killall nautilus".  Nautilus will immediately start up again and work. At least this way you don't have to close all your apps and start over. 

For me this began happening when I started listening to a lot of music (.flac). I'm hoping that the fix mentioned above works. Hopefully there is a real bug fix for this in future updates, because this is an annoying one. :)

- Em

---

