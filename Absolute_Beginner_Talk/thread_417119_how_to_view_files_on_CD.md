---
title: "how to view files on CD?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by HiJolly on 2007-04-21
FIRST:  I have no Internet / network on my laptop, though I do on my XP desktop.  The laptop had no OS at all, so I installed Kubuntu but haven't done anything with it yet.  Don't know unix/linux but do know windows. 

Maybe I shouldn't be jumping into Kubuntu, I can't see any files!  I have 6.10 (just installed) and just burned the 7.04 Alt CD but can't see anything on it, and it isn't starting up for me.  

in DOS I could dir but what do I do in K?  


HiJolly

---

### Post by Toontwnca on 2007-04-21
> **HiJolly said:**
> FIRST:  I have no Internet / network on my laptop, though I do on my XP desktop.  The laptop had no OS at all, so I installed Kubuntu but haven't done anything with it yet.  Don't know unix/linux but do know windows. 

Maybe I shouldn't be jumping into Kubuntu, I can't see any files!  I have 6.10 (just installed) and just burned the 7.04 Alt CD but can't see anything on it, and it isn't starting up for me.  

in DOS I could dir but what do I do in K?  


HiJolly

I had the same problem; I think.
I downloaded the iso and burned it to cd.
When I tried to boot, nothing happened.

So I re-burned the iso at a slower speed 
and all was well. The first burn did not 
write the table of contents to the disc.
The second, slower burn did.

---

### Post by HiJolly on 2007-04-21
No, the ISO was great, no problem with the CD.  I mean I can't even see files in Konqueror.  nothing.  The CD has files on it, I can see it in WinXP...   Just nothing on the Kubuntu OS/laptop.  

I was hoping to upgrade to Fiesty (7.04) using the Alt CD, but ---  nothing!  


HiJolly

---

### Post by bobplano on 2007-04-21
you should always burn .isos at a lower speed anyway to avoid errors. you can also check the md5sum to make sure even if it writes the table of contents that there are no errors. the thread with the md5sums is in this forum somewhere so just search for it

---

### Post by HiJolly on 2007-04-21
You guys (gals?) are making this harder than it must be - or no one would EVER go to linux.  For crying out loud, how do I browse directories/drives?  Shouldn't Konqueror do that?  Why doesn't mine?  


HiJolly

---

### Post by HiJolly on 2007-04-21
How do I view any files anywhere in Kubuntu?  


HJ

---

### Post by bobplano on 2007-04-21
sorry i didn't read your post before mine. konquerer should work for viewing files i don't understand why you can't see the CD files

---

### Post by HiJolly on 2007-04-21
I can't see any files on the HDD, either.  but yet Kubuntu boots up - I can run Konqueror, other stuff.  Yet I see nothing but 'home' and 'media' folders - with zero files.  I feel rediculously stupid.  


HiJolly

---

### Post by louieb on 2007-04-21
> **HiJolly said:**
> You guys (gals?) are making this harder than it must be - or no one would EVER go to linux. For crying out loud, how do I browse directories/drives? Shouldn't Konqueror do that? Why doesn't mine? HiJolly
Thats what Konqueror does. It a file browser and web browser all rolled int one. 
 
Are you saying you put a CD in a computer running XP and can see the folders and files on it.
and you put that same CD into a computer running Kubuntu and can't see anything? 
Does Kubuntu/Konqueror even show you have a CD in the drive? Have you tried a diffrent CD? HAve you tried a music CD?

---

### Post by HiJolly on 2007-04-21
You got it.  THANKS for your response.  

How would Konq show me I have a cd in the drive?  How would I know if it were showing me?  

Just tried a music CD - nothing.  no music, no startup of anything, no files showing in Konq.  


HiJolly

---

### Post by HiJolly on 2007-04-21
When I go into Konsole (shell) and type:  

teacher@laptop00:~$ sudo -i      ---then it asks for the password and that works.  Then I type 

root@laptop00:~# knoqueror   --- and I get the following:  


xlib: connection to ":0.0" refused by server 
xlib: No protocol specified 

Konqueror: cannot connect to X server :0.0 


HiJolly

---

### Post by HiJolly on 2007-04-21
in the meantime, when I select cdrom0 in Konqueror I get a blank window with "No items - No Files - No Folders" at the bottom of the window.  

Home gives me an icon of the desktop & a shortcut to Examples, with "2 items - No files - 2 folders" at the bottom.  


HiJolly

---

### Post by bobplano on 2007-04-21
why don't you check in the terminal for files on the CD. it sounds like your konquerer is acting odd

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> why don't you check in the terminal for files on the CD. it sounds like your konquerer is acting odd

