---
title: "software list in synaptic old?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by gingerj on 2007-02-24
hi all I get an error when I run a ./configure command and I've been told that I need to install my kernel source. I checked my kernel version and it's 2.6.15-27-386 but when I ran synaptic the only kernel source in there is like 2.4.... which is a lot older than my current build. does anyone know how to get synaptic to get the latest kernel source?

I'm running UBuntu 6.06 and I tried dowloading the older version of the kernel source and it didn't remedy the problem. So I'm pretty sure I need to the version that's the same as my kernel.

cheers!

---

### Post by i.am.canadian on 2007-02-24
Hey there,

I'm going to guess that you haven't recompiled your kernel since you don't already have the source on your machine, and I'm going to guess you keep your install up to date.  If this is the case then you should go to the terminal and type the following

```
sudo aptitude update
sudo aptitude install linux-tree
```

This should download the source for you and you should be able to go ahead.  If you still get the error message you may want to try creating symlink by doing 

```
sudo ln -s /usr/src/linux-2.6.12 /usr/src/linux
```

Where 2.6.12 is the kernel version you downloaded.  I hope this helps, though to be totally honest this second step is just a guess.  I'm still new at this stuff too, but I like to help where I can.

Cheers and best of luck!

---

### Post by crispy_420 on 2007-02-24
This is not my work but a cut and paste from [here]("http://hyams.webhop.net/mythtv/myth_ubuntu.html").

> First, type the following, and remember the output.

    ```
uname -r
```

For my system, the output is

    ```
2.6.12-10-686
```

It is important to remember both parts. The 2.6.12 is the kernel version (henceforth referred to as <kver>), and the -10-686 part is the extra tag. This will be important later. Now, to install the proper kernel source, execute the following command:

    ```
apt-get install linux-source-<kver> linux-headers-`uname -r`
```

where <kver> is replaced with your current kernel version that you found out from the uname -r command above. Recall that mine was 2.6.12.  And notice the backticks in the above command!  The tick used here is the one next to your 1 key, not the quote next to your Enter key.

Now that we have the source, we need to unpack it and configure its pseudo-location:

    ```
tar xvjf /usr/src/linux-source-*.tar.bz2 -C /usr/src/
    ln -s /usr/src/linux-source-<kver> /usr/src/linux
    ln -s /usr/src/linux /lib/modules/`uname -r`/build

```
Now switch to the /usr/src/linux directory:

    ```
cd /usr/src/linux
```

We need to make sure to remember our extra "tag" in the kernel source Makefile. Edit /usr/src/linux/Makefile with your favorite editor, and set the variable EXTRAVERSION (about the fourth line of the Makefile) to your "tag" that we found out from the uname -r command above. My tag was -10-686, for example. Therefore, the line in the Makefile should read something similar to:

    ```
EXTRAVERSION = -10-686
```

Now lets configure the source tree to get it ready for compiling, without actually compiling it:

    ```
cp /boot/config-`uname -r` /usr/src/linux/.config
    make oldconfig
    make prepare0
    make scripts

```
Lastly, do the following:

    ```
cd /lib/modules/`uname -r`/
    ls -l build

```
If this symbolic link points to /usr/src/linux, we don't have to do anything.  However, if it does not, manually delete it and make the link yourself:

    ```
rm build
    ln -s /usr/src/linux build

```
Yay! We finally have our build environment ready. 

---

### Post by gingerj on 2007-02-24
And this is why I'm contemplaying trying another distro cos all of that is taking the piss. Why isn't stuff like this installed by default?

I try doing this stuff and it throws errors everywhere... Try and get flash working it dies, try and get sound working it dies, try to get aptana to work it dies.

Even my theme manager doesn't want to update the list of installed themes.

Is this a 6.06 issue or is Ubuntu just painful to get anything working full stop?

---

### Post by i.am.canadian on 2007-02-24
Hi again,

I feel your pain.  I have reinstalled my system more times than I care to count, and even now I have to manually active my swap partition every time I restart my computer (I could fix it properly, but the only way I know how to do that is to reinstall again, just call me lazy).

However, to be entirely honest with you, Ubuntu is known to be one of the easier distributions to use.  Flash is a linux wide problem, changing distro's probably isn't going to make that any easier.  That said, feel free to try other distro's, that's the joy of linux.  Just to caution you though, you are most likely going to have to learn a whole new set of tools, acronyms, and command line entries.  This doesn't even mention the new problems will encounter that will be different, but probably just as annoying.

My advice?  Just stick with it.  Its frustrating, sometimes you will want to pull your hair out, but once you get it working, well that's just satisfying.  Just keep posting on the forum and you'll get the help you need.  Unless you have a particular reason to stay on dapper it might be to your advantage to upgrade, some things will have been resolved and the repos will be more up to date.

So, that's a really long post, but I hope you stick around.  You never know, you might just get it.

Cheers.

---

