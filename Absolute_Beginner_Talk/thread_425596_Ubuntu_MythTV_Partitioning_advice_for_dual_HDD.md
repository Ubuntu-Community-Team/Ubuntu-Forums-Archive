---
title: "Ubuntu MythTV Partitioning advice for dual HDD"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by DiscMan on 2007-04-27
I am wanting to convert my home PC from Windows XP to Ubuntu. I am a very experienced Windows user as I develop software for Microsoft platforms for work, but I am new to Linux. The main reason for the conversion is that I want my home PC to run as a MythTV Backend and regular desktop. I have always wanted to try Linux as well and this was a great excuse! :)

I have 2 hard drives... a 40gb IDE and a new 320gb IDE. I plan to use the 320gb mainly for storage of my recordings. This box will solely be a Ubuntu box (no WinXp) so I don't have to worry about dual booting. Two people will be using this box as regular desktop (internet, email, word processing etc).

What partitioning scheme would you recommend that I use? I was thinking of using LVM2 as I like the idea of being flexible and being able to expand any partitions if my initial sizings are out.

If LVM2 is the way to go, should I use one or two LVM2 logical groups? One could span the first hard drive (40gb) where /usr, /home, /opt, /var and /tmp could be on separate partitions and the second volume group spanning the second hard drive (320gb) for /var/video.

I don't mind getting my hands dirty; I was just looking for some pointers in the right direction.

Thanks in advance for any help. :)

Jason

---

### Post by darkdays on 2007-04-27
I'm not sure I get why you would use it? 

A standard install don't need different partitions for "/usr, /home, /opt, /var and /tmp" and I can't understand what positive things could come out of such partitioning. If I was about to set up a box for your uses, I'd settle for the standard partitions (swap & /) and use one more for /home to get a smoother ride in the event of a reinstall. All these on the 40gb drive unless it's really slow. I'd use these; 1gb swap, 10gb / and the rest as /home for documents and other stuff.

For a reference  the disk usage in the /-partition on my install at the moment is <3gb with open office, gimp, firefox, thunderbird, etc.
I use 10gb for / and I suspect it's overkill for a Ubuntu desktop.

---

### Post by DiscMan on 2007-04-27
I wanted to separate /var/video as MythTV recordings can be multi-gigabyte in size and I want to use the JFS filesystem for this partition only. I wanted to use LVM2 as I don't want to allocate the full 320gb to the partition straight off. I also thought that having this on a separate physical drive would have less impact on my desktop experience when recordings were underway at the same time.

So what if on hda I have SWAP (1gb), / (10gb) and /home (rest ~29gb) and on hdb I have /var/video?

Should I be using LVM2? Suggestions?

Thanks,
Jason

---

### Post by darkdays on 2007-04-27
I'm afraid I can't help much with the specifics of MythTV, never used it. I think the scenario where you're better off using LVM is if you want to add another disk later on. I also would guess that you could use any location for /var/video either through config or linking /var/video to whereever you want it. Doing a big 320gb JFS partition and having the MythTV storage in a folder inside it would probably work just fine, leaving the option to store other stuff on the partition and have it mounted in a, for other storage needs, more intuitive location like /media/fancyname

The point in not doing LVM is keeping it simple to setup and handle when in a still new environment, there's always the risk of losing data when doing clever things with filesystems.

You might try the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") forum, there's a better chance that some Myth-wizards see your post over there and can advise you better. I answered first thinking it was just about partitioning for normal needs and didn't realise the need for JFS, I hope I managed to help a little anyways..

---

