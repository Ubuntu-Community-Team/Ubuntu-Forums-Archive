---
title: "installation of realplayer in ubuntu"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by sriniwas sharan upadhyay on 2007-10-09
i have downloaded real player10 gold but facing prblem in installing it

---

### Post by philinux on 2007-10-09
If anyone is going to help they'll need details like errors messages, you system spec, which version your running and how you attempted to the install etc :-k

when you say download from where, I think its in synaptic

---

### Post by overlord.gaurav on 2007-10-09
> **sriniwas sharan upadhyay said:**
> i have downloaded real player10 gold but facing prblem in installing it
What problem(s) are you facing in installing it?

---

### Post by ThrobbingBrain66 on 2007-10-09
```
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin
```

Have you followed the above instructions from the website?

---

### Post by maduranga on 2007-10-11
I got downloaded the above bin file in to the Desktop. and I executed the above post's command. but the last command gives the following output.


 ./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by por100pre1 on 2007-10-11
The easiest way (if using Feisty):

```
sudo su -c 'echo deb http://archive.canonical.com/ubuntu feisty-commercial main >> /etc/apt/sources.list'
```

```
sudo aptitude update && sudo aptitude install realplay
```

---

### Post by 1danjack on 2007-10-12
i also get a problem installing RealPlayer on my Feisty 7.04.

I've downloaded RealPlayer10GOLD.bin to my desktop.

I open a terminal window and type cd Desktop to take me to: dan@black-silver:~/Desktop$

When i type chmod +x RealPlayer10GOLD.bin and hit enter then dan@black-silver:~/Desktop$ appears on the next line.

When I then type ./RealPlayer10GOLD.bin i get the following two lines:

bash: ./RealPlayer10GOLD.bin: No such file or directory
dan@black-silver:~/Desktop$ 


I get the same error after typing sudo su and doing the above in root.

The following did not find any realplay (or realplayer)

sudo aptitude update && sudo aptitude install realplay

---

