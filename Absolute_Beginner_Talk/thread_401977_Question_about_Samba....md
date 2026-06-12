---
title: "Question about Samba..."
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-04-05
Hi again, I set up Samba a while ago and it was real easy. I made my computer part of the same work group as my other two windows computers and I can see both of them, I can also share directly to them by of course dropping whatever file I want to share into their shared folder areas on my Ubuntu computer. My only problem seems to be when I try the other way around. While I can log into the windows computers and see the files I transfered from Ubuntu to it in the shared docs area, I can't actually see ubuntu in the network only the other windows computer. Do I need to download something special on my windows PCs, is there an option on Ubuntu I need to check?

Just to point out, I did set up a public folder on my desktop to share with my windows network. And I do have firewalls on both my PCs but I have permitted unrestricted network access to them.

On a side note, I also tried to share my storage drive (A FAT32 partitioned drive, swap area between windows and my ubuntu install) and it appears empty when I browse to it from the shared folders menu... There a reason for that?

Hope someone can help, thanks. I shall check back later.

---

### Post by Kaput1982 on 2007-04-05
Did you give your server a name in the smb.conf file?

---

### Post by SniperSlap on 2007-04-05
I'm not entirely certain the smbd/nmbd (together referred to as "Samba") services are installed and started by default.
Bear in mind that there are various security concerns with Samba, and so this is why they don't just plonk it down in front of you.  That being said, I truly believe that Samba is only prohibitively risky on Windows computers.

I'm not at my Ubuntu computers at the moment, so I can't check this out in detail for you.

Check in synaptic and make sure "samba" is installed.  By default all Ubuntu computers will install with the needed software to view Samba shares on a network, so make sure it isn't that you are seeing.

Sharing data out, you will have to do a bit of setting up.

Also worth looking at is SWAT which gives a great birds eye view of the Samba situation.

---

