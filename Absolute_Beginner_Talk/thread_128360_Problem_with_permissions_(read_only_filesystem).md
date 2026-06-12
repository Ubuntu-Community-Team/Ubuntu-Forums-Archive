---
title: "Problem with permissions (read only filesystem)"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by jsiii on 2006-02-11
I have got this problem: I installed Ubuntu and mounted one NTFS partition as /data. Now, I cannot access this /data nor can I change permissions for it.

I was able to get inside like superuser (this worked):
```
sudo bash
cd /data
```

But I was not able to change permissions for that:
```
root@home:~# chmod -v 777 /data
failed to change mode of `/data' to 0777 (rwxrwxrwx)
chmod: changing permissions of `/data': Read-only file system
```

I even tried assigning this to other user (js) so that I would be able to access it without sudo bash:
```
root@home:~# chown -v js /data
failed to change ownership of `/data' to js
chown: changing ownership of `/data': Read-only file system
```

Can anyone help please?

---

### Post by Vinze on 2006-02-11
You can install pmount, then whenever you would use mount, you can use pmount instead, as normal user, so without sudo. Then you should be able to access it as user.

> sudo apt-get install pmount

---

### Post by jsiii on 2006-02-11
Umm, can you please help me a little bit more. I am new to this linux thing and know nothing about mounting.

I have pmount installed, hda mounted as /data. What should I do to mount it so that I can use it. Thank you.

---

### Post by Vinze on 2006-02-11
Let me see, do you want to mount hda as /data? Then you would have to go to a terminal or press ALT+F2, then type > pmount /dev/hda /data. Then you should be able to access it. I do find it weird that it isn't mounted by default, but well... If it's not mounted by default, you should set the command above to run on startup, don't know by heart how to do this but I believe it was somewhere in the preferences menu. If you have more questions, just ask :D

---

### Post by jsiii on 2006-02-11
[QUOTE=Vinze]I do find it weird that it isn't mounted by default[/QUOTE]

It is mounted by default, but as readonly and you suggested to use pmount. So I am asking how should I do it... maybe I should check that startup mounting and remove the readonly option if it is there. Like I said I am pretty new to this thing :-)

---

### Post by jsiii on 2006-02-11
Can anyone help me, please

---

### Post by cotcot on 2006-02-11
Have you checked this : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only) ?

---

### Post by jsiii on 2006-02-12
[QUOTE=cotcot]Have you checked this : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only) ?[/QUOTE]
**SOVED**: Very good, this is exactly what I needed, thank you wery much :-)

---

### Post by bscbrit on 2006-02-12
Duplicate thread 128710 - I replied on the other thread but it is already solved here.  Please only post once.

---

### Post by jsiii on 2006-02-13
[QUOTE=bscbrit]Duplicate thread 128710 - I replied on the other thread but it is already solved here.  Please only post once.[/QUOTE]

Oh no, It is not duplicate. I solved this problem, but the problem with link still exists.

I can acces the /data folders, I can enter it even from the link on the desktop. But the link on the desktop seems to be locked and I cannot do anything with it (only as a superuser).

---

### Post by bscbrit on 2006-02-13
OK, but I am still on the other thread!

---

