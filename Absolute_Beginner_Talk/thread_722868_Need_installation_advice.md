---
title: "Need installation advice"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-12
I'm dual booting with feisty on three seperate computers fine.
My fourth computer is solely XP because I use it as a DAW & have always been cautious about doing anything with it other than music. I finally decided to install feisty & then upgrade the repos for Ubuntu studio. I have a 120 gig IDE & 250 gig SATA running XP so far.
I just installed another  160 gig IDE slave & planned to use the whole drive for Ubuntu.
It has not been formatted yet. I put in the live CD (feisty) & get an error when I get to the partition stage of the installation & I can't go any further. I assumed the installation would give me an option to format after the drive was partitioned . Am I wrong or could it be the SATA thats causing the problem? 
Can someone tell me what I'm missing?
Also iif I go into /dev directory booting from the live CD it shows all 3 drives but with little x's around the icons.  1- Seagate IDE          1- Western Dig  IDE         1- Seagate SATA

*** Since Gparted doesn't  work I wonder if I could use fdisk to partition the whole new drive since  " fdisk -l"  sees it  & says its not partioned. I would need step by step instructions before I would attempt so I wouldn't touch any of my other two XP drives. Especially now that I found I was mistaken about my 1st IDE drive. Its also 160 gig like the new one I installed & has the exact same stats in fdisk except not being partitioned & formatted.

---

### Post by Forrest Gumpp on 2008-03-12
I think I have read somewhere on this Forum within recent days that the (Desktop) Live CD is not capable of installing upon an unformatted drive.  Its either that, or that it cannot install well to partitions that have already been created for a Linux installation before the Desktop Live CD is attempted to be used.

I shall look for this reference, but in the meantime aysiu's Ubuntu Linux Resources Site,  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
or Herman's Illustrated Dual Boot Site,  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  may have something on it.

I understand that the Alternate CD can install to an unformatted or pre-partitioned drive.  You can download the Alternate CD from a link provided on Herman's site.

---

### Post by garyed on 2008-03-13
I haven't found out anything yet but I believe you're right.
fdisk recognizes all 3 drives in terminal so I think it just can't partition the unformatted drive.
I was thinking of trying Gparted to see if that would work but I'm afraid of messing anything up
on my other drives,  not knowing what I'm doing for sure.

---

### Post by sandysandy on 2008-03-13
> **garyed said:**
> I haven't found out anything yet but I believe you're right.
fdisk recognizes all 3 drives in terminal so I think it just can't partition the unformatted drive.
I was thinking of trying Gparted to see if that would work but I'm afraid of messing anything up
on my other drives,  not knowing what I'm doing for sure.

u can disconnect the other drives and then give gparted a try.

i am surprised that ubuntu live CD cannot partition unformatted drive. all the unformatted space will be shown as free space.

regards

---

### Post by garyed on 2008-03-13
Sorry for the double post but I wanted to make sure the update worked.

*** Since Gparted doesn't work I wonder if I could use fdisk to partition the whole new drive since " fdisk -l" sees it & says its not partioned. I would need step by step instructions before I would attempt so I wouldn't touch any of my other two XP drives. Especially now that I found I was mistaken about my 1st IDE drive. Its also 160 gig like the new one I installed & has the exact same stats in fdisk except not being partitioned & formatted.
__________________

---

