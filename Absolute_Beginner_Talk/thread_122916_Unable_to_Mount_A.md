---
title: "Unable to Mount A: ?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by stanz on 2006-01-28
After days of messing up~ somehow... I'm still trying to get online~
by trying to figure out- how to set up an internet connection, to my isp.
I've printed out the "DialupModemHowto", and am starting at the beginning again.
I saved the "scanmodem.gz" tool, on a 3.5 floppy, and cannot open the drive.
Maybe i'm screwing up, by doing it the "win" way?, 
*->Places->Computer->Computer-File Browser= *shows[I] 'floppy', 'cd-rom', 'cd-dvd', 'filesystem'.
[/I]'right-click', or 'any click', to open floppy, brings window-[I] 
"Unable to Mount Volume", [/I]with more details telling-[I] 
"Error: given UDI is not a mountable volume".
[/I]I can't find info, to understand the workings behind this. 
They all respond the same~ 'cept...i've got tunes playing fine  \\:D/

How do i get into A: drive or floppy~ to get started with modem stuff?
I noticed 'root' is the owner~ now how do i get permission...?

Continuing my search....Thanks                      :confused:

---

### Post by Terry of Astoria on 2006-01-28
Sometimes I can mount windows-formatted floppies better with the command,
```
sudo mount -t vfat /dev/fd0 /mnt/floppy
```
Of course, since there was no directory of that name by default in my Ubuntu distro, I had to first create it with:
```
sudo mkdir /mnt/floppy
```
Then I could copy files from the floppy which was mounted at /mnt/floppy

Don't forget to 
```
sudo umount /mnt/floppy
```
before removing the disk.
However, is the file on your windows partition? If so you can mount that too. 
There's a thread on that somewhere.

---

### Post by stanz on 2006-01-29
Thanks Terry, I'll work this asap...

~* Do I understand this right ~ It's not the 'hardware' i'm mounting, 
 It's the (win) format?
> "Sometimes I can mount windows-formatted floppies" ========================================
> "is the file on your windows partition?  
Nope~ I'm keeping it strictly "*Linux in my box*". 
Ubuntu v1.5 in one, & Xandros v3 in the other. When i learn partition stuff,
I'll have Debian, but~ "I'm done doing Windows."
[U]
Update:[/U]
*I had to come back asap*... It didn't work for me~*first dozen tries*~ I didn't expect
it to,,LoL... I need to grasp the way someone explains those command options.
Yours are kewl Terry...its the others that followed!
I found out my disk had 'gif's & jpeg's on it- which somehow- i need to relay to it.

---

### Post by funkjunkie on 2006-02-27
thank you, thank you, thank you thank you thank you, thank yu, thank you, thank you kindly sir.

is it bad etiquette to thank a post? i only do it when i cant contain myself anylonger.  is it jus wasting space.  ijust cant help it, i justget so happy over the community support here.

---

### Post by stanz on 2006-02-27
Hi All,
That's kewl~ funkjunkie is one happy camper! 
I've had little success, trying to get those disks read. I've got permissions
all good, and fiddled with fstab.
It reads it all as 'read-only' files, so i thought to change the 'auto' to 'vfat',
then trying 'gif' & 'jpeg'. I got a glance of thumbnails once~
but, had already pulled out the disk...grrrrr!
I also think i learnt, to 'unmount' the drive- 'before' ejecting the disk!
I do like the ease of the 'mounting drive'- desktopett thing they got.
Well,,, i'll be checking in here- for any new ideas!
Thanks all....Laterzzzz

---

### Post by Bartender on 2006-02-27
Hi, stanz -
Yeah, I learned the hard way that floppies don't behave the same in Linux.  You put the floppy in, then mount it using the command line, then when you're done you unmount BEFORE popping that floppy out.  I've got a couple of floppies that are just flat unusable - can't format them or anything - after popping them out of the Linucx PC the Windows way, sticking them in my Windows machine & wondering what was wrong...
I believe Dapper will handle floppies more conveniently...

---

### Post by stanz on 2006-02-28
Hi All,  Hey Bartender,
I sure hope Dapper Deals Wit Dis Problem! I've now tried to get pics off a cd, for a webpage...and naadda!    :evil:
Now it's beyound personal tweaking/playing around.
Like~ do i NEED M$ now...to do these things? aaAAAHHHH !!!
Below is a pic, with details.
Taking Deep Breath...
_________
[Screenshot-Mount Error.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=6529&stc=1&d=1141158047")
_________

---

### Post by Bartender on 2006-02-28
Whoah -
That sure doesn't look like the same error message I got...
"dev/hdc" isn't your floppy

---

### Post by stanz on 2006-03-01
For Sure...Whoah! 
Nope...one of those- mini cd's, from a digital camara thingy...
not the place for this thread- maybe... but i was bummed when it
wouldn't mount- in a snap!
It's hitting 2am & i'm doing an upgrade... gonna try to fix this..
before stomping my feet around! LOL

---

### Post by dvarsam on 2006-03-01
When you posted this, I had just created a Tutorial on this...

Read on the Article#: 137737

Tutorial &#8211; How to "Mount"/"Umount" Partitions 

Hope it helps you...

---

### Post by stanz on 2006-03-07
Hi All.. & Thanks much dvarsam!!
That was well explained & in depth. I'll work on this when time permits,
and keep this link handy!

[Article#:137737, Tutorial &#8211; How to "Mount"/"Umount" Partitions]("http://www.ubuntuforums.org/showthread.php?t=137737")

---

