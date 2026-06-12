---
title: "booting problem"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by striker4678 on 2007-06-19
Ok so I just installed ubuntu feisty on my laptop.  I had xp running when I installed ubuntu and I want to be able to choose which one to boot from, xp or ubuntu.  I thought the GRUB thing would let me choose which one, but whenever the grub menu comes up it only has 3 things, all 3 of which are ubuntu, normal, safe mode, and recovery I think, but there isn't any windows.  I might have set up the partition wrong, I just used the default selection when the partition menu thing came up when I was installing, I don't really know, I'm not the best with computers, if you could give me some advice that'd be great.
you may need to baby feed me the help =p
thanks!

---

### Post by dje on 2007-06-19
When you installed ubuntu which partition option did you chose? You may have deleted windows off your hd.

---

### Post by dje on 2007-06-19
If you selected 'guided' it will have deleted windows off your hard drive, formatted and installed ubuntu onto it as the only operating system!

---

### Post by sailor2001 on 2007-06-19
when setting up, it asks if you want to install on the whole disk or partition the free space.... you clicked the wrong thing... reinstall windows and the start again with the ubuntu install

---

### Post by jrev on 2007-06-19
Before installing windows again prepare your partitionning with the Gparted live CD where you can partition your hard drive without making any such mistakes and then reinstall windows on the first primary partition

---

### Post by striker4678 on 2007-06-19
did i really uninstall windows?
so all the stuff I had on windows is gone?

for windows reinstallation i don't think I have my disk, but can i use a different one if it's still an xp disk, like if i have a compaq and it came with a dell?

---

### Post by Yes on 2007-06-19
Yeah, thats fine.

---

### Post by striker4678 on 2007-06-19
but all my music and everything? it's gone?

---

### Post by LaRoza on 2007-06-19
First make sure you really did delete it all, use a live cd to find out. If you did delete everything, yes, it is gone.

I recommend in the future you save such things on a partition or drive dedicated to storing music and such.

---

### Post by striker4678 on 2007-06-19
how would i find out using a live cd?

---

### Post by Yes on 2007-06-19
Whenever you're doing anything that major to a hard drive, always make sure you have backups of everything you don't want to lose, incase something goes wrong.

---

### Post by LaRoza on 2007-06-19
When you boot from a live cd, you can see all the storage devices and their contents easily. If you see on big partition and one little one, Windows is gone, if you see an NTFS partition, that is probably Windows.

---

### Post by striker4678 on 2007-06-19
ok thanks...
the live cd, just the cd i burned ubuntu on?

wow i was stupid =\

---

### Post by LaRoza on 2007-06-19
Loosing data by accident is frusterating, not stupid.

---

### Post by striker4678 on 2007-06-19
eh...well when i re-install windows using the disk that came with the dell instead of the laptop, will it still install all the same things?

and there were things like ATI control panel and graphics and stuff that i remember seeing in my program list on the laptop...how can i get those back?

and will everything else work ok?

---

### Post by LaRoza on 2007-06-19
Using the restore disks bring the computer back to the state is was in when you bought it. Have you a compelling reason to use Windows?

If not, you could just use Ubuntu.

---

### Post by striker4678 on 2007-06-19
I very well could..there's no reason really...and could i install windows after ubuntu?  instead of uninstalling ubuntu and then installing windows and then installing ubuntu again...

but there are a few reasons unless you can help me find a different way

one that strikes me is my zune and zune player, i dunno if  that will work for ubuntu?

---

### Post by BHelts on 2007-06-19
if you really did delete your windows partition, and you did it recently, it's quite possible that most if not all of your music is recoverable.  There is going to be no way to get around reinstalling windows and your apps and drivers and such.  But DATA could very well be recoverable.  If you want to try to recover the data, you will not want to use the hard drive often, the more writes the hard drive makes, the more data will potentially be lost.

---

### Post by striker4678 on 2007-06-19
how can it be recovered?

---

### Post by BHelts on 2007-06-19
ok, here's the deal.  when you wipe a partition, it doesn't actually wipe the data on that partition.  it just wipes the master file tables, which are the pointers to the files.  but the more you write to the drive, the more data you lose because writing data overwrites the previous data.  Anyway, you can use this [tool]("http://www.datarecoverylinux.com/") or search for an open source/free data recovery tool.  The only hitch in the giddyup here is that since windows is on there now, these tools may not see the NTFS partition.  Likewise, a windows repair tool may see the NFTS partition but probably wouldn't be able to figure the file tree.  So, i'd try a linux version first on your drive and if it doesn't recognize your NTFS partition, i'd use the GParted LiveCD and wipe the NTFS partition and make it ext2 or reiser or whatever you used for ubuntu, and try with that partition, without installing ubuntu on it.

---

