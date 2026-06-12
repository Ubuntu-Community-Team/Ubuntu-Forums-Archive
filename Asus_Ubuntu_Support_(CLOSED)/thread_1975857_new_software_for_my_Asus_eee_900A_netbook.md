---
title: "new software for my Asus eee 900A netbook?"
date: 2012-05-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Rrory on 2012-05-07
I love this netbook,it was my first experience in an all Ubuntu environment and it was great but I haven't upgraded the software it since I bought it over 3 years ago ; is there anything available as it has a tiny memory. But then I always store my stuff in a flashdrive so I've never had problems either.
cheers
rory

---

### Post by wandalalakers on 2012-05-08
Try Xubuntu or Lubuntu.

---

### Post by Plumtreed on 2012-05-09
I suggest you consider Slitaz and a Puppy project named Saluki. Both install very small and are complete systems.

Each will operate in RAM for exceptionally fast performance.

They both work well on my eeePC701 and should do just as well on your 900A

---

### Post by Carborundum on 2012-05-09
I'd recommend you to go for regular Ubuntu 12.04. It runs great on my 901, which has pretty much the exact same specs as your 900A.

---

### Post by Rrory on 2012-05-12
wow thanks for the great advice. Maybe I'll go for regular Ubuntu 12.04. as I'm so familiar and love it. Right now I'm trying Lubuntu but I'm having trouble getting it to boot from my USB.
Could you please tell me what the Bios function key for Asus is & then will it be easy like on a regular pc.

---

### Post by Rrory on 2012-05-17
Bother: my eee 900a has  1GB RAM
           4GB SSD

I tried and couldn't install Ubuntu 12.04 , Xubuntu or Lubuntu, said I didn't have enough space on my drive.

 So what is the best distro for my little netbook? I only need it for Libre office and to Skype.
Rory

---

### Post by Sudan on 2012-08-28
> **Rrory said:**
> Bother: my eee 900a has  1GB RAM
           4GB SSD

I tried and couldn't install Ubuntu 12.04 , Xubuntu or Lubuntu, said I didn't have enough space on my drive.

If your problem is still unresolved, this thread offers a fix.  I installed Peppermint 3 with no problems onto my 900A.  And using the info in the thread you could also install Lubuntu.

[http://peppermintos.net/viewtopic.php?f=9&t=4911](http://peppermintos.net/viewtopic.php?f=9&t=4911)

---

### Post by Rrory on 2012-08-28
Wow, I really appreciate the link as yeah I hadn't solved it at all. Off I go to install.
thanks!

---

### Post by OldAdamUser2 on 2012-09-03
Why not buy an inexpensive 8 GB SD card and boot Ubuntu from that? I run Ubuntu 11.10 on my Eee 900 in that manner and it is perfect. Here is a link to a detailed description of my installation and the various tweaks it took to get fluxbox working correctly as the gui. (Fluxbox is much lighter and faster than the standard Unity desktop.)

[http://lakenorforkadventures.blogspot.com/2012/08/installing-ubuntu-1110-on-asus-eee-900.html](http://lakenorforkadventures.blogspot.com/2012/08/installing-ubuntu-1110-on-asus-eee-900.html)

---

### Post by Rrory on 2012-09-17
Okay, I made a bootable USB with Lubuntu, plugged in another empty 8G flashdrive into the netbook.
  When I pressed F2 & edited the Bios settings I got this:

1.[removable device]
2. [ATAPI CD-ROM]
3. [HDD: SM-ASUS-Phison}

but there is this message on the right screen:
A device enlosed in parenthesis has been disabled in the corresponding type. I tried to get rid of the parenthesis but failed.

Anyway when I try to restart the computer it won't boot from my flashdrive. Either with choice 1# or 2# I get the old software. I don't know what I'm doing wrong. 
thanks
Rory

---

### Post by snowpine on 2012-09-17
Press the Esc key at the BIOS screen to get a list of boot options. You should be able to choose your USB from this list. (Removable devices do not appear in the F2 BIOS menu.)

---

### Post by Rrory on 2012-09-18
> **snowpine said:**
> Press the Esc key at the BIOS screen to get a list of boot options. You should be able to choose your USB from this list. (Removable devices do not appear in the F2 BIOS menu.)

That did the trick snowpine. It booted Lubuntu , I clicked on 'English' and then I got this message

(initramfs) unable to find a medium containing a live file system

I got the same message with Ubuntu & no success with Peppermint 3 either; what's going on?

---

### Post by snowpine on 2012-09-18
What method did you use to create the bootable USB?

Can you test it on a different computer?

---

