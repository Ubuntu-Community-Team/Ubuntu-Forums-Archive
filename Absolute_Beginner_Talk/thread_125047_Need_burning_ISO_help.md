---
title: "Need burning ISO help"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Protoman on 2006-02-02
I need to burn a iso I have but I have no idea how to under LInux.  I tried looking in the thread [here.]("http://www.ubuntuforums.org/showthread.php?t=33183") I looked there, and even in that link at the bottom and found a command

cp /dev/cdrom mycd.iso 

and 

mount -o loop mycd.iso /mnt/cdrom


I tried the first one and...it didn't work for me, even after having it point to my iso.  Can anyone help me out?


EDIT: Forgot to post what error I had. The error I got was cp: missing destination file

---

### Post by xequence on 2006-02-02
I would assume Gnomebaker or K3B would be able to burn... If they cant, something is wrong ;)

Oh, and I think nero has a linux version. Nerolinux...

---

### Post by AndyCooll on 2006-02-02
Install K3b (if you haven't already). You may also need to install cd cdrdao (one of the programs it uses to burn stuff).

Then select the drop down menu "Tools". One of the options there is to burn a CD image.

:cool:

---

### Post by Protoman on 2006-02-02
Oh man I totally forgot about looking under Nero.  I was looking under Alcohol and Daemon tools. Thanks for pointing those out.

---

### Post by TeeAhr1 on 2006-02-02
I just right-clicked on the icon of the ISO file and picked "write to disc."  Do you have that option?

---

### Post by viper474 on 2006-02-02
TeeAhr1, are you using a HP computer, just wondering?  Also, you could try right-clicking and say "send to->" then the burning program.

---

### Post by TeeAhr1 on 2006-02-02
Yes, why?

---

### Post by deBaas on 2006-02-02
[QUOTE=Protoman]Oh man I totally forgot about looking under Nero.  I was looking under Alcohol and Daemon tools. Thanks for pointing those out.[/QUOTE]
Those are for mounting .iso's not for burning.

---

### Post by Protoman on 2006-02-02
Daemon Tools I'm not sure of, I've just used it a bit but was too used to Alcohol.  But I do know Alcohol does work for burning ISOs, it's what I use for burning ISO's and mounting them to a emulated drive in XP Pro.


Also, just wanted to say thanks all the advice and especially to xequence for telling me about gnomebaker.  It works just fine and is easy to use.

---

### Post by ardchoille on 2006-02-02
If you want to do it from command line:

**Make an ISO file from a directory of files**

```
mkisofs -o /desired/path/to/filename.iso -R /path/to/source/dir
```

or

```
mkisofs -r -J -o /desired/path/to/filename.iso -R /path/to/source/dir
```

-r generates Rock Ridge long names for Linux
-J generates Joliet long names for Windows

Read man mkisofs for more info


**Burn the ISO to a CD-R**

```
cdrecord dev=/dev/cdrom driveropts=burnfree -v -data cd_image.iso
```

To burn a data CD

---

