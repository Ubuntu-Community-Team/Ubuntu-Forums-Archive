---
title: "G3 Pismo Ubuntu Install"
date: 2006-08-14
forum: Apple PPC Users
---

### Post by mauijunk on 2006-08-14
Aloha all!

  First, forgive the length of this post. I'm new to forums in general and I've got a lot to say.
  Secondly, thanks to all for the help! I couldn't have done this without the great support I found on this site. 
  And thrice, for anyone looking to go Ubuntu 6.06 on a G3 Pismo, I hope you never have to go through what I went through.
  Having said this, if your first attempt to install Ubuntu Dapper Drake doesn't go so hot, you're not alone! Here's a short-ish rundown of my experience and my advice. 

  I first downloaded the ppc version of Ubuntu 6.06, burned it to a DVD and tried to load that. Wouldn't work. Nautilus kept crashing. 
  Thought the "lighter" Xfce desktop of Xubuntu would be better on an older machine, but, that kept giving me errors about not finding a buffer for my video card.
  2 days and several reboots, re-partionings, and lots of Monster energy drinks (plus a Guinness), I thought about trying the "Alternate" powerpc .iso image.
  That worked. Like a charm. Since I was starting fresh (ie no dual boot) I had the installer just erase the whole damn disk and repartition and reformat. I had previously attempted unsuccessfully to partition my disks prior to installation, but, the installer went into error, made some comments about bootstraps and HFS. (I don't even wear boots, I wear sneakers... (Yea, that was a joke.)) So, I decided to erase and install clean. Anyway, now I've got a Ubuntu Pismo powerbook, with working sound and airport.
  
  
Some advice
    1) When downloading and burning the .iso image, burn to a -R and not a -RW.
    2) Download the "Alternate" CD/DVD if the regular version doesn't seem to work and try that. It worked for me.

    I'd have more advice, but, as this is my first linux distro, and my first successful install, I can't say much...

  Thanks again
a hui hou

mauijunk

    I

---

### Post by Jim Baker on 2006-09-24
I can relate to difficulty installing, but solved it with the regular shippit CD. The problem? I was trying to manually install in partitions set up by OS X installer. It SHOULD have worked, given a main partition for the distro and a swap setup just like the instructions said. But it wouldn't. I had 3 partitions on a fresh Seagate 40 gb hd, one with OS X already installed, one with OS 9 already installed, the 3rd open. Finally, I removed OS 9 (actually meant to remove OS X but couldn't tell which partition it was in so goofed on that). Then with no critical files other than OS X install on the drive, I chose the auto install option in Dapper. It opts to install in the "Largest continuous space" on the hd. With fingers crossed, the install went without a hitch.
Now I can't figure out how to get Dapper configured to Airport--help appreciated.
Jim

---