I just think I'm a total newbie.  How do I check in the terminal for files on the cd?  


HiJolly

---

### Post by bobplano on 2007-04-21
```
cd /
cd media
cd cdrom
ls
```
if it lists some names then it is definetly your konquerer

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> ```
cd /
cd media
cd cdrom
ls
```
if it lists some names then it is definetly your konquerer

root@laptop00:/media/cdrom# ls    ----gives me exactly nothing.  

I tried it with both a music CD and the Kubuntu Alternate CD.  Nothing.  This is the same CD drive that I used to install Kubuntu in the first place - so I know it works.  <sigh>  


HiJolly

---

### Post by z1p101 on 2007-04-21
You can't view a music CD because it it has no filesystem to mount.
Try a data CD and click on Storage Media the disk should be there.
If not open a Konsole  and type
mount /mnt/cdrom
ls /mnt/cdrom

If it lists the files then its a Konquor problem

then type

umount /mnt/cdrom

to unmount it

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> You can't view a music CD because it it has no filesystem to mount.
Try a data CD and click on Storage Media the disk should be there. 
Did that already.  No data is found (see previous posts in this thread) 

> **z1p101 said:**
> If not open a Konsole  and type
mount /mnt/cdrom
ls /mnt/cdrom

If it lists the files then its a Konquor problem

then type

umount /mnt/cdrom

to unmount it

I did the mount /mnt/cdrom and got this:  

root@laptop00:/# mount /mnt/cdrom 
mount: can't find /mnt/cdrom in /etc/fstab or /etc/mtab  


HiJolly

---

### Post by z1p101 on 2007-04-21
look in the file /etc/fstab and see how and there should be a /dev/cdrom or somthing like that
next to it there should be a /mnt/[something] and use that before the mount command

---

### Post by annda on 2007-04-21
try:

sudo mount /dev/cdrom /mnt/cdrom

or

sudo mount /dev/cdrom /media/cdrom

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> look in the file /etc/fstab and see how and there should be a /dev/cdrom or somthing like that
next to it there should be a /mnt/[something] and use that before the mount command

I swear I AM A NEWBIE!!  So, how do look in the file and see?  do you mean fstab is a file?  why no extension?  I am willing, just don't know how to do what you are asking me to do - 


HiJolly

---

### Post by HiJolly on 2007-04-21
> **annda said:**
> try:

sudo mount /dev/cdrom /mnt/cdrom

or

sudo mount /dev/cdrom /media/cdrom

Did the first of the two, and the drive spun up and is still spinning with no output on Konsole.  ??? What's it doing?  

OK, it stopped and returned with:  

mount: mount point /mnt/cdrom does not exist  


HiJolly 



HiJolly

---

### Post by bobplano on 2007-04-21
to check your fstab type in

```
gksudo kate /etc/fstab
```

if it comes up with a warning don't worry about it

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> to check your fstab type in

```
gksudo kate /etc/fstab
```

if it comes up with a warning don't worry about it

root@laptop00:/# gksudo kate /etc/fstab   --gets me the following;  

-bash: gksudo: command not found           -- remember, I'm on kubuntu  


HiJolly

---

### Post by z1p101 on 2007-04-21
sorry
Linux files don't have extensions generally
Open Konquor and press the up arrow until you get to /
there will be a folder there called etc, go into that and there will be file fstab, right click on it and open it with a text editor

Or type on the command line
cat /etc/fstab

---

### Post by bobplano on 2007-04-21
well i thought gksudo stood for graphical sudo but anyway then run 
```
sudo kate /etc/fstab
```

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> well i thought gksudo stood for graphical sudo but anyway then run 
```
sudo kate /etc/fstab
```

comes badk with:  

"xlib: connection to ":0.0" refused by server 
"xlib: No protocol specified 

"Kate: cannot connect to X server :0.0 

sound familiar?  I've seen it before as described in previous posts in this thread.  


HiJolly

---

### Post by z1p101 on 2007-04-21
just type
sudo cat /etc/fstab

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> sorry
Linux files don't have extensions generally
Open Konquor and press the up arrow until you get to /
there will be a folder there called etc, go into that and there will be file fstab, right click on it and open it with a text editor

Or type on the command line
cat /etc/fstab

In Konq all I see at / is:  

home   (and)  media 

---- 
doing the cat command on the Konsole I get: (a bunch of stuff) 

looks like it works, but jeez it's messy!  


HiJolly

---

### Post by z1p101 on 2007-04-21
click on home and then use the up arrow to get to /

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> click on home and then use the up arrow to get to /

Did that.  Only see 'home' and 'media'.  That's all.  

