---
title: "Help me copy a file, please."
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2005-12-13
I have Ubuntu 5.10 on a dual boot PC.

Since I have yet to be able to get online, I am hoping to be able to copy information from my 'Terminal', onto a floppy, or a CD, so that I can explain where I'm getting stuck.

Copying from my Floppy to the Desktop seems to be as easy as 'drag & drop' but, trying to go the other way has not worked for me, yet.  Whatever I try, I get as message saying, "You don't have permission to do this", or words to that effect.

Would someone please be good enough to type out what the 'copy' command should look like, to get a file from 'Home' or 'Desktop' onto my floppy.

Also, after I 'mount' my floppy, I appears on the Desktop as 'floppy0'.  Is that a 'zero', or an 'Oh' ?

Sorry if these are DUMB questions.    :-)

Thanks.

---

### Post by kane77 on 2005-12-13
I don't realy know the reason why shouldn't you normally drag and drop... (personally I'd try to set up permissions for you) but othervise you can use terminal and type "sudo cp /your/path/file.extension /media/floppy0/file.extension" That should help... 

(replace paths and filenames :))) 
In floppy0 it's zero...

PS: There's no such thing as dumb question...

---

### Post by cstudent on 2005-12-13
I'll start by answering the one question I know the answer to. Yes it's a zero.

Now for the rest. I'm sort of reading between the lines here. I'm thinking you are  trying to get text from an error into a text file that you can transfer to XP, which resides on the same machine. And you're not able to get online with Ubuntu because you are on dialup? If the floppy is formated for DOS you may need to use the mcopy command. Check this site [http://www.ss64.com/bash/mtools.html](http://www.ss64.com/bash/mtools.html)

I would think the command line would look like this:

mcopy /home/user/file.txt /floppy0/

I'm not an expert at bash (yet), but this might be what you will need. However, coping to a CD might be easier. You should be able to burn the file right from Nautilus.

---

### Post by L Campbell on 2005-12-13
[QUOTE=kane77]  SNIP

 type "sudo cp /your/path/file.extension /media/floppy0/file.extension" That should help... 

*****

Hi, thanks for your suggestion.  I typed:-

sudo cp /home/lcampbell/terminus.odt/media/floppy0/terminus.odt

Answer:-  cp: missing destination file   

Did I do somehing wrong?

Kind regards.

---

### Post by cstudent on 2005-12-13
There should be a space between your source and destination paths.

---

### Post by NiTsi on 2005-12-13
sudo cp /home/lcampbell/terminus.odt/media/floppy0/terminus.odt



you didn't leave a blank i.e.  : sudo cp /home/lcampbell/terminus.odt  /media/floppy0/terminus.odt

---

