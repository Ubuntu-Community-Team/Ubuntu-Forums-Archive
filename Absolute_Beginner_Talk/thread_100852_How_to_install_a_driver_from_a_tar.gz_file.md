---
title: "How to install a driver from a tar.gz file?"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by andras on 2005-12-08
I know that it's a stupid question, but I was trying for a hour without success and it is a vital driver for DVI support. I've downoaded the file mgadriver-x86-4.3.0.tar.gz to my computer, but when I try to unpack and install it in a terminal window I always get an error like this:

andras@andras:~$ sudo -i
Password:
root@andras:~#  tar zxvf mgadriver-x86-4.3.0.tar.gz
tar: mgadriver-x86-4.3.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@andras:~#

What's wrong?

Thank you for your help!

---

### Post by Brunellus on 2005-12-08
1) you shouldn't need to be root simply to untar the file.  

2) you're missing a leading hyphen .  like should read

$ tar -zxvf mgadriver-x86-4.3.0.tar.gz

---

### Post by Estariel on 2005-12-08
Are you sure that the mgadriver does not come with ubuntu (e.g. is not in the repositories?)

You would save yourself a LOT of trouble if you could get it via synaptic...

---

### Post by andras on 2005-12-08
[QUOTE=Brunellus]1) you shouldn't need to be root simply to untar the file.  

2) you're missing a leading hyphen .  like should read

$ tar -zxvf mgadriver-x86-4.3.0.tar.gz[/QUOTE]

I've tried adding the hyhen, but the problem persists:

andras@andras:~$ sudo -i
Password:
root@andras:~# tar -zxvf mgadriver-x86-4.3.0.tar.gz
tar: mgadriver-x86-4.3.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I'm going root - as indicated in an another thread and by Matrox - because the next step should be to install the driver.

---

### Post by andras on 2005-12-08
[QUOTE=Estariel]Are you sure that the mgadriver does not come with ubuntu (e.g. is not in the repositories?)

You would save yourself a LOT of trouble if you could get it via synaptic...[/QUOTE]

Yes, before posting I've already tried via Synaptic, but this driver is not available there... It is the driver indicated by Matrox's Support for having DVI with their G450 videocard under Linux...

---

### Post by Estariel on 2005-12-08
[QUOTE=andras]I've tried adding the hyhen, but the problem persists:

andras@andras:~$ sudo -i
Password:
root@andras:~# tar -zxvf mgadriver-x86-4.3.0.tar.gz
tar: mgadriver-x86-4.3.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I'm going root - as indicated in an another thread and by Matrox - because the next step should be to install the driver.[/QUOTE]

Are you in the directory in which mgadriver-x86-4.3.0.tar.gz is saved when you issue the tar command?
In other words, since you are in your home directory, is mgadriver-x86-4.3.0.tar.gz in your home directory?

If you issue the command like this, you have to be in the same directory in which the file lies.
Otherwise, specify the path to the file instead of the filename alone.
/home/yourusername/path/to/the/file

---

### Post by andras on 2005-12-08
[QUOTE=Estariel]Are you in the directory in which mgadriver-x86-4.3.0.tar.gz is saved when you issue the tar command?
In other words, since you are in your home directory, is mgadriver-x86-4.3.0.tar.gz in your home directory?

If you issue the command like this, you have to be in the same directory in which the file lies.
Otherwise, specify the path to the file instead of the filename alone.
/home/yourusername/path/to/the/file[/QUOTE]

Maybe the problem is really around this point. At the beginning the compressed file was on my desktop, then I placed a copy also in the home directory. However I've tried to issue this comand as root. I've tried to copy the file also to the root directory via drag and drop, but I could not manage to have the permission to copy to root.  Can you tell me how to copy the file to root?

---

### Post by Estariel on 2005-12-08
sure, but you need not compile it as root, only installation (after compiling must be done as root).

Copying a file is done by
```
cp /path/to/source/file /path/to/target/directory/
```

But I would suggest you do the following:

Open a terminal
```
cd ~
``` will change to your home directory (in case you are not there)

now let's look for the file
```
ls
```
all files will be listed. Do you see your file?

issue the tar command. Do NOT enter the complete mgadriver-x86-4.3.0.tar.gz filename. Let's use something called autocompletion:

```
tar -zxvf mga
``` Do not press enter yet, but press the tab key. If there is a file starting with "mga" in the directory you are in, your terminal will complete the filename for you. If it does that, you can be sure the file will be there.

No need to use the root account yet.

You can even do all the compiling without root.
Only the "make install" step requires a sudo in front of it.

Good luck!

---

### Post by andras on 2005-12-10
[QUOTE=Estariel]sure, but you need not compile it as root, only installation (after compiling must be done as root).

Copying a file is done by
```
cp /path/to/source/file /path/to/target/directory/
```

But I would suggest you do the following:

Open a terminal
```
cd ~
``` will change to your home directory (in case you are not there)

now let's look for the file
```
ls
```
all files will be listed. Do you see your file?

issue the tar command. Do NOT enter the complete mgadriver-x86-4.3.0.tar.gz filename. Let's use something called autocompletion:

```
tar -zxvf mga
``` Do not press enter yet, but press the tab key. If there is a file starting with "mga" in the directory you are in, your terminal will complete the filename for you. If it does that, you can be sure the file will be there.

No need to use the root account yet.

You can even do all the compiling without root.
Only the "make install" step requires a sudo in front of it.

Good luck![/QUOTE]

Estariel, thank you very much! Very nice explanation and it worked very well!

---

