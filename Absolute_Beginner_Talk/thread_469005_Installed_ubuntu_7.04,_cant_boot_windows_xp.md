---
title: "Installed ubuntu 7.04, cant boot windows xp"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Anticitizen2 on 2007-06-09
Ok, after building a new computer, I decided the time was right to start messing with a linux based operating system.  So, after I got everything working well in windows xp, I made a ubuntu 7.04 x64 install disk(liveCD version) and installed it on a partition I set aside when I installed xp.  It installed easily, and ubuntu works great so far.  However, I am unable to boot into xp.  By default, it now boots into unbuntu and when I press the escape key to bring up the GRUB, only ubuntu, the recovery ubuntu, and memtest86+ show up on the screen.  During the install process, it never says it detects a windows xp installation.  Also, I definately didnt overwrite or delete my windows partition, because it shows up on the ubuntu desktop.

Yeah, I know i should have researched it a bit more before attempting to install ubuntu, but whats done is done.  If anyone could shed some light onto this issue and help me, it would be greatly appreciated.  I'm fairly proficient with computers, but this problem has me stumped.  I have tried looking at some of the how-to guides here, but so far, I haven't found anything that addresses my issue.  Any addition info you might need will be provided, thanks in advance.

---

### Post by FDPOD on 2007-06-09
n00b to n00b ...

The releases seem to differ content wise between Ubuntu, Kubuntu, .... whatever
I was trying Kubuntu 7.04 as well as the Ubuntu 7.04 64b and it did not recognize my XP partition or data.
Only Ubuntu 7.04 32b did in the end install the bootloader + make my XP data available ....
I installed the *&%$ at least 4 times until I finally settled with Ubuntu 7.04 32b

This whole thing is not very consistent yet across the whole range IMHO

---

### Post by darkfame on 2007-06-09
Check /boot/grub/menu.lst.

Look for the following text:

title Windows XP
root (hd0,0)
makeactive
chainloader +1


If it's commented out (# in the beginning of each line). Remove all the # and save the file. You'll now be able to boot WinXP from grub.

If your NTFS partition (WinXP) is located on another partition, adjust root(hd0,0) accordingly. For example, root (hd1,2) means harddrive number two, the third partition.

---

### Post by durrell on 2007-06-09
You could try to edit your GRUB list to see if you can get it to list Windows.

```

title		 Microsoft Windows XP Home
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

As seen in this thread:
[http://ubuntuforums.org/showthread.php?t=468646&highlight=ubuntu+64+bit+windows+xp](http://ubuntuforums.org/showthread.php?t=468646&highlight=ubuntu+64+bit+windows+xp)

The boot menu list is in /boot/grub/menu.lst. You'll have to take ownership of the file before you can edit and save it. It's worth a shot.

Edit: Looks like someone beat me to it. :)

---

### Post by Anticitizen2 on 2007-06-09
Thank you all for the quick replies.  I tried what you said, but it still doesnt work.  I edited the file, and windows now shows up in the grub list, but when I try to boot it it gives an "Error 12: Invalid device requested" message.   Could someone tell me what this means?  Ubuntu reads the  windows partition as "hda6" which I am assuming means that it is partition #6 and in the partition manager during installation, it was shown as /media/hda6.  Because of this, I used the line "hd(0,5)".  After that didnt work, I tried pretty much every other number that comes before 8, which is the partition that ubuntu is on.  I got the same error every time.  Am I just not doing it right, or is this a sign of a greater issue?  Well, thanks again for the help,I hope I have given you all enough additional info to solve this problem.

---

### Post by Anticitizen2 on 2007-06-09
bumping so it doesnt get buried.  any additional help or advice would be greatly appreciated.  i have a windows disk if a reformat is the only option, but for obvious reasons i dont really want to do that.

---

### Post by Orochi on 2007-06-09
Are Ubuntu and Windows installed on the same physical drive or separate drives? What does Grub say Ubuntu is? (what drive and partition) If you load gparted and look at the drive you should just be able to count the partitions from the left to get which number Windows is on. I'm sure there's a better way to do it, but I think that should work.

---

### Post by Anticitizen2 on 2007-06-10
Thanks for the reply.  windows and ubuntu are installed on the same drive.  it says ubuntu is on hd(0,8) and in the partitioner it said it was on partition 9, so that checks out.  also, at this point, if i could just get windows back up and running i would be happy.  im not giving up on ubuntu, but at this point, i lose most of my functionality without windows.  so, if anyone  could give me fairly detailed instructions on how to just get windows booting again(without a reformat, if possible...lol), i would be grateful.

---

### Post by Orochi on 2007-06-10
Well, I'm not totally sure about this one, but if you boot off of your Windows XP cd I know there are recovery options. One of them might restore the WinXP bootloader, erasing GRUB. That way you'd at least get Windows back. I've not sure that's even an option on the XP boot cd, but you could check I suppose.  The only other idea I have is to post the contents of your grub menu.lst here so we can check it for errors/typos that might be causing the problem.

---