### Post by L Campbell on 2005-12-13
[QUOTE=cstudent]  SNIP

 Check this site [http://www.ss64.com/bash/mtools.html](http://www.ss64.com/bash/mtools.html)

I would think the command line would look like this:

mcopy /home/user/file.txt /floppy0/

************

Thanks for your suggestion.  I typed:-

mcopy /home/lcampbell/terminus.odt/floppy0/

Answer:  command not found.

Would that be an indication that 'mtools' are not loaded in Ubuntu?

Kind regards.

---

### Post by varunus on 2005-12-13
Did this (sudo cp /home/lcampbell/terminus.odt/media/floppy0/terminus.odt) not work after you added a space?

It should look like this:
```
sudo cp /home/lcampbell/terminus.odt /media/floppy0/terminus.odt
```

There has to be a space.

And your floppy can't be written by a user?  That's interesting...do you know what filesystem the floppy is?  (What is it formatted for on the box?  It'll say Mac, or Windows, or something...)

Can you type the following into a terminal and post the output here?
```
cat /etc/fstab
```

---

### Post by cstudent on 2005-12-13
[QUOTE=L Campbell]
Thanks for your suggestion.  I typed:-

mcopy /home/lcampbell/terminus.odt/floppy0/

Answer:  command not found.

Would that be an indication that 'mtools' are not loaded in Ubuntu?

Kind regards.[/QUOTE]

Yep. I'm home now. I wasn't earlier. So I've taken a look. mtools is not installed. The command suggested by kane77 should work for you. From your post where you tried his suggestion you left out a space between /home/lcampbell/terminus.odt and /media/floppy0/. Try that command again with the space and see if it does the trick for you.

---

### Post by L Campbell on 2005-12-13
[QUOTE=cstudent]Yep. you left out a space between /home/lcampbell/terminus.odt and /media/floppy0/. Try that command again with the space and see if it does the trick for you.[/QUOTE]


Many thanks, that was my problem, I appreciate your help.

BTW, soon after that I typed ' $ cd ./Modem ' and am now stuck in that directory.  Do you have a fix for that?

Trust me, I'm writing down all the correct answers so, hopefully, I won't have to ask the same questions twice.    :-)

Kind regards.

---

### Post by L Campbell on 2005-12-13
[QUOTE=varunus]Did this (sudo cp /home/lcampbell/terminus.odt/media/floppy0/terminus.odt) not work after you added a space?

It should look like this:
```
sudo cp /home/lcampbell/terminus.odt /media/floppy0/terminus.odt
```

There has to be a space.

And your floppy can't be written by a user?  That's interesting...do you know what filesystem the floppy is?  (What is it formatted for on the box?  It'll say Mac, or Windows, or something...)

Can you type the following into a terminal and post the output here?
```
cat /etc/fstab
```[/QUOTE]


Thanks for your help.  You hit the nail on the head.  I added a space between ' .odt and/media ' and it works fine now.

I'm not sure where I formatted the floppy.  I did a couple with Ubuntu and a couple with Win 98 but, since I added the space, I have successfully copied a file onto it, using using the ' sudo cp .... ' .

I will try to post the ' cat /etc/fstab ' results soon.

Kind regards.

---

### Post by nikopol on 2005-12-13
Hi there.

to step back from a directory do 
cd ..
that will get you out of modem and move you back to where you were.

cd stands for change directory btw. a . will refer to the current directory (like when you said cd ./modem that meant change to the modem directory in the current folder (the ./ bit) ).

you can also add theses commands together: 
move up two directories
cd ../..
move up one directory then head into another one on that level
cd ../media (which is what you would want at the minute I assume).

the TAB key is also useful for autocompleting a path to instead of typing all of 
cd ../media
you could do
cd ../med[TAB] and it should finish it off for you or at least list possible completions.

Hope that helps you ;)

---

### Post by L Campbell on 2005-12-13
[QUOTE=L Campbell]Thanks for your help.  You hit the nail on the head.  I added a space between ' .odt and/media ' and it works fine now.

I'm not sure where I formatted the floppy.  I did a couple with Ubuntu and a couple with Win 98 but, since I added the space, I have successfully copied a file onto it, using using the ' sudo cp .... ' .

I will try to post the ' cat /etc/fstab ' results soon.

Kind regards.[/QUOTE]

OK, here are the results:-

lcampbell@ubuntulewis:~/Modem$ cd ..
lcampbell@ubuntulewis:~$ sudo mount /media/floppy
Password:
lcampbell@ubuntulewis:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
lcampbell@ubuntulewis:~$

Kind regards.

---

### Post by L Campbell on 2005-12-13
[QUOTE=nikopol]Hi there.

to step back from a directory do 
cd ..
that will get you out of modem and move you back to where you were.

cd stands for change directory btw. a . will refer to the current directory (like when you said cd ./modem that meant change to the modem directory in the current folder (the ./ bit) ).

you can also add theses commands together: 
move up two directories
cd ../..
move up one directory then head into another one on that level
cd ../media (which is what you would want at the minute I assume).

the TAB key is also useful for autocompleting a path to instead of typing all of 
cd ../media
you could do
cd ../med[TAB] and it should finish it off for you or at least list possible completions.

Hope that helps you ;)[/QUOTE]


Yes, that was very helpful, thanks.

The ' TAB ' didn't work but the rest did.

Kind regards.

---

### Post by nikopol on 2005-12-14
[QUOTE=L Campbell]Yes, that was very helpful, thanks.

The ' TAB ' didn't work but the rest did.

Kind regards.[/QUOTE]

I mean the Tab key which tends to be just above Caps Lock on a keyboard - is that what you used?

Good to see you're getting all this Command line stuff down to a T :)

---

### Post by L Campbell on 2005-12-14
[QUOTE=nikopol]I mean the Tab key which tends to be just above Caps Lock on a keyboard - is that what you used?

Good to see you're getting all this Command line stuff down to a T :)[/QUOTE]


Thanks for checking up on me.    :-)

