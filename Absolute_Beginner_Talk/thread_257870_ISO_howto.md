---
title: "ISO howto"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by empcrono on 2006-09-15
Yes how do you mount a ISO. I mean mount a ISO as if it were cd in a cdrom. i.e. like nero img vitual driver software but in linux. i heard you could do it natively with no such software. does any one know how?

---

### Post by risbac on 2006-09-15
I give it a try:

```
sudo mkdir /media/name_of_your_mount
sudo mount /path/to/your/ISO.iso /media/name_of_your_mount
```

Can someone confirm if it's enough? 

Of course it will mount it once, at next reboot you won't have anything in /media/name_of_your_mount.

---

### Post by Najand on 2006-09-15
> **risbac said:**
> I give it a try:

```
sudo mkdir /media/name_of_your_mount
sudo mount /path/to/your/ISO.iso /media/name_of_your_mount
```

Can someone confirm if it's enough? 

Of course it will mount it once, at next reboot you won't have anything in /media/name_of_your_mount.

It won't mount unless you add the partition/device type to it. Also as it is just  a file you need to  add loop option to it.

So, a fast way is to:
```

$ sudo mouunt -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom

```
you can now even see the iso file as a CD-ROM on your desktop too

---

### Post by xyz on 2006-09-15
Am excellent right-click-on-.iso by **animacide**:
[http://www.ubuntuforums.org/showthread.php?t=87369&highlight=mount+.iso+file](http://www.ubuntuforums.org/showthread.php?t=87369&highlight=mount+.iso+file)

---

### Post by risbac on 2006-09-15
Ok, so you had the newbie answer, and the answer-from-the-guy-who-knows :)

---

### Post by empcrono on 2006-09-15
> **risbac said:**
> Ok, so you had the newbie answer, and the answer-from-the-guy-who-knows :)

"sudo mouunt -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom"


I couldnt get it to mount through the commnad line. it said 

"tarCraft.iso /media/cdrom
mount: invalid option -- 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
william@william-desktop:~$ sudo mount -t iso9660 -0 loop /home/william/Desktop/StarCraft.iso /media/StarCraft
mount: invalid option -- 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
"


and im trying to understand it now.

---

### Post by xyz on 2006-09-15
> "sudo mouunt -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom"

isn't there a "u" (sudo mouunt) too many...in the command line?

---

### Post by Najand on 2006-09-15
Oh, Sorry I mistyped:
```
sudo [COLOR="Red"]mouunt[/COLOR] -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom
```
It should be like:
```
sudo [COLOR="Blue"]mount[/COLOR] -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom
```

---

### Post by empcrono on 2006-09-15
> **Najand said:**
> Oh, Sorry I mistyped:
```
sudo [COLOR="Red"]mouunt[/COLOR] -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom
```
It should be like:
```
sudo [COLOR="Blue"]mount[/COLOR] -t iso9660 -o loop <PATH>/<FILENAME>.iso /media/cdrom
```

LOL ok i figured so much typo with the extra u and was one step ahead of you guys there. but just incase i was wrong i also tried the extra u however one thing i didnt try and i will now is the <> in the path name and file name ie is it literialy <my path name belongs in these things <> > or just my/path/name no <>

note this is what i got when i tried the <>
bash: /: Is a directory

this is what i typed in first time:

sudo mount -t iso9660 -0 loop /home/william/StarCraft/StarCraft.iso /media/cdrom

second time i typed in 
sudo mouunt -t iso9660 -0 loop /home/william/StarCraft/StarCraft.iso /media/cdrom

thrid time i typed in 
sudo mount -t iso9660 -o loop </home/william/StarCraft>/<StarCraft>.iso /media/cdrom

---

### Post by Najand on 2006-09-15
It is just the path of your iso file.

---

### Post by empcrono on 2006-09-15
> **Najand said:**
> It is just the path of your iso file.

note this is what i got when i tried the <>
bash: /: Is a directory

this is what i typed in first time:

sudo mount -t iso9660 -0 loop /home/william/StarCraft/StarCraft.iso /media/cdrom

second time i typed in
sudo mouunt -t iso9660 -0 loop /home/william/StarCraft/StarCraft.iso /media/cdrom

thrid time i typed in
sudo mount -t iso9660 -o loop </home/william/StarCraft>/<StarCraft>.iso /media/cdrom

as above

---

### Post by Najand on 2006-09-15
sudo mount -t iso9660 -o loop /home/william/StarCraft/StarCraft.iso /media/cdrom is RIGHT.

---

