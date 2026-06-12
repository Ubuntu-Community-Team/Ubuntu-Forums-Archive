---
title: "Defragging other partitions..."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-12-10
I've got a 430GB NTFS partition that I was using for both my Windows and Linux to access, in anticipation that I was going to be using Windows more often that I do.  Well, I haven't really booted into Windows at all except for once to test something about my USB card reader, and plan on doing away with that partition (the Windows one, not the 430GB one) fairly soon to install another Linux distro.

Then I was thinking...  What about defragging the NTFS share?  I was just going to keep it as is (though I was also thinking about backing it up and changing it to Ext3).  Just after defragging my girlfriends (Windows) computer, though, I thought "don't I have to occasionally defrag my NTFS volume?"

Of course, I could just boot into Windows and defrag from there (at least I think I can--it's honestly been a while since I'e used Windows).  However, since I plan on getting rid of Windows, I was wondering if there was a (reliable) tool for defragging NTFS from Linux.  (I say "reliable" because I've searched for other threads on this matter and found some people saying that defragging could potentially screw things up majorly.)



While I'm on the subject, what are the pros and cons of ext3 versus ntfs?

---

### Post by LaRoza on 2007-12-10
NTFS isn't the best to use in Linux. The NTFS specs are not released, so the developers reverse engineer them, so it is open to flaws. 

If you still use Windows, use NTFS and defrag from NTFS. Once you go to Linux only, use EXT3.

---

### Post by atlfalcons866 on 2007-12-11
ext3 does have a defragger but it is not needed. Plus the defragger is not maintanted anymore and it requires you to convert ext3 back to ext2.

---

### Post by insane_alien on 2007-12-11
jdong's pyfrag tool will work its a file defragmenter and can work on any filesystem just search the forum for 'pyfrag'.

although if you use a filesystem like ext3, XFS and so on you'll quickly find that it is not needed.

actually theres a thought, XFS has a defragger, xfs_fsr iirc i haven't defragged it in months and it is at 0.1% fragmentation even with heavy use and a couple of megalithic files on it.

---

### Post by HermanAB on 2007-12-11
NTFS is very similar to the more modern Linux file systems.  It is a robust tree structure with a transaction log and therefore defragmenting it is not necessary, since it will make no perceptible difference.

Cheers,

Herman

---

### Post by atlfalcons866 on 2007-12-11
But jdongs defragger only defrags files it dosent compact them together or make free space contiguious.

Defragging is needed on JFS though.

---

### Post by insane_alien on 2007-12-11
i beg to differ herman, my mums laptop(runs XP nothing i can do abut it since it is a council laptop) is NTFS it needs defragging badly and it is only 60% full. it was incredibly slow. i had o bump in an ophcrack CD to get the password(112s from boot) to be allowed to defrag it but onceit had it was quite speedy again.

it is a myth that NTFS never needs defragged.

---

