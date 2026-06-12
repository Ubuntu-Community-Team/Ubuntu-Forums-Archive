---
title: "problem with modifing files."
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by timmins on 2007-01-29
HI, I have all of my music files on my slave drive I want to change the tags on mass numbers of them, but I'm having trouble because I don't have permissions to write to the files. I really don't want to have to modify every folder one by one.

I am the only user on the computer, how to I give myselff full privledged for all files?

Thanks

---

### Post by meng on 2007-01-29
What sort of partition is this? ext3? fat32? ntfs?

---

### Post by Fasga on 2007-01-29
```
man chown
```

---

### Post by ComplexNumber on 2007-01-29
> **timmins said:**
> HI, I have all of my music files on my slave drive I want to change the tags on mass numbers of them, but I'm having trouble because I don't have permissions to write to the files. I really don't want to have to modify every folder one by one.

I am the only user on the computer, how to I give myselff full privledged for all files?

Thanks
can you copy them over to linux, then change the tags and copy them back again?
do you have any write access to your slave drive at all, and what file system is it (eg fat32, ntfs, etc)?

---

### Post by timmins on 2007-01-29
> **meng said:**
> What sort of partition is this? ext3? fat32? ntfs?

It's ext3

> **Fasga said:**
> ```
man chown
```

how exactly does this work, do I just put that code into the terminal?

> **ComplexNumber said:**
> can you copy them over to linux, then change the tags and copy them back again?
do you have any write access to your slave drive at all, and what file system is it (eg fat32, ntfs, etc)?

I can write to the slave drive, but my user doesn't seem to have permission to write to the files, I have to go into every directory, highlight the items and give permission to myself it's really annoying.

Thanks

---

### Post by Fasga on 2007-01-29
Yes, just put it in the terminal.  I don't know much about hard drives/Linux stuff, but you could try:
```

sudo chown -R yourUsername /pathToSlave

```

---

### Post by meng on 2007-01-29
Could try navigating to the mountpoint, and:
chmod -R a+w *

---

### Post by ComplexNumber on 2007-01-29
> sudo chown -R yourUsername /pathToSlaveslight correction in the syntax needed there. its the following:
sudo chown -R yourUsername:yourUsername /pathToSlave. the group is required too, so it ebcomes "username:group"

---

### Post by timmins on 2007-01-29
kyle@ubuntu:~$ sudo chown -R kyle:kyle/pathToSlave
Password:
chown: missing operand after `kyle:kyle/pathToSlave'
Try `chown --help' for more information.
kyle@ubuntu:~$




here's what I got

---

