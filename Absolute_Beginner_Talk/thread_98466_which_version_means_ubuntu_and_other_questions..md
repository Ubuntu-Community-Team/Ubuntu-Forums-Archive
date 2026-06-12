---
title: "which version means ubuntu and other questions."
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by brianfoster on 2005-12-03
i've seen three different kinds of linux mostly: 
linux
freeBSD
SuSE

for instance looking at the nvidia drivers, or trying to download and install gtkpod. i dont see an ubuntu download, so which one do i download?

i guess i'll just ask lots of questions here. i tried to install the flash extension for firefox, and it told me to type this string of letters into the command box, or the "Terminal". i cant remember exactly what is said, but it was a "cannot compute" kind of message. am i missing something, or is it b/c i have ubuntu and not one of those three aforementioned versions?

does rhythmbox support .m4a? well, i guess i tried an mp3 as well, and it told me "the following files cannot be loaded" what's wrong there?

well, assume a "pretty please" at the beginning of this post, and expect a "thank you, i love you" at the end. you guys rock.

---

### Post by Kvark on 2005-12-03
First follow [these instructions](http://www.psychocats.net/linux/sources.php).

Then open Synaptic Package Manager from the menu. If there is an Ubuntu version of the program then you can find it by searching for keywords in Synaptic.


If you can't find the program with Synaptic then the secound best bet is to download a .tar.gz file and look for instructions in a file called install or readme in the archive you downloaded. Check out [this guide](https://wiki.ubuntu.com/ConfigureMakeMakeInstall) to how tar.gz files are usually installed. Tar.gz files should work with any linux distro but it might take a little or a lot of work to get it working properly with your distro.

You'll need to install a package called build-essential with Synaptic before you can install tar.gz files.


[Here](http://wiki.ubuntu.com/RestrictedFormats) is the info you need to play various media formats with Ubuntu.

---

### Post by AndyCooll on 2005-12-03
Linux and BSD are operating systems (different types), just like Windows is an operating system.

SUSE, Ubuntu, Red Hat are flavours of Linux, just as XP, CE, 2000 etc are flavours of Windows. The same can be said of FreeBSD in relation to BSD.

SUSE, UBuntu and Red Hat are simply made by different companies but using the Linux kernel and are often referred to as distros. See here for more information:
[http://www.linux.org/info/index.html]("http://www.linux.org/info/index.html") 

:cool:

---

### Post by teaker1s on 2005-12-03
anything with .deb will work as ubuntu is debian based or you can install 'alien' and install rpm packages for other linux distro's

---

### Post by philipMac on 2005-12-03
[QUOTE=brianfoster]i've seen three different kinds of linux mostly: 
linux
freeBSD
SuSE
[/QUOTE]
Alright mate. 
So, Linux is Linux. What it actually is, is a kernel, or the part of the operating system that talks to the hardware. What the nice people in Ubuntu (and Suse, and Fedora, Debain etc etc) have done, is gather up that kernel, the ordinary "vanilla" Linux kernel, and basically package it all up with lots of nice open software. This is where you get your various distributions from. Suse is a type of Linux, in this way, but FreeBSD is actually not. Its a completely differant kernel. 
Just FYI. 

[QUOTE=brianfoster]
for instance looking at the nvidia drivers, or trying to download and install gtkpod. i dont see an ubuntu download, so which one do i download?
[/QUOTE]

Have a look for debian. Ubuntu is similar to Debian in some ways. 

> 
i guess i'll just ask lots of questions here. i tried to install the flash extension for firefox, and it told me to type this string of letters into the command box, or the "Terminal". i cant remember exactly what is said, but it was a "cannot compute" kind of message. am i missing something, or is it b/c i have ubuntu and not one of those three aforementioned versions?


You might want to be a bit more specific here. It worked ok for me...

> 

does rhythmbox support .m4a? well, i guess i tried an mp3 as well, and it told me "the following files cannot be loaded" what's wrong there?

well, assume a "pretty please" at the beginning of this post, and expect a "thank you, i love you" at the end. you guys rock.

Yup. They are very good people here. I also take my hat off to them. 
Good luck.

---

### Post by teaker1s on 2005-12-03
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for playback problems

---

### Post by az on 2005-12-03
Gtkpod is in universe

[http://packages.ubuntu.com/breezy/sound/gtkpod](http://packages.ubuntu.com/breezy/sound/gtkpod)

Add the universe repository to your sources and you are good to go to install it:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by brianfoster on 2005-12-03
sweetness. there are several terms you guys have mentioned that i understand, and it makes alotta sense.

i'll check it out pretty soon. im excited!

---

### Post by JimmyBEng on 2005-12-03
as for installing the nvidia drivers check the Ubuntu 5.10 Starter guide. Here's how to find it.
Go to System -> Help
Look on the first page there should be a link for Ubuntu 5.10 Starter Guide.
The part on the nvida drivers in in the section called Hardware. its the first question listed.

---

### Post by brianfoster on 2005-12-03
to Kvark, i did the first thing you told me to do, followed the directions, it ended with this message:

Fetched 4330kB in 35s (123kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

lol, dont have a clue if this changes anything, whether its good or bad, but i got a new updates memo, which i shall install pretty soon.


...and so now im just fiddling around with it, with 500 apps going all the time.

edit, oh yeah, and if i install the nvidia driver, will my dual-screens work?

---

### Post by ssam on 2005-12-03
[QUOTE=brianfoster]
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
[/QUOTE]

that message means that you have another package manager process running. this could be synaptic, apt-get, update-notifier.

check that all the others are closed, then try again.

---

