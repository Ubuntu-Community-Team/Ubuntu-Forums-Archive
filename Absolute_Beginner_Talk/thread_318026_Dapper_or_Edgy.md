---
title: "Dapper or Edgy"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Nopposan on 2006-12-13
Hi, I'm having a little trouble deciding which distro to choose.  Here's what I want to do:
I want to have a solid little OS with the Xfce desktop running on an old 166MHz pentium laptop with 128mb RAM.  I also want to install web filtering software (Dansguardian with tinyproxy & firehol, etc.) on this laptop.

I've had a little trouble with Xubuntu Edgy Eft.  CDrom wasn't recognized and a few other difficulties.

I'm willing to put forth some effort to learn more about Ubuntu and maybe even contribute something that would make it easier for folks to use Ubuntu to do what I'm doing --> save an old laptop from the trash heap and make it an educational and fun computer for a youth.

Please give me some advice on whether to stick with Edgy or go with Dapper.  It's no big deal to reinstall at this point.

---

### Post by taurus on 2006-12-13
Go with Dapper (Xubuntu) and make sure you burn it at a slow speed like 4x...  You can also use the alternate CD instead of the desktop CD/LiveCD to install it on your machine.

---

### Post by Nopposan on 2006-12-13
Check.

Downloading Xubuntu Dapper now.

However, I noticed on my Xubuntu Edgy install that it includes Gimp and Gimp-print.  When I tried to use Synaptic to uninstall -- Gimp runs too slow -- Synaptic told me that Xubuntu-desktop would be removed.  What's that mean exactly?  Do I need to keep Gimp to have Xubuntu?

Thanks.

---

### Post by eldepeche on 2006-12-13
xubuntu-desktop is a meta-package. All it does is depend on all the packages that are part of the default Xubuntu desktop. You can remove it with no problem.

---

### Post by Nopposan on 2006-12-13
Cool.  Thanks, and 'sorry for my digression into a somewhat separate issue.  Sometime's it's difficult to keep on track.

So, I'll install Dapper tonight and then remove Gimp and maybe Oowriter but install some smaller apps with related functions.  Well, first of all I'll see whether my cdrom works "out-of-the-box"; I hope it does.  If I successfully install and configure the OS and apps to make this work then maybe I should post a little summary on how I did it.

Cheers.

---

### Post by Nopposan on 2006-12-14
'Burned Xubuntu 6.06 at 4x speed like you said, Taurus, but my MD5 checksum failed on ./pool/main/s/slang2/libslang2_2.0.5-1build2_i386.deb

'Wondering if I should just go with Edgy after all.  It installed fine.

Please advise.  Should I try another burn?

---

### Post by MetalMusicAddict on 2006-12-14
Try [Fluxbuntu]("http://fluxbuntu.org/").

---

### Post by mcduck on 2006-12-14
Did you do the md5 check for the downloaded .iso file before burning? If there's a problem with that one there's no way to burn a workin CD out of it..

Anyway, if possible you should use torrent download to get the iso, as torrents do automatic md5 checking so there's no way to get a bad download.

But yes, if the Edgy worked I don't see any reason why you couldn't use that one.

---

### Post by Shatrat on 2006-12-14
Before you try to burn again, perhaps you should check the iso you downloaded against the official md5sums here to see if it is corrupt.
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/MD5SUMS](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/MD5SUMS)
Just use ```
md5sum xubuntu-6.06.1-desktop-i386.iso
``` if you downloaded it to another linux machine.

---

### Post by Nopposan on 2006-12-14
O.K., thanks for the tip about Fluxbuntu; it might be helpful for the future as I'm interested in reviving old computers -- especially laptops and compact desktops.  However, I've decided on Xubuntu for this one as I know Xfce has run fine on it in the past.  Hey, it's loaded; It's got 128mb RAM and a 166GHz processor, cdrom, 2 pcmcia slots!

Anyway, as for the MD5sums, I burned the first cd using an old version of Roxio at work on my Windows desktop there.  It said it was burning at 4x but it didn't allow me to do an MD5sum check.

Also, sorry but it's too late.  I'm already using K3b on Kubuntu desktop to burn a new one.  'Couldn't wait to start over again.  'Think I'm addicted to installing Linux.

---

### Post by Sef on 2006-12-14
> Anyway, as for the MD5sums, I burned the first cd using an old version of Roxio at work on my Windows desktop there. It said it was burning at 4x but it didn't allow me to do an MD5sum check.

You can md5sum from the terminal.  Just go to the directory where the file is downloaded to and then type md5sum name_of_file.

---

### Post by Nopposan on 2006-12-15
Cool, I didn't know that.

Oh, K3b checked this one prior to allowing me to burn it, so I'm o.k. there I guess.

'Haven't begun using it to install though -- no time last night.  This computer is quite slow, and so is its cdrom.

---

### Post by robc02 on 2007-01-12
My young son has recently tried Edgy instead of Dapper. It booted quicker but he said he had a few crashes with Opera (his and my favoured web browser) and also his Creative Zen could not be recognised (we had installed Gnomad2 2.8.9 which worked perfectly in Dapper). I think he may have had a few other problems as well. Anyway, he now uses his Dapper installation again, which had been kept on a separate partition - just in case. His computer is based on an AMD K6-2 500 with 256Meg of RAM. Incidentally, he started with Kubuntu, which he liked  but was just too slow.

---

### Post by Nopposan on 2007-01-13
Thanks for the advice to stick with Dapper.  (However, I am running Kubuntu Edgy on another machine and it's working pretty well.)  It's cool that your slow machine can run Gnome.  I do like KDE better, but it's a heavy load.  Xfce seems very good on the slower machines, so you might like to try it; it has a clean and snappy look that's very similar to Gnome and it's also very customizable and lean.  (About as lean as you want it to be, that is; they add more and more options but you don't have to install them all.)

Oh, the little laptop is now running Xubuntu Dapper and making a youngster happy with the Gaim internet messenger, lots of old-fashioned arcade games, and Firefox including web filtering via DansGuardian and Tinyproxy.

Thanks, everyone, for all your help.

Cheers.

---