Yes, that is the TAB key I tried.

Kind regards.

---

### Post by nikopol on 2005-12-14
[QUOTE=L Campbell]Thanks for checking up on me.    :-)

Yes, that is the TAB key I tried.

Kind regards.[/QUOTE]

Ok - Sorry for assuming the worst but one never knows ;)
Try this:
open a terminal and press tab a few times - you should see something like this
```
Display all 2942 possibilities? (y or n)
```
Press y and it will give you all the possible endings (there'll be loads as we haven't yet specified a starting letter sequence.
type the first few letters of a folder or file in your directory (type ls to list the contents).
then press tab (maybe more than once) and see what happens.

the use of Tab is so useful it's worth getting it working :D

---

### Post by L Campbell on 2005-12-14
[QUOTE=nikopol]Ok - Sorry for assuming the worst but one never knows ;)
Try this:
open a terminal and press tab a few times - you should see something like this
```
Display all 2942 possibilities? (y or n)
```
Press y and it will give you all the possible endings (there'll be loads as we haven't yet specified a starting letter sequence.
type the first few letters of a folder or file in your directory (type ls to list the contents).
then press tab (maybe more than once) and see what happens.

the use of Tab is so useful it's worth getting it working :D[/QUOTE]

Thank you again.  It seems to be working now:-

lcampbell@ubuntulewis:~$
Display all 1634 possibilities? (y or n)
lcampbell@ubuntulewis:~$
lcampbell@ubuntulewis:~$ sudo mount /media/floppy
Password:
lcampbell@ubuntulewis:~$

Kind regards.

---

### Post by nikopol on 2005-12-14
Excellent - it does save an awful lot of typing, believe you me!

---

### Post by varunus on 2005-12-20
A couple of questions.

After inserting a floppy, can you go browse its files in the GNOME file manager?  Try going to Places->Computer and double clicking the floppy drive; can you see your files?

Then, try copying on to your desktop; can you do that by dragging and dropping?

Then, make a file in your favorite program, and try to drag and drop it to the floppy window.  This is what you said didn't work, correct?  Could you post the exact error text?

Also, *after* mounting the floppy with the mount command, or by double clicking in the Computer place, can you type the command "sudo fdisk -l" into a terminal and post the output?)  That's a lowercase L after the fdisk, not a 1 or a |.

---

### Post by L Campbell on 2005-12-21
Hi, thanks for your interest.

I have actually made a little progress lately and have successfully used some code to do stuff.    :-)

After inserting a floppy, can you go browse its files in the GNOME file manager? Try going to Places->Computer and double clicking the floppy drive; can you see your files?

[ Yes ]

Then, try copying on to your desktop; can you do that by dragging and dropping?

[ Yes ]

Then, make a file in your favorite program, and try to drag and drop it to the floppy window. This is what you said didn't work, correct? Could you post the exact error text?

[ I still get, 'You do not have permissions to write to this folder", however, I achieve my objective by opening Terminal and typing ' sudo cp ' and the rest of that code ]

Also, after mounting the floppy with the mount command, or by double clicking in the Computer place, can you type the command "sudo fdisk -l" into a terminal and post the output?) That's a lowercase L after the fdisk, not a 1 or a |.
>>>>>>>

lcampbell@ubuntulewis:~$ sudo fdisk -l

Disk /dev/hda: 30.7 GB, 30750031872 bytes
16 heads, 63 sectors/track, 59582 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       58658    29563600+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 5762 MB, 5762727936 bytes
255 heads, 63 sectors/track, 700 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         667     5357646   83  Linux
/dev/hdb2             668         700      265072+   5  Extended
/dev/hdb5             668         700      265041   82  Linux swap / Solaris

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   c  W95 FAT32 (LBA)
lcampbell@ubuntulewis:~$
<<<<<<<<

Kind regards.

---

### Post by varunus on 2005-12-24
Hm...It looks like your permissions are set wrong on your floppy drive.

Can you type the command "mount" and post the output here?  Just plain mount.

Also, can you unmount the floppy drive (you should be able to right click in the computer place and choose unmount or eject) and then type into a terminal:
```
cd /media
ls -l
```
and post the output here?

Try the following, does this let you drag and drop files to the floppy disk?  Do this when the floppy is unmounted.
```
sudo chown YOUR_USERNAME_HERE /media/floppy0
```

---

