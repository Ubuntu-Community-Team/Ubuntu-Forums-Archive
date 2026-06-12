---
title: "How can I install this"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-02-10
Can someone please take a look at this program Torque Game Engine Demo.

[http://www.garagegames.com/products/1/](http://www.garagegames.com/products/1/)

Please I need the demo.

Thanks.

---

### Post by deadgobby on 2007-02-10
Just DL the file to the Desktop. Left click the zip file to extract here.
it will create a new folder. open the folder up and read the README file.

---

### Post by Repent on 2007-02-10
This is all it has for Linux.

Linux

Required Hardware:

        * Pentium II/400 - AMD/400 (or better), 128+MB RAM
        * NVIDIA 3D card recommended. Other cards may work but are untested.

Required Software:

        * XFree86 4.0 or greater with a appropriate 3D drivers (GLX/DRI) for your video card.
        * Kernel 2.4.17 is not recommended.
        * The prebuilt binary packages require the following dynamic link libraries:
              o libm.so.6
              o libdl.so.2
              o libpthread.so.0
              o libc.so.6
              o /lib/ld-linux.so.2

---

### Post by Repent on 2007-02-10
Bump.

---

### Post by nickoli_02 on 2007-02-10
Use apt-get to install the required libraries:

```
sudo apt-get update
sudo apt-get install xfree86 libm.so.6 libdl.so.2 libpthread.so.0 libc.so.6 /lib/ld-linux.so.2
```

---

### Post by Repent on 2007-02-10
This is what I get.

joe203@joe203-desktop:~$ sudo apt-get install xfree86 libm.so.6 libdl.so.2 libpthread.so.0 libc.so.6 /lib/ld-linux.so.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xfree86
joe203@joe203-desktop:~$ 

Thanks for helping me.

---

### Post by Maestro23 on 2007-02-10
> **Repent said:**
> This is what I get.

joe203@joe203-desktop:~$ sudo apt-get install xfree86 libm.so.6 libdl.so.2 libpthread.so.0 libc.so.6 /lib/ld-linux.so.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xfree86
joe203@joe203-desktop:~$ 

Thanks for helping me.

Can you post the output from your /etc/apt/sources.list

> cat /etc/apt/sources.list

---

### Post by nickoli_02 on 2007-02-10
You probably don't need to install xfree86. Just remove it and install the libraries.

---

### Post by Repent on 2007-02-10
Here you go.

joe203@joe203-desktop:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security universe

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
#AUTOMATIX REPOS END
joe203@joe203-desktop:~$

---

### Post by Repent on 2007-02-11
Bump, I really need this program!

---

### Post by deadgobby on 2007-02-11
Are you installing the Demo version? Have you looked into their forum site?
[http://www.garagegames.com/index.php?sec=mg&mod=resource&page=view&qid=10028](http://www.garagegames.com/index.php?sec=mg&mod=resource&page=view&qid=10028)
[http://www.garagegames.com/mg/forums/result.forum.php?qf=72](http://www.garagegames.com/mg/forums/result.forum.php?qf=72)

---

### Post by Repent on 2007-02-11
Come on guys I really need this program, PLEASE PLEASE PLEASE. Sorry I didn't see your post thank you I will read up on it.

---

### Post by Repent on 2007-02-11
The first link is dead and the second link is my post at Garage Games the info she gave me was for the full version  that needs to be compiled.

So I still need help.

---

### Post by Mr Nick on 2007-02-11
The first link is not dead. It works for me.

---

### Post by Maestro23 on 2007-02-11
First link is good.

---

### Post by kaptainlange on 2007-02-11
> sudo apt-get install xfree86 libm.so.6 libdl.so.2 libpthread.so.0 libc.so.6 /lib/ld-linux.so.2

Well that definitely will produce errors.  But you shouldn't need to install those libraries, they seem to be pretty standard libs.  They should already be on your system.  To be sure you can do:

```
locate libm.so.6
```

For libm.so.6 as an example.  It should output something, which would be where that file is located.  If it shows its on the hard drive, then you most likely have it.  I see no reason why you wouldn't have those already.

I just downloaded and expanded the demo you downloaded.  All you should have to do is the following, which is explained in the file runtorque.sh:

```
#  Startup script.  This is used on linux only.  Its primary purpose is to 
#  set the LD_LIBRARY_PATH environment variable so that ogg/vorbis/openal
#  can be found.
#
#  You can supply "debug" as the first argument to make this script run
#  the debug executable.  Otherwise it defaults to the release executable.
#
#  The script can be run in two ways:
#  chmod +x runscript.sh
#  ./runscript.sh
```

You will also have to do chmod +x for torqueDemo.bin, kept complaining it couldn't find executable when running the script.

---

### Post by Repent on 2007-02-12
OK OK the first link isn't dead but the link to he's guide  on the page is dead and I asked for a new link . 

kaptainlange I had no idea there would be any info in the runscript.sh thank you I will see what I can do.

---

### Post by Repent on 2007-02-12
Ok here is what I tried, what am I doing wrong?



joe203@joe203-desktop:~$ cd torgueDemo.bin
bash: cd: torgueDemo.bin: No such file or directory
joe203@joe203-desktop:~$ cd'/home/joe203/TorqueDemoLinux-1.4.2' sh '/home/joe203/TorqueDemoLinux-1.4.2/show' 
bash: cd/home/joe203/TorqueDemoLinux-1.4.2: No such file or directory
joe203@joe203-desktop:~$ cd torgueDemo.bin sh '/home/joe203/TorqueDemoLinux-1.4.2' 
bash: cd: torgueDemo.bin: No such file or directory
joe203@joe203-desktop:~$ cd TorgueDemoLinux-1.4.2 sh '/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin' 
bash: cd: TorgueDemoLinux-1.4.2: No such file or directory
joe203@joe203-desktop:~$ cd: TorgueDemoLinux-1.4.2 '/home/joe203/TorqueDemoLinux-1.4.2' sh '/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin' 
bash: cd:: command not found
joe203@joe203-desktop:~$ cd TorgueDemoLinux-1.4.2 '/home/joe203/TorqueDemoLinux-1.4.2' sh '/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin'
bash: cd: TorgueDemoLinux-1.4.2: No such file or directory
joe203@joe203-desktop:~$ cd '/home/joe203/TorqueDemoLinux-1.4.2' 
joe203@joe203-desktop:~/TorqueDemoLinux-1.4.2$ sh '/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin' 
/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin: 1: Syntax error: "(" unexpected
joe203@joe203-desktop:~/TorqueDemoLinux-1.4.2$ sh torqueDemo.bin 
torqueDemo.bin: 1: Syntax error: "(" unexpected

---

### Post by kaptainlange on 2007-02-12
> **Repent said:**
> joe203@joe203-desktop:~$ cd '/home/joe203/TorqueDemoLinux-1.4.2' 
joe203@joe203-desktop:~/TorqueDemoLinux-1.4.2$ sh '/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin' 
/home/joe203/TorqueDemoLinux-1.4.2/torqueDemo.bin: 1: Syntax error: "(" unexpected
joe203@joe203-desktop:~/TorqueDemoLinux-1.4.2$ sh torqueDemo.bin 
torqueDemo.bin: 1: Syntax error: "(" unexpected

Alright, right there you were in the correct directory.  While in that directory do the following:

```
chmod +x runscript.sh
chmod +x torqueDemo.bin
./runscript.sh
```

To explain what this is doing, its setting the executable bit on runscript.sh and torqueDemo.bin.  You need to run the script, runscript.sh because it sets some environment variables torqueDemo needs.

You do ./runscript.sh instead of just runscript.sh because the command runscript.sh is not in your PATH, which is where the shell looks for commands to execute.  By specifying, ./ which means current directory, you are telling the shell where to look for the command.

If after you do all that, and you run ./runscript.sh and you get someting about a syntax error, you may want to just do the following.  In the file runscript.sh on the first line it should say this:

```
#!/bin/sh
```

This is called a shebang, and it tells the shell which command to use to run the script.  As I said, if you get errors about syntax, just replace that line with this:

```
#!/bin/bash
```

Hope this helps.

---

### Post by Repent on 2007-02-12
Wow I clicked on the runscript.sh file to drag in into the Terminal and the Game Engine fired up....lol I didn't even know it loaded.

@ kaptainlange

Thank so much I really appreciate it.:)

---

