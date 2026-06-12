---
title: "&quot;ntldr missing&quot; replaced grub"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by threegremlins on 2007-04-06
My poor old 486 laptop I use for word processing has been acting up and finally wouldn't boot at all. It's running DOS so I went into my W2k partition and formatted some disks until I found enough to turn one into a flash in case the laptops bios had become corrupted and the rest for F-Prot in the event there was a virus lingering in the laptops innurds. The Flash helped somewhat and F-Prot happily reported no viruses.  While I was doing this just for security I ran a virus scan on the desktops W2k partition. This is when my troubles began, after rebooting all that would come up is "ntldr missing" and no matter what I tried nothing would replace this infuriating message. What had the virus scanner done?
I tried

sudo grub
root (hd0,x)
setup (hd0,x)
quit

several times
the Ubuntu installation disk would allow me to boot from the first hard drive so I tried apt-getting grub and synapting grub only to be met with "ntldr missing". I tried recover broken system on the cd and recovery on the grub menu list without any success. I didn't want to re-install the whole thing with Feisty Fawn about to come out in a couple of weeks. I had one more option available, that I knew of anyway, I could load grub onto a floppy and boot from it. When I went to find the last spare formatted disk I knew was around somewhere, well slap my damn red necked forehead silly, it was in the floppy drive. Popped it out, rebooted and viola' the grub menu appeared, there never was anything wrong. Just goes to show, ya got a problem, check the simplest things out first.
Still upset about my laptop though, it's pretty beat up after all these years, a true companion. I think it'll struggle to the very end if I ask it but I think it's earned it's place in the corner of the closet. 
Dave

---

### Post by steve.horsley on 2007-04-06
Thaks for the laugh. I can't begin to imagine how long it would have taken me to figure that one out.

---

### Post by jhenager on 2007-04-06
NTLDR missing is always a good reason to see if that little floppy eject button is sticking out a little farther than usual. :)

---

