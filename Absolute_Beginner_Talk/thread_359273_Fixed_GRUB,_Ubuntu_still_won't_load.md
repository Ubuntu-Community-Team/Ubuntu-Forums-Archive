---
title: "Fixed GRUB, Ubuntu still won't load"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by slumcat05 on 2007-02-11
OK, I'm probably not the first noob who has messed his system up this bad, but I think i have a pretty unique situation and couldn't find any helpful info elsewhere, so I'm counting on the experts here who have always come through for me (no pressure though). I recently mounted my girlfriend's Windows HD to rescue some of here files from a ruined XP session, and somehow I think that's what started this all. Here's what's happened so far:

[INDENT]1. Somehow ended up with a Grub error 17.

2. LiveCD failed to boot (Buffer I/O error on device dm-5, more on this later)

3. Used Freespire LiveCD, installed Freespire on extra partition to try to fix problem

4. "fdisk -l" listed Ubuntu partition (hda1) as FAT16, although GParted recognized it as ext3

5. Tried repairing GRUB in Freespire, still got error 17 when booting Ubuntu

6. In Freespire, ran fsck on hda1, no errors reported

7. In Freespire ,copied all data from hda1 to an empty partition using rsync -aS

8. Using Gparted, reformatted hda1 to ext3

9. Tried Ubuntu LiveCD again, failed, but then I unplugged the Windows drive, and it worked, for whatever reason.

10. In Ubuuntu Live session, copied all data from extra partition back to hda1 using rsync -aS

11. Ran grub, [root (hd0,0), setup (hd0)]. Succesfully repaired Grub

12. Boot proceeds through Grub. Load screen (black Ubuntu screen with orange progress bar) loads, but progress bar does not move, and hard drive does not appear to be doing anything[/INDENT]

I feel like one of two things happened. First I'm worried about what happened to the permissions when I copied everything over in Freespire, although all of the root level files still appear to have root permissions. Second, the files in the bin folder look suspicious and unfamiliar to me, like maybe when Freespire mounted the Ubuntu partition it wrote its own bin's over mine?

Anyways, I would prefer to avoid a complete reinstall. I still have access to all my data because I copied it over, but the majority of what I'm trying to rescue is my installed programs and configuration and whatnot. I spent a lot of time getting it all set up (as I'm sure all of you can empathize with).

Thanks in advance for any help. The Ubuntu community rocks!

---

### Post by slumcat05 on 2007-02-11
If any mod or admin reads this, I apologize, I feel like I probably should have posted this in the General Help forums.

---

### Post by seshomaru samma on 2007-02-12
I usually use Knoppix and never used Freespire so I don't know what happened
If you want to save your settings , create a separate /home partition copy your home partition and reinstall Ubuntu keeping /home intact. The newly installed system will have all your old settings. More info about it [here ]("http://www.psychocats.net/ubuntu/separatehome"), you might need to do some adjusting due to your special setting.

---

### Post by slumcat05 on 2007-02-12
Thanks. Like I said, I still have a copy of everything that was on the partition, so when I do get Ubuntu running again, I will use that guide to help restore my home folder (which I assume is where the desktop customization settings live).

What I'm hoping is to not have to do a fresh install (thus eliminating all the programs I installed over the course of the last few months), but instead somehow repair the files that are already there to get Ubuntu running again.

Thanks for the guide though, I will definitely check it out.

---

