---
title: "[SOLVED] Where programs go after installation"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-19
In windows most of the time ( Sorta a standard ) programs .exe go to the program files
folder. Of course dll file and what not shoot all over the OS.  Well, someone told me
that linux wasn't like this But from what I have seen there is no real standard were a program
ends up.  Sometimes you'll see programs end up  in /usr/bin sometimes in /usr/lib.  I've also
seen them in other places...... Is there not a standard place to arrange the executables?

---

### Post by hyper_ch on 2007-10-19
Read here:   [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by Dr Small on 2007-10-19
The programs have to end up in at least one of the locations in your $PATH.
Otherwise, it could not run. But that is just the bash file, not all of the other configuration files that make it work.

Try "echo $PATH" in the terminal to see all of the different locations of where you can execute files.

Dr Small

---

### Post by Hobo Joe on 2007-10-19
Typically they will go into the /home folder, just with a prefix of a period(folders with a period in front will be hidden), if you want to see them, just press CTRL+H.

---

### Post by hyper_ch on 2007-10-19
Hobo:

Programs don't usually go in /home/USER... the user config files for the programs go there...

---

### Post by FredB on 2007-10-19
> **Orbital75 said:**
> In windows most of the time ( Sorta a standard ) programs .exe go to the program files
folder. Of course dll file and what not shoot all over the OS.  Well, someone told me
that linux wasn't like this But from what I have seen there is no real standard were a program
ends up.  Sometimes you'll see programs end up  in /usr/bin sometimes in /usr/lib.  I've also
seen them in other places...... Is there not a standard place to arrange the executables?


/usr/bin => path for executable.

/usr/lib => path for dll-like files in linux (please, don't shoot me !)

And config files are 99% of the time in your home folder.

In a console, just type :

```

ls -al

```

And you'll get a lot of .something directories.

---

### Post by tuxmentat on 2007-10-19
Sigh... The correct answer here is: it depends.

Executable files will usually go into /usr/bin
Libraries will usually go to /usr/lib
Shared resources might go to /usr/share
Global config files will go to /etc, while local config files go to /home

In other words a typical linux installation throws files all over your file system. This is why package management is so important. Manually deleting software is a pain.

If you want to know 'exactly' where your files went, you need to ask apt. Install apt-file:

```
sudo apt-get install apt-file
```

Then if you want to know where does say Firefox live you do:

```
apt-file list firefox
```

It will list location of all the files that shipped with the firefox package.

I hope this helps. :)

---

### Post by montres on 2007-10-19
> **tuxmentat said:**
> If you want to know 'exactly' where your files went, you need to ask apt. Install apt-file:

```
sudo apt-get install apt-file
```

Then if you want to know where does say Firefox live you do:

```
apt-file list firefox
```

It will list location of all the files that shipped with the firefox package.

I hope this helps. :)

I installed apt-file  but when I tried to use it, it didn't display anything. It just returned to the command line:
```
jg@jg-desktop:~$ apt-file list Firefox
jg@jg-desktop:~$

```

Any idea why?

---

### Post by hyper_ch on 2007-10-19
you first have to update it:

```

sudo apt-file update

```

---

### Post by Lord_Dicranius on 2007-10-19
Case sensative, maybe? (I'm not at home, so I can't try it out).

---

### Post by Dr Small on 2007-10-19
Try:
```
whereis firefox
```

---

### Post by montres on 2007-10-19
> **hyper_ch said:**
> you first have to update it:

```

sudo apt-file update

```

Yes, that was it.
I tried to update but I got a bunch of 404 error messages (page not found etc).
I will tryagain some other time.

Thanks anyway!

---

### Post by Orbital75 on 2007-10-19
Yeah, that's the thing..... I wish there was an absolute standard.
I guess it's not that big of a deal but I was told that it didn't install
files all over your system and in reality, it really does..... Well,
at least we don't have a nasty registry to deal with....  :)

I plan on buying a book that can help me out out with a lot
of this.  You guys are amazing in the help you provide but
sometimes I feel like I ask way to many questions. So I'm
looking at getting this book " Ubuntu 7.10 Unleashed " Anyone
had any experience with this particular book.  Would it
answer questions such as the one in this post? I'm a pretty
smart computer user but just don't understand Linux that
well. I'm thinking a book I can grow into instead of out of
would be best for me.....

---

### Post by hyper_ch on 2007-10-19
nope, never had an Ubuntu book in my hand... apache & bind yes; but other linux books? No....

---

