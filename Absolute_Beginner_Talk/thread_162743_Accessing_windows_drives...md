---
title: "Accessing windows drives.."
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by michaelharg on 2006-04-19
I'm struggling to get access to my windows partitions, i want read only access to a NFTS partition. Heres what happens when i follow the guide in the Wiki:

```
michael@michael:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
michael@michael:~$
```


Now theres somthing blatently wrong i am doing here so could some one point me in the right direction?

---

### Post by mostwanted on 2006-04-19
[QUOTE=michaelharg]I'm struggling to get access to my windows partitions, i want read only access to a NFTS partition. Heres what happens when i follow the guide in the Wiki:

```
michael@michael:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
michael@michael:~$
```


Now theres somthing blatently wrong i am doing here so could some one point me in the right direction?[/QUOTE]

there is already a directory called windows in the media directory. Just proceed with the next step.

edit: just to elaborate: mkdir is short for "Make directory" and the argument supplied is the directory you want to create. The reason that you have to make a directory is because you'll need a mount point you can open in Nautilus, the default Ubuntu file manager, for example (a folder which is essentially your entire Windows disk).

---

### Post by michaelharg on 2006-04-19
I have followed the Wiki through and when i get to the point where i reload fstab i get the following message:
```

michael@michael:~$ sudo mount -a
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1
```

Not really sure what this means... What do i do next?

---

### Post by IYY on 2006-04-19
Are you sure that hda1 is your Windows partition? On my system, hda1 is the Ubuntu partition and something like hdb1 is the Windows one. Show us what your /etc/fstab file looks like.

---

### Post by michaelharg on 2006-04-19
I figured it out, i still had hda1 mounted when i was trying to mount it at media/windows, its all sorted now. Thanks for your help!

---

