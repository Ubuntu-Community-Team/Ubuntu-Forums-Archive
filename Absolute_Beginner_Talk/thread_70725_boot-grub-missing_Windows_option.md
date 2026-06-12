---
title: "boot-grub-missing Windows option"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by canuck45 on 2005-10-01
Ok some background.
Installed breezy and no problems, had dual booting.
Allowed ubuntu to do updates and my windows options disappeared.  Logged into linux and under system was a program titled 'boot'.  It allowed me to add or delete options through a graphic interface.  I added windows/hda1 and then rebooted and had windows back. 


Today I updated again and once more windows option disappeared. Full of confidence I went to system and this time however there was no 'boot' program to allow me to add other OS's to the boot menu.:confused: 


While panicking, I searched these forums and found 'grub' and info on it.  
Finally located it on my computer and was a little overwhelmed by its contents.  In the end I copied the example they gave (commented out) cut and pasted it in the 'real' info section of grub, removed the comment indicators (#) and it worked.  whew


Trial by Fire is a great way to learn but only if you have a strong heart...


So I am happy I figured it out BUT it scared the bejeezes out of me.  I am not that comfortable in linux yet.  I was ready to wipe the MBR and go back to windows only.  WHY Do they do this to us newbies?...is it a test?   ...or did I do something wrong.:confused:

---

### Post by rippon on 2005-10-01
I have a similar situation. I was messing around with the partitions when installing breezy, (then found out it was too unstable and went back to hoary) and I think I messed it up becuase right after that it wouldnt let me boot into my Windows XP partition, I broke grub. I figured if I installed hoary it would write over the old grub from FC4 and fix it. Well it boots Hoary from the grub boot list but when I try to boot Windows XP it doesnt work.

Anyway, If anyone could help me, my thread is here:
[http://ubuntuforums.org/showthread.php?p=380504#post380504](http://ubuntuforums.org/showthread.php?p=380504#post380504)

---

### Post by aysiu on 2005-10-01
I think you handled yourself pretty well. I've done a lot worse to my system. My approach is basically: as long as I have time to fix things and I back up all my files, who cares what goes wrong?

Also, consider the high standard you're setting for Linux--how easy does Windows make it to set up a dual-boot with Linux? When you think about it that way, it's amazing how easy it was for you to solve the problem, isn't it?

---

### Post by canuck45 on 2005-10-01
Good point, windows bootloader for other OS's  hahahahahah.

Actually compared to the time I have spent fixing windows problems, it was relatively easy to get windows as an option in grub.  Its just that I had gotten used to the 'boot' program and suddenly I had to do it manually.  It actually required thinking instead of point and click.

I put the window option first above the ubuntu listings so it would be the default boot selection as default is set to 0

All I used in the menu.lst is

title   Windows XP
root  (hd0,0)


and it worked...what could be simpler...right!

---

