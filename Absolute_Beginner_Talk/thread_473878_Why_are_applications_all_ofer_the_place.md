---
title: "Why are applications all ofer the place?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-14
I noticed that applications are located in different folders.

Most are in /usr/lib64, while others are in /usr/lib32, and others are in /usr/local

Other than organization, is there any importance in separating 32 and 64 applications by folder? And why are any in /usr/local as opposed to /usr/lib[32/64]?

---

### Post by Sparkster185 on 2007-06-14
/usr/lib contains libraries.  They are separated into 32/64 bit because not all libraries need to be compiled 64 bit, since 64 bit architectures can support 32 bit instructions sets.

Generally /usr/bin contains executables (binaries).

---

### Post by earobinson on 2007-06-14
I can tell you its just an orginsational thing for the 32 and 64 bit apps but I cant tell you why

---

### Post by ggaaron on 2007-06-14
In this folders are only libraries used by programs (this lib32 lib64 folders) and they should be separated, because there are the same libraries but in different versions installed in parallel.

Applications are in many folders, /bin or /usr/bin - executables, /etc - config files, and so on=)

---

### Post by eentonig on 2007-06-14
/bin is for "system" executables and most likely will require root access to use them
/user/bin is for executables that regular users will use (Firefox, mail, etc...)

/etc is for the configuration on how you want the apps to behave.

---

### Post by Johnny K on 2007-06-14
So say I'm installing Sunbird 32, I should extract it to /usr/lib32?

---

### Post by Bluecircle on 2007-06-14
If your compiling it with make, or installing a .deb, it will automatically install to the correct folder.

---

### Post by Peverel on 2007-06-14
So, after compiling it with make etc...I can delete the extracted tar file since it installed it somewhere else?

Didn't know that....

---

### Post by sessine on 2007-06-14
yes, after the 'make install' step you can delete the source if you want.  I do this sometimes but I always keep the original tar file

---

### Post by Johnny K on 2007-06-14
> If your compiling it with make, or installing a .deb, it will automatically install to the correct folder.

But for .tar.gz files, I have to extract it myself. So should I extract it to /usr/lib[32,64]?

---

### Post by eljalill on 2007-06-14
No, just extract it to the Desktop or whatever. Than you'll either have an install dialogue, that will do the actual install to the right locations, or you'll have to compile and install, and then see above.

---

### Post by Johnny K on 2007-06-14
> **eljalill said:**
> No, just extract it to the Desktop or whatever. Than you'll either have an install dialogue, that will do the actual install to the right locations, or you'll have to compile and install, and then see above.

I extracted Thunderbird ([http://ftp-mozilla.netscape.com/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz](http://ftp-mozilla.netscape.com/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz)) to the Desktop, but I did not see an installer. It extracted the folder "thunderbird" to my desktop. In that folder is the actual application.

Sorry for not knowing much, this is my second day of Ubuntu.

---

### Post by eljalill on 2007-06-14
Welcome then :) .
Just as a hint also, it is a lot easier to install using synaptics or automatix. Programs like Thunderbird should be in there by default, and they are great means of showing you, what is out there too.

---

### Post by Johnny K on 2007-06-14
> **eljalill said:**
> Welcome then :) .
Just as a hint also, it is a lot easier to install using synaptics or automatix. Programs like Thunderbird should be in there by default, and they are great means of showing you, what is out there too.

I can't seem to find Thunderbird 2 in Synaptic.

And shouldn't the main Thunderbird application be located somewhere else, like in /usr/something?

---

### Post by sailor2001 on 2007-06-14
If I'm not mistaken thunderbird 1.5 is in synaptics but tb2 is in automatix

---

### Post by eljalill on 2007-06-14
In Synaptics thunderbird is called mozilla-thunderbird. The version in the normal repositories seems to be 1.15, but I am sure you can enable the mozilla repository and get the newest version through synaptics. I am not sure what exactly the address of that repository would be though, because I myself don't use mozilla much.. :) 

In you file system you won't really find the "main application" od Thunderbird. The binaries for it are in /bin, its libraries with the libraries and so on and so forth. But you have the application Launcher in the Main Menu and you can create another launcher wherever you like to have it... 

Btw this is another reason to install via synaptics or apt-get or so: this way it is usually easier to uninstall and update.

---

### Post by gn2 on 2007-06-14
I think USR Local is for non-repo software that is added by the user. 

I used this guide to install Sunbird on 32-bit Xubuntu, perhaps it may help.

[http://ubuntuforums.org/showthread.php?t=278206](http://ubuntuforums.org/showthread.php?t=278206)

---

### Post by Bluecircle on 2007-06-14
I have Thunderbird 2.0.0.4 in synaptics, but I'm on Gutsy. I'm pretty sure it was there when I was on Feisty though. If you download the source code from mozilla.com, simply unzip the folder, open a terminal window and cd to the folder you just extracted, and do:

```

./configure
make
sudo make install

```
after it's done installing, you can delete the source files folder and .tar.gz that you just used. Thunderbird should now be in the main menu.

---

### Post by Johnny K on 2007-06-14
> **Bluecircle said:**
> 
```

./configure
make
sudo make install

```


This is what I'm getting:
```
john@John:~/Desktop/thunderbird$ ./configure
bash: ./configure: No such file or directory
john@John:~/Desktop/thunderbird$ make
make: *** No targets specified and no makefile found.  Stop.
john@John:~/Desktop/thunderbird$ sudo make install
make: *** No rule to make target `install'.  Stop.
john@John:~/Desktop/thunderbird$ 

```

---

### Post by Bluecircle on 2007-06-15
is it a package or source code? type "ls" in the command line while your in the thunderbird directory, what is listed?

---

