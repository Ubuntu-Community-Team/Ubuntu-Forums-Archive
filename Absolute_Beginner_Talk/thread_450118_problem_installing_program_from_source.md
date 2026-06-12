---
title: "problem installing program from source"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by onchilti on 2007-05-21
I am running Dapper Drake on an i386 machine. My situation is that I have tried to install a program called Cn3D-4.1. it is a protein structure modelling program. ok my steps were:
 1. I installed Build-essential (i read on another post that you needed this to compile a program from source to binary)
 2. I installed ckeckinstall
 3. I downloaded this program from NCBI    [**(http://www.ncbi.nlm.nih.gov/Structure/CN3D/cn3dunix.shtml**]("(http://www.ncbi.nlm.nih.gov/Structure/CN3D/cn3dunix.shtml"))
 4. I unziped and tarred the file. It left me with an executable, data folder, and help
       (the executable does nothing when I double click on it)
 5. I located the file in terminal and typed **./configure**
     got  bashed
 6. Then I tried  **make**
it said " make: *** No targets specified and no makefile found.  Stop."

I am thinking that this file is compiled already... so what do I do now?
Also sidenote - on the link above it specifies that I need to change internet browser settings, but firefox is not on the list and the settings in firefox are not even the same as the ones mentioned. It did have directions for Opera which I downloaded from synaptic but Opera won't work for some other strange reason......

Any help would be most appreciated,

---

### Post by kh4nh on 2007-05-21
> **onchilti said:**
> 
 4. I unziped and tarred the file. It left me with an executable, data folder, and help
       (the executable does nothing when I double click on it)
 ,

You don't need to compile anything, just cd to the untar folder and run the executable file from a **terminal**: ```
**./cn3d**
```

---

### Post by Pragmatist on 2007-05-21
You could also try mozilla/netscape.  However, did you try clicking their test image while using firefox?  You should get a popup window asking for what application to use, right?

It definitely looks like you don't need to compile anything.  After unzipping, you already have the executable and you just need to configure your system in certain ways (the directions say something about setting an environment variable pointing to the program files)

---

### Post by onchilti on 2007-05-22
I have tried "cd" ing to the executable in terminal and ./Cn3D and this is what I got 
./Cn3D: error while loading shared libraries: libpng.so.2: cannot open shared ob ject file: No such file or directory
and when I try to test on NCBI's webpage I find the program in the open with bx but then nothing happens...
Thanks but still nothing

---

### Post by Bachstelze on 2007-05-22
Which Ubuntu are you running ?

---

### Post by WW on 2007-05-22
From the web page:
> 
i386 Linux. Requires system-installed shared libraries of GTK 1.2.7 - 1.2.10, and standard image libraries (libpng, libz, libjpeg, libtiff).

Install these packages: **libgtk1.2**, **libpng12-0**, **zlib1g**, **libjpeg62**, **libtiff4**, and try running the command again.  You can use Synaptic, or give the command
```

sudo apt-get install libgtk1.2 libpng12-0 zlib1g libjpeg62 libtiff4

```

---

### Post by Bachstelze on 2007-05-22
It searches for libpng 2, not libpng 1.2. Telling him to install libpng 1.2 definitely won't work...

What disturbs me is that libpng 2 is only availaple in Warty, Hoary and Breezy. We'll have to mess up with it manually, I guess.

---

### Post by WW on 2007-05-22
> **HymnToLife said:**
> 
It searches for libpng 2, not libpng 1.2. Telling him to install libpng 1.2 definitely won't work...

Good point!
> **HymnToLife said:**
> 
What disturbs me is that libpng 2 is only availaple in Warty, Hoary and Breezy. We'll have to mess up with it manually, I guess.
Ah, so that's why I couldn't find it.

---

### Post by onchilti on 2007-05-22
ok so I have read your posts (hymn to life + WW ) and installed in synaptic all those lib's including the dev -(don't know if I needed to) and still no go. by the by I have libpng 12.0 and libpng 3.0 but nothing else?......Thank you for your help

---

### Post by WW on 2007-05-22
You don't need the -dev packages, because you are installing a precompiled version of the program.  The problem is that the program uses an old version of libpng.

You can try installing old versions of the png library by grabbing the old .deb files.  Here are the packages that will provide the shared library libpng.so.2:
[http://archive.ubuntu.com/ubuntu/pool/universe/libp/libpng/libpng2_1.0.18-1ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libp/libpng/libpng2_1.0.18-1ubuntu3_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng10-0_1.0.18-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng10-0_1.0.18-1ubuntu3_i386.deb)
These do not appear to conflict with other packages, so it should be harmless to install them.  (If you are using standard Ubuntu, and the Firefox web browser, then clicking on the links should automatically start up "gdebi", with which you can install the package.)  I am running dapper (Ubuntu 6.06), and gdebi appears to have installed these without any problems.

However, I have not tried to run (or even install)  the program that you are interested in; there may be other issues that could prevent it from working with these (or other) libraries.

EDIT: OK, I downloaded the program and tried to run it. It also needs a different (older) version of libtiff:
```

~/install/Cn3D/Cn3D-4.1$ ./Cn3D
./Cn3D: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
~/install/Cn3D/Cn3D-4.1$

```
But I think that will be the last problem:
```

~/install/Cn3D/Cn3D-4.1$ ldd Cn3D
        linux-gate.so.1 =>  (0xffffe000)
        libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0xb7e4f000)
        libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0xb7e18000)
        libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0xb7e15000)
        libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0xb7df1000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7dee000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb7de6000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7dd9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7cf2000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7cd0000)
        libpng.so.2 => /usr/lib/libpng.so.2 (0xb7cad000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7c8e000)
        libtiff.so.3 => not found
        libz.so.1 => /usr/lib/libz.so.1 (0xb7c7a000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c67000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b38000)
        /lib/ld-linux.so.2 (0xb7fa6000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b35000)