but on the "cat /etc/fstab" thing, now THAT worked.  What do you want me to do, type in all the response?  It'll take a while.  I got hda1 & hda5 & hdc & <blank> .  


HiJolly

---

### Post by z1p101 on 2007-04-21
Or maximize the Konsole and type
sudo cat /etc/fstab | grep '/dev/*'

---

### Post by z1p101 on 2007-04-21
Or In Konquor at the top where it says location type in / then enter

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> Or maximize the Konsole and type
sudo cat /etc/fstab | grep '/dev/*'

Ooh, I like that!  

Here's what I got:  

# /dev/hda1 
# /dev/hda5 
/dev/hdc        /media/cdrom0  udf,iso9660 user,noauto       0       0 
/dev/             /media/floppy0  auto      rw,user,noauto   0      0  

I am so happy that at last some commands are giving back info -- keep it up, Z1p101!!  -and thanks!  

HiJolly

---

### Post by bobplano on 2007-04-21
ok so the whole point of that was to get the mount info if i understand correctly? wow. anyway so now run that command where they told you to look in that file and put it before mount or whatever

try this
```
sudo mount /dev/hdc/media/cdrom0
```

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> ok so the whole point of that was to get the mount info if i understand correctly? wow. anyway so now run that command where they told you to look in that file and put it before mount or whatever

try this
```
sudo mount /dev/hdc/media/cdrom0
```

Yeah, what a pain!!  Thanks to you, too, BobPlano (BTW, I used to live in Allen) so...  

I typed it in and got the same old message:  

mount: can't find /dev/hdc/media/cdrom0 in /etc/fstab or /etc/mtab  

I have no idea what that means.  Why can't this stuff just work?  Why can't Konqueror show me my files?  Can it not show me system files?  Are ALL my files 'system' files?  is that the problem?  >augh<  


HiJolly

---

### Post by pppetter on 2007-04-21
> **HiJolly said:**
> Did the first of the two, and the drive spun up and is still spinning with no output on Konsole.  ??? What's it doing?  

OK, it stopped and returned with:  

mount: mount point /mnt/cdrom does not exist  
HiJolly 
HiJolly

The first command you were advised to enter did not work for the exact reason that the directory /mnt/cdrom doesn't exist.

Did you try the second command?
sudo mount /dev/cdrom /media/cdrom
Becouse that directory does exist on your system....

Anyways. Since you just installed your system, there is no other files in your home directory, except for the hidden ones. It's the same thing when you go to / in konqueror, there are no directorys except for media and home, the rest are hidden. If you want to, you may show them by clicking View-->View hidden files, in konqueror. 

Your problem is however very strange, all cds are suppose to mount automatically, but it seems you are on a good way of fixing them :)

---

### Post by z1p101 on 2007-04-21
Hey new user It takes some time
If that doen't work try
sudo mount /media/cdrom0
If that works try
sudo ls /media/cdrom0
then
sudo umount /media/cdrom0

---

### Post by pppetter on 2007-04-21
Ok sorry, just saw the output from fstab 
and bobplano just did a typo, input this instead:
> sudo mount /dev/hdc /media/cdrom0

EDUT: the difference is a single space in between /dev/hdc and /media/cdrom
EDITagain: bobplano--> for the future, notice, gksu is graphical sudo in ubuntu, and in kubuntu it's called kdesu.

---

### Post by HiJolly on 2007-04-21
Oh, man!  That did it!  

I did:  

sudo mount /dev/cdrom /media/cdrom    --and then the cd drive revved up and I got this:  

mount: block device /dev/cdrom is write-protected, mounting read-only 

And the "show hidden" think in Konq worked too.  So!!  what is the proper "sudo mount" command?  did I need to type the whole thing?  (I mean, including the "/media/cdrom")  Now maybe I can try to upgrade to Feisty from the Alt CD.  

Or should I worry about why the CD didn't mount automatically?  Can that be fixed?  


HiJolly

---

### Post by bobplano on 2007-04-21
thanks for that pppeter. yes the whole command is sudo mount /dev/hdc /media/cdrom0 (this time it has the space)

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> thanks for that pppeter. yes the whole command is sudo mount /dev/hdc /media/cdrom0 (this time it has the space)

I don't understand that, Bob -- it was the "mount /dev/cdrom /media/cdrom" that actually worked, and are you saying that that was wrong and it should have been "mount /dev/hdc /media/cdrom0"?  There are two differences in those commands!  What is up?  


HiJolly

---

### Post by bobplano on 2007-04-21
"sudo mount /dev/cdrom /media/cdrom" works because it supposed to mount a cd which files go in the media folder, but  "sudo mount /dev/hdc /media/cdrom0"  is the correct version of the command that i gave you just now

