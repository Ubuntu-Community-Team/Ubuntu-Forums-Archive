---
title: "Beginner: My: How to install Ubuntu on a partition -question"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Kevf on 2007-01-01
A few days a go, I've reinstalled xp and was planning to give 6.06 another try. This time using a dual boot. 

I have a 250 gig hard drive and divided it into 3 sections. 

C: 20 gig (windows xp: NTFS)
D: 20 gig (for ubuntu. 20 gig is rather big I know, but I like to have some extra space to mess around in: FAT 32)
E: 220 gig (data: NTFS)

During the installationprocess I've came across the manual change partition table (or something like that), and didn't understand it. Apparently (from what I've read), Ubuntu needs a few partitions of its own in that partition. 

My questions to you: 
What is the most common or easiest partition setup, regarding my wishes (info I've gathered so far; 3 partitions, with the one for the data formatted as FAT32)

Can I change the E: drive to FAT32 with partition magic or another program?

Is there somewhere on the web and tutorial for how to use the partition table? I didn't recognize the names ubuntu mentioned? And just didn't know what to do ](*,) 

Hope you guys can help me. 

Kevin 
The Netherlands (as an apology for misspelling ;) )

---

### Post by squeedps on 2007-01-01
I used Partition Magic 8 to create my partitions for Ubuntu.  there is a Wizard item that is called Install New Operating System.  it will walk you through setting up a partition for Linux and also make a swap partition.  one suggestion that i can give you though.  Don't click the button at the end of the wizard that says "Install new OS now".  Use the other option, "Install new OS later"  What happens is, Partition Magic sets your XP partition to hidden and if you don't know how to set it back to active, you won't be able to boot into it through GRUB.  After you restart your system and the "DOS" version of Partition Magic creates the new partitions, you'll be able to restart your system, insert your live cd and install Ubuntu.  I re-formatted the Linux partition during the install to be sure it was set specifically for Ubuntu.

hope this helps.


Shaun (squee)

---

### Post by garwaymatt on 2007-01-01
Some quck ideas. Ubuntu needs two partitions, the actual partition where ubuntu is installed, and a swap partition, which I belive to be the same as the pagin file in windows. The actual partition that ubuntu is installed on cannot be a fat42 partition, linux typically usually uses ext3. This is set up during the install process. I have the same system set up on my machine(except ive got a teeny 60 gig hard drive.) The partition you have decided to use for ubuntu should be identifieable by the size, and I think it shows up the format type as well. 

1. Select the partition which you have selected to install ubuntu on, the 20 gig fat32.
2. select the delete option, so you end up with 20 gig of free space.
3. at the begining of this create a partition 'swap', formatted with linux swap( this only needs to be small, i think there are guidelines on the install page, but mine is 1gig
4. create a partition for ubuntu in the rest of the free space, formatted using ext3

Next window

You need to assign a root partition( That ubuntu is installed on) The mount point for this would be /  and this needs be assigned to the ext3 partition you just created.
this needs to have a tick in the 'reformat' box.

Do the same for the swap partition, this also should be formatted.
[COLOR="Red"]Make sure that the partitions containing windows and data are NOT selected in the reformat box, Otherwise byebye data. Make backups before you start, as all this has come from my memory of installing it[/COLOR]

---

### Post by Kevf on 2007-01-01
Thanks for the quick response! The partition magic did the trick. I now have a partition ext3 15 gig and a swap 500 mb.

The box dialogue is planned for tomorrow. Enough ubuntu and google for one day ;) 

I'll keep you informed.

---

