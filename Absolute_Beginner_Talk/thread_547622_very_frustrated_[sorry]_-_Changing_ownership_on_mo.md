---
title: "very frustrated [sorry] - Changing ownership on mounted drive"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by dac10 on 2007-09-10
ok i dont like to double post but im getting extremely annoyed with linux right now. my current 37gb raptor hdd is about to burst and i need to be able to use my other 250gb hdd ASAP. ive been through all the rigmarole of mounting it etc but i dont know how to set the file permissions on the folder. so as you can imagine im very frustrated cause i am the only person using this computer yet i dont (me the owner of the damn thing!) have "permission" to use my own hardware. 

ive read web pages on using the terminal etc but i just dont seem to be able to do it. even when i use kdesu konqueror it still says it cant change the permission. 

if i cant get this hard drive working then ill be forced to switch back to xp as 37gb is simply not enough space.

thanks,

---

### Post by BrendanM on 2007-09-10
If you've already got it mounted, then you can set the file permissions using this command
```
sudo chown username:username /place_where_you_mounted_it
```

This will change the ownership of that drive to your user account.

As you've noticed, Linux tends to be a lot pickier about file permissions than Windows. This can be irritating at times, but it's also really good for security.

---

### Post by hyper_ch on 2007-09-10
And next time please use a thread topic title that reflects the conent of the question/problem that you have.

---

### Post by mlentink on 2007-09-10
> **BrendanM said:**
> This will change the ownership of that drive to your user account.

Hmm. Not add '-R'?

---

### Post by dac10 on 2007-09-10
once again i am sorry. 

Brendan i still cant create folders in their, the terminal says this;

"dean@Pluto:~$ sudo chown dean /newmaxtor
chown: changing ownership of `/newmaxtor': Read-only file system
dean@Pluto:~$
"

---

### Post by BrendanM on 2007-09-10
Maybe add -R. Does that make it recursive? I'm very very far from being a 1337 bash hacker. I usually have to have the man page up in another window when I'm doing anything.

---

### Post by BrendanM on 2007-09-10
dac10, ok. It sounds like the drive has been mounted as read-only for some reason. Do you know how the drive is formatted? Is it an NTFS drive formatted for windows?

---

### Post by Arwen on 2007-09-10
I think his original thread was "Second SATA HD" and he doubleposted in an act of desperation :-P

---

### Post by dac10 on 2007-09-10
it says Ext3 in the file manager.

---

### Post by BrendanM on 2007-09-10
That's fine. Whatever. Server space is cheap. We can afford a little double-posting here and there.

---

### Post by dac10 on 2007-09-10
> **Arwen said:**
> I think his original thread was "Second SATA HD" and he doubleposted in an act of desperation :-P

correct. and i deeply apologise but blah blah........ etc etc :)

---

### Post by BrendanM on 2007-09-10
dac10, can you post the contents of your /etc/fstab file please?
I'm assuming you successfully added the drive to fstab. If you mounted it manually, can you tell me exactly the command you used? You can press the "up" key in the terminal to scroll back through commands you entered previously.

---

### Post by dac10 on 2007-09-10
> **BrendanM said:**
> dac10, can you post the contents of your /etc/fstab file please?
I'm assuming you successfully added the drive to fstab. If you mounted it manually, can you tell me exactly the command you used? You can press the "up" key in the terminal to scroll back through commands you entered previously.

im not sure, i just plugged it in and used gparted to partition it and then 'disk and filesystem' to format it under ext3 and mount it.'

---

### Post by BrendanM on 2007-09-10
Ok, gparted probably already added an entry to fstab for you then. Use gedit to open /etc/fstab and then post the contents of that here.

The fstab file tells Linux what drives/filesystems to automount on startup. It's likely that it's set read-only in there. We can change it pretty easily.

---

### Post by BrendanM on 2007-09-10
I won't deny that Linux is harder in some respects, but it's also dramatically more powerful and flexible. Almost everything in Unix systems is done the way it is for good reasons. If you have the patience to stick with it, you'll be glad you did.


Edit: Here's some information on fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by dac10 on 2007-09-10
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=ef066d41-ffe7-43af-b544-3cd699d3dede / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=1e232b69-ad1c-4ce5-952a-4470ca185217 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda3 /newmaxtor ext3 users,atime,noauto,ro,dev,exec,suid 0 0

---

### Post by BrendanM on 2007-09-10
Ok, see this line:
```
/dev/sda3 /newmaxtor ext3 users,atime,noauto,**ro**,dev,exec,suid 0 0
```

That little "ro" is "read only", if you change it to "rw" (read-write) and then either unmount/remount the drive (or just reboot), it should work. 

In order to edit fstab, you'll have to use "gksudo gedit /etc/fstab"

---

### Post by dac10 on 2007-09-10
i have the same problem if i try to create a folder in '/'.

---

### Post by BrendanM on 2007-09-10
Yeah, you don't want to put stuff in "/" you should keep all of your user files in your /home/username/ or I guess on your other drive. The "/" (called root) is usually reserved for system files. I know this all seems kind of stupid, but it keeps you (or other users) from accidentally breaking important system files, and these kind of security restrictions are a big reason why Linux doesn't get viruses and malware.

---

### Post by dac10 on 2007-09-10
i get this error message;

dean@Pluto:~$ gksudo gedit/etc/fstab
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

jeez.....

---

### Post by Terl on 2007-09-10
Did you have a space between gedit and the /etc/fstab?  It does not look as though you did in your post.

---

### Post by BrendanM on 2007-09-10
Yeah, that's one of those famously cryptic Unix error messages. I'm sure that all means something. It looks like you might have missed a space between "gedit" and "/etc/fstab". Is that what happened?

---

### Post by dac10 on 2007-09-10
ok im just gonna reboot.

---

### Post by dac10 on 2007-09-10
its still not working. when i open fstab it says "rw" but the owner of the file etc is still root and im not allowed to create a folder in there.

---

### Post by dac10 on 2007-09-10
i need to change the owner of the file to me, how do i do that?

---

### Post by BrendanM on 2007-09-10
Use the chown command given earlier. "chown" = "**ch**ange **own**er" Add the -R switch, too.

---

### Post by dac10 on 2007-09-10
arrrrrrrggggggggghhhhhhhhhh ive done it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!11ONE!!!!!!!!!!ELEVEN!!!!111 :D :D i used the kdesu konqueror and its now working. brill, thanks guys.

---

### Post by BrendanM on 2007-09-10
You changed the owner using konqueror? Good job. Congrats!

---

### Post by dac10 on 2007-09-10
thanks, i can continue using linux now :D 
















until the next problem comes along lol

---

### Post by BrendanM on 2007-09-10
Exactly. But at least you learned some things solving that problem. After you get more used to Linux, it becomes less of a hassle sorting out the glitches which inevitvably arise. Just get good at using Google/the forums search. There's lots of information out there.

---

