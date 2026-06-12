---
title: "FreeBSD 7.0 Is In The Wild"
date: 2008-02-27
forum: BSD
---

### Post by justin whitaker on 2008-02-27
For those of you that have been waiting for the official release of 7.0, it's been updated to the FreeBSD FTP server.

[ftp://ftp.freebsd.org/pub/FreeBSD/releases/i386/ISO-IMAGES/7.0/](ftp://ftp.freebsd.org/pub/FreeBSD/releases/i386/ISO-IMAGES/7.0/)

Have fun! :)

---

### Post by qpieus on 2008-02-29
I just installed 7.0 on a vmware VM. This was my first try at freebsd. Installation was fairly easy, it has a text based installer, like arch or debian. The post installation was not easy for me, though. I used the installer to install X and KDE base. The X configure process did not work, I kept getting errors when I tried to startx. I ended up booting DesktopBSD in another VM and copied its xorg.conf to the freebsd VM. That worked OK - it gave me a working X. I put "exec startkde" in .xinitrc, like the handbook said, but KDE would not start with a "startx". I ended up enabling kdm in the rc.conf file and then startx actually started kde. The freebsd handbook did not indicate that I needed to enable KDM in rc.conf, but for gnome it said to do that (for gdm of course). So I tried it and it worked. So now I have a nice clean KDE desktop.

I also installed a few apps using the ports system. I installed yakuake and firefox. Interestingly, the bsd version of firefox did not install (the make process returned an error code 1, whatever that means), but the linux version of firefox installed just fine, although the installation took forever because a bunch of dependencies had to be built too. The yakuake install took much longer than it would on my ubuntu pc, too. For such a s small program, I figured the install would be quick. It wasn't - I guess because of the build process - I don't build much software on linux so I don't have a good idea of the time it takes.

I'm pretty geeked that I got this baby running, like I said, I've never messed around with any BSDs before. I'll continue to play around with it. I can't imagine freebsd would replace ubuntu for me, but you never know....

---

### Post by HuBaghdadi on 2008-03-02
Hey,
I have been waiting FreeBSD 7 for a long time.
Does FreeBSD downloaded image file contain ports (for example FireFox, GNOME, Java, Python...)?
I don't have an Internet connection on the PC that I intended to install FreeBSD on.

---

### Post by angryfirelord on 2008-03-08
> **HuBaghdadi said:**
> Hey,
I have been waiting FreeBSD 7 for a long time.
Does FreeBSD downloaded image file contain ports (for example FireFox, GNOME, Java, Python...)?
I don't have an Internet connection on the PC that I intended to install FreeBSD on.
I believe if you grab all three CDs, (disc 1, disc 2, & disc 3) it'll give you all of the binary packages for the release. I'm not so sure about the sources since I haven't used FreeBSD for a while.

Since wpi is supported for F7, I think I'll try it on my laptop. Hopefully the whole boot loader issue with Vista has been fixed.

---

### Post by dontgetshocked on 2008-03-09
I'm glad someone got it running because it would not install on my machine for nothing and it was NOT the disks either.Just a fast moving screen full of garbage that NEVER stopped.

---

### Post by odiseo77 on 2008-03-09
Hello people, I'm downloading the first FreeBSD 7.0 iso image. My question is, do I need the whole 3 CD's set, or I'm fine with just the first CD? (I've just installed/used FreeBSD twice, and if I'm not wrong there was only one or two CD's -and I'm too impatient to wait for the 3 CD's to download) I don't have problems with installing a minimal base system with some graphical environment and installing the remaining packages from there :)

---

### Post by angryfirelord on 2008-03-09
> **odiseo77 said:**
> Hello people, I'm downloading the first FreeBSD 7.0 iso image. My question is, do I need the whole 3 CD's set, or I'm fine with just the first CD? (I've just installed/used FreeBSD twice, and if I'm not wrong there was only one or two CD's -and I'm too impatient to wait for the 3 CD's to download) I don't have problems with installing a minimal base system with some graphical environment and installing the remaining packages from there :)
Here's what the site says:

