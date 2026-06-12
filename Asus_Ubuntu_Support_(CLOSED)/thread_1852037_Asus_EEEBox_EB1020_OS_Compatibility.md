---
title: "Asus EEEBox EB1020 OS Compatibility"
date: 2011-09-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mattwilkes512 on 2011-09-29
Anyone know if the [Asus EEEBox EB1020]("http://www.amazon.com/Asus-EB1020-B0020-ASUS-Desktop-Black/dp/B005AKSG7O/ref=cm_cd_pdp?_encoding=UTF8&cdPage=1&noLL=1&newContentID=Tx3OIAPD5ULSYWT#CustomerDiscussions") is fully compatible with Ubuntu "out of the box"?

I'd like to purchase this machine because it fits within my budget but only want it if it'll run Ubuntu. Additionally I've read there are updates for the AMD C-50 which allow the CPU to run as a C-60 with significant performance enhancements. If this is possible with Ubuntu I'd like to know too.

Anyone done this yet?

Thanks!;)

---

### Post by mattwilkes512 on 2011-09-29
Looks like AMD does offer support for Linux c-50 and Catalysts Installer-see [here]("http://www2.ati.com/relnotes/Catalyst_11.9_Linux_Installer.pdf").

Still would like to hear from anyone who has the EB1020 with Ubuntu installed...?

---

### Post by paxmark1 on 2011-11-28
Got 11.10 Ubuntu on.  Quite slow.  Got 11.10 xubuntu on.  Faster.  Had wierd stuff on boot after grub with Debian testing, even on rescue mode.  could not get a terminal on rescue mode.  Chroot did not work for me (novice to chroot).  But via puppy linux I was able to chroot.  Had to go with non-linux-firmware and fglrx, but satisfactory results.

In general, thing that would be useful for any variant of debian.  You want to add ram.  I386 versions will install easier.  A small swap (I put on the usb stick)is a good thing.   Do not use AMD64 unless you have more ram.  (I still have 1gb ram with 300mb going to video)  A 16 gb usb stick will work for /home  

And for me, I have to figure out - buy something for the s/pdif.  I thought it was a standard audio output.  I thought I had no sound.  Live and learn in linux.

Days later.  No sound in any debian flavour of linux, Lup386 (puppy), Lubuntu, Ubuntu (both amd64) or Debian testing i386.  Only way I got sound was to go to the dark force of WinXP.  Inquiries off to ASUS.


Weeks later
I did get digital sound up finally quite well.  I installed pulse audio I went at alsa every which way to no avail.  NOTE:  not on ubuntu, on crunchbang Nov 2011 release.

---

### Post by erikpz on 2011-12-18
hi,
after many attempts solved the no sound problem  (analogic) on asus EB 1020 (ALC887).
on ubuntu 11.04 I tried to completely install pulseaudio with no changes.

then i tried many changes in 

/etc/modprobe.d/alsa-base.conf

as recommended in [http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)

adding:

options snd-hda-intel model=auto index=1

has worked well for me. now i have analogic sound.

---

### Post by nikkkko on 2012-04-16
Hi,

I just thought I'd add that I bought an eeebox EB1020 not so long ago and had the sound problem, like everyone else.  Last week I did a clean install of 12.04 and everything just works.  Everything - no sound problems at all.

Nick

---

### Post by livecd1965 on 2012-04-16
I had a sound issue and had to go Win7-64.
Other than that it worked
[http://ubuntuforums.org/showthread.php?p=11848414](http://ubuntuforums.org/showthread.php?p=11848414)

---

