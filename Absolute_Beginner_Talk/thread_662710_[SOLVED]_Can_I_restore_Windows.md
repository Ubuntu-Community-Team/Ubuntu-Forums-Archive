---
title: "[SOLVED] Can I restore Windows?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by typeadam on 2008-01-09
I'm an extreme noobie at this so please bear with me...

I installed Kubuntu 7.10 yesterday. I used GParted to manually make the partition onto which Kubuntu was to be installed on. Today I tried to load Vista and it is telling me that "winload.exe" is missing or corrupt.

I DO NOT have a Vista CD since my notebook came w/ it preinstalled and the "recovery" is on the computer.

So my question is, if I run the "system restore" from the computer's recovery program will kill my Kubuntu partition? The recovery program says that it makes everything go back to factory specs but since this is not a Windows partition, would it leave it alone?

I don't care about the data on my HDD since it is all backed up so I don't mind losing it.

I would prefer not to have to partition my drive again though b/c it takes very long but I will if I have to.

I am attaching a screenshot of GParted as it is now.

Please help.
Thanks,

---

### Post by Pevichaey5 on 2008-01-09
is it a laptop computer? such as acer or is it a dell of somekind?

on acer laptops, you can boot into the recovery partition by pressing 'Alt + F10' while the acer bios screen is up

---

### Post by LowSky on 2008-01-09
Did you resize the Vista partiion without defragmenting? Thats a big no no!!

Windows likes to just throw data any where it can and if you dont defrag the drive then when you resize the partition you can damage the data.

---

### Post by aeiah on 2008-01-09
in answer to your question, yes, it will delete kubuntu. it will reformat and repartition the whole hard drive.

im not used to vista and i dont know why the error occured, but it may have to do with vista not being on the first partition (because the restore software is on there). a dell i installed ubuntu to had this problem with xp. you should probably find a guide that mentions installing dual boot when vista and a restore partition are present in case this is the case and why it broke vista.

---

### Post by typeadam on 2008-01-09
- So should I just restore my drive and then create partitions (ext3 and swap) in Windows using Partition Magic or something?

- No I did not defragment my drive. Should I have done that in Vista before I launched the LiveCD?

- I installed Ubuntu on another computer of mine which has XP Pro and that computer is OK. However, during the partition segment of the installer I went w/ option 1 and let Ubuntu do the default.

---

### Post by Taboo Mirage on 2008-01-09
> **LowSky said:**
> Did you resize the Vista partiion without defragmenting? Thats a big no no!!

Windows likes to just throw data any where it can and if you dont defrag the drive then when you resize the partition you can damage the data.

No defragging is needed.  Read the [manual](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25).

---

### Post by typeadam on 2008-01-09
In case anyone is interested or comes across this:

I ran the system restore, which is actually accessible from GRUB or by pressing F10 before boot or other combinations for other people and it did restore the HDD to factory specs and did a clean reinstall of Vista but DID NOT touch the ext3 partition, which is exactly what I wanted to do - run a complete system recovery w/o touching my ext3 partition.

Now when I boot into my fresh/clean Vista it shows that my C drive is only 80GB instead of 120GB (the difference I allocated to Kubuntu).

Thank you for everyone's help.

---

