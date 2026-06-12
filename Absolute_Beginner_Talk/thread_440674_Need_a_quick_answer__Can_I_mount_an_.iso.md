---
title: "Need a quick answer:  Can I mount an .iso?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-11
For Ubuntu Studio, I can't find a DVD to burn to, but I do have a 2gig USB drive and a LiveCD for Feisty Fawn.  Can I boot that, mount the ISO from the USB drive, and install from there?  Or something?

---

### Post by Cypher on 2007-05-11
Absolutely..
```

sudo mount -t iso9660 /path/to/iso/file /path/to/mount/point

```

---

### Post by gohanssjn on 2007-05-11
Cool cool, would that let me install it?

---

### Post by gohanssjn on 2007-05-11
Ok, did this

sudo mkdir /ubuntustudio

sudo mount -t iso9660 /media/USBKEY/ubuntustudio.iso /ubuntustudio

I keep getting that the .iso does not exist.  Any ideas?

---

### Post by Cypher on 2007-05-11
Can you do "ls -l /media/USBKEY" and see the ISO file there?

---

### Post by taurus on 2007-05-11
Is it on /media/USBKEY and have you checked the filename (upper case characters are not the same as lower case characters)?

```
ls -la /media/USBKEY
```

---

### Post by gohanssjn on 2007-05-11
> **taurus said:**
> Is it on /media/USBKEY and have you checked the filename (upper case characters are not the same as lower case characters)?

```
ls -la /media/USBKEY
```

Yup, even changed it to 1234.iso, same result.

---

### Post by taurus on 2007-05-11
Can you at least post the output of that command from a terminal?

---

### Post by Cypher on 2007-05-11
can you cut-n-paste the exact error. It might be complaining about the iso9660 filesystem not being supported in the Kernel as opposed to the ISO file not be present.

---

### Post by gohanssjn on 2007-05-11
> ubuntu@ubuntu:~$ sudo mount -t iso9660 /media/USBKEY/1234.iso /1234
mount: /media/USBKEY/1234.iso is not a block device (maybe try `-o loop'?)
ubuntu@ubuntu:~$ ls -la /media/USBKEY
total 1003496
drwx------ 6 ubuntu root      4096 2007-05-11 21:38 .
drwxr-xr-x 7 root   root       200 2007-05-11 21:38 ..
-rwx------ 1 ubuntu root 909676544 2007-05-11 20:52 1234.iso
-rwx------ 1 ubuntu root  36808256 2007-04-03 19:47 iTunesSetup702.exe
-rwx------ 1 ubuntu root     80384 2007-04-30 22:06 List.doc
-rwx------ 1 ubuntu root        61 2007-05-11 21:20 new file
-rwx------ 1 ubuntu root         0 2007-05-11 21:19 new file~
drwx------ 2 ubuntu root      4096 2007-04-30 22:53 NST
drwx------ 2 ubuntu root      4096 2007-05-02 22:41 Ubuntu
drwx------ 8 ubuntu root      4096 2007-05-11 21:04 Ubuntu_Backup
drwx------ 9 ubuntu root      4096 2007-02-22 22:13 Utilities
ubuntu@ubuntu:~$ sudo mount -t iso9660 /media/USBKEY/1234.iso /1234
mount: /media/USBKEY/1234.iso is not a block device (maybe try `-o loop'?)
ubuntu@ubuntu:~$ 


There ya go!

---

### Post by taurus on 2007-05-11
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop /media/USBKEY/1234.iso /media/iso
ls -la /media/iso
```

---

### Post by gohanssjn on 2007-05-11
Awesome, worked great...but how do I run it to have it install UbuntuStudio?

Thanks for the help so far, MUCH appreciated :D

---

### Post by nubutu on 2007-05-11
I mount .iso files this way:

sudo modprobe loop

sudo mount /path_to_my_iso.iso /path_to_mount_point -t iso9660 -o loop

---

### Post by gohanssjn on 2007-05-11
So I can view the files...but not exicute it now, wasn't there a way to make it into an executable...or am I just thinking of scripts.....

---

### Post by gohanssjn on 2007-05-11
Ok, I found a blank DVD!  Maybe this will just be the best option...but it's an alternative cd, right?  Does that mean anything to me or will it act as a LiveCD?

---

### Post by nubutu on 2007-05-11
Uhm, I don't know why you can't execute the files...you can check the permissions by doing ls -l, you'll see something like:

dr--r--r-- 1 root ....whatever

meaning that it´s a directory to which you only have read access.

To change them you issue

sudo chmod -R xyz your_file

x=owner's permissions
y=group's permissions
z=rest of the cosmos' permissions

and some acceptable values for them are:

7=read, write and execute allowed
5=read and execute allowed
2=just read
0=keep your nose away

but the thing is that I have the feeling that you can't change the permissions of a mounted .iso as it probably is read only. In any case, I just have mounted a windows.xp iso I happen to have here and it allows me to execute whatever I want since the permissions I have on it are r & x...

---

### Post by gohanssjn on 2007-05-11
Ok, anyway I can just get the studio packages out of this thing?  Even package manager sees it as a folder and not a CD.

---

### Post by TriggerHappyChewie on 2007-05-11
The best way would be to just burn the Ubuntu Studio DVD and install from there.  I'm not sure where the install executable is located in the ISO, so I'm not sure how to install from it.  If you can find the executable, you should be able to install from the ISO.

---

### Post by gohanssjn on 2007-05-11
Well, I think I've decided to keep my Ubuntu install and just to the packages for now.

Can they be grabbed from the iso?

---

### Post by gohanssjn on 2007-05-11
Well, guess I can't do this tonight, bed soon.  Try again tomorrow I suppose.

---