### Post by meng on 2007-01-29
sudo chown -R kyle:kyle /pathtoSlave
(you need a space AND you need to specify your pathtoSlave (which I doubt is really /pathtoSlave)

---

### Post by ComplexNumber on 2007-01-29
> **timmins said:**
> kyle@ubuntu:~$ sudo chown -R kyle:kyle/pathToSlave
Password:
chown: missing operand after `kyle:kyle/pathToSlave'
Try `chown --help' for more information.
kyle@ubuntu:~$




here's what I got
you need a space between kyle:kyle and "path to slave".  what is your path to the slave drive? for example, the path to the cd is /media/cd, the path to the floppy is /media/floppy. 

btw don't write "/pathToSlave" because that means nothing to the computer. you need to tell it the actual path. don't forget that computers are dumb :p

---

### Post by timmins on 2007-01-29
> **ComplexNumber said:**
> you need a space between kyle:kyle and "path to slave".  what is your path to the slave drive? for example, the path to the cd is /media/cd, the path to the floppy is /media/floppy. 

btw don't write "/pathToSlave" because that means nothing to the computer. you need to tell it the actual path. don't forget that computers are dumb :p

ok I tried the code with my path to save being /dev/hda

whay can't I just change every file in the whole directory and make it writable? I have to go into every file make it writtable and then enter every one of its subfolders writable. is there any way to logon as administrator and make every file writable/

Thanks

---

### Post by ComplexNumber on 2007-01-29
>  whay can't I just change every file in the whole directory and make it writable?
you can. the "-R" bit in the command that was suggested to you means make the changes recursively.

---

### Post by timmins on 2007-01-29
I have many paths to my music folder, where would I find the "pathtoslave" that I'm looking for/

Thanks

---

### Post by timmins on 2007-01-29
kyle@ubuntu:~$ sudo chown -R kyle:kyle /media/bigdisk
kyle@ubuntu:~$



I get nothing when I type this why?

Thanks

---

### Post by ComplexNumber on 2007-01-29
where is the top directory of your music on your slave drive? 
for example, if the path to your slave drive is /media/hda, the path to your music is /media/hda/music, and the path to a particular artist is /media/hda/music/some-artist......then just use the command:
** sudo chown -R kyle:kyle /media/hda/music**



to find the path, just firs up nautilus and navigate to wher the top level of your music is. nautilus will show you where you are navigating to, so just write that down and use it in the above command highlighted in bold.



btw you probably get nothing because its executed successfully. if there were any errors, it would tell you.

---

### Post by timmins on 2007-01-29
I'm quite a noob, what's nautilus and how do I access it?

Thanks

---

### Post by ComplexNumber on 2007-01-29
> **timmins said:**
> I'm quite a noob, what's nautilus and how do I access it?

Thanks
nautilus is the file manager in gnome  (just like windows explorer in windows). don't you have a 'kyles home' icon on your desktop? if so, just double click on it. thats nautilus.

---

### Post by timmins on 2007-01-29
I just want to make sure that I've explained my problem properly:

I have all of my music on my slave drive

I'm the only user, I ca read and execute every file, but for some reson the "write" box is unchecked, I can change it with no problem, but then all of the subfolder below that folder lockup and don't allow me to write to them. It seem like it has soething to do with settings on the computer.

Thanks

---

### Post by Fasga on 2007-01-29
Nautilus is the default GNOME file manager.  Whenever you open a folder, or see your desktop icons, that's nautilus.

Edit:  If you do have permission, do this:
```
chmod -R 777 /pathToSlave
```
Again, replacing /pathToSlave with the other hard drive.

---

### Post by timmins on 2007-01-29
do you mean my home folder? if so the path for my music folder would be: /kyle/desktop/My Media/Music/, does that sound right? are spaces and capitals important/


Thanks

---

### Post by ComplexNumber on 2007-01-29
> **Fasga said:**
> Nautilus is the default GNOME file manager.  Whenever you open a folder, or see your desktop icons, that's nautilus.

Edit:  If you do have permission, do this:
```
chmod -R 777 /pathToSlave
```Again, replacing /pathToSlave with the other hard drive.
when i was talking about chown before, i made a booboo. i meant chmod. thats the one that changes permissions. cheers for pointing out.


> are spaces and capitals important
yes

---

### Post by Fasga on 2007-01-29
Sorry, for some reason I keep thinking it's on a slave drive.  Yes, that's what you want.  Go into a terminal and type:
```
chmod -R 777 /kyle/desktop/My\ Media/Music/
```
Notice the slash after 'My'.  You have to add that to escape the space.

---

### Post by timmins on 2007-01-29
chmod -R 777 /kyle/Desktop/My\ Media/Music/


I tried this and it didn't work
do I have to put "home/" first?

---

### Post by Fasga on 2007-01-29
Sorry, my mistake.
```
chmod -R 777 ~/Desktop/My\ Media/Music/
```
~/ is basically a substitute for /home/yourUsername.

---

### Post by timmins on 2007-01-29
I love you both. It worked. Thanks for taking time to help a noob. what goes around comes around my friends.

-Kyle

---

### Post by ComplexNumber on 2007-01-29
> **timmins said:**
> I love you both. It worked. Thanks for taking time to help a noob. what goes around comes around my friends.

-Kyle
glad it worked :).

---

