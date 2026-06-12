---
title: "installing with a .csh file in Ubuntu?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by rlhorn on 2007-06-13
Is it possible to do an install of a program that the install file is (install.csh)? If so, how do I go about doing it?

Thank you.

---

### Post by jcronkhite on 2007-06-13
What are you trying to install?  Are you being instructed to run a file of this type?  You've got me curious now.  Please provide any URL's to downloads or other info on the program you are trying to execute.

---

### Post by rlhorn on 2007-06-13
The program is OpenCASCADE. I have tried all the tricks listed on their forum for installing into Ubuntu with no luck.  Thought I might ask here.
This is the error I am receiving...
robert@XPSM140:/media/cdrom0# ./install.csh
-bash: ./install.csh: /bin/csh: bad interpreter: Permission denied

I have tried installing as myself and root with no luck.

Thank you.

---

### Post by mlentink on 2007-06-13
Isn t that a shell script? As far as i know, it could be a shell script for the C-shell, but Ubuntu uses bash. So in all likelyhood, bash will not be able to interpret all the commands in that file, and you will get errors.

---

### Post by jcronkhite on 2007-06-13
I did some looking around and came across this page:
[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/opencascade&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3Drun%2BOpenCASCADE%2Bon%2Bubuntu%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DvSt%26sa%3DG%26pwst%3D1]("http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/opencascade&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3Drun%2BOpenCASCADE%2Bon%2Bubuntu%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DvSt%26sa%3DG%26pwst%3D1")

The URL will translate the page to English.  Basically, it looks like you need to install JRE if you haven't already, and then using Java you install OpenCASCADE.  At least that's what it looks like to me at a glance.

If you just need a 3d modeling program, consider installing [Blender]("http://www.blender.org/") from the repos.  Good luck!

---

### Post by Skrynesaver on 2007-06-13
While ubuntu uses bash by default, there are lots of shells available, csh can be installed 
sudo apt-get install csh
then try executing the file again

---

### Post by rlhorn on 2007-06-13
> **jcronkhite said:**
> If you just need a 3d modeling program, consider installing [Blender]("http://www.blender.org/") from the repos.  Good luck!

Thank you for the info.  I will look over it when I get home tonight and give it a try.

Blender is good.  I use it every once in a while.  What I am looking for is a replacement for "Solidworks"  I tried to get it to work in wine with no luck.  this "'OpenCASCADE" looks promising.  Hopefully Ubuntu will be able to run it, I would hat to switch to Redhat or Fudora?.

Varicad looks promising also, but I really do not want to spend $700.00 for it.

Thank you again.

---

### Post by MichaelSM on 2007-08-06
Having problems as above with installing OpenCascade. I have Java 5.0 and csh. I also downloaded and installed libstdc++2.10-glibc2.2 which seemed to be an issue. Obviously the Java is working because I get the install wizard up and running but after accepting licence etc. and clicking NEXT I get the following: Well it's an attached screen-shot. What on earth does that error box mean?

Thanks for reading this.
Mike.
PS the Error box reads: 'Error-/opt/OpenCASCADE.2.0. is not writable'
I went through permissions and enabled execution of program. Was that wrong?

---

### Post by mcduck on 2007-08-06
> **MichaelSM said:**
> Having problems as above with installing OpenCascade. I have Java 5.0 and csh. I also downloaded and installed libstdc++2.10-glibc2.2 which seemed to be an issue. Obviously the Java is working because I get the install wizard up and running but after accepting licence etc. and clicking NEXT I get the following: Well it's an attached screen-shot. What on earth does that error box mean?

Thanks for reading this.
Mike.
PS the Error box reads: 'Error-/opt/OpenCASCADE.2.0. is not writable'
I went through permissions and enabled execution of program. Was that wrong?

Either the directory doesn't exist, or you don't have rights to write there. (/opt is owned by root, so the program must also be run as root if it needs to write there).

Anyway, .csh files can be run simply with "csh file.csh"

---

### Post by MichaelSM on 2007-08-06
Thank you mcduck. This forum is amazing with its help. I think I know a bit of what you mean, but need a walk-through. By the way it's my own personal PC so there should be no admin problems re. password etc..

