---
title: "/bin/sh: bad interpreter: Permission denied"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by emamm on 2006-04-02
Hello

I am running kubuntu and  I need to install a software, so I did:

a) sudo su
b) /media/cdrom0/install

but this is what I got:

bash: /media/cdrom0/install: /bin/sh: bad interpreter: Permission denied


What am I doing wrong?

Thanks

Ed

---

### Post by taurus on 2006-04-02
That is not how you install a program!  What program do you plan to install anyway?  You can use apt-get from a terminal as
```

sudo apt-get install program_name

```

---

### Post by Sutekh on 2006-04-02
What are you trying to install?  What format is the file?

---

### Post by emamm on 2006-04-02
Hi ya

Matlab doesn' t install with apt-get!  

Ed

---

### Post by Sutekh on 2006-04-02
Is the version of Matlab that you have the one for Windows or Linux?

---

### Post by emamm on 2006-04-02
Linux.   

Ed
PS. I have no problem matlab on Mandriva LE2005.

---

### Post by taurus on 2006-04-02
Is there a README or INSTALL that tells you how to install it?  Is it on a CD or did you download it?  You need to provide a little more info so others can show you exactly how to install it...

---

### Post by Sutekh on 2006-04-02
[QUOTE=emamm]Linux.   

Ed
PS. I have no problem matlab on Mandriva LE2005.[/QUOTE]
How did you install it in Mandriva?

The install file is probably an executable script.  You can confirm it with
```
cd /media/cdrom0/
ls -l install
```
If the file is install.sh, then use
```
cd /media/cdrom0
sudo ./install.sh
```

---

### Post by emamm on 2006-04-02
Hello

I have installed matlab for linux since version 4.2. I had no problem to install Matlab under Solaris, debian, Mandriva  ...

One have just to run install (a bin/sh file). Instlal is a file that comes in the first matlab cd.

Ed

---

### Post by xtacocorex on 2006-04-02
The only way I could get Matlab (R13) to install on Kubuntu 5.10 was to mount the cd and then copy the contents to a folder in my home directory. Then the general install method worked.

Hope this helps.

---

### Post by emamm on 2006-04-02
Hi 

I think I will try what is suggested at:

[http://ubuntuforums.org/showthread.php?t=74708](http://ubuntuforums.org/showthread.php?t=74708)

Cheers

Ed

---