### Post by xyz on 2006-09-15
LOL man! > ok i figured so much typo with the extra u and was one step ahead of you guys there. but just incase i was wrong i also tried the extra u however one thing i didnt try and i will now is the <> in the path name and file name ie is it literialy <my path name belongs in these things <> > or just my/path/name no <>
Reply With Quote

I think the problem then would be capital letters, try:
<path>/<filename>.iso...;)

---

### Post by empcrono on 2006-09-15
mount: invalid option -- 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

is what happens

---

### Post by Najand on 2006-09-15
It is not:
```

sudo mount -t iso9660 [COLOR="Red"]-0[/COLOR] loop /home/william/StarCraft/StarCraft.iso /media/cdrom

```
It is

```

sudo mount -t iso9660 [COLOR="blue"]-o[/COLOR] loop /home/william/StarCraft/StarCraft.iso /media/cdrom

```

You should use "small o", not "zero", nor "Capital O"

---

### Post by xyz on 2006-09-15
I don't if I am blind but your first line > mount: invalid option -- 0
has a 0 (zero) in it ..and if I read the command line posted earlier in the thread, it has an "o" in it...o as in oh my god!

---

### Post by empcrono on 2006-09-15
> **Najand said:**
> It is not:
```

sudo mount -t iso9660 [COLOR="Red"]-0[/COLOR] loop /home/william/StarCraft/StarCraft.iso /media/cdrom

```
It is

```

sudo mount -t iso9660 [COLOR="blue"]-o[/COLOR] loop /home/william/StarCraft/StarCraft.iso /media/cdrom

```

You should use "small o", not "zero", nor "Capital O"

*smacks self* boy LMAO i feel not to smart now. this happens to me once in a while i get a "big head" and think wow im starting to kick *** in linux and somthing a lame typo like this gets the best of me it was the "o" and i was using the "0" wow you guys are good i wouldnt have ever caught that

---

### Post by Najand on 2006-09-15
Could you already mount it or it is still unmounted yet?

---

### Post by empcrono on 2006-09-15
> **Najand said:**
> Could you already mount it or it is still unmounted yet?

Its mounted now thanks to you guys thnx. you were awesome lol most of the time peeps cant awnser my questions ^_^

---

### Post by Najand on 2006-09-15
Hmm, try to take a note of the ISO mount command somewhere as it is usually helpful.

---

### Post by empcrono on 2006-09-15
you wont have to tell me twice this command is gold as far as i am concerned. i love mounting ISO and i always did in windows and now that i know this command i know its a 1000x better in linux no more buygging out on me because its a nero virtual drive ^_^

---

### Post by xyz on 2006-09-15
oooooooooooooooooooooooooooooooo...we are sooooooooooooooooooo..happy 4 you!:grin: 
Happy Ubuntu to you then!

---

### Post by Najand on 2006-09-15
LOL, that was a good time... 
Now it is time for me to  drink a [COLOR="Sienna"]Quad Shot of Ubuntu[/COLOR]

---

### Post by xyz on 2006-09-15
> **Najand said:**
> LOL, that was a good time... 
Now it is time for me to  drink a [COLOR="Sienna"]Quad Shot of Ubuntu[/COLOR]
I guees in Japan...it's later in the day than we think! LOL
I'll have just a shot...a little later!

---

### Post by Najand on 2006-09-15
It is now Friday 8 pm and I am just thinking of going out for some beer or probably some Tequila Shots...

---

### Post by xyz on 2006-09-15
> **Najand said:**
> It is now Friday 8 pm and I am just thinking of going out for some beer or probably some Tequila Shots...
I'd be very happy to meet you there...here it's only 1 PM...so I'll just be a little late! But I'll be there! LOL
Have a good time!

---

### Post by Najand on 2006-09-15
Thanks.... You have a good time, too...

---

### Post by empcrono on 2006-09-15
I can never do enough tweaking *takes a shot* and over here ware i am its a 4:26 am looks like i pulled a all nighter having fun tweaking and fiddling muahahahah a^_~

---

### Post by xyz on 2006-09-15
> **empcrono said:**
> I can never do enough tweaking *takes a shot* and over here ware i am its a 4:26 am looks like i pulled a all nighter having fun tweaking and fiddling muahahahah a^_~
...and so you live on the US West Coast...I spent 12 years of my life there!
**but we should stop "cluttering" the foruum!**

---

### Post by empcrono on 2006-09-15
> **xyz said:**
> ...and so you live on the US West Coast...I spent 12 years of my life there!
**but we should stop "cluttering" the foruum!**

O yeah?!? ware about. I was raised on the east coast but i have lived here on the west coast for about 4 years

---

### Post by xyz on 2006-09-15
**we really should stop "cluttering" the foruum!**
check your PM!

---

