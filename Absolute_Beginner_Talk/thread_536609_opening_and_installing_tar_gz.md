---
title: "opening and installing tar gz"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-08-27
I am still having no success installing tar gz. I must be missing something. If the file is downloaded to the desktop, what do I have to do to get it on 7.04?

---

### Post by dwhitney67 on 2007-08-27
A file.tar.gz can be uncompressed and installed with one command, however that is only if it is prescribed by the installation instructions... which you have not provided.

Anyhow, here is the command to tell you what is in a .tar.gz package:

[FONT="Courier New"]$ tar tzvf file.tar.gz[/FONT]

And this is the command to extract it:

[FONT="Courier New"]$ tar xzvf file.tar.gz[/FONT]

If it needs to be extracted into a directory (folder... jeez this sound like windoze talk), then precede the last command with sudo.

---

### Post by aysiu on 2007-08-27
What are you trying to install? Are you sure you have to use a .tar.gz to do it?

---

### Post by Dark Star on 2007-08-27
What is the type of app's is inside .tar.gz.. i mean its a theme or a software or what :? Plz be clear ;)

---

### Post by pdlethbridge on 2007-08-27
one is sanes backends for a scanner and the other is firefox
/home/pdleth/Desktop/firefox-2.0.0.6(2).tar.gz
/home/pdleth/Desktop/sane-backends-1.0.18.tar.gz

---

### Post by Dark Star on 2007-08-27
To install Unzip .tar.gz and paste the unzipped folder in /home/<user name> directory then .
do this in terminal :)

```
./configure
make
su make install
```

---

### Post by Majorix on 2007-08-27
Why don't you get Firefox from the repositories?

Open a terminal (in applications > accessories) and copy&paste this there:
```
sudo apt-get install firefox
```

And it will update firefox. Though it will be automatically updated if you run a software update.

I don't know a thing about the second package though sorry.

---

### Post by Majorix on 2007-08-27
> **Dark Star said:**
> To install Unzip .tar.gz and paste the unzipped folder in /home/<user name> directory then .
do this in terminal :)

```
./configure
make
su make install
```

He meant "sudo make install". su make install will cause errors.

---

### Post by aysiu on 2007-08-27
**Sane Backends**:
Instead of compiling *sane-backends* from source, why don't you use [this .deb file?](http://http.us.debian.org/debian/pool/main/s/sane-backends/libsane_1.0.19~cvs20070730-1_i386.deb)

Download the file. Then double-click it to install it.

**Firefox**
If you're using Ubuntu 7.04, Firefox should already be 2.0.0.6. I don't know why you need a .tar.gz for that.

---

### Post by pdlethbridge on 2007-08-27
the firefox is a new version that is not in the repositories

---

### Post by sumguy231 on 2007-08-27
> **Dark Star said:**
> To install Unzip .tar.gz and paste the unzipped folder in /home/<user name> directory then .
do this in terminal :)

```
./configure
make
su make install
```

Also note that this won't work for everything distributed as a source tarball - always read the README or INSTALL file first. In fact, Firefox is one example of an application where this won't work because it's already been compiled and is distributed as binaries. But always install from the repositories before installing something from source or from third party packages.

---

### Post by Majorix on 2007-08-27
> **pdlethbridge said:**
> the firefox is a new version that is not in the repositories

Huh? I believe 2.0.0.6 is in the repos?

---

### Post by aysiu on 2007-08-27
> **pdlethbridge said:**
> the firefox is a new version that is not in the repositories
If you're using Ubuntu 7.04, the Firefox in the repositories *is* the latest version (2.0.0.6).

Maybe you should go to Synaptic and mark all upgrades and apply them.

---

### Post by pdlethbridge on 2007-08-28
the deb file gave me a libc6 error. yuck!!!!!!  The Firefox is 2.0.0.6 but I can't use some features when I go to Yahoo. beta. It just kicks me back to my regular yahoo. All my downloads go to the desktop until they are installed,

---

### Post by sumguy231 on 2007-08-28
Firefox 2.0.0.6 is available in both Feisty and Edgy, but if you're using an older version you can install it manually by these directions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Remember, the wiki can actually be pretty helpful sometimes. If you're in doubt, it's a good place to look.

> the deb file gave me a libc6 error. yuck
Which deb? The one in the repositories for your version of Ubuntu? That shouldn't happen. Post your Ubuntu version and the error output.

P.S. You can put what version of Ubuntu you're using in your forums profile - I recommend this since it helps others help you.

---

### Post by pdlethbridge on 2007-08-28
Feisty fawn is my OS. I was using Gdebi package installer when I got that error.

---

### Post by sumguy231 on 2007-08-28
Yeah, but where did you get the .deb from? And why not install from Synaptic?

Edit: Uhh, apparently you did get it installed. I still would like to know those things out of sheer curiosity though.

> All my downloads go to the desktop until they are installed,
Edit -> Preferences -> Main -> Downloads

> I can't use some features when I go to Yahoo. beta. It just kicks me back to my regular yahoo
Check your cookie settings in Edit -> Preferences -> Privacy -> Cookies. If you still have problems, you can try forums.mozillazine.org.

---

### Post by pdlethbridge on 2007-08-30
I am still having no success loading the sanes backend tar gz files

---

### Post by telmo on 2007-09-01
Golden rule for you...

If it's not broken don't try to fix it!
Why should you go and make things complicated? Leave it as it is.

If you want a good challenge, try to install Opera with flash and multimedia plugins. That is worth it.

;)

Good luck

---

### Post by Roasted on 2007-11-22
Not to jack the thread... but what am I doing wrong?


jason@jason:~$ cd Desktop
jason@jason:~/Desktop$ ls
realtek-linux-audiopack-4.07a  realtek-linux-audiopack-4.07a.tar.bz2
jason@jason:~/Desktop$ tar xzvf realtek-linux-audiopack-4.07a
tar: realtek-linux-audiopack-4.07a: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