[http://www.freebsd.org/releases/7.0R/announce.html]("http://www.freebsd.org/releases/7.0R/announce.html")
> The contents of the ISO images provided as part of the release has changed for most of the architectures. Using the i386 architecture as an example, there are ISO images named ``bootonly'', ``disc1'', ``disc2'', ``disc3'', ``livefs'', and ``docs''. The ``bootonly'' image is suitable for booting a machine to do a network based installation using FTP or NFS. The ``disc1'', ``disc2'', and ``disc3'' images are used to do a full installation that includes a basic set of packages and does not require network access to an FTP or NFS server during the installation. To boot into a ``live CD-based filesystem'' and system rescue mode ``disc1'' and ``livefs'' are needed. The ``docs'' image has all of the documentation for all supported languages. Most people will find that ``disc1'', ``disc2'' and ``disc3'' are all that are needed if you want to install some packages during the initial install, and just ``disc1'' if you prefer to install packages after the initial install is completed.
In other words, I really don't know. :) The torrents are really fast though, so unless you have a cap on your bandwidth, getting the three cds shouldn't take too long.

---

### Post by Methuselah on 2008-03-09
Setting this up right now to use as my main OS.
Had one network interface problem that was resolved with a patch.

I have always loved this OS.

It's the first open source operating system I got into.
It's probably not for everybody though.

If you prefer linux mint over ubuntu because of what comes preconfigured, you won't touch FreeBSD.

---

### Post by odiseo77 on 2008-03-09
> **angryfirelord said:**
> Here's what the site says:

[http://www.freebsd.org/releases/7.0R/announce.html]("http://www.freebsd.org/releases/7.0R/announce.html")

In other words, I really don't know. :) The torrents are really fast though, so unless you have a cap on your bandwidth, getting the three cds shouldn't take too long.

Thanks. I made a minimal install, but since I'm behind a wireless connection, I'm having problems getting online because the wpa_supplicant package is not in the first cd (which means, I can't install anything else from the ports collection). I should have followed your advice and download at least the first 2 cd's :-|
Well, I'm downloading the 2nd cd now (45 minutes left and the whole night to get my install completely working).

---

### Post by angryfirelord on 2008-03-09
> **odiseo77 said:**
> Thanks. I made a minimal install, but since I'm behind a wireless connection, I'm having problems getting online because the wpa_supplicant package is not in the first cd (which means, I can't install anything else from the ports collection). I should have followed your advice and download at least the first 2 cd's :-|
Well, I'm downloading the 2nd cd now (45 minutes left and the whole night to get my install completely working).
Heh, I did the same thing myself when I first tried FreeBSD.

As for 7.0, it installed smoothly w/o disrupting Vista (in fact, the FreeBSD bootloader can boot Vista), but the wpi driver still isn't ready yet. I get an error when I try to load it. This is my laptop, so wireless is a priority. Oh well, maybe I'll just install FreeBSD via VirtualBox and use it there.

---

### Post by Bachstelze on 2008-03-13
> **odiseo77 said:**
> Thanks. I made a minimal install, but since I'm behind a wireless connection, I'm having problems getting online because the wpa_supplicant package is not in the first cd (which means, I can't install anything else from the ports collection). I should have followed your advice and download at least the first 2 cd's :-|
Well, I'm downloading the 2nd cd now (45 minutes left and the whole night to get my install completely working).

It's a bit overkill to download a whole CD image just for a single package... Anyway, I've yet to try it on 7.0, but my IPW3945 has always worked perfectly with the wpi driver ever since 6.1.

---

### Post by odiseo77 on 2008-03-13
Yes, you're right. Anyway, since I needed a GUI (and some music) while setting up my system, I ended up downloading the 2nd cd in order to install gnome (I'm still getting familiar with FreeBSD so I didn't know *pkg_add -r* could download binary packages and install them without having to spend to much time with compilation) :)

BTW, I installed KDE from the ports collection and it spent more than one day compiling the whole set of packages in my core 2 duo :o .After that, I checked the disk usage and my /usr partition (9.5 Gb) is being used at 79 %. This surprises me since I just have Gnome and KDE installed. I guess it's because all the files created by the compilation of KDE, but I don't know how to clean my system after that. Does anyone know if there's a way to do it? Thanks in advance.

---

### Post by angryfirelord on 2008-03-13
> **HymnToLife said:**
> It's a bit overkill to download a whole CD image just for a single package... Anyway, I've yet to try it on 7.0, but my IPW3945 has always worked perfectly with the wpi driver ever since 6.1.
Did you do anything additional to get it working? I always got the ic_scan_start not found error on 6.x.

---

### Post by jnbek on 2008-04-02
> **odiseo77 said:**
> BTW, I installed KDE from the ports collection and it spent more than one day compiling the whole set of packages in my core 2 duo :o .After that, I checked the disk usage and my /usr partition (9.5 Gb) is being used at 79 %. This surprises me since I just have Gnome and KDE installed. I guess it's because all the files created by the compilation of KDE, but I don't know how to clean my system after that. Does anyone know if there's a way to do it? Thanks in advance.

you can remove all the files in /usr/ports/distfiles/ to get back some space.
also, when you ran the build did you run
```
 make install clean 
``` ?

not running the clean means all the build files are still there If not, install cvsup and fastest_cvsup using pkg_add:
```
 pkg_add -r cvsup fastest_cvsup 
```
then
```
cp /usr/share/examples/cvsup/ports-supfile /etc

```
then remove the /usr/ports/ directory, then run:

```
 cvsup -h `fastest_cvsup -q -c us` -g /etc/ports-supfile 
```

This will download the latest ports tree from whatever server fastest_cvsup has found to be fastest. After cvsup has finished downloading and installing the ports tree, ALWAYS REMEMBER to run
```
 make install clean distclean 
```

To break it down:
make:
   Fetches, extracts and verifies dependencies, as well as building needed dependencies FROM SOURCE.
install:
   Installs the package and dependencies in /usr/local/
clean:
   Cleans up the files used to compile the package and dependencies
distclean:
   Cleans up the tarballs, or other downloaded files from /usr/ports/distfiles/

---

### Post by Bachstelze on 2008-04-02
> **angryfirelord said:**
> Did you do anything additional to get it working? I always got the ic_scan_start not found error on 6.x.

Did you install the firmware?

---

### Post by odiseo77 on 2008-04-02
@ jnbek: Thanks for this detailed explanation! I'll try it when I set up my FreeBSD install again (had to install it again because I preferred it to be in my second HDD's first partition, so I must go through the whole configuration process again). However, I think I'll install KDE from binary packages with pkg_add if possible, because I don't want to spend too much time with the compilation.

---

### Post by Ptero-4 on 2008-04-02
> **HymnToLife said:**
> It's a bit overkill to download a whole CD image just for a single package... Anyway, I've yet to try it on 7.0, but my IPW3945 has always worked perfectly with the wpi driver ever since 6.1.

A couple questions. Is the IPW3945 the same wificard used in the inspiron 1420n? Also what did you do in freebsd 6.2 to get your wifi going and how do you extract the firmware?

---

### Post by jnbek on 2008-04-02
> **odiseo77 said:**
>  I think I'll install KDE from binary packages with pkg_add if possible, because I don't want to spend too much time with the compilation.
It should be possible [ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-7.0-release/Latest/](ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-7.0-release/Latest/) shows kde.tbz so a simple:

```
pkg_add -r kde
```
or
```
pkg_add -r kde-lite
```
If you want the bare minimum KDE install, should install it and it's deps, though personally I find installing from source the better alternative, yes it takes forever, but it's built optimized for your system and you have better control as to the specific packages that get installed, where with pkg_add you're stuck with whatever the package creator thought was necessary. </rant>
8-[

---

### Post by Antman on 2008-04-03
> **HymnToLife said:**
>  but my IPW3945 has always worked perfectly with the wpi driver ever since 6.1.

Hmm... glad to hear this. Do you use WPA encryption for your wireless network? I heard that this is an issue with the wpi driver. 

Once DesktopBSD 1.7 is released (based on FreeBSD7), I will probably move my desktop to it.

---

### Post by Bachstelze on 2008-04-03
> **Antman said:**
> Hmm... glad to hear this. Do you use WPA encryption for your wireless network? I heard that this is an issue with the wpi driver.

No. I know FreeBSD now has WPA support but not about that particular driver. Not like I care, though :p

---

### Post by neptho on 2008-05-12
> **Antman said:**
> Hmm... glad to hear this. Do you use WPA encryption for your wireless network? I heard that this is an issue with the wpi driver. 

It hasn't been an issue for quite a while; however, as a former (and current) FreeBSD guy, I have to say that 7.0 is still not quite ready for common use.

The wpi driver is still flakey in 7.0-RELEASE; it's only slightly better in 7.0-STABLE.  Attempting to unload/reload when it dies often causes a full system crash.

The 915 kernel driver doesn't support the 965(GM) in 7.0-RELEASE, and neither does DRI.

Making HDA Audio work is even more confusing with the myriad of device hints available, and the single option that (may) work.

Several common ethernet cards are not yet supported; I had to patch BCM5906 in from an old pre-7.0 diff I found, then add the missing parts from the DragonFlyBSD code base. 

I'd wait for 7.1 unless you like patching a lot of junk and know the basics of doing so; but my Vostro 1400 is working 100% under 7.0-STABLE now (other than the modem).

---

