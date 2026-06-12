---
title: "New Hard Drive"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by manifresh006 on 2007-08-22
I installed a clean hard drive,BUT I can save anything on it 
Shows up in System>Administration>Disks

Can't partition it or use it 
Any help?????:confused:

---

### Post by manifresh006 on 2007-08-22
Cleaned it with DBAN:)

How can I use it:confused:

---

### Post by manifresh006 on 2007-08-22
Anyone please!!!!:confused:

---

### Post by Aishiko on 2007-08-22
have you mounted the drive yet?  that could be the issue.

---

### Post by splintercellguy on 2007-08-22
Has it even been formatted with any file system?

---

### Post by palintheus on 2007-08-22
You have to make sure it is not mounted and use a partition manager to partition and format it prior to use if you used Dban on it.

---

### Post by manifresh006 on 2007-08-22
Well I have the os in a 40g hard drive this would be for extra space...
How would I mount it or should I not mount it I'm :confused::confused:

Had xp on it but was cleaned.:)

---

### Post by Aishiko on 2007-08-23
ou have to partitation and format it before you mount it, I'm not at my Linux computer so I can't emember how to do that.

---

### Post by manifresh006 on 2007-08-23
Ok

Is there someone that knows how to foramat the drive and partition it too.

---

### Post by splintercellguy on 2007-08-23
GPartEd?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
hello 
do you know how to use the turminal

---

### Post by splintercellguy on 2007-08-23
Don't really need the terminal, GUI partitioners can do the trick.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
type 
[PHP]sudo gparted[/PHP]

it may not be installed not a big deal 

[PHP]sudo apt-get install gparted[/PHP]

any way run gparted tell us what shows up

---

### Post by splintercellguy on 2007-08-23
NEVER use sudo with GUI apps. gksudo is what you do:

gksudo gparted

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
the qustion about the terminal was thats how i get to gparted then some mounting stuff just easyer in turminal
lol i wish i could spell

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
why

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
i mean it works right is there anything bad about useing sudo in sted of gksudo
i just dont see the advantage can you give me a link to read more on it

---

### Post by manifresh006 on 2007-08-23
Sorry but don't know what that means.:lolflag::lolflag:

---

### Post by manifresh006 on 2007-08-23
Well the drive shows up as unallocated:confused:

---

### Post by manifresh006 on 2007-08-23
What do I do now?:confused:

---

### Post by Aishiko on 2007-08-23
partitaion it so you an format it.

---

### Post by manifresh006 on 2007-08-23
Well this is what I see

[ATTACH]41429[/ATTACH]

[ATTACH]41430[/ATTACH]

Then I press ADD+   and   APPLY

[ATTACH]41431[/ATTACH]

This is what came out, how do I know is working

[ATTACH]41432[/ATTACH]

Also add an other 

SIDECANDY MOUNT
(To tell me how much space I have left)

---

### Post by manifresh006 on 2007-08-23
So is it working?Or what do I have to do?:confused::confused:

---

### Post by manifresh006 on 2007-08-23
Does anyone know what to do now?

To find out if it's working and making it show up on SIDECANDY:confused::confused:

---

### Post by manifresh006 on 2007-08-23
Well how about the gDesklets?

Sorry to keep posting but if I don't I will just get left behind:lolflag:

---

### Post by palintheus on 2007-08-23
looks like its formatted and should auto mount when you plug it in.

---

### Post by manifresh006 on 2007-08-23
But it's pluged in via IDE inside the computer:confused:

When I try to mount it it tells me

-----------------------------------------------------------------------------
UNABLE TO MOUNT THE SELECTED VOLUME               

DETAILS>
              error: device /dev/hdd1 is not removable

              error: could not execute pmount

---

### Post by philinux on 2007-08-23
If this is a second hard drive go in the bios and set it to be removable. Make sure you dont set your original HD though

---

### Post by manifresh006 on 2007-08-23
Were is the BIOS in here??:lolflag:

---

### Post by Aishiko on 2007-08-23
The Bios can only be accessed and modifid before OS startup generally it is  "esc" or F2 during boot up (at least ont eh machines I've used) and from there you can change the settings.

---

### Post by manifresh006 on 2007-08-23
Okay let me see what I can do?

---

### Post by zeehat on 2007-08-23
If it is an NTFS/ S-ATA drive you may need to run ntfs-3g.  I did, and now I can read and write off of my NTFS/S-ATA drive.

---

### Post by manifresh006 on 2007-08-23
I'm at the BIOS right now but where do I go to set it up as a removable HD?:confused:

---

### Post by manifresh006 on 2007-08-23
Ha come on:) are yall going to leave me stuck here:):lolflag:

---

### Post by palintheus on 2007-08-23
depends on the BIOS manufacturer, google the manufacturer. It will be at the top or bottom of the of the screen(usually).

Also, there are people that a)never get any replies, or b) have to wait days. Be appreciative and don't bump every few hours

---

### Post by manifresh006 on 2007-08-23
Thanx 

Sorry about the bumps but I have a small laptop turned on which takes about 5min to load a page w/ cable internet and about another 5min to post:lolflag:

---

