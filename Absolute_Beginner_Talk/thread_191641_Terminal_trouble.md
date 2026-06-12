---
title: "Terminal trouble"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-06-07
I am trying to follow the instructions at hplip.sourceforge.net in order to get my printer running properly.  In Step 3 the following command is supposed to be entered:
$ tar xvfz [HPLIP filename.tar.gz]

The terminal keeps coming back with errors.  The first was:
$ no such command
So I tried removing the space between $ and tar.  Then I got
xvfz no such command
So I checked the help for tar and saw that command modifiers seem to always have a - before them, so I tried again and got
-xvfz no such command

Has the Dapper terminal changed from older versions?  How do I get this command string to work?

---

### Post by meng on 2006-06-07
1. The $ is just a prompt, you don't type it! Just type "tar ------ etc."
2. HPLIP is in the dapper repositories. You can use apt-get or synaptic to install it.

---

### Post by Baasha on 2006-06-07
[QUOTE=meng]1. The $ is just a prompt, you don't type it! Just type "tar ------ etc."
2. HPLIP is in the dapper repositories. You can use apt-get or synaptic to install it.[/QUOTE]

Thanks Meng,
Yes I know about hplip being installed, by my printer still doesn't work very well.  I poked around the forums looking for help, and there is a lot available, but it is mostly contradictory.  Everybody claims to have a solution, and they are all different.

I finally decided that the hplip website was probably the safest to start with.  Synaptic contains a rather outdated driver so I wanted to get the latest one using the instructions on the website.  I will go back and try again with out using the $.  It seems rather strange that someone would tell us newbies to type in the following code and then expect us to know that they really didn't mean type it exactly :( 

I have a feeling that -xvfz or its variations is still going to reject, but I'll let you know.

---

### Post by Baasha on 2006-06-07
Ok, so far so good.  Now I got down to the "./configure --prefix=/usr" command and it bombed out again.  This time it appears that the file is not compiling.  This is the printout after entering that command:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I checked in Synaptic again and found out that I do indeed have gcc installed, but the terminal apparently doesn't think so.  What do you suggest i do now?

---

### Post by Nequeo on 2006-06-07
[QUOTE=Baasha]Ok, so far so good.  Now I got down to the "./configure --prefix=/usr" command and it bombed out again.  This time it appears that the file is not compiling.  This is the printout after entering that command:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I checked in Synaptic again and found out that I do indeed have gcc installed, but the terminal apparently doesn't think so.  What do you suggest i do now?[/QUOTE]

You'd have the GCC support files installed, but not the GCC program itself.

Just type 'sudo apt-get install build-essential' from the command line to install all the necessary compiling programs

---

### Post by Baasha on 2006-06-07
[QUOTE=Nequeo]You'd have the GCC support files installed, but not the GCC program itself.

Just type 'sudo apt-get install build-essential' from the command line to install all the necessary compiling programs[/QUOTE]

Thanks!

The configure command failed several more times, but each time I went looking in Synaptic for the things it choked on.  Finally, it completed.  The printer is still working, which is a miracle, but it is not doing any better than before the new driver install.  Many features which work flawlessly in Windows, are either not available or are not working properly in Ubuntu.

I was warned that printing support was a big problem in Linux, and I guess it's true.  This is a very basic and fundamental requirement for most computer systems.  It is a shame that more attention has not been to it. ](*,)

---

