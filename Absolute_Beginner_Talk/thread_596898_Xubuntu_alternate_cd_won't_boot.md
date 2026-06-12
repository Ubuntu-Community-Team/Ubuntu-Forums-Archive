---
title: "Xubuntu alternate cd won't boot"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by docinsano on 2007-10-30
I'm having some problems getting the Xubuntu Gutsy alternate cd to boot on my computer. I've verified the checksums and burned the cd according to the iso burning howto. The cd rom is set to boot first in the bios settings, still it will not boot from cd. it will start up lilo but since my last install was incomplete, xubuntu does not start up. Any ideas? thanks in advance

---

### Post by Crafty Kisses on 2007-10-30
> **docinsano said:**
> I'm having some problems getting the Xubuntu Gutsy alternate cd to boot on my computer. I've verified the checksums and burned the cd according to the iso burning howto. The cd rom is set to boot first in the bios settings, still it will not boot from cd. it will start up lilo but since my last install was incomplete, xubuntu does not start up. Any ideas? thanks in advance

Did you burn the CD on a MAC?

---

### Post by docinsano on 2007-10-30
> **Codename said:**
> Did you burn the CD on a MAC?


Yes, burned on a Mac.

---

### Post by kboykowboy on 2007-10-30
I have the same problem - but i still have my 7,04 running... i burned it on a mac too... but it worked with edgy and fisty... ?! cant find a way to make the md5sum on mac - ofcourse it must be a problem with the download or burn... but is there is not really a good way of checking checksums on the mac?!

---

### Post by docinsano on 2007-10-30
> **kboykowboy said:**
> I have the same problem - but i still have my 7,04 running... i burned it on a mac too... but it worked with edgy and fisty... ?! cant find a way to make the md5sum on mac - ofcourse it must be a problem with the download or burn... but is there is not really a good way of checking checksums on the mac?!

Everything you need to know is here:  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

But, as I have said, I verified the MD5 sums and they're all fine.  I burned the cd at 4x with disk utility, but it still will not boot.
Maybe there's just something with burning the iso's on a mac?  I don't know, but I'd really like to be able to get Gutsy installed on my pc.

---

### Post by kboykowboy on 2007-10-30
ok ... to late for tonihgt to try it out... but looks good! 

i burned older distros on my mac... and that worked fine?! let you know tomorrow if i get it running!

night

---

### Post by kboykowboy on 2007-10-31
ok  - now i testet my downloads and what i've burned to cd's... the checksums are the same! soooo... i'm in the same situation as Docinsano! strange... think i'll try to burn it on my pc just in case?! but that should'nt do any difference when the checksums are the same !? right?!

now- is there not a way to install 7.10 from a remote server?!

EDIT:

ok ... i burned it on my pc... now it works!? i have NO IDEA why!? maybe there is something wrong with apples burning utility!

---

### Post by docinsano on 2007-10-31
> **kboykowboy said:**
> ok  - now i testet my downloads and what i've burned to cd's... the checksums are the same! soooo... i'm in the same situation as Docinsano! strange... think i'll try to burn it on my pc just in case?! but that should'nt do any difference when the checksums are the same !? right?!

now- is there not a way to install 7.10 from a remote server?!

EDIT:

ok ... i burned it on my pc... now it works!? i have NO IDEA why!? maybe there is something wrong with apples burning utility!

Hmmmm....Strange.  I'll have to transfer the iso to my laptop and burn it from there.  I'll update once I test out the disc.  I have no idea why burning is any different on a mac either, but apparently there is a difference.

Update: burned a cd with my laptop, unfortunately it didn't work
Another Update: burned another, no success. 
Why wont these cd's boot if they appear to be fine? is it my cdrom drive?

---

### Post by docinsano on 2007-11-05
:idea:  Wow, i think this may be a great idea.
I have an old external firewire drive that doesn't see much use anymore. I think i just may disassemble it and put it in the old HP to see if the cdrom is the culprit. Once all is said and done, i'll drop a line. Time for class... later

---

### Post by docinsano on 2007-11-06
Oh, crap.  I think my old HP has died. I pulled the cdrom and put in one of my unused cdrw drives. Plug it in, turn it on, nothing.  I figure it may be the power supply, i could get a new one but this system is old. I may just get a barebones system. Anyone know of a good one? Until them I'm stuck trying to get my ppc mac to run ubuntu. Damn you old Hewlett Packard computer, now i cant use my favorite os. Later dudes.

---

### Post by ramjet_1953 on 2007-11-06
The problem may be with Firewire interfaces.

I have a laptop with a Firewire interface and an external DVD burner that has both USB and Firewire ports.

Under Linux, the external burner works flawlessly with the USB interface, but is very flakey with the Firewire port.

I'm not sure if your Apple uses Firewire, or not, but if so, it may be worth investigating.

Regards,
Roger :cool:

---