~/install/Cn3D/Cn3D-4.1$

```
libtiff.so.3 appear to be the only missing shared library.

---

### Post by WW on 2007-05-22
I got libtiff.so.3 from this older package:
[http://archive.ubuntu.com/ubuntu/pool/universe/t/tiff3g/libtiff3g_3.6.1-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tiff3g/libtiff3g_3.6.1-2_i386.deb) 
Now I don't get any complaints about missing shared libraries.  Unfortunately, I get this:
```

$ ./Cn3D
Illegal instruction
$

```
I have no idea what to do with that!  At this, point, if I really needed to run this program, I would track down the source code and compile it myself.

---

### Post by Pragmatist on 2007-05-22
Success!!  All I did to get it to work was make symbolic links for the libraries.  Specifically, when I got this message:

> ./Cn3D: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directoryI looked for libpng.so.2 and, lo and behold, did not find it.  I did find something very similar, however.  This reminded me of the symbolic link work around.  The program is looking for "libpng.so.2" and ONLY "libpng.so.2".  I have "libpng12.so". To the program, this is not the same thing!  The solution is to make a symbolic link:
```
cd /usr/lib
``````
sudo ln -s libpng12.so libpng.so.2
```I had to do the same with libtiff.  The program wants libtiff.so.3 and I have libtiff.so.4.2.1   Again, I made a symbolic link.

After making those two symbolic links, the program ran with no problem.  I started it via the command line with **./Cn3D**  (in the Cn3D directory of course).  Then, I used the test image on the Cn3D website and again, had no problems.

This work around using symbolic links is quite effective when the real problem is that the program only wants a specific version of a library.  Some programs are smart and allow libraries equal to, or above, the given version number.  Others, however, require a library of a certain version at the time the program is first released.  Then, as time goes by, the version numbers change, but the actual library is more than sufficient for the program's needs.  The problem tends to occur if you use libraries that are OLDER than the one requested by the program.

---

### Post by onchilti on 2007-05-23
It looks like you are running feisty fawn -- cause this doesn't work for me I made symbollic links to the libs you specified - I even made symbolic links (after the first failure to the names in synaptic of the libs -- ie without the "so." and still no go --- I am still at a loss plus how do you remove the symbolic links - ie. the extra ones I added in....
Again thank you all for your prompt replies

---

### Post by Pragmatist on 2007-05-23
> **onchilti said:**
> ...this doesn't work for me I made symbollic links to the libs you specified...
Please post the output of these commands (BEFORE you remove anything you made):

```
ls -l /usr/lib/libpng*
``` 
```
ls -l /usr/lib/libtiff*
```

> **onchilti said:**
> ...how do you remove the symbolic links...
You can just delete the symbolic links that you made.

---

### Post by onchilti on 2007-05-23
Code:
me@me-laptop:~$ ls -l /usr/lib/libpng*
-rw-r--r-- 1 root root 181594 2006-11-15 16:31 /usr/lib/libpng12.a
lrwxrwxrwx 1 root root     13 2007-05-21 21:43 /usr/lib/libpng12.so -> libpng12.so.0
lrwxrwxrwx 1 root root     19 2006-12-09 12:58 /usr/lib/libpng12.so.0 -> libpng12.so.0.1.2.8
-rw-r--r-- 1 root root 142304 2006-11-15 16:31 /usr/lib/libpng12.so.0.1.2.8
lrwxrwxrwx 1 root root     10 2007-05-21 21:43 /usr/lib/libpng.a -> libpng12.a
lrwxrwxrwx 1 root root     11 2007-05-21 21:43 /usr/lib/libpng.so -> libpng12.solrwxrwxrwx 1 root root     11 2007-05-22 20:51 /usr/lib/libpng.so.2 -> libpng12.so
lrwxrwxrwx 1 root root     13 2007-05-21 21:43 /usr/lib/libpng.so.3 -> libpng12.so.0

and 

me@me-laptop:~$ ls -l /usr/lib/libtiff*
-rw-r--r-- 1 root root 397344 2006-08-02 05:20 /usr/lib/libtiff.a
-rw-r--r-- 1 root root    818 2006-08-02 05:20 /usr/lib/libtiff.la
lrwxrwxrwx 1 root root     16 2007-05-22 07:38 /usr/lib/libtiff.so -> libtiff.so.4.1.4
lrwxrwxrwx 1 root root     16 2007-05-22 20:52 /usr/lib/libtiff.so.3 -> libtiff.so.4.2.1
lrwxrwxrwx 1 root root     16 2006-10-01 19:20 /usr/lib/libtiff.so.4 -> libtiff.so.4.1.4
-rw-r--r-- 1 root root 327428 2006-08-02 05:20 /usr/lib/libtiff.so.4.1.4
-rw-r--r-- 1 root root   6194 2006-08-02 05:20 /usr/lib/libtiffxx.a
-rw-r--r-- 1 root root    844 2006-08-02 05:20 /usr/lib/libtiffxx.la
lrwxrwxrwx 1 root root     18 2007-05-22 07:38 /usr/lib/libtiffxx.so -> libtiffxx.so.0.0.4
lrwxrwxrwx 1 root root     18 2007-05-22 07:38 /usr/lib/libtiffxx.so.0 -> libtiffxx.so.0.0.4
-rw-r--r-- 1 root root   7280 2006-08-02 05:20 /usr/lib/libtiffxx.so.0.0.4

here you are pragmatist

---

### Post by Pragmatist on 2007-05-23
Your listing of /usr/lib/libpng* looks fine for the most part.  The problem is with libtiff:

The program is looking for : 
/usr/lib/libtiff.so.3

You have this link: 
lrwxrwxrwx 1 root root     16 2007-05-22 20:52 /usr/lib/libtiff.so.3 -> **libtiff.so.4.2.1**

You don't have libtiff.so.4.2.1  Your actual library's name is:
-rw-r--r-- 1 root root 327428 2006-08-02 05:20 /usr/lib/**libtiff.so.4.1.4**

You made the same symbolic link as I did, but you don't have the same library.

Here is what you need to do:
```
cd /usr/lib
``````
sudo rm libtiff.so.3
``````
sudo ln -s libtiff.so.4.1.4 libtiff.so.3
```The program should work now.  The only other thing that seems strange is you have much more files for libtiff than I do.  Did you install other libtiff libraries?  Here are my listings, just for reference:

[quote=Pragmatist]
-rw-r--r-- 1 root root 177824 2006-12-20 07:01 /usr/lib/libpng12.a
lrwxrwxrwx 1 root root     18 2007-05-16 10:15 /usr/lib/libpng12.so -> libpng12.so.0.15.0
lrwxrwxrwx 1 root root     18 2007-05-16 10:01 /usr/lib/libpng12.so.0 -> libpng12.so.0.15.0
-rw-r--r-- 1 root root 139592 2006-12-20 07:01 /usr/lib/libpng12.so.0.15.0
lrwxrwxrwx 1 root root     10 2007-05-16 10:15 /usr/lib/libpng.a -> libpng12.a
lrwxrwxrwx 1 root root     11 2007-05-16 10:15 /usr/lib/libpng.so -> libpng12.so
lrwxrwxrwx 1 root root     11 2007-05-22 14:29 /usr/lib/libpng.so.2 -> libpng12.so

lrwxrwxrwx 1 root root     16 2007-05-22 14:31 /usr/lib/libtiff.so.3 -> libtiff.so.4.2.1
lrwxrwxrwx 1 root root     16 2006-11-21 19:30 /usr/lib/libtiff.so.4 -> libtiff.so.4.2.1
-rw-r--r-- 1 root root 335596 2006-08-08 01:53 /usr/lib/libtiff.so.4.2.1
[/quote]

Notice that our listings of libpng are similar, but you have much more files for libtiff.  I have one library (**libtiff.so.4.2.1**) and you have 6 libraries! (libtiff.a, libtiff.la, **libtiff.so.4.1.4**, libtiffxx.a, libtiffxx.la, libtiffxx.so.0.0.4)

This should probably not prevent your program from working if you follow my directions and just change the libtiff.so.3 link.  However, it might be useful to figure out why you have those other libraries (i.e. if you added them while trying to get this program to work, you might want to uninstall them if they don't help.  However, keeping them shouldn't matter either, they will just take up a little more space on your hard drive.)

---

### Post by onchilti on 2007-05-23
ok I fixed it like you said ... actually I copied and paste -ed the command line .... Now I get this
code 
me@me-laptop:~/Desktop/Cn3D-4.1$ ./Cn3D
Illegal instruction           

ok what to do now?
and thank you

---

### Post by Pragmatist on 2007-05-24
Well, I installed an older library just for testing purposes (3.7.4) and the program still worked.  Consequently, now that you created the proper links, I'm not sure what the problem is.

If it were me, I would upgrade my system.  If I really didn't want to do that, I would troubleshoot the libraries some more, including re-installing what is in the repositories for Dapper, and possibly installing other versions.  If all of that didn't work, I would try to find more information to troubleshoot with (Illegal Instruction is pretty general, like Segmentation Fault and Core Dump)

Is there some reason you don't want to upgrade to a newer version of Ubuntu?

---

### Post by onchilti on 2007-05-25
I think that upgrading would probably introduce too many issues to my system right now... I am too busy to deal with invalid source lists as I had during the install of Dapper... But thank you all for your generous help...maybe someday I will upgrade and it will work

---

