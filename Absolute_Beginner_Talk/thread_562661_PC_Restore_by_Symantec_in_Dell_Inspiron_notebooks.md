---
title: "PC Restore by Symantec in Dell Inspiron notebooks"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by teabuntu on 2007-09-29

Hello,
Not sure if this is the right forum for this question but since I'm new here, thought I'd post on this forum.  Would anyone know how to copy the PC Restore by Symantec that comes with practically all Dell computers?  I have Inspiron 640M, and from what I'm told, once I format the hard drive which came with my laptop (which is what I'm currently using), I will completely lose PC Restore.  Someone mentioned on another site that to copy this, you must use some imaging software, but not sure if this is the only option.  If so, can using the ISO Recorder work in copying PC Restore?

Thank you for your time and help on this matter,
Teabuntu

---

### Post by teabuntu on 2007-09-29
bump

---

### Post by Daveth on 2007-09-29
Hi.  Welcome to the Ubuntu Forum
Can you clarify your post a bit please? You have feisty already on the hard drive? Is this dual boot with XP etc, or a pre-loaded Dell Ubuntu pc?

[http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?journalid=4DF3D5C7F72F11DABF6307F3ED3748CF&docid=DC493DC313321A9BE030A68F27281E82](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?journalid=4DF3D5C7F72F11DABF6307F3ED3748CF&docid=DC493DC313321A9BE030A68F27281E82)

rather makes the pojnt that a full hard drive format would trash the hidden partition where the PC Restore image is saved. Do you just want to keep it safe from being over-written then?
Or what......?

---

### Post by teabuntu on 2007-09-29
Hi Daveth,
Thanks for your reply.  No, I don't have any Ubuntu on my system.  I got my CDs from Canonical recently, but they were defective so I could not even take a look at the Live CD.  I posted this problem on another thread.

Currently, I only have Windows XP Home Edition on Inspiron 640M.  I'm looking to find ways to copy the PC Restore because I know for sure that once I wipe out my current hard drive, then I would lose it forever.

---

### Post by Daveth on 2007-09-30
defective in what sense? Could you not run the live cd at all - what happened? Did you remember to alter your bios to boot from the cd drive?

Are you going to dual boot with Xp and feisty then? Might be worth reading this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I'm still not sure where the hard drive wipe comes in. Tis true that being a hidden data resource I'm not sure how one could avoid damaging PC Restore accidentally. Have you another hard drive or an external you could backup onto?

---

### Post by teabuntu on 2007-09-30
No, I'm not trying to do a dual boot, I'm not even there yet.  Finally discovered that the CDs that were sent by Shipit were defective.  

As for PC Restore, I'm trying to find out how to save it.  I know that it's in a hidden partition, and it's not as easy as simply copying it like an ordinary file, but I do not know the details of doing just that.  Someone was talking about the MBR and how that is needed? together with PC Restore ( I could be wrong about this).  I don't have the exact details of how to go about copying (if possible) the PC Restore.  In terms of how it relates to Ubuntu, well, if Windows and Ubuntu are to be installed under one hard drive, then it would mean changing the partition table, and so PC Restore would be lost forever, because I did read somewhere that once you fiddle around with the way things are set up with the hard drive that came shipped from Dell, you would lose PC Restore capability for good, and Dell does not send out copies of this feature on a CD or DVD at all.  Thanks.

---

### Post by Jose Catre-Vandis on 2007-09-30
You could use partimage to make a full backup of your XP partition (if you have the space and a separate partition to back it up to, meaning that you would not have to worry about losing the PC restore partition.

If it helps, I have a Dell Inspiron which is happily dual booting XP and Feisty. if I have to return to pure XP (its a work laptop) I know that the hidden partitions are still there after installing Feisty, and its simply a matter of repairing the mbr with tools I can find on the net.

---

### Post by kolinab on 2007-09-30
I remember briefly considering this issue before wiping XP from my Dell laptop and installing Ubuntu. What I ended up doing was formatting the whole drive . . . System Restore be damned. I did call Dell to have them send me my XP CD though since they were too cheap to send me one with my system.

BUT as for the partimage suggestion above, I don't see why you couldn't use partimage to backup the RESTORE partition (and your existing XP partition if you like). You could burn the restore partition to CD then blitz the whole drive and be XP free.

Search the forum for partimage and see a useful howto on the subject.

K

---

### Post by dhruva023 on 2007-10-01
i had the same problem,  i called dell and ask for operating system and drives cd's.  they send it to me,  i tried it in virtual machine, and then i reformated my whole hard dick and instellad ubuntu.

i suggest you to order cd's from dell.

---

### Post by teabuntu on 2007-10-03
Hello,
Thank you all for your posts.  I do have CDs from Dell which feature pretty much all of the software that came with my laptop, except for the PC Restore.  I will look for information about partimage.  But would copying PC Restore also work with the latest version of Ghost 12.0?  

As with PC Restore, I heard that you can't just copy the file, and that it's in a hidden partition.  Someone was saying something about MBR is needed and so even if you manage to copy PC Restore, it would not work.  I didn't quite understand what was being said.

Thank you.

---

### Post by Incense on 2007-10-03
If you format your entire drive AND blow out the partitions, then you will lose PC Restore. From what I can tell the only way to copy PC Restore would be to make a bit by bit copy of that partition.I would just leave it as is, though if you have a copy of the restore discs, then it shouldn't be a big deal if you lose it or not. You may want to hit up dell support for this question though.

---

### Post by teabuntu on 2007-10-03
Hi,
thanks for your post.  I've asked Dell, their reply was that they don't give out copies of PC Restore.  So once it's gone, it's gone for good, which is really inconveinient to say the least, because for customers who end up having to format the hard drive that came with their original system, there is no recourse.  I've heard that lots of people like to wipe out their hard drive when they first get their Dell system, but there are those like myself, who are placed in a situation because of things like Mediadirect not working for some reason, that they have to format and reinstall everything.  PC Restore is such a useful tool because you get the original factory condition in a matter of few minutes.  You don't have to reinstall everything.  As far as I knnow, it only restores the partition (if there is any) which has the OS on it.  Thanks.

---

### Post by daverich on 2007-10-03
> **teabuntu said:**
> Hi,
thanks for your post.  I've asked Dell, their reply was that they don't give out copies of PC Restore.  So once it's gone, it's gone for good, which is really inconveinient to say the least, because for customers who end up having to format the hard drive that came with their original system, there is no recourse.  I've heard that lots of people like to wipe out their hard drive when they first get their Dell system, but there are those like myself, who are placed in a situation because of things like Mediadirect not working for some reason, that they have to format and reinstall everything.  PC Restore is such a useful tool because you get the original factory condition in a matter of few minutes.  You don't have to reinstall everything.  As far as I knnow, it only restores the partition (if there is any) which has the OS on it.  Thanks.

Personally I wouldn't worry about it. There are ghost-like tools available for ubuntu which should work for you.

Kind regards

Dave Rich

---

### Post by P235 on 2007-12-18
PC Restore on a hidden partition on the hard drive?  Forgive me for my ignorance as I have little experience with Dell computers, but that set up seems a little foolish and anachronistic.  Say if something goes wrong with a Dell computer and the PC Restore partition is fuddled, do Dell owners receive a PC Restore CD packaged with their PC to return the PC to factory settings or are they completely stranded?

---