---

### Post by z1p101 on 2007-04-21
Well I'm new to Ubuntu so there are things I don't know but now that you know the CD mounts, umount it the same way.
There is a KDE/fstab issue with some systems, mine included, these days so try to comment out the line in fstab

Basically chage this
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
to this
# /dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

restart your coputer and see if it works

EDIT:I think its ether with hal or dbus, can't remember

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> "sudo mount /dev/cdrom /media/cdrom" works because it supposed to mount a cd which files go in the media folder, but  "sudo mount /dev/hdc /media/cdrom0"  is the correct version of the command that i gave you just now

I don't understand what makes it correct.  And I admit, I haven't tried it.  perhaps after dismounting, I'll try it & see how it goes.  

Are you saying that cdrom0 and cdrom are identical in effect?  and what is the difference between "hdc" and "cdrom"?  None? 

HiJolly

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> Well I'm new to Ubuntu so there are things I don't know but now that you know the CD mounts, umount it the same way.
There is a KDE/fstab issue with some systems, mine included, these days so try to comment out the line in fstab

Basically chage this
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
to this
# /dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

restart your coputer and see if it works

EDIT:I think its ether with hal or dbus, can't remember

...um...  

What is with hal or dbus?  and what are hal & dbus?  (yes, I'll try that if I can ever figure out how to edit a file)...  


HiJolly

---

### Post by bobplano on 2007-04-21
the command i gave you was wrong because the cd is not on a harddrive and the command pppeter had was the right version of the command but it was wrong for this situation. as for cdrom and cdrom0 i have 2 cd drives so that may be the difference. i'll check that now

---

### Post by bobplano on 2007-04-21
i think the one you want might be cdrom0 because my other drive is labeled dvdrecorder

---

### Post by z1p101 on 2007-04-21
Hal and dbus are programs the desktop uses to deal with hardware, don't worry about them.

To get to the file 
open Konqueor 
in the location box type /etc and hit enter
click on the fstab file and then you should be able to type

Also in Konqueor go to view -->show hidden files if you don't see it.

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> Hal and dbus are programs the desktop uses to deal with hardware, don't worry about them.

To get to the file 
open Konqueor 
in the location box type /etc and hit enter
click on the fstab file and then you should be able to type

Also in Konqueor go to view -->show hidden files if you don't see it.

Yeah, now we're cooking with gas!  

OK, I'm going to comment out the line in /etc/fstab that lists my CDROM drive.  uh, can't save the file after adding the comment char and following space.  why?  not root?  

how do i get root in Kate?  


HiJolly

---

### Post by z1p101 on 2007-04-21
According to pppeter before try this

kdesu Kate /etc/fstab

then you should be able to save it

If it doesn't work, replace Kate with KEdit or KWrite

---

### Post by HiJolly on 2007-04-21
> **z1p101 said:**
> According to pppeter before try this

kdesu Kate /etc/fstab

then you should be able to save it

If it doesn't work, replace Kate with KEdit or KWrite

OK, that worked!  So, I commented out the line & rebooted, but the CD drive is still not mounting automatically.  

Any suggestions, anyone?    ...and THANKS everybody!!  You guys are great!  HoHoHo!  


HiJolly

---

### Post by pppetter on 2007-04-21
When it comes to editing files that you need root permissions for,  the easiest way is to enter
> kdesu kate /directory/file
in Konsole.

When You are manually mounting a cd on your system it won't matter if you type:
> sudo mount /dev/hdc /media/cdrom
or
> sudo mount /dev/hdc /media/cdrom0
Becouse /media/cdrom is a symbolic link to cdrom0(which is a directory).

---

### Post by z1p101 on 2007-04-21
Exactly pppetter thanks you said it better than I could

Try in Konqueror to go into the media files directory and see if the cd is there

The K icon at the bttom left->inernet->Konqueror web browser

I know what is wrong but I can't fix it in Ubuntu help someone its a hal, dbus, then a pludev group thing.

---

### Post by bobplano on 2007-04-21
it sounds like it mounts but not if the cd is just put in if i'm getting this correctly. it sounds like everytime they want to use the cd they have to use mount commands, and they want to have it mount automatically

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> it sounds like it mounts but not if the cd is just put in if i'm getting this correctly. it sounds like everytime they want to use the cd they have to use mount commands, and they want to have it mount automatically

Yup, that's how it is...   I guess all told it's OK.  But it shouldn't be this way, that's for sure.  Please check the forum for my new thread.  Fun!  


HiJolly

---