Thinking about it, of course installing a program is an administration job. 

How do I do that?

I have something totally weird to add, mcduck. I have two completely separate Ubuntu boxes which are never ON at the same time. The one I'm using now is loaded with EDGY, and is the box and hd I downloaded OpenCascade to just before. The other box is Ubuntu Studios, and has admin rights as in michael-YYYYY. The one I'm using right now has admin rights as michael-XXXX.
When I go to File>Properties>Permissions for OpenCascade the admin rights are the ones for the OTHER BOX! As in michael-YYYYY. How can that be?

Thank you for your assistance.

Michael.

---

### Post by mcduck on 2007-08-06
> **MichaelSM said:**
> Thank you mcduck. This forum is amazing with its help. I think I know a bit of what you mean, but need a walk-through. By the way it's my own personal PC so there should be no admin problems re. password etc..

Thinking about it, of course installing a program is an administration job. 

How do I do that?

I have something totally weird to add, mcduck. I have two completely separate Ubuntu boxes which are never ON at the same time. The one I'm using now is loaded with EDGY, and is the box and hd I downloaded OpenCascade to just before. The other box is Ubuntu Studios, and has admin rights as in michael-YYYYY. The one I'm using right now has admin rights as michael-XXXX.
When I go to File>Properties>Permissions for OpenCascade the admin rights are the ones for the OTHER BOX! As in michael-YYYYY. How can that be?

Thank you for your assistance.

Michael.
I'm not sure if I understood correctly what you are talking about :D

Since the program is going to be in /opt, it shold probably be owned by root, not you. And to install it, you need to run the install script with sudo (so the installer can actually write into /opt), like "sudo csh install.csh".

---

### Post by MichaelSM on 2007-08-06
Hi again mcduck. I'm a bit lost here. I ran what you suggested:

michael@michael-desktop:~$ sudo csh install.csh
InstallShield Wizard

Initializing InstallShield Wizard...

Preparing Java(tm) Virtual Machine...
...................................
...................................
...................................
...................................
...................................
...................................
...................................
...................................
...................................
./tmp/isjoj1AwP/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

michael@michael-desktop:~$ 

Is that any help?

Thank you,
Michael.

---

### Post by mcduck on 2007-08-06
> **MichaelSM said:**
> Hi again mcduck. I'm a bit lost here. I ran what you suggested:

michael@michael-desktop:~$ sudo csh install.csh
InstallShield Wizard

Initializing InstallShield Wizard...

Preparing Java(tm) Virtual Machine...
...................................
...................................
...................................
...................................
...................................
...................................
...................................
...................................
...................................
./tmp/isjoj1AwP/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

michael@michael-desktop:~$ 

Is that any help?

Thank you,
Michael.
It's still missing some library. Try to find & install that one with Synaptic, or check if it's already installed but in deiiferent place than where that nsaller is looking for it with "sudo updatedb && locate libstdc"

---

### Post by MichaelSM on 2007-08-06
Thanks again. I still have no luck, mcduck. Basically I've found and installed the 'missing' libs. I obviously don't know much about what I'm doing,
Let's get back to basics if that's OK with you.

On my Desktop I have the package /home/michael/Desktop/OpenCASCADE_Linux.tgz

 Using Archive Manager I extracted 'it' and now I have a file simply called 'Linux' there as well. On Desktop. 

At this stage I need to know how to install it as Administrator. I can start the jar file with Java but it stops at the point I mentioned earlier. 

As usual there will be something entirely simple which needs doing. For instance, how do I start the install wizard as root? Is that the issue?

Cheers and thank you,
Michael.

---

### Post by mcduck on 2007-08-07
> **MichaelSM said:**
> 
As usual there will be something entirely simple which needs doing. For instance, how do I start the install wizard as root? Is that the issue?
.

