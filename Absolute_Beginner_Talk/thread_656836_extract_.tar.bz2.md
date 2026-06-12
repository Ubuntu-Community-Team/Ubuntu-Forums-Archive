---
title: "extract .tar.bz2"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-03
I have tried extracting a .tar.bz2 file with the command

> tar -xvjf xine-lib-1.1.8.tar.bz2

and I get the following error:

> bzip2:  (stdin) is not a bzip2 file.
tar:  Child returned status 2.
tar:  Error exit delayed from previous errors

What is going wrong here?

Thanks,
John

---

### Post by dwhitney67 on 2008-01-03
It appears that it is not a bz2 file.

Btw, the '-' is not necessary.  If you try the following command and it still does not work, then you have a 'bum' download.  Try downloading again.

```
tar xjvf xine-lib-1.1.8.tar.bz2
```


P.S.

x = extract
j = bz2 format
v = verbose
f = file

P.S.S.  I'm a "old-school" *nix'r, but I also believe that the 'j' is unnecessary in today's world.

---

### Post by Rocket2DMn on 2008-01-03
The file could be corrupted - Try redownloading the file.  There is also a program called bunzip2 - give that a try.  bzip2recover is available for accessing damaged archives (tho I wouldnt install anything from a damaged archive).

---

### Post by ~LoKe on 2008-01-03
Try...
```
tar xzvf xine-lib-1.1.8.tar.bz2 
```

**EDIT**: Woops, it's .bz2 not .gz.  I'm going to have to agree that the package seems damaged.

---

### Post by rsambuca on 2008-01-03
> **dwhitney67 said:**
> It appears that it is not a bz2 file.

Btw, the '-' is not necessary.  If you try the following command and it still does not work, then you have a 'bum' download.  Try downloading again.

```
tar xjvf xine-lib-1.1.8.tar.bz2
```


P.S.

x = extract
j = bz2 format
v = verbose
f = file

P.S.S.  I'm a "old-school" *nix'r, but I also believe that the 'j' is unnecessary in today's world.

Huh??  I think the '-' dash is definitely required.

---

### Post by dwhitney67 on 2008-01-03
> **rsambuca said:**
> Huh??  I think the '-' dash is definitely required.
Brew some more coffee my fellow Ubunter.  I've been doing extracting of s/w packages far more than I care to remember, and I know for fact that the '-' is not required.  In fact, (as I posted in the P.S.S. section), I believe the even the 'j' (for .bz2) and 'z' (for .gz) is no longer required when un-tarring.

---

### Post by rsambuca on 2008-01-03
> **dwhitney67 said:**
> Brew some more coffee my fellow Ubunter.  I've been doing extracting of s/w packages far more than I care to remember, and I know for fact that the '-' is not required.  In fact, (as I posted in the P.S.S. section), I believe the even the 'j' (for .bz2) and 'z' (for .gz) is no longer required when un-tarring.

Weird!  I always use the dash!  As long as it works, though.  Thanks for the info!

EDIT:  I knew about the j and z stuff, but the dash?  Even if you look at the man pages it shows the - as correct usage.  However, like I said, as long as it works.

---

### Post by ~LoKe on 2008-01-03
> **rsambuca said:**
> Weird!  I always use the dash!  As long as it works, though.  Thanks for the info!

I'm starting to second guess myself.  I can't remember if I did or not...

**EDIT**: Nope, always did it without the dash.

---

### Post by dwhitney67 on 2008-01-03
> **rsambuca said:**
> Weird!  I always use the dash!  As long as it works, though.  Thanks for the info!

EDIT:  I knew about the j and z stuff, but the dash?  Even if you look at the man pages it shows the - as correct usage.  However, like I said, as long as it works.

No worries.  I still to this day get errors when I use the 'z' to unpack a '.bz2', only to repeat the command (correctly) with the 'j'.  If only I could remember that the file type is no longer required!  As for the dash, I think that went away long ago.  Nobody likes to write documentation... perhaps that's the reason the man-page is how it is written.

Errr... With my luck, the maintainers of the 'tar' code will screw me and reinstate the necessity of the '-' tomorrow so that their documentation is correct.  Probably best to continue using it (the dash).

---

### Post by jhvillegas2 on 2008-01-03
Ok, thanks for your help with the previous step in installing Xine.  So, now when I move from extracting the necessary files, and move on to actually installing the files, I start with installation of the 'lib' files.  And I enter
> ./configure
Then I get the following error.
> configure:  error:  C compiler cannot create executables
See 'config.log' for more details.
Thank you in advance for any good suggestions?

---

### Post by dwhitney67 on 2008-01-03
You may need to install the development tools on your system, if you haven't already done so.  Here's how:

```
$ sudo apt-get install build-essential
```

You are correct with the './configure' statement.

---

