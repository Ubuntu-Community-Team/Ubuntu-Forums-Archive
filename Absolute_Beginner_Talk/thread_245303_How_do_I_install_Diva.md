---
title: "How do I install Diva?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Darrious on 2006-08-27
Just as it says. I have a video editor that I downloaded called [diva]("http://www.diva-project.org/wiki"), and I've looked at the instructions on installing it, but I really don't understand it. I've tried kino, cinelerra, and LIVES, but this seems the most easiest to use.

---

### Post by Crosbie on 2006-08-27
It looks to me like this is *very* early in development.  It's a 0.02 version, in Alpha, and almost certainly incomplete.  They only offer source code for you to compile - and it looks like it hasn't been worked on since May.  I'd try another solution for now. Have you found [PiTiVi](http://pitivi.sourceforge.net/?go=download)? Looks like it has an Ubuntu version ready to go. :)

---

### Post by Darrious on 2006-08-28
I'm trying to get Pitivi installed right now, but there are a bunch of dependencies missing. I tried to get the ubuntu package, but there does not seem to be one. If anybody can get one then that would be great.

---

### Post by norwyn on 2006-09-03
I would also like instructions on how to install PiTiVi. 
Thanks in advance.

---

### Post by norwyn on 2006-09-03
Just write ```
sudo apt-get install pitivi
``` in a terminal.

---

### Post by danielph on 2006-09-14
> **norwyn said:**
> Just write ```
sudo apt-get install pitivi
``` in a terminal.

Yes, this does install it, but it does not seem ready to use yet. Tried an mpg and an avi which load up ok and you can even create a project, but you can't do anything else.

Good luck to the developers of this and I hope it grows into something good, but for now its ```
sudo apt-get remove pitivi
``` for me.

---

### Post by Marsolin on 2006-09-14
[Avidemux]("http://linuxappfinder.com/package/avidemux") and [KDEnlive]("http://linuxappfinder.com/package/kdenlive") are others you can try. Avidemux is in the Ubuntu repositories. KDEnlive is in the Marillat (Debian Multimedia) repository.

---

### Post by Flamekebab on 2006-10-03
Is Diva dead?

---

### Post by Darrious on 2006-10-04
I would like to ask the same question about Diva. Has it many any new releases? Also, I would not recommend it, even though it does seem interesting, it is still in the ALPHA stages. I would wait till beta.

---

### Post by xenoalien on 2006-11-30
I sure hope they're not dead... diva's main webpage has been down for a long time... but you can still get releases:

[http://files.diva-project.org/releases/](http://files.diva-project.org/releases/)

can someone please help me install it.

thanks

---

### Post by danielph on 2006-11-30
> **xenoalien said:**
> 
[http://files.diva-project.org/releases/](http://files.diva-project.org/releases/)

can someone please help me install it.

thanks


You will need to install Scons. I believe it is in the repos. (edgy)

Download the diva tarball and unpack it into a folder. 

In a terminal change to the folder you unpacked and run

```
scons install PREFIX=/usr
```Help should be available at [http://www.diva-project.org/wiki/Installation](http://www.diva-project.org/wiki/Installation) , but it seems to still be down.

---

### Post by xenoalien on 2006-11-30
When I try to install with the terminal this is what it says:
================================================================
xenoalien@xenoalien:~$ cd /home/xenoalien/Desktop/appz/diva-0.0.2
xenoalien@xenoalien:~/Desktop/appz/diva-0.0.2$ scons install PREFIX=/usrscons: Reading SConscript files ...

Dependency check:

   Checking for pkg gstreamer-0.10 >= 0.10.4 ...                (cached) no
xenoalien@xenoalien:~/Desktop/appz/diva-0.0.2$ 
=================================================================
Anyone know how to solve this?

---

### Post by Darrious on 2006-11-30
I remember somewhere I had installed diva from apt-get install diva.

I forget the link though sorry. I'll find it soon.

---

### Post by danielph on 2006-11-30
If you have gstreamer installed and you need the latest version these links may help you. Hopefully Darrious will find the link which would be a lot easier.

These may help you.

This is the latest gstreamer.
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

This was how it was done on Dapper with gstreamer-cvs install instructions
[http://ubuntuforums.org/showthread.php?t=157565](http://ubuntuforums.org/showthread.php?t=157565)

---

### Post by Darrious on 2006-12-01
Well I have found these two links.

[http://rpmseek.com/rpm/diva-0.0.2-2mdv2007.0.src.html?hl=com&cx=2000:D:0:2986883:0:0:0](http://rpmseek.com/rpm/diva-0.0.2-2mdv2007.0.src.html?hl=com&cx=2000:D:0:2986883:0:0:0)

and

[http://ubuntuforums.org/showthread.php?t=157565&highlight=HowTo+install+diva](http://ubuntuforums.org/showthread.php?t=157565&highlight=HowTo+install+diva)

---

### Post by danielph on 2006-12-01
> **Darrious said:**
> Well I have found these two links.

[http://rpmseek.com/rpm/diva-0.0.2-2mdv2007.0.src.html?hl=com&cx=2000:D:0:2986883:0:0:0](http://rpmseek.com/rpm/diva-0.0.2-2mdv2007.0.src.html?hl=com&cx=2000:D:0:2986883:0:0:0)


I could only find an x86_64 rpm here

The other link is the same as the one I posted.:)

I had a look around for a deb, but no joy. For now I guess it's a manual install.

---

### Post by Killtown on 2007-07-22
[Here]("http://nq6.blogspot.com/2007/05/diva-um-exelente-editor-de-video-do.html") is a deb package for Dapper Drake:

[http://download.ubuntu.pl/_Dapper_Drake/diva/diva_0.0.2-1_i386.deb](http://download.ubuntu.pl/_Dapper_Drake/diva/diva_0.0.2-1_i386.deb)


Crashes on Feisty though.

It would be cool if someone could write a noob how-to-install for Diva instead of the non-noob instructions:

[http://www.diva-project.org/wiki/Installation](http://www.diva-project.org/wiki/Installation)

---

### Post by Killtown on 2007-07-22
> **danielph said:**
> You will need to install Scons. 

Download the diva tarball and unpack it into a folder. 

In a terminal change to the folder you unpacked and run

```
scons install PREFIX=/usr
```
If you do that you'll get this:

> MESSAGE OF THE DAY: 05-09-2006

This is an internal release of Diva, thanks for trying it out. Make sure you have applied the patches in the /patches dir to gst-plugins-good. We still require gst patching, but this situation will be fixed in future 
 versions. Thanks for your patiance.

---

### Post by Cryophallion on 2007-07-27
I'm pretty sure diva died, with kdenlive rising from its ashes. You may want to try that (as mentioned earlier here) if you keep having problems getting diva up and running.

Best of luck.

---

