---
title: "Mount HDD automatically?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-01-13
My Ununtu install is on a 40Gb Hdd. I also have a 80Gb hdd connected but it does not mount automatically. Is this ok? If I go to "Computer" and click "74.5 Gb volume" it mounts as "disk".
Is this a normal behavior?

---

### Post by insane_alien on 2008-01-13
if it wasn't connected when ubuntu was installed then yes.

you can add it to /etc/fstab so it mounts automatically on boot if you want.

---

### Post by jesrani on 2008-01-13
And exactly how do I do this. I am a total newbie and need detailed instructions. In windows we have c: and d: drives and so on. but in linux it is all different and bit difficult for me.
what do i mount it as?

---

### Post by Malta paul on 2008-01-13
Hi, you can normaly mount your disk at boot up use:
sudo mount -a
then reboot your computer.

You can also name the HD what you like.

Here are some references that may help you:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/)

Have fun:)

---

### Post by Keith Hedger on 2008-01-13
To start use:```

sudo mkdir /media/MOUNTNAME
sudo vol_id /dev/DISK 

``` to get the uuid of your disk where DISK is the dev number (/dev/sdb1 for instance) and MOUNTNAME is the name that you want to see the disk mounted as, then use ```
sudo gedit /etc/fstab
``` to open your fstab file for writing then add the line ```
UUID=UUIDFROMVOL_ID /media/MOUNTNAME               ext3    defaults 0       0
```
where UUIDFROMVOL_ID is the uuid you got from vol_id, and presumming you are using an ext3 filesystem on your disk if not you will have to change ext3 above to whatever is appropriate.
save the file and quit gedit
the next time you boot/login your disk will be auto mounted, you can check that youve done everything right by using ```
sudo mount -a
``` which will mount everything according to your fstab.
Hope this helps

---

### Post by jesrani on 2008-01-15
Hello everyone, thanks for the replies.
I got detailed instruction from the link by Malta paul. Thanks
Now I hae mounted my 80Gb Hdd as "BackupDisk".
When I open "Places --> Computer", I see my Home folder, Desktop, File System, CD drive. But to access "BackupDisk" I have to go to file system.
My question is, can I have this under "Places". I am used to Windows and quite like the idea of having each partition seen as C:, D: etc. Wish I could have this under Ubuntu too.

---

### Post by HemiGTX on 2008-01-15
in your file browser go to your BackupDisk .
at the top choose bookmarks and add bookmark, this will add it to Places>Bookmarks

---

