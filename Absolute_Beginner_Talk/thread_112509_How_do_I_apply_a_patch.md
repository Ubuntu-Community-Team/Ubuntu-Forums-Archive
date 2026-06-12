---
title: "How do I apply a patch"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by IainUx on 2006-01-04
I have downloaded a patch for DVB which I need to apply to run my Pinnacle PCTV 300i card from

[http://dl.bytesex.org/patches/2.6.12-rc3-1/All-2.6.12-rc3.diff.gz](http://dl.bytesex.org/patches/2.6.12-rc3-1/All-2.6.12-rc3.diff.gz)

, but I do not know how to apply the patch - can someone tell me how this is done?

---

### Post by schilcha on 2006-01-04
So, I think you want to patch the kernel-source...

First of all, you'll need to install the kernel-source. It is containted in the package linux-source-2.6.12 -- install it via synaptic (use the search freature to look it up). 

Then apply the patch to the code via something like 
```

cd /usr/src/linux-source-2.6.12
bzip2 -dc /your/path/All-2.6.12-rc3.diff.gz | patch -p1

```
(This example was taken from [http://kernelnewbies.org/faq/index.php3#patch]("http://kernelnewbies.org/faq/index.php3#patch") just have a look at it...)
Open a terminal and enter these commands. MIND: replace "/your/path" with the full path to where you saved the patch, like (/home/your_user_name/Desktop).

Finally you need to recompile the kernel -- theres an article in the ubuntu-wiki ([https://wiki.ubuntu.com/KernelCompileHowto]("https://wiki.ubuntu.com/KernelCompileHowto")). I refer to the wiki, since I've never compiled a kernel under ubuntu (only on SuSE, but I've heard things are different here).

Good Luck!

P.S. Sorry for the frequent edits, but this is my first reply in the Beginner Community and I don't want to make it too short...

---

### Post by IainUx on 2006-01-05
cheers - so far so good except the file is not a bzip2 file - suffix gz requires which archive tool?

---

### Post by estel on 2006-01-05
gzip2?

Sorry, can't remember... too tired and away from Linux box. I'd generally use tar.

---

### Post by carlosqueso on 2006-01-05
gzip requires a -z, so you'd use ```
tar -xvzf
```  Dang, SSH makes doing this from my office soooo much easier.

---

### Post by Suger on 2006-01-05
Recent versions of tar, including the one shipped with ubuntu, are able to autodetect some types of archives, like bz2 and gz. So
```
 tar xvf whatever.tar.gz 
``` is enough

If it's just a .gz (no t.tar.gz), you can also use gunzip.

---

### Post by IainUx on 2006-01-06
Cheers - got well on down thwe road now - compiled kernel, followed instructions, changed another menu.lst to refer to the new kernel after I found the one automatically changed was not the 1 being booted from, etc..

But on booting I get message: kernel panic   not syncing: VFS: unable to mount root fs on unknown-block (0,0) [4294668.866000]

I compiled without using initrd (?). Should I have done.
OR
Is there something I have 4gotten/need to learn about?

---

### Post by schilcha on 2006-01-06
Seems you have some flaw in your kernel. Probably, it's lacking the support to read your root-partition. Find out which filesystem is on your root partition -- you can see it via System -> Administration -> Disks. In the "partitions" tab of your harddisk, the filesystem is printed (in my case it's ReiserFS, but it might also be Extended 3 or something else). The driver for this filesystem-type needs either to be compiled directly into the kernel or at least as loadable module for the kernel. Check your kernel configuration to see which alternative applies to you:
```

cd /usr/src/linux-source-2.6.12
make menuconfig

```
(menuconfig is a text-based user-interface (no mouse!), but you don't need any extra packages installed (I hope). If you really dislike it, you can also try xconfig or gconfig, which will need QT- and GTK-devel packages installed)
Go to the "Filesystems" section and see if the filesystem support of your root-partition-filesystem is marked with "M" (=compile as module) or with "*" compile into the kernel or not at all!

If "M" applies (it seems to be the default), you'll need an initrd (seems to be easy to do -- according to the wiki), or you simply change it to "*", save configuration, recompile, reinstall the kernel as you already did. 
If "*" applies, something else went wrong...
If no mark is set, you're in desperate need of this kernel feature. For the sake of simplicity, give it a "*", save the configuration, recompile and install...

Good Luck

---

### Post by IainUx on 2006-01-17
Thanks - (I have been on holiday for a week) I will give it a try as soon as I have a space of time for it, and get back to report...

---

### Post by IainUx on 2006-01-18
Once again thanks for seeing that through with me - it was indeed the initrd that was needed, complicated by the fact that I then had to amend the menu.lst from an AMD64 Ubuntu installation that my pc has taken to booting from, instead of from the automatically corrected menu.lst from the Ubuntu installation I was compiling!

Now all I hve to do is figure out why the DVB frontend isnt there even though dvb is installed - but I guess that's another thread!!

---

