---
title: "[SOLVED] How to create a Trash for my second drive?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by GoCool on 2008-04-06
I have a second drive and when I delete something from it I don't find it in the trash.

I am sure there should be some way of getting it there...any help?

---

### Post by Oldsoldier2003 on 2008-04-06
> **GoCool said:**
> I have a second drive and when I delete something from it I don't find it in the trash.

I am sure there should be some way of getting it there...any help?

it doesn't show in your personal trash bin?

---

### Post by GoCool on 2008-04-06
No it doesnt. It's empty.

Actually this is the case.
1. I have a 40 gb hdd (primary) and a 200 gb hdd (secondary).

2. I had xp on it and as usual it crashed, so I tried to install ubuntu. But it failed to install in the primary for reasons best known to it so I asked it to install on the secondary.

3. Now it shows both the disks, but when ever I click on the 40 gb hdd it displays an error saying "The folder contents cannot be displayed." But the 200 gb is fine, but this is what I discovered, that when I delete anything from it, it's not shown in the trash.

I might have given lot's of irrelevent information, but I thought it's better to give a full picture so that you can help me better.

---

### Post by momist on 2008-04-06
> **GoCool said:**
> I have a second drive and when I delete something from it I don't find it in the trash.

I am sure there should be some way of getting it there...any help?

Well I'm no expert, but seeing as no-one else has chimed in except OldSoldier, maybe I can contribute.  I would get hold of a copy of System Rescue-CD (Google is your friend) and use GParted from that to examine what's wrong with the set up of your hard drives.  The CD will have all the other tools you might need, depending on what you find.

If your Windows is totally trashed and unrecoverable, I'd be tempted to swap which hard drive is master, and go from there with the 200GB as primary and the small one as secondary, perhaps for storing 'valuable' records separately from the 'working' hard drive.  Lets say, all your photographs or maybe your /home folder - whatever your priorities are.

Hope that helps!

---

### Post by Wandering on 2008-04-06
On my system, each additional drive ends up with a hidden folder in the root direcory called ".trans"  Notice:  Hidden  and the name starts with a period.  If you open that folder in Nautilus by turning on view hidden folders, you will find all the items deleted from that drive. I don't know why it is not integrated with the trash folder on my system drive, but that's how it is here

Good luck.

---

### Post by GoCool on 2008-04-06
Thank you Wandering .......it's really appreciated. Yes I could find the trash.

---

### Post by momist on 2008-04-07
> **Wandering said:**
> On my system, each additional drive ends up with a hidden folder in the root direcory called ".trans"  Notice:  Hidden  and the name starts with a period. 

Hi Wandering,
I wondered if ".trans" was a typo in your message, or what the directory is really called on your system.  Here I've found mine are called ".Trash-ian" which makes a little more sense.  I'm shown as owner, with permissions also for users.

I think these should be made visible by default, and not hidden.  And how do you empty the whole folder? I mean, what is the usual (aka correct) way, like "empty recycle bin" in Windows?  The options are to "Delete from deleted items folder" on an individual file basis, which strikes me as clumsy.  Maybe I'm being stupid here, I'll play around some more with it.

---

### Post by Wandering on 2008-04-26
Yes, .trans was a typo for .trash with nothing after.  I simply delete the whole folder. It will recreate automatically the next time you delete something on that drive. Sorry, I lost the post, and I hope this helps.

---

