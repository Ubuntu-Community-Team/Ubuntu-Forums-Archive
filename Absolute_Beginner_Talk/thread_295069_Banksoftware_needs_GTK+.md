---
title: "Banksoftware needs GTK+"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-11-07
In my continuing quest to find out if Linux/Ubuntu can offer me everything I need, I tried installing my security module for connecting to my online bank. I knew they had a Linux module so I am very hopefull this will work. 

Step 1: 
> 1. check the presence of this library
Example:
$ ls -l /usr/lib/libwx*
If you see nothing or other files than libwx_gtk-2.2.so.6.1.6 you must download this library.
- Download of the x86 compiled version;
- Download of the PPC (PowerPC) compiled version

2. install the library after identifying yourself as administrator (“root” account)
Example:
$ su -
Password:

3. decompress (=untar) the archive libwx_gtk-2.2.so.6-x86.tar.gz or libwx_gtk-2.2.so.6-ppc.tar.gz
# cd /usr/lib
# tar-xfz /path/to/archive/libwx_gtk-2.2.so.6-x86.tar.gz


Checked it, and it wasn't there. So I downloaded it and untarred (is that how you would say this) in the /usr/lib directory. I followed the rest of the info about untarring the module to /opt/HomeBank. And ran the configuration file. All worked well. But when I tried to run it. I got the following message. 

> HBSecGui: error while loading shared libraries: libgtk-1.2.so.0. Cannot open shared object file: No such file or directory

In the notes of the software, I found this:

