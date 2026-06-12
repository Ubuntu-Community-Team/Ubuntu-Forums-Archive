---
title: "how do i delete these folders?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-07
hi i cant delete these folders?

shane@Darkstar:~$ su
Password: 
root@Darkstar:/home/shane# cd /media
root@Darkstar:/media# ls
&#49352; &#48380;&#47464;       &#49352; &#48380;&#47464;______       &#49352; &#48380;&#47464;____________     disk
&#49352; &#48380;&#47464;_      &#49352; &#48380;&#47464;_______      &#49352; &#48380;&#47464;_____________    floppy
&#49352; &#48380;&#47464;__     &#49352; &#48380;&#47464;________     &#49352; &#48380;&#47464;______________   floppy0
&#49352; &#48380;&#47464;___    &#49352; &#48380;&#47464;_________    &#49352; &#48380;&#47464;_______________  mynewdrive
&#49352; &#48380;&#47464;____   &#49352; &#48380;&#47464;__________   cdrom                   newdrive
&#49352; &#48380;&#47464;_____  &#49352; &#48380;&#47464;___________  cdrom0                  windows
root@Darkstar:/media# rmdir 
root@Darkstar:/media# rmdir &#49352; &#48380;&#47464;
rmdir: &#49352;: No such file or directory
rmdir: &#48380;&#47464;: No such file or directory
root@Darkstar:/media# exit
exit

obviously there is a space in between the Korean characters...any ideas?

thanks...

---

### Post by Cypher on 2007-08-07
Put the entire directory name in quotes "like so" and it should work..

---

### Post by 505 on 2007-08-07
well, if you want the delete all the contents of the media folder, use
```
rm -r media
```
It will recursively delete everything in media.

Otherwise, you could also try
```
r mdir &#49352; &#48380;*
```
and let the shell expand everything and deal with the corrent names.

---

### Post by Hopeless on 2007-08-07
shane@Darkstar:~$ rmdir &#49352; &#48380;*
rmdir: &#49352;: No such file or directory
shane@Darkstar:~$ rmdir &#49352; &#48380;*
rmdir: &#49352;: No such file or directory
rmdir: &#48380;*: No such file or directory

and 

root@Darkstar:/home/shane# rmdir  "&#49352; &#48380;&#47464;"
rmdir: &#49352; &#48380;&#47464;: No such file or directory

doh!!!

---

### Post by Hopeless on 2007-08-07
Soooooooooooorry!!!!

root@Darkstar:/home/shane# rmdir  "&#49352; &#48380;&#47464;"
rmdir: &#49352; &#48380;&#47464;: No such file or directory
root@Darkstar:/home/shane# rmdir /media/newdrive/
root@Darkstar:/home/shane# rmdir /media/&#49352;*
root@Darkstar:/home/shane# ls /media/
cdrom  cdrom0  disk  floppy  floppy0  mynewdrive  windows

i forgot to cd to /media/ :lolflag:

awww  thanks you guys... i really feel great the response time i feel i belong to you guys and Ubuntu....!!!

---

### Post by asmoore82 on 2007-08-07
this would delete everything that doesn't start with a regular letter ...

```
~ $ cd /media
media $ rm -rf [!a-zA-Z]*
```

---

### Post by Hopeless on 2007-08-07
cool!! thanks...

---

### Post by stchman on 2007-08-07
> **Hopeless said:**
> hi i cant delete these folders?

shane@Darkstar:~$ su
Password: 
root@Darkstar:/home/shane# cd /media
root@Darkstar:/media# ls
&#49352; &#48380;&#47464;       &#49352; &#48380;&#47464;______       &#49352; &#48380;&#47464;____________     disk
&#49352; &#48380;&#47464;_      &#49352; &#48380;&#47464;_______      &#49352; &#48380;&#47464;_____________    floppy
&#49352; &#48380;&#47464;__     &#49352; &#48380;&#47464;________     &#49352; &#48380;&#47464;______________   floppy0
&#49352; &#48380;&#47464;___    &#49352; &#48380;&#47464;_________    &#49352; &#48380;&#47464;_______________  mynewdrive
&#49352; &#48380;&#47464;____   &#49352; &#48380;&#47464;__________   cdrom                   newdrive
&#49352; &#48380;&#47464;_____  &#49352; &#48380;&#47464;___________  cdrom0                  windows
root@Darkstar:/media# rmdir 
root@Darkstar:/media# rmdir &#49352; &#48380;&#47464;
rmdir: &#49352;: No such file or directory
rmdir: &#48380;&#47464;: No such file or directory
root@Darkstar:/media# exit
exit

obviously there is a space in between the Korean characters...any ideas?

thanks...

If you have this solved then please put SOLVED in the thread title.

Also you can do a sudo nautilus in the future.

---

