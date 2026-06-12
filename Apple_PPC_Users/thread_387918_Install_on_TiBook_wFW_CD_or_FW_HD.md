---
title: "Install on TiBook w/FW CD or FW HD"
date: 2007-03-18
forum: Apple PPC Users
---

### Post by anhunt on 2007-03-18
Hey Folks,
I'm having trouble booting from an external FW CD/HD on a G4 Titanium, does anyone know if the older Open Firmware versions might prohibit that? If not, I can't figure out how to tell it to boot from either of those options.

1. I burned the .iso and can boot from it on my G5 iMac so I presume that it's a good burn...

2. The internal DVD drive on the TiBook is no good, so trying to use either an external CD or the FW HD I'd like to install it on.

3. I tried the HD boot as suggested in the [Prepairing Files for Hard Disc Booting]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html#files-newworld") Documentation to no avail.

Any suggestions?

---

### Post by ssam on 2007-03-19
does holding down alt at boot offer you booting from the fw dvd?

yellowdog used to do installing to an ipod. [http://www.linuxjournal.com/article/8903](http://www.linuxjournal.com/article/8903) so it should be possible.

---

### Post by anhunt on 2007-03-20
Hey,
Thanks for addressing my post Ssam.
I had previously tried your suggestion (It was in the Install Documentation). Holding down Option (Alt) does pull up the option screen (One image of a HD with 'X' on and another with the penguin on it). I was able to select the Linux disc image, but after clicking the Arrow, it just flashes a white screen for a second, then returns to that same option screen, with the graphics looking less polished.

I am unable to select to boot from the external CD, and the version I put on the FW HD does not even show up as a bootable option.

---

### Post by Bellefonte6718 on 2007-03-20
anhunt, it looks like we're having very similar problems... [http://ubuntuforums.org/showthread.php?t=389026](http://ubuntuforums.org/showthread.php?t=389026) :-) I should have noticed your post before I started a similar thread.

Hope you can figure it out!

---

### Post by grazie on 2007-03-21
anhunt,

It is my understanding that you need a bootstrap partition in order to hard disk boot New World Macs. The link in your option 3 doesn't actually state this (the content should be updated) and is therefore incorrect in my opinion. The link in the previous posting gives some very useful information.

---

### Post by stmiller on 2007-03-21
Yeah I have a G4 Tibook 867Mhz. It would not boot the ubuntu disc from a FW CD drive. (Though it DID boot and install OS X.4 from the FW CD drive....)

I had to get a replacement internal CD drive to install ubuntu on that machine.

---

