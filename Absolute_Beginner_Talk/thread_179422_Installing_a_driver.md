---
title: "Installing a driver"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by dontpanic0 on 2006-05-19
Hi, I am trying to install a driver for a USB WLAN adapter.  I found this one on google:
[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

I extracted it, but now what do I do to install it? I tried to follow the instructions on the webpage, but they didn't seem to work, because I don't fully understand them.  Could someone help me out on this?

Thanks in advance,
    Dontpanic0

---

### Post by meng on 2006-05-19
At which step did the errors occur, and what were the errors? Did you "sudo" the steps?

---

### Post by dontpanic0 on 2006-05-19
It didn't recognise "untar".  What does "sudo" do?

---

### Post by aysiu on 2006-05-19
Can you post a link to the driver you downloaded and a link to the instructions? That first link you posted has a whole list of drivers--I don't know which one you're using.

---

### Post by meng on 2006-05-19
Ok first move the file (---.tar.bz2) to a separate directory (just in case).
Then: tar xvf [nameoffile].tar.bz2
Then: ls
and tell us what that gives you.

This should untar (unarchive) the file for you.

---

### Post by dontpanic0 on 2006-05-19
[QUOTE=aysiu]Can you post a link to the driver you downloaded and a link to the instructions? That first link you posted has a whole list of drivers--I don't know which one you're using.[/QUOTE]


Look at the bottom of that page, theres a download link there and the instructions are there too.  I think the long list is supported hardware.

---

### Post by dontpanic0 on 2006-05-19
Its a tgz file, and it came up with a long list when I did "tar xvf zd1211-driver-r77.tgz"
when I did "ls" it said:
zd1211-driver-r77   zd1211-driver-r77.tgz

---

### Post by aysiu on 2006-05-19
Ugh...

This looks complicated. It's compiling from source, but the only thing in the top-level directory of the zipped file is the makefile.

I'm not sure if these instructions'll work, but you can try it. I've never compiled from source before, but I know how to do it... in theory.

First thing you have to do is unzip the .tar.gz to your desktop. So double-click it and then click *extract* (or if you're using KDE, click the purple "up" arrow).

It should now be an unzipped folder on your desktop called zd1211-driver-r77.

Go to a terminal (see my sig) and paste in these commands: ```
cd ~/Desktop/zd1211-driver-r77
./configure
make
sudo make install
``` Then, when you get errors--and my guess is that you will--post them back here, and someone who really knows how to compile from source will help you.

---

### Post by dontpanic0 on 2006-05-19
The folder is not called what you said it would be, its called 'zd1211-driver-r77'.  It had an error at the ./configure step.  It says 'No such file or directory'
Thanks anyway.

---

### Post by meng on 2006-05-19
Yeah, what aysiu said. Except, assuming you've chosen the correct driver, it should be (from where you last were):
cd zd1211-driver-r77
./configure
make
sudo make install

---

### Post by meng on 2006-05-19
[QUOTE=dontpanic0]The folder is not called what you said it would be, its called 'zd1211-driver-r77'.  It had an error at the ./configure step.  It says 'No such file or directory'
Thanks anyway.[/QUOTE]

Then just
make
sudo make install

---

### Post by aysiu on 2006-05-19
[QUOTE=dontpanic0]The folder is not called what you said it would be, its called 'zd1211-driver-r77'.  It had an error at the ./configure step.  It says 'No such file or directory'
Thanks anyway.[/QUOTE] Sorry. I'm stuck on Windows right now, and it perverted the file name.

I've modified my instructions.

Do you still get the same error?

---

### Post by dontpanic0 on 2006-05-19
Yeah, thats what I did, but as I said it had an error with ./configure.
me:
It had an error at the ./configure step. It says 'No such file or directory'

---

### Post by Sef on 2006-05-19
To compile (build from source), build-essential needs to be installed.

Open the Terminal, then type

Sudo apt-get update

sudo apt-get install build-essential

---

### Post by Sef on 2006-05-19
> What does "sudo" do?

Read this to understand what sudo does

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by aysiu on 2006-05-19
Sef, thanks for covering me. I totally forgot about *build-essential*.

---

### Post by dontpanic0 on 2006-05-19
It couldn't download the files, im not connected to the internet.  Thats why I am trying to install this driver.
Could I download it to my connected comp and copy it over? (this one doesn't have linux installed)

Thanks for the info on sudo, but normally I just use su.

---

### Post by aysiu on 2006-05-19
[QUOTE=dontpanic0]It couldn't download the files, im not connected to the internet.  Thats why I am trying to install this driver.
Could I download it to my connected comp and copy it over? (this one doesn't have linux installed)[/QUOTE] Oh... this is really going to be painful.

Does the computer that has an internet connection run Ubuntu's live CD okay? In other words, if you boot a Ubuntu live CD on the connected computer, can the live CD detect your connection?

---

### Post by dontpanic0 on 2006-05-19
I tried running the live cd, but it restarted for some reasonn while booting.  I didn't see if it had an error, because I was doing something else while it started up.

---

### Post by glotz on 2006-05-19
Wonder if the driver really is a source code or if it's just a zipped binary. When you extracted it, what files did it contain?

---

### Post by dontpanic0 on 2006-05-19
These are the files:
apdbg.c
copying
Makefile
sta

Directory: src

---

### Post by dontpanic0 on 2006-05-19
If any knows of a different, easier to install driver for the same thing, please tell me where to get it.

---

### Post by akiro.yamamoto on 2006-05-19
As far as I know build-essentail is on your Ubuntu Install CD. As well as ALL the files for basic compilation.... !!
If the files are located in the src directory......then simply try:
```

cd src (or where the files are located eg: cd ~/my-driver-77/src )
./configure
make
sudo make install

```
You probably got the error about missing files because you were not in the correct directory....... ;)

---

### Post by dontpanic0 on 2006-05-19
I found a different driver, I think it's compiled already.  
[http://sourceforge.net/projects/zd1211/](http://sourceforge.net/projects/zd1211/)
The readme just says to copy the files to /lib/firmware/zd1211 where it can be loaded by the rewritten zd1211 driver.  I copied the files there. What should I do now?

---

### Post by dontpanic0 on 2006-05-19
No, I was in the correct directory.
EDIT: Nevermind, I WAS in the wrong directory.  I didn't notice the /src.  
Thanks.

---

### Post by dontpanic0 on 2006-05-19
I still got the "No such file or directory" error message

---