### Post by ugm6hr on 2007-10-12
Try this method as an alternative:
[http://ubuntuforums.org/showpost.php?p=2720883&postcount=4](http://ubuntuforums.org/showpost.php?p=2720883&postcount=4)

---

### Post by drs305 on 2007-10-12
1danjack,

Did you enable the canonical repository in sources.list with the command listed by por100pre1? If that repository isn't in your sources.list, you have to do this before you try to install it with aptitude.

```
sudo su -c 'echo deb http://archive.canonical.com/ubuntu feisty-commercial main >> /etc/apt/sources.list'
```

I have this repository listed in my sources.list and realplay ver 10 is in synaptic. After you execute the above line, then do the sudo update and install commands. Should work...

Edit: You can see if realplay is in the repositories you have enabled by opening synaptic. Then either click on 'search' and type in 'realplay' or click on the 'origin' tab in the lower left section and select 'archive.canonical.com/main' to see which apps that repository contains.

---

### Post by por100pre1 on 2007-10-12
> **1danjack said:**
> 

I get the same error after typing sudo su and doing the above in root.

The following did not find any realplay (or realplayer)

sudo aptitude update && sudo aptitude install realplay

Try this:

```
sudo gedit /etc/apt/sources.list
```

and add this line manually:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

Then:

```
sudo aptitude update && sudo aptitude install realplay
```

---

### Post by 1danjack on 2007-10-12
> **drs305 said:**
> 1danjack,
Edit: You can see if realplay is in the repositories you have enabled by opening synaptic. Then either click on 'search' and type in 'realplay' or click on the 'origin' tab in the lower left section and select 'archive.canonical.com/main' to see which apps that repository contains.

Hi, thanks for quick reply, i did have 'canonical supported open source software (main) selected in 'software sources/ ubuntu software' and in 'archive.canonical.com/main' i've only got two items:
vmware-server and vmware-server-kernel-source

---

### Post by 1danjack on 2007-10-12
> **por100pre1 said:**
> 

and add this line manually:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


thanks for the advice, the above line was already there three times, i added again but ended up with:

```

dan@black-silver:~$ sudo aptitude update && sudo aptitude install realplay
Get:1 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB
Get:2 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Get:3 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Get:4 http://gb.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-security/main Translation-en_GB
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB
Hit http://archive.canonical.com feisty-commercial Release
Ign http://gb.archive.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty Release
Hit http://gb.archive.ubuntu.com feisty-updates Release             
Hit http://gb.archive.ubuntu.com feisty-security Release            
Hit http://archive.canonical.com feisty-commercial/main Packages
Hit http://gb.archive.ubuntu.com feisty/main Packages               
Hit http://archive.canonical.com feisty-commercial/main Packages
Hit http://archive.canonical.com feisty-commercial/main Packages
Hit http://archive.canonical.com feisty-commercial/main Packages
Hit http://gb.archive.ubuntu.com feisty/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/main Sources
Hit http://gb.archive.ubuntu.com feisty/restricted Sources
Hit http://gb.archive.ubuntu.com feisty/universe Packages
Hit http://gb.archive.ubuntu.com feisty/universe Sources
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com feisty-security/main Packages
Hit http://gb.archive.ubuntu.com feisty-security/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-security/main Sources
Hit http://gb.archive.ubuntu.com feisty-security/restricted Sources
Hit http://gb.archive.ubuntu.com feisty-security/universe Packages
Hit http://gb.archive.ubuntu.com feisty-security/universe Sources
Hit http://gb.archive.ubuntu.com feisty-security/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-security/multiverse Sources
Fetched 4B in 1s (4B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
  kmplayer-konq-plugins 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
dan@black-silver:~$ 



```

---

### Post by por100pre1 on 2007-10-12
Are you using other than the i386 version of Feisty? I'm using the i386 version of Feisty. :-k

---

### Post by 1danjack on 2007-10-12
> **ugm6hr said:**
> Try this method as an alternative:
[http://ubuntuforums.org/showpost.php?p=2720883&postcount=4](http://ubuntuforums.org/showpost.php?p=2720883&postcount=4)

Should have said i'm on the amd64 version of ubuntu not the i386.

p.s. i've got vlc to play wma files it only won't play 'protected' wma files

---

### Post by 1danjack on 2007-10-12
i'm learning, should have summarized earlier on which version, think i'll do it i my forum sig...

what i cannot get my head around is that i've downloaded the .bin why can i not now just extract and run?

---

### Post by por100pre1 on 2007-10-12
> **1danjack said:**
> i'm learning, should have summarized earlier on which version, think i'll do it i my forum sig...

what i cannot get my head around is that i've downloaded the .bin why can i not now just extract and run?

Put in your desktop and do [this]("http://ubuntuforums.org/showpost.php?p=2383581&postcount=4").

---

### Post by 1danjack on 2007-10-13
Tried the above please see copy of terminal text here:

```

dan@black-silver:~$ cd Desktop
dan@black-silver:~/Desktop$ ls
RealPlayer10GOLD.bin
dan@black-silver:~/Desktop$ chmod 755 RealPlayer10GOLD.bin
dan@black-silver:~/Desktop$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
dan@black-silver:~/Desktop$ 
```

Nothing happened after
```
 chmod 755 RealPlayer10GOLD.bin
```
is this normal?

---

### Post by Frak on 2007-10-14
Try installing linux32 and see if it helps
```
sudo aptitude safe-update
sudo aptitude install linux32
```

---

### Post by 1danjack on 2007-10-14
Great got it installed, thanks.

It's not running et as during the install i got an error message saying the following libraries were missing:

        GTK+ 2.0 (libgtk-x11-2.0.so)
        ATK 1.0 (libatk-1.0.so)
        Pango 1.0 (libpango-1.0.so)
        PangoX 1.0 (libpangox-1.0.so)

How do i go about installing these?

---

### Post by jayaramk on 2007-10-14
what the problem in intsalling real player for ubuntu... there's a .deb package file and so u can easily install it......

type in the terminal

sudo apt-get install libstdc++5
wget -c [http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb

---

### Post by Frak on 2007-10-14
Try
```
sudo aptitude install libgtk* libatk libpango libpangox
```

Random install, but it should work.

---

### Post by 1danjack on 2007-10-14
> **jayaramk said:**
> what the problem in intsalling real player for ubuntu... there's a .deb package file and so u can easily install it......

type in the terminal

sudo apt-get install libstdc++5
wget -c [http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb


Error message relating to 32bit install:

```
dan@black-silver:~$ sudo dpkg -i realplayer_10.0.8-0.1_i386.deb
dpkg: error processing realplayer_10.0.8-0.1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 realplayer_10.0.8-0.1_i386.deb
dan@black-silver:~$ 

```

---

### Post by 1danjack on 2007-10-14
> **Frak said:**
> Try
```
sudo aptitude install libgtk* libatk libpango libpangox
```

Random install, but it should work.

No joy here either:

```
dan@black-silver:~$ sudo aptitude install libgtk* libatk libpango libpangox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
Couldn't find package "libgtk*", and more than 40
packages contain "libgtk*" in their name.
Couldn't find package "libatk".  However, the following
packages contain "libatk" in their name:
  libatk1.0-0 libatk1.0-data libatk1.0-dbg libatk1.0-dev libatk1.0-doc libatk1-ruby 
Couldn't find package "libpango".  However, the following
packages contain "libpango" in their name:
  libpango1.0-0-dbg libpango1.0-common libpango1.0-dev libpango1.0-doc libpango1-ruby libpango1.0-0 
Couldn't find any package whose name or description matched "libpangox"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
dan@black-silver:~$ 

```

---

### Post by jayaramk on 2007-10-14
the real player given by me is an i386 versio.. in oprde u con't want to install real player but u want to see movies in .rm format then see this link

[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

---

### Post by Frak on 2007-10-14
> **1danjack said:**
> No joy here either:

```
dan@black-silver:~$ sudo aptitude install libgtk* libatk libpango libpangox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
Couldn't find package "libgtk*", and more than 40
packages contain "libgtk*" in their name.
Couldn't find package "libatk".  However, the following
packages contain "libatk" in their name:
  libatk1.0-0 libatk1.0-data libatk1.0-dbg libatk1.0-dev libatk1.0-doc libatk1-ruby 
Couldn't find package "libpango".  However, the following
packages contain "libpango" in their name:
  libpango1.0-0-dbg libpango1.0-common libpango1.0-dev libpango1.0-doc libpango1-ruby libpango1.0-0 
Couldn't find any package whose name or description matched "libpangox"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
dan@black-silver:~$ 

```
Thanks for the output, try
```
sudo aptitude install libatk1.0-0 libatk1.0-data libatk1.0-dbg libatk1.0-dev libatk1.0-doc libatk1-ruby libpango1.0-0-dbg libpango1.0-common libpango1.0-dev libpango1.0-doc libpango1-ruby libpango1.0-0 libgtk2.0-0
```

Hope that helps.

---

### Post by 1danjack on 2007-10-14
Cheers jayaramk, i'll give it a go but it's to watch clips from [www.bbc.co.uk](www.bbc.co.uk) 

There is an open in stand alone player option that might work...

---

### Post by jayaramk on 2007-10-14
if u still need to play files streaming from net... u still have only one option left.....

download real player availablle in rpm format from 
[http://www.real.com/linux](http://www.real.com/linux)


and convert it into .deb using alien..... thats it ur done!!!!

---

### Post by 1danjack on 2007-10-14
> **Frak said:**
> Thanks for the output, try
```
sudo aptitude install libatk1.0-0 libatk1.0-data libatk1.0-dbg libatk1.0-dev libatk1.0-doc libatk1-ruby libpango1.0-0-dbg libpango1.0-common libpango1.0-dev libpango1.0-doc libpango1-ruby libpango1.0-0 libgtk2.0-0
```

Hope that helps.

They all installed but realplayer still doesn't work.

The icon is clickable under Applications>Sound & Video but does nothing.
When I try to un-install it in Add/Remove Apps it doesn't exist!

Also I keep getting an error message in terminal:

```
Message from syslogd@black-silver at Sun Oct 14 20:06:27 2007 ...
black-silver kernel: [  150.643400] Disabling IRQ #7

```
Is this related?

---

### Post by Frak on 2007-10-14
> **1danjack said:**
> They all installed but realplayer still doesn't work.

The icon is clickable under Applications>Sound & Video but does nothing.
When I try to un-install it in Add/Remove Apps it doesn't exist!

Also I keep getting an error message in terminal:

```
Message from syslogd@black-silver at Sun Oct 14 20:06:27 2007 ...
black-silver kernel: [  150.643400] Disabling IRQ #7

```
Is this related?
run uname -a and paste the output.

---

### Post by 1danjack on 2007-10-14
Linux black-silver 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux

---

### Post by Frak on 2007-10-14
> **1danjack said:**
> Linux black-silver 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
Your current kernel doesn't have the ability to successfully interrupt Parallel Port 1 or your sound card from working, so it disabled the interrupting. Not a big issue. Doesn't hurt sound or your computer in any way.

---

### Post by 1danjack on 2007-10-14
Thanks for the reassurance.

---

### Post by 1danjack on 2007-10-14
> **jayaramk said:**
> the real player given by me is an i386 versio.. in oprde u con't want to install real player but u want to see movies in .rm format then see this link

[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

great link but won't open .ram files as stand alone player.

Think i'll have to leave the alien suggestion for another year (linux isn't even my 2nd language!)

---

### Post by jayaramk on 2007-10-15
u just need to convert it into .deb package by using alien comand in the terminal...... even i installed it in the same way and now it works fine..........

firstly navigate to the place where the .rpm file is present
use the command

sudo alien filename.rpm

then in the same place a .deb file is created and so u can install it!!!!



if ur system doesn't have the alien installed.. u can download it from the repositories......... or type in terminal

sudo apt-get install alien

---

### Post by Frak on 2007-10-15
> **jayaramk said:**
> u just need to convert it into .deb package by using alien comand in the terminal...... even i installed it in the same way and now it works fine..........

firstly navigate to the place where the .rpm file is present
use the command

sudo alien filename.rpm

then in the same place a .deb file is created and so u can install it!!!!
Actually, you need to run
```
sudo aptitude install alien
```
first

---

### Post by 1danjack on 2007-10-15
Thanks for your info, the website looks a bit much but the command prompt was nice and easy.
Unfortunately it didn't work, below is the log file if you are able to decipher it:
```
dan@black-silver:~/Desktop$ sudo alien RealPlayer10GOLD.rpm
Warning: Skipping conversion of scripts in package RealPlayer: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/realplayer
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information dan@black-silver:~/Desktop$ sudo alien RealPlayer10GOLD.rpm
Warning: Skipping conversion of scripts in package RealPlayer: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/realplayer
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: RealPlayer-10.0.9.809: No such file or directory
dan@black-silver:~/Desktop$ 
for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: RealPlayer-10.0.9.809: No such file or directory
dan@black-silver:~/Desktop$ 

```

---

### Post by Frak on 2007-10-15
I just thought, why are we messing around with converting?

```
sudo alien install /path/to/file
```

Reduces errors.

---

### Post by 1danjack on 2007-10-16
Many thanks for your perseverance.

I'm only a few days into command line language i tried the following without success:

```
dan@black-silver:~$ sudo alien install /Desktop/
Password:
File "install" not found.
dan@black-silver:~$ cd Desktop
dan@black-silver:~/Desktop$ ls -a
.   RealPlayer             RealPlayer10GOLD.bin
..  RealPlayer-10.0.9.809  RealPlayer10GOLD.rpm
dan@black-silver:~/Desktop$ cd
dan@black-silver:~$ sudo alien install /Desktop/RealPlayer10GOLD.rpm
File "install" not found.
dan@black-silver:~$ cd Desktop
dan@black-silver:~/Desktop$ sudo alien install RealPlayer10GOLD.rpm
File "install" not found.
dan@black-silver:~/Desktop$ cd
dan@black-silver:~$ sudo alien install /Desktop
File "install" not found.
dan@black-silver:~$ 

```

---

### Post by 1danjack on 2007-10-16
I though i'd figured out where I was going wrong:

```

dan@black-silver:~$ sudo alien RealPlayer10GOLD.rpm install
Password:
File "RealPlayer10GOLD.rpm" not found.
dan@black-silver:~$ sudo alien /Desktop/RealPlayer10GOLD.rpm install
File "/Desktop/RealPlayer10GOLD.rpm" not found.
dan@black-silver:~$ sudo alien /Desktop RealPlayer10GOLD.rpm install
File "/Desktop" not found.
dan@black-silver:~$ cd Desktop
dan@black-silver:~/Desktop$ sudo alien RealPlayer10GOLD.rpm install
Warning: Skipping conversion of scripts in package RealPlayer: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `RealPlayer-10.0.9.809': File exists
mkdir: cannot create directory `RealPlayer-10.0.9.809/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/realplayer
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: RealPlayer-10.0.9.809: No such file or directory
dan@black-silver:~/Desktop$ 

```


How do I delete locked folders from my desktop? 
Surely (hopefully) I do not have to go into each folder one by one and delete all files one by one??

---

### Post by Frak on 2007-10-16
> **1danjack said:**
> Many thanks for your perseverance.

I'm only a few days into command line language i tried the following without success:

```
dan@black-silver:~$ sudo alien install /Desktop/
Password:
File "install" not found.
dan@black-silver:~$ cd Desktop
dan@black-silver:~/Desktop$ ls -a
.   RealPlayer             RealPlayer10GOLD.bin
..  RealPlayer-10.0.9.809  RealPlayer10GOLD.rpm
dan@black-silver:~/Desktop$ cd
dan@black-silver:~$ sudo alien install /Desktop/RealPlayer10GOLD.rpm
File "install" not found.
dan@black-silver:~$ cd Desktop
dan@black-silver:~/Desktop$ sudo alien install RealPlayer10GOLD.rpm
File "install" not found.
dan@black-silver:~/Desktop$ cd
dan@black-silver:~$ sudo alien install /Desktop
File "install" not found.
dan@black-silver:~$ 

```
Sorry, gave you the wrong command
try
```
cd ~/Desktop
sudo alien -i RealPlayer10GOLD.rpm
```

---

### Post by 1danjack on 2007-10-16
Still getting same errors:

```
dan@black-silver:~$ cd ~/Desktop
dan@black-silver:~/Desktop$ sudo alien -i RealPlayer10GOLD.rpm
Password:
Warning: Skipping conversion of scripts in package RealPlayer: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `RealPlayer-10.0.9.809': File exists
mkdir: cannot create directory `RealPlayer-10.0.9.809/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/realplayer
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-x11-2.0 (soname 0, path libgdk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libatk-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libatk-1.0 (soname 0, path libatk-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf-2.0 (soname 0, path libgdk_pixbuf-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangoxft-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangoxft-1.0 (soname 0, path libpangoxft-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpangox-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpangox-1.0 (soname 0, path libpangox-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpango-1.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpango-1.0 (soname 0, path libpango-1.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgobject-2.0 (soname 0, path libgobject-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-2.0 (soname 0, path libgmodule-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-2.0 (soname 0, path libglib-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-x11-2.0.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-x11-2.0 (soname 0, path libgtk-x11-2.0.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: RealPlayer-10.0.9.809: No such file or directory
dan@black-silver:~/Desktop$ 

```

---

### Post by siddartha on 2007-10-16
> **sriniwas sharan upadhyay said:**
> i have downloaded real player10 gold but facing prblem in installing it

Have you tried mplayer? It handles RealMedia as well as many other formats.

---

