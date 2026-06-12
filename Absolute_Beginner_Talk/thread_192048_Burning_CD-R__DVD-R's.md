---
title: "Burning CD-R / DVD-R's"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by mmccloskey on 2006-06-08
Being new to Linux and Ubuntu I'm kind of stuck on an issue. Have two machines that I'm setting up. Got the OS installed OK. One machine has a Lite-On DVD-R. When I create a data cd (Using Gnome, just copy/paste - write cd) it seems to work fine. I can see the files/folders on the CD when I open it on the other machine. I can actually copy them to the desktop on the second machine.

But....there is a funny little padlock on the icon. And when I try to use / execute the file I get a message about not having permission.

Thanks for any help.

---

### Post by taurus on 2006-06-08
What is the permissions on the file on your CD?  You can see that with
```

ls -la /media/cdrom0 
(assuming that your CD is mounted on /media/cdrom0)

```

---

### Post by mmccloskey on 2006-06-08
mike@Base:~$ ls -la /media/cdrom0
total 8
dr-xr-xr-x  3 root root 2048 2006-06-07 21:10 .
drwxr-xr-x  4 root root 4096 2006-06-07 15:52 ..
dr-xr-xr-x  2 root root 2048 2006-06-07 21:10 Clone of Test
mike@Base:~$

---

### Post by taurus on 2006-06-08
Are you trying to execute "Clone of Test?"  You certainly CAN'T because it's a directory.  Therefore, you need to change to it first before you can run anything in there...  What is the output of this command then?
```

ls -la "/media/cdrom0/Clone of Test"

```

---

### Post by mmccloskey on 2006-06-08
mike@Base:~$ ls -la "/media/cdrom0/Clone of Test"
total 1350
dr-xr-xr-x  2 root root   2048 2006-06-07 21:10 .
dr-xr-xr-x  3 root root   2048 2006-06-07 21:10 ..
-r--r--r--  1 root root      0 2006-06-07 21:10 Clone of Test.vmsd
-r--r--r--  1 root root    519 2006-06-07 21:10 Clone of Test.vmx
-r--r--r--  1 root root     11 2006-06-07 21:10 Clone of Test.vmx.WRITELOCK
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s001.vmdk
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s002.vmdk
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s003.vmdk
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s004.vmdk
-r--r--r--  1 root root  65536 2006-06-07 21:10 Test-cl1-s005.vmdk
-r--r--r--  1 root root    484 2006-06-07 21:10 Test-cl1.vmdk
mike@Base:~$

---

### Post by taurus on 2006-06-08
[QUOTE=mmccloskey]mike@Base:~$ ls -la "/media/cdrom0/Clone of Test"
total 1350
dr-xr-xr-x  2 root root   2048 2006-06-07 21:10 .
dr-xr-xr-x  3 root root   2048 2006-06-07 21:10 ..
-r--r--r--  1 root root      0 2006-06-07 21:10 Clone of Test.vmsd
-r--r--r--  1 root root    519 2006-06-07 21:10 Clone of Test.vmx
-r--r--r--  1 root root     11 2006-06-07 21:10 Clone of Test.vmx.WRITELOCK
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s001.vmdk
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s002.vmdk
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s003.vmdk
-r--r--r--  1 root root 327680 2006-06-07 21:10 Test-cl1-s004.vmdk
-r--r--r--  1 root root  65536 2006-06-07 21:10 Test-cl1-s005.vmdk
-r--r--r--  1 root root    484 2006-06-07 21:10 Test-cl1.vmdk
mike@Base:~$[/QUOTE]
Well, there are your files on the CD, not in /media/cdrom0 but in /media/cdrom/Clone of Test!!!  So, just copy them to wherever you want and maybe you want to fix the permissions of those files as well.

---

### Post by mmccloskey on 2006-06-08
OK... pretty much got the fact that it was permission problem.. 

guess i want to know this, is there a proceedure to just copy data files to cd, go to another machine and open them up and use them without this permission problem..

don't shot me for this but i'm used to the dos/windows world and don't know if i'm doing it wrong or is this a fact of life in linux land?

thanks for your help!

---

### Post by taurus on 2006-06-08
The problem is not whether you are using Windows or Linux.  The problem is with the media.  Since you are using CD-R, you can only read and execute from it.  Therefore, before you copy anything to a CD, you need to make sure it has at least the read and executable permissions.  Otherwise, you have to copy it to your harddrive and change the permission since you know it by now that you can't change permissions for files already on CD...

So, you are current only have a read permission on those files, not executable so you are not going to be able to run them...

---

### Post by mmccloskey on 2006-06-08
thanks. really appreciate your help.

---

