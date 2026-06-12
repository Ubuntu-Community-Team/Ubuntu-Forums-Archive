---
title: "PPC &amp; big hard drives"
date: 2006-11-13
forum: Apple PPC Users
---

### Post by sleestak on 2006-11-13
I am currently setting up a G3 B&W to be a music server/web test server at my house.  So far I have a LAMP install done, desktop added and webmin installed. So far so good....

I pulled the HD from our old fedora box and plugged it in...no dice. Booted into OSX and still no dice...the drive isnt readable for some reason. Figured maybe I needed to back up data and either reformat the HD or find another solution.

I was reading that the older PPC's have issues with drives over 128GB and I would like to stuff a 250GB in there to store music. So my questions to you are:

Should I consider using an external Firewire drive instead of internal? Will it fix my issue with the large drive? I have read that this will work in OSX, just wondering if that ol' firewire port will cut it with newer external hd cases and work in Ubuntu :-k

Also, what format is BEST for the hard drive in this application?


Thanks Much

---

### Post by sleestak on 2006-11-14
end solution:  os x

serving web pages just fine for test enviro, shares external HD in FAT32 format to all machines in house and is in the process of getting iceCast installed. All done in less than a fraction of the time as it would have taken in ubuntu...way less hassle.

---

### Post by stmiller on 2006-11-15
> **sleestak said:**
> end solution:  os x

serving web pages just fine for test enviro, shares external HD in FAT32 format to all machines in house and is in the process of getting iceCast installed. All done in less than a fraction of the time as it would have taken in ubuntu...way less hassle.

Doesn't FAT32 have a limitation of 30GB partition size max? Go with HFS+ if it's not too late.

---

### Post by Decade on 2006-11-15
Wow, you gave up on Ubuntu quickly.

FAT32 has the 32GB limit only with Windows 98 and the Windows XP formatter. However, you don't need FAT32 if you're serving files; the network file protocols are completely independent of the disk format. The format you use simply should be what works best with the OS. Choose something with journalling.

The 128GB limit is tricky. All G3 and most G4 Power Macs suffer from it. If you don't boot from the drive, Linux could use the entire drive easily, but MacOS X won't unless you pay for a third-party extension. If you boot from the drive, it takes some more trickery to get Linux working on it reliably. It's a software limit, but some of the boot software is burned into the Mac's ROM.

External USB and Firewire enclosures get around that problem, as long as the enclosure's firmware includes LBA48 support. However, you probably won't get SMART warning messages. I'm sure it works with Ubuntu.

---

