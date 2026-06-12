---
title: "Fixing broken packages on a computer without an internet connection"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by mathwizard44 on 2007-03-29
Hello there, all. I'm a long time Windows user (currently using XP in my main machine, a laptop). But I have, as an ongoing experiment, resurrected an old Gateway machine that ran Windows 98SE, and pressed it back into service by installing Xubuntu 6.10 onto it. Even though the install and use of Linux and Xubuntu has so far been, for me, not problem-free, I am very happy with what Xubuntu has once again enabled an old computer to do.

However, today I ran into what I estimate to be a serious problem. I wanted to listen to MP3 files, and found out that gxine did not recognize them. Looking to Sourceforge for a suitable program, I found **mp3blaster**, which to me was attractive because it was run in a terminal window. In retrospect, this is where my problems had their root.

I downloaded the source package, unzipped it into my home directory, and read the installation instructions. Being a Windows user, who is used to running MSIs and installation EXEs, most of what I read seemed alien, but I decided to give it a try, anyway. The instructions were to enter three commands onto a terminal window:

```

./configure
make
make install

```

I ran into a problem at configure, finding out that gcc was not able to create executables at the time. So, after reading in some forums, I was able to discern that I need to install a package called 'build-essential', and that I could get this package from the Xubuntu Live CD by adding the CD to my Synaptic repository.

This worked, getting me past that point in the configure script. However, later, I came upon the need to procure and install the "(n)curses lib and include files" as said in the configure script. Looking back in Synaptic, I discover that there are versions of libncurses5 and some related packages already installed. However, a little more googling and forum-reading left me with the conclusion that I actually need a package named libncurses5-dev, which I didn't see in the list of packages. As my linux box was not connected to the Internet, I began to look for another way in. This time I decided to look up the Debian packages myself. I went to the website where they were kept, downloaded the package, and brought it (via flashdrive) to the Linux machine. I found out how to install .deb packages:

```
sudo -i dpkg /path/to/libncurses5-dev
```

and tried it. But when I opened Synaptic, I found out that it is a different version from a dependent library already installed in my computer--who else, if not libncurses5, which caused Synaptic to report libncurses5-dev to be a "broken" package.

In an act of hubris, of biting off more than I could chew, I went to the same website and downloaded the libncurses5 package, thinking that installing this would finally allow me to compile the program. I then ran the install for libncurses5. That's when things went wrong.

Now Synaptic tells me that because so many programs and libraries depended on the *old* libncurses5 package, there was now a grand total of **32** (thirty-two) broken packages! I am not able to find out how to resolve it, without having an internet connection. I understand that Synaptic can upgrade a system, looking up the required libraries and files if the machine was connected to the Internet. This is not currently possible, though, as my home has recently moved to cable internet and wireless access. I am afraid of turning off my computer, for fear that the mess of broken packages may rear its ugly head upon restart.

Will I have to reinstall Xubuntu (which I've had to do a couple of times this week) to get the old files back? Or is there another way I can get back the old configuration of my system without an internet connection? I'm willing to do as much hands-on as it takes. I estimate that I've learned volumes on Linux just by going through the install process.

Thanks in advance for any help.

MW

P.S. On a lighter note, I was able to continue and finish the mp3blaster install process (by itself not trivial, either). :) And now I have it playing MP3s in the terminal window, which is what I wanted to do all along. Is there a way that I can keep the program as I roll back the rest of the other packages? Thanks for the help, guys, if you should give it.

---

### Post by annda on 2007-03-29
i'm afraid i can't help you directly. but for the future, try getting packages from
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

you can download anything that is in the repositories (including mp3blaster), precompiled and prepackaged for your version of ubuntu. all dependencies are listed as well, so if you put your two computers side-by-side, the ubuntu one with synaptic open, you will see which packages you have and which you need to upgrade or install. download them all and start with installing the dependencies. you can even perversely double-click the .deb packages you downloaded to install them...

all in all, maybe another reinstall is not such a bad idea, if you have so many packages messed up. or try downgrading by removing the newer libncurses and installing the earlier version manually. see what happens.

---

### Post by mathwizard44 on 2007-03-29
Thanks for the reply. I have estimated that the solution would take considerable labor, but I'd be happy to do it. ^_^ I'm learning so much in these first few days of using linux.

Thanks again.

MW

---

### Post by mathwizard44 on 2007-03-30
This issue has been **resolved**. Thanks guys!

What I did: I went to the Ubuntu package repository online at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), selected my release (in this case, Dapper Drake), and looked for the curses packages that I have so inconsiderately replaced: libncurses5 and libncurses5-dev, both of which were of version 5.5.1-ubuntu-i386. After transferring those files onto my Linux box, I went to my terminal window:
```

sudo -i
dpkg -i [COLOR="Teal"]/path/to/[/COLOR]libncurses5
dpkg -i [COLOR="teal"]/path/to/[/COLOR]libncurses5-dev
exit

```
I had to type my password to enter superuser. (Oh, and "/path/to/" means the path to where the package was downloaded to.)

Once that was done, I checked Synaptic and the fearful little red squares are gone. ^_^ All is well again for my system. Thanks, everyone. Your help was invaluable. Let this thread serve as a warning to future hobbyists: **Don't make the same mistake as I did!**

---

