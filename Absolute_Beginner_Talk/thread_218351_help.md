---
title: "help"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by deadkarma on 2006-07-18
i need help in seting permissions so that i can write to my hard drives and also on how i can get my ipod to work with ubunto.  in the chat room on irc someone suggested that i use rythembox, and while it will recognize the ipod it won't play the music.  so please if anyone could help i'd really appreciate it.  oh, and if say use the terminal for anything please explain it very carefully.  thanks in advanced

---

### Post by k420 on 2006-07-18
ok this is just an assumption but i thinkl the reason rythmnbox will not play your ipod files is because you do not have the proper codecs installed.  The codecs for most users are not preinstalled due to copyright problems.  If you can not play these check a script written called automatix that installs these codecs automatically for you and many other useful programs that are not preinstalled in ubuntu.  [http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by k420 on 2006-07-18
oh and what do you mean by writing to diskl are you using the live cd and not an hdd install ubuntu that would be the problem if so

---

### Post by deadkarma on 2006-07-18
thanks for the answer about the ipod, i'll go see if that works as soon as i can. no, i do have it installed on the hdd, but i'm unable to create a file or move things from my ipod onto the hdd.  i'm being told that i don't have write permission.

---

### Post by k420 on 2006-07-18
i do beleive that the script i metioned has applications for ipod that migh help

---

### Post by deadkarma on 2006-07-18
that might be able to help me write to my hdd?

---

### Post by k420 on 2006-07-18
yes i "beleive so" the application suite is called ilinux and it is a replacement for ilife

---

### Post by deadkarma on 2006-07-18
okay thanks i'll try that

---

### Post by deadkarma on 2006-07-18
oh, and am i able to have spaces in my file names or do i need to names files and use underscores?

---

### Post by deadkarma on 2006-07-18
oh, thanks for the help with getting ubuntu to play music.  now can you please tell me how to get ubuntu to let me create folders, so that i can start getting my music and a couple of other things off of my ipod and flash drive?

---

### Post by Crosbie on 2006-07-18
> **deadkarma said:**
> oh, thanks for the help with getting ubuntu to play music.  now can you please tell me how to get ubuntu to let me create folders, so that i can start getting my music and a couple of other things off of my ipod and flash drive?

Is Linux the only operating system on your computer?  Or do you have, say, Windows XP using NTFS on it?

---

### Post by k420 on 2006-07-18
try this open up a shell ```
mkdir /home/usrname/Desktop/worked
```
*usrname = your login name*  
if this works good sign if not copy and paste (with right click on terminal ) the error msg and post it here

---

### Post by deadkarma on 2006-07-18
> **Crosbie said:**
> Is Linux the only operating system on your computer?  Or do you have, say, Windows XP using NTFS on it?

no i spent all of last night installing ubuntu.  i found out before i left that i can create folders and all that with my main hdd, but i'd still like to know what is going on with the other.  does whether or not it's labled as hdb, or hda make a difference?

---

### Post by k420 on 2006-07-18
go to shell and type ```
 gedit /etc/fstab
``` then copy and paste what is in that file nto tis frm

---

### Post by deadkarma on 2006-07-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb      ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by deadkarma on 2006-07-18
sorry i was just thinking.  i might be making things harder than they need to be.  the problem that i seem to be having with my second hdd is that when i look at the properties and go to permissions it say that i'm not the owner so i can't change the permissions.  i'd like to change that so that i can put stuff on that hdd

---

### Post by k420 on 2006-07-18
look up in the forum how to mount that drive somewhere else i have my other drives not mounted under media but in my home folder like this```
/dev/hda5       /home/katalyst  reiserfs defaults        0       2

```

---

### Post by k420 on 2006-07-18
change your fstab to ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /home/usrname/hb1 ext3 defaults 0 2
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```
put your usrname where it says usrname and then save it  and then open uo shell again and type```
 sudo mount -a
```

---

### Post by deadkarma on 2006-07-18
i've tried that and that is what i get

mount: mount point /usrname/hd1 does not exist
 
course i did replace usrname with my usrname so that wasn't a mistake

---

### Post by k420 on 2006-07-18
ok sorry i couldnt help with that problem i would suggest opening a new thread in the dapper - hardware forum and someone there should help gpood luck

---

### Post by deadkarma on 2006-07-18
okay thanks that's what i'll do.  i appreciate the help that you've been.  i found this place more helpful than going on irc

---

### Post by k420 on 2006-07-18
just thought of something you have to make that folder we just created in the hoime folder
you know in home make whatever you mounted that drive too the folder needs to be there

---

### Post by deadkarma on 2006-07-18
make a folder in the home dir called hd1?

the folder claims that since i'm not the owner i can't change the permissions, which means that it is read only

---

### Post by k420 on 2006-07-18
sorry i meant make a folder called hb1 or whatever we mounted your drive in fstab at so that when u do sudo mount -a again it has a folder that it is mounted too

---

### Post by deadkarma on 2006-07-18
i think my life might be easier if i knew how to change the permissions so that i could write to a folder that it claims i can't because of ownership.
i'm unable to create a folder in the home dir

---

### Post by Third Thoughts on 2006-07-18
> **deadkarma said:**
> i think my life might be easier if i knew how to change the permissions so that i could write to a folder that it claims i can't because of ownership.
i'm unable to create a folder in the home dir

Changing permissions is done with the chown command. Type man chown to bring up the manual page on the chown command. You'll have to run it with sudo though. 
However, I woudln't reccommend changing the permissions willy nilly. Instead try and create a folder in /home/username. Then mount the drive in this directory. Once you've got it mounted if you still need to change the permissions use the chown command like I mentioned.

~Andrew S.

---

### Post by deadkarma on 2006-07-18
> **Third Thoughts said:**
> Changing permissions is done with the chown command. Type man chown to bring up the manual page on the chown command. You'll have to run it with sudo though. 
However, I woudln't reccommend changing the permissions willy nilly. Instead try and create a folder in /home/username. Then mount the drive in this directory. Once you've got it mounted if you still need to change the permissions use the chown command like I mentioned.

~Andrew S.

that's just it, /home will not let me create a folder.  that is why i'd like to be able to change permission.

---

### Post by Third Thoughts on 2006-07-19
but can you make a folder in /home/username? You don't have permissions in /home by default, and unless there's a really good reason you probably shouldn't change that. If you don't have permissions in /home/username then that's really weird. You should, so if you can change that with chown then do so.

~Andrew S.

---

### Post by deadkarma on 2006-07-19
yes i can do what i want in /home/usrname
my problem is more of having access to my second hdd.  i think that i am going to reinstall and have it mount in /home/usrname.  i hope that fixes it.

---

### Post by Third Thoughts on 2006-07-21
You don't need to re-install, just change your /etc/fstab file. Open it up in gedit. Earlier you posted that your /etc/fstab looked something like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /media/hdb ext3 defaults 0 2
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
Reply With Quote
```

I'm assuming that the hard drive you care about is /dev/hdb1 So you should make that line look like this
```

/dev/hdb1 /home/<username>/harddrive2 ext3 defaults 0 2

```

Then make the directory /home/username/harddrive2, finally mount the drive

~Andrew S.

---