To run programs as root, just add 'sudo' in front of the command you use to start the program. (or 'gksudo' if it's a graphical program).

Anyway, the error in your last post doesn't look like it has anything to do with permissions, just that it can't find some file. Did you try running "sudo updatedb && locate libstdc" to search for the missing file?

---

### Post by MichaelSM on 2007-08-07
Hi again. I just ran that updater ...

michael@michael-desktop:~$ sudo updatedb && locate libstdc
Password:
/var/lib/dpkg/info/libstdc++6-4.1-dev.md5sums
/var/lib/dpkg/info/libstdc++6-4.1-dev.list
/var/lib/dpkg/info/libstdc++5.list
/var/lib/dpkg/info/libstdc++5.md5sums
/var/lib/dpkg/info/libstdc++5.postinst
/var/lib/dpkg/info/libstdc++5.postrm
/var/lib/dpkg/info/libstdc++5.shlibs
/var/lib/dpkg/info/libstdc++6.list
/var/lib/dpkg/info/libstdc++6.md5sums
/var/lib/dpkg/info/libstdc++6.postinst
/var/lib/dpkg/info/libstdc++6.postrm
/var/lib/dpkg/info/libstdc++6.shlibs
/var/lib/dpkg/info/libstdc++2.10-glibc2.2.postinst
/var/lib/dpkg/info/libstdc++2.10-glibc2.2.list


/var/lib/dpkg/info/libstdc++2.10-glibc2.2.prerm
/var/lib/dpkg/info/libstdc++2.10-glibc2.2.shlibs
/var/lib/dpkg/info/libstdc++2.10-glibc2.2.md5sums
/home/michael/Desktop/DESKTOP EXTRAS/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb
/home/michael/google-earth/libstdc++.so.6
/home/michael/tmp/compat-libstdc++-296-2.96-135.i386.rpm
/home/michael/tmp/usr/lib/libstdc++-2-libc6.1-1-2.9.0.so
/home/michael/tmp/usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
/home/michael/tmp/usr/lib/libstdc++-libc6.2-2.so.3
/home/michael/tmp/compat-libstdc++-296-2.96.tgz
/home/michael/libstdc++-libc6.1-1.so.2
/usr/lib/gcc/i486-linux-gnu/4.1.2/64/libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.1.2/64/libstdc++.a
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.a
/usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.5.0.7
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6.0.8
/usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
/usr/lib/libstdc++-libc6.2-2.so.3
/usr/share/doc/gcc-4.1-base/C++/README.libstdc++-baseline
/usr/share/doc/gcc-4.1-base/C++/libstdc++_symbols.txt
/usr/share/doc/gcc-4.1-base/C++/changelog.libstdc++.gz
/usr/share/doc/libstdc++6-4.1-dev
/usr/share/doc/libstdc++5
/usr/share/doc/libstdc++5/README.Debian
/usr/share/doc/libstdc++5/changelog.Debian.gz
/usr/share/doc/libstdc++5/copyright
/usr/share/doc/libstdc++6
/usr/share/doc/libstdc++2.10-glibc2.2
/usr/share/doc/libstdc++2.10-glibc2.2/changelog.Debian.gz
/usr/share/doc/libstdc++2.10-glibc2.2/README.Debian
/usr/share/doc/libstdc++2.10-glibc2.2/copyright
/usr/share/doc/libstdc++2.10-glibc2.2/README.Bugs.gz
michael@michael-desktop:~$ 

Then I ran sudo csh install.csh with the same results as before.  And the installwizard stalls at the same spot. 

I am worried that I am wasting your time. If the .opt/ error is a major point of drama, how can I get around it?
Michael.

---

### Post by MichaelSM on 2007-08-07
Re. Topic.

I checked out OpenCascade's feedback and it looks like it's an on-going issue for a lot of people. One dude was a bit angry about something I guess to do with ancient architecture (R7,  8 which no-one else uses any more (?) )  so it looks like I gotta wait for OpenCascade people to come back from holidays to sort something out......

Thanks for the help, mcduck.
Mike.

---

### Post by barna on 2007-09-11
It seems that the Linux/setupLinux.bin executable (called from install.csh) uses an other Java (probably shipped with the installation source), which has problems with the shared libraries. Try this:

cd Linux
sudo java -jar setup.jar

(they recommend: sudo java -cp setup.jar run, which I have not tested...)

This seems to work for me. However, I have not figured out yet, how to launch, what the program really does, etc.

---