> Note: The library itself uses the GTK+ 1.2 version or a subsequent version. If you do not have one yet, you can find it on the page indicated above or at the address [http://www.gtk.org](http://www.gtk.org).
If you have an earlier version of the security module, please delete it first.

But on GTK.org, I can only find higher versions. Will this matter a lot and is there one in the repositories I can apt-get install?

---

### Post by po0f on 2006-11-07
Belgatom,

[libgtk1.2](http://packages.ubuntu.com/edgy/libs/libgtk1.2) is in the repos.  And you really should have untarred that wxGTK tarball in /usr/local/lib;  when you go to install wxGTK from the repos, it will probably complain or just outright overwrite those libraries.

---

### Post by Belgatom on 2006-11-07
> belgatom@belgatom-desktop:~$ sudo apt-get install libgtk1.2
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libglib1.2
The following NEW packages will be installed:
  libglib1.2 libgtk1.2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 953kB of archives.
After unpacking 2085kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main libglib1.2 1.2.10-10.1build1 [116kB]
Get:2 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main libgtk1.2 1.2.10-18 [837kB]
Fetched 953kB in 0s (1214kB/s)
Selecting previously deselected package libglib1.2.
(Reading database ... 84364 files and directories currently installed.)
Unpacking libglib1.2 (from .../libglib1.2_1.2.10-10.1build1_i386.deb) ...
Selecting previously deselected package libgtk1.2.
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-18_i386.deb) ...
Setting up libglib1.2 (1.2.10-10.1build1) ...
ldconfig: /usr/lib/libwx_gtk-2.2.so.6-x86.tar.gz is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libwx_gtk-2.2.so.6 is not a symbolic link


Setting up libgtk1.2 (1.2.10-18) ...
ldconfig: /usr/lib/libwx_gtk-2.2.so.6-x86.tar.gz is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libwx_gtk-2.2.so.6 is not a symbolic link


OK, and I assume what you wrote about the libwx... is probably the reason why I get the errors in the end. 

When I run the software now, I get another lib that's missing:

> 

belgatom@belgatom-desktop:~$ HBSecurity
HBSecGUI: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


Now looking at your advise. I should be able to figure out which library to download and install. But treading carefully, I'd like to run it by you guys first.

> sudo apt-get install libc6.2

Would that be the correct package? And do I need to reinstall the libwx_gtx library aswell?

And where do you get this info? How do I figure out what is in the repositories? Is this what I can find in synaptic - advanced ?

---

### Post by po0f on 2006-11-07
Belgatom,

I like searching [http://packages.ubuntu.com/](http://packages.ubuntu.com/) personally, but you can search through Synaptic as well, if you are more used to a GUI.  System->Administration->Synaptic.

---

### Post by Belgatom on 2006-11-07
I have looked through synaptic and the dapper repositories, but alas, I haven't figured out what to install. So any advice is still welcome. Currently seems to be that the libstdc++ is giving an error. 

> belgatom@belgatom-desktop:~$ HBSecurity
HBSecGUI: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2006-11-07
On edgy it is: (It might be a bit diffrent on dapper)

```
sudo aptitude install libstdc++2.10-glibc2.2
```

---

### Post by Belgatom on 2006-11-08
Tried both "sudo apt-get" and the exact thing above. Both failed to find a package. I just can't seem to figure out what the name is of the package that contains this needed library. 

> belgatom@belgatom-desktop:~$ sudo apt-get install libstdc++-glibc2.2
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc++-glibc2.2
belgatom@belgatom-desktop:~$ sudo aptitude install libstdc++-glibc2.2
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "libstdc++-glibc2.2"No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


---

### Post by Perfect Storm on 2006-11-08
Have you enable universe in the sourcelist?

---

### Post by Belgatom on 2006-11-08
I will check tonight. Currently at work on a MS machine. Thanks for bearing with me. Please keep an eye on this thread. My total dedication to Linux is dependent on this. If I can't do my banking on Ubuntu, it will be hard to stick with it. 

I am also contacting the bank itself today, so if anything comes out of that, it will be noted here.

---

### Post by Belgatom on 2006-11-08
Aaahhh, finally home. Time for some linux experimenting. 


> **Artificial Intelligence said:**
> Have you enable universe in the sourcelist?

I think so. 

> deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://ftp.belnet.be/packages/ubuntu/ubuntu](http://ftp.belnet.be/packages/ubuntu/ubuntu) dapper main restricted universe multiverse
deb-src [http://ftp.belnet.be/packages/ubuntu/ubuntu](http://ftp.belnet.be/packages/ubuntu/ubuntu) dapper main restricted universe multiverse

deb-src [http://imbrandon.com/packages](http://imbrandon.com/packages) dapper amarok
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


What now?

---

### Post by genzo on 2006-11-08
duno if it will help, im new myself

try installing libwxgtk2.4-1

```
sudo apt-get install libwxgtk2.4-1
```

---

### Post by Belgatom on 2006-11-08
Looked a good idea but alas. Same result as before. Still stuck on:

> belgatom@belgatom-desktop:~$ HBSecurity
HBSecGUI: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

It did install though.

---

### Post by Perfect Storm on 2006-11-08
Open synaptic and search for:

libstdc++

---

### Post by Belgatom on 2006-11-08
I did look at this yesterday but there were too many options. 

[IMG]http://users.telenet.be/belgatom/ubuntu/synaptic.jpg[/IMG]

Any advice which to select?

---

### Post by Perfect Storm on 2006-11-08
libstdc++2.10-glibc2.2

---

### Post by Belgatom on 2006-11-08
Shout Gouranga!

That's it. Perfect, runs like a dream now. 

Question: How did you distinguish that the correct one would be libstdc++2.10-glibc2.2, while the error spoke of libstdc++-libc6.2-2.so.3 (that 6 put me on the wrong track). Is there some kind of nomenclature I should learn about? 

Anyway, thank you very much. Linux world domination is imminent. (Well at least on this computer it is)

---

### Post by Perfect Storm on 2006-11-08
Well, you could search for the first thing like libstdc andd see what's shows up.
Orther than that you can check under each lib or applications in synaptic you have installed which files they contains. And ofcause when you've used linux in some time you'll get a grasp about which files belongs too and so on.

---

