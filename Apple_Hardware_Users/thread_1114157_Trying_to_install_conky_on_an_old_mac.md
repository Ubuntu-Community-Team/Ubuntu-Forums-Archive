---
title: "Trying to install conky on an old mac"
date: 2009-04-02
forum: Apple Hardware Users
---

### Post by lowenduser on 2009-04-02
I have a Blue & White with a G4 400 mhz cpu (orginally a G3), 512 mb ram, 10 GB HDD, and a Radeon 7000 video card.  I have xubuntu 6.06.1 installed.  I would like to install conky.
I first tried:  sudo apt-get install conky and the system returned:
E: Couldn't find package conky
So I downloaded conky_1.4.4-1~dapper1_powerpc.deb from here:
[http://packages.ubuntu.com/dapper-backports/utils/conky](http://packages.ubuntu.com/dapper-backports/utils/conky) and ended up with conky_1.4.4-1~dapper1_powerpc.deb on the Desktop.
I then tried install conky_1.4.4-1dapper1_powerpc.deb and the system returned: install: missing destination file operand after 'conky_1.4.4.1~dapper1_powerpc.deb'

I can't seem to find a lot of information on how to install conky on a ppc machine.  Most of the info I'm finding is for the intel/amd architecture.  I'm not very sophisticated with this linux stuff so verbose explanations would be helpful.

---

### Post by cyberdork33 on 2009-04-02
sounds like there is an error in that installer in one of the scripts.

I don't think there is much difference between x86 and PPC for conky. You could always build from source.

---

### Post by lowenduser on 2009-04-02
There must be a significant difference because there were three options: amd64, i386, and powerpc.  Anyway, compling from source seems more sophisticated than my current linux skills.  I was hoping for a more straighforward way to work with the package I've downloaded.  If I must compile from source I could use some direction.  Thank you.

---

### Post by lowenduser on 2009-04-02
I tried to compile with the following commands I found at [http://conky.sourceforge.net/documentation.html:](http://conky.sourceforge.net/documentation.html:) 

   1. $ ./configure
   2. $ make
   3. # make install

However, when I tried the command:
 ./configure conky_1.4.4-1~dapper1_powerpc.deb
it returned: bash: ./configure: No such file or directory

What am I doing wrong?

---

### Post by cyberdork33 on 2009-04-02
> **lowenduser said:**
> There must be a significant difference because there were three options: amd64, i386, and powerpc.
The difference is in the binary form, not the source code. It still operates the same on each architecture.

> **lowenduser said:**
> I tried to compile with the following commands I found at [http://conky.sourceforge.net/documentation.html:](http://conky.sourceforge.net/documentation.html:) 

   1. $ ./configure
   2. $ make
   3. # make install

However, when I tried the command:
 ./configure conky_1.4.4-1~dapper1_powerpc.deb
it returned: bash: ./configure: No such file or directory
You have to download the source, unpack it, and then run those commands in the source's folder. (a deb file is a package of precompiled code).

So, I googled "conky source" and it took me here:
[http://sourceforge.net/project/showfiles.php?group_id=143975&package_id=158249&release_id=621564](http://sourceforge.net/project/showfiles.php?group_id=143975&package_id=158249&release_id=621564)

Ok so that downloads a tar archive (I got the *.gz version, but either will do). I keep my source code in a directory in my home folder. You can put yours elsewhere. So I moved the gz file to /home/cyberdork33/Sources/

once there, you unpack it. you can do this by right-clicking and choosing to 'extract here'.

now open a terminal and navigate to the source folder. for me, I do:
```
cd ~/Sources/conky-1.6.1
```now, I run the commands to compile (you make need to install some other stuff to allow you to compile first such as the build-essential package [sudo apt-get install build-essential]):
 ```
./configure
make
sudo make install
```After that, if everything goes without error, you should be able to run conky. I am not sure if it has a config file by default though.

---

### Post by lowenduser on 2009-04-03
I took your suggestion and created a Sources folder in the home directory and followed your directions.  However, when I ran the "./configure" command, it looked like everything worked except after a long output, the following was returned:

checking for pkg-config...no
configure: error pkg-config is required!

I tried the "make" command but the system returned:

make: ***No targets specified and no makefile found.  Stop.

It sounds like a config file is missing.  If so, what is the next step?  I went ahead and tried the "make" command but the following was returned:

make: *** No targets specified and no makefile found.  Stop.

I didn't bother with the "sudo make install" command.

---

### Post by kerry_s on 2009-04-03
6.0.6 dapper is a old version you should try something more up to date, like debian.
here's the net installer, it can install all debian versions.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso)

---

### Post by cyberdork33 on 2009-04-03
> **lowenduser said:**
>  checking for pkg-config...no
configure: error pkg-config is required!
It is saying that a required package is missing. Try "sudo apt-get install pkg-config" and try again.

You definitely should consider a newer release. I didn't realize you were using 6.06

---

### Post by lowenduser on 2009-04-03
I've tried Yellow Dog 5.02 & 6.1, openSuSe 11.1, Slackintosh 12.1, Ubuntu 8.04, Debian 5.0, and Xubuntu 6.06, 7.10, & 8.10 on this old mule.  Xubuntu 6.06 and 7.10 seemed to offer the best balance between performance and usability "out of the box" for a linux user with limited command line skills.  I decided to go with Dapper because it was the last offical powerpc release as far as I know. The best solution would consider a minimal ubuntu or Debian install with a light window manager like fluxbox, LXDE or openbox but that seemed formidible with my current linux skills.  I wish there were a CrunchBang powerpc port.

Anyway, I think we're making progress.  I tried the "sudo apt-get install pkg-config" command following but ./configure and a lot more "stuff" flew by on the terminal window before stopping at:

checking for X...no
configure: error: Can't locate your X11 installation

Thanks for your help.

---

### Post by cyberdork33 on 2009-04-03
> **lowenduser said:**
> 
checking for X...no
configure: error: Can't locate your X11 installation
Well, that's odd...

You do have Xorg installed right? If so, it is probabaly an error in the source configure script, which I would not feel comfortable trying to debug...

Dapper was the last "official" release, but since then, the powerpc port has been maintained by the community. there are several newer versions, including jaunty...
[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

---

### Post by lowenduser on 2009-04-03
I'm using xfce so I assume that means Xorg installed, right?  Anyway, I did a quick google search and run the following command "sudo apt-get install libx11-dev" and then ./configure again.  This time the terminal ran even longer before returning the following:
configure: error: Could not find XdbeQueryExtension in -lXext

Any ideas?

---

### Post by lowenduser on 2009-04-03
More progress.  I ran another command: "sudo apt-get libXext-dev" and then ./configure again.  The system then returned:
checking for XDamageQueryExtension in -lXdamage...no
configure: error: Could not find XDamageQueryExtension in -lXdamage

I ran "sudo apt-get install libxdamage-dev libglib2.0-dev"

More progress...returned:

checking for Xft...configure: error: Package requirements (xft) were not met:
No package 'xft' found
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
Alternatively, you may set the environment variables Xft_CFLAGS
and Xft_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any suggestions would be greatly appreciated.

---

### Post by cyberdork33 on 2009-04-03
> **lowenduser said:**
> More progress.  I ran another command: "sudo apt-get libXext-dev" and then ./configure again.  The system then returned:
checking for XDamageQueryExtension in -lXdamage...no
configure: error: Could not find XDamageQueryExtension in -lXdamage

I ran "sudo apt-get install libxdamage-dev libglib2.0-dev"

More progress...returned:

checking for Xft...configure: error: Package requirements (xft) were not met:
No package 'xft' found
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
Alternatively, you may set the environment variables Xft_CFLAGS
and Xft_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any suggestions would be greatly appreciated.
sounds like you are figuring this out... let's step back for a second.

Originally you said you tried to install conky directly, but it could not be found... do you have the universe repo enabled? This shows that is should be there:
[http://packages.ubuntu.com/dapper/conky](http://packages.ubuntu.com/dapper/conky)

If you want to continue:
libxft-dev is the package you need this time I think.

---

### Post by lowenduser on 2009-04-04
Universe repo enable?  I don't know what that is.  It sounds like something that would have made this a lot easier.

Anyway, I ran the command "sudo apt-get install libxft-dev" and then the ./configure command worked.  The then ran "make" and "make install".  I notice the following in the output:
/usr/bin/install: cannot create regular file `/usr/local/bin/conky': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/user/Sources/conky-1.6.1/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/user/Sources/conky-1.6.1/src'
make: *** [install-recursive] Error 1

I decided to go ahead anyway. I used instructions I found here: [http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)
to create a configuration file.  I started conky from the command line and it appeared on the Desktop.  However, I the NAME PID CPU% MEM% headers don't line up over the columns and the information of under those headers is readable over for a moment because getting overwritten.  In other words, If I pass a window over it, it looks great for a moment and then it gets garbled as if it's not getting refreshed.  I going to restart to see this this clears up the problem.

---

### Post by lowenduser on 2009-04-04
After the first restart the headers were lined up correctly.  I didn't care for the "logging" section so I removed that section and restarted.  Now the headers aren't lined up correctly again and I notice that background isn't transparent all the time.  I suspect the "Fortune" section is the cause of this when it refreshes.  Any thoughts on this and the header problem?

---

### Post by cyberdork33 on 2009-04-06
> **lowenduser said:**
>  /usr/bin/install: cannot create regular file `/usr/local/bin/conky': Permission denied
you should run 'sudo make install' you can still do that to install the binaries you have compiled correctly... Right now, they only reside in the source directory.

> **lowenduser said:**
> After the first restart the headers were lined up correctly.  I didn't care for the "logging" section so I removed that section and restarted.  Now the headers aren't lined up correctly again and I notice that background isn't transparent all the time.  I suspect the "Fortune" section is the cause of this when it refreshes.  Any thoughts on this and the header problem?
Well, this just sounds like conky configuration file stuff. Probably need to take this up in the greater forum now that you have conky running.

For the universe repo, check /etc/apt/sources.list or goto System > Adminstration > Software Sources

---

### Post by lowenduser on 2009-04-07
Thanks for your expert help.  It was very helpful.

---

