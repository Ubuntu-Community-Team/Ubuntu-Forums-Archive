---
title: "A few questions (mostly about Update Manager)"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by lunatikx7 on 2005-12-27
I've installed Ubuntu as well as the unofficial add-on cd. There are a few issues that I've come across that I have no idea what to do about.

First off, this is probably my stupidity, but when I'm in the terminal and I try to become the Super User by typing su giving my password (it's the right password) when prompted, I get this responce:

garrett@ubuntu:~$ su
Password:
su: Authentication failure
Sorry.
garrett@ubuntu:~$

Next is a problem with the Update Manager that I got before the last one. When I tried to reload before I got an error box saying this:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found

Another strange issue I have is with this program that is aparantly open called English/Keyboard. It looks to be open twice on the top-right of the screen by the time and date. I'd like to know how to get this off the desktop.

Yet another question I have is about Firefox 1.5. It wasn't on Synaptic so I downloaded the .tar.gz from the official website, but I don't know what to do with it. There were no directions on the site.

Thank you for any help.

---

### Post by John.Michael.Kane on 2005-12-27
mirrormax is dead. if your using brezzy then you need to use this list [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by anil_robo on 2005-12-27
If you're new to Ubuntu, you need to know that there is no root account in Ubuntu to start with. You can use your user password to do most root actions. It means **su** won't work, but **sudo** will!

Moreover, if you've set up your root password, but still are not able to login as root, be sure to check the caps lock key. It often leads to stupid errors! ;)

---

### Post by lunatikx7 on 2005-12-27
I wanted to upgrade to Breezy but gnomebaker won't work for me.

I open gnomebaker, go to Burn CD Image, select the .iso, set it to my CD-R/RW and to 4x speed, then hit start. For some reason it tells me to insert the cd into writer, which it already is. I hit ok then my screen locks up for a while and once it's back to normal it just sits there, nothing happens. I'd like to use Breezy but until I can burn CDs with Hoary I'm in a bind.

Thanks again.

---

### Post by Madpilot on 2005-12-28
First of all, [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Gnomebaker never burns anything but coasters for me, so you're not alone! For burning ISOs, just use Nautilus - the file manager in Ubuntu. Right click on your .ISO file, select "Burn To Disc" and go from there.

K3B also works nicely for burning. It's a KDE app so it's got a really funky interface - oddball buttons all over the place - but it burns usable CDs and that's the important part...

If all you're doing is upgrading from Hoary to Breezy, though, you don't need to burn anything - you can upgrade in place quite easily: [https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

---

### Post by lunatikx7 on 2005-12-28
I tried using Nautilus. After I select Write the box goes away then nothing happens. I also tried K3B but Synaptic couldn't get the entire thing for some reason.

---

