---
title: "Grub Trouble"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by sosamv on 2006-10-06
Hi! im having a hard time installing grub on my 2nd HD MBR, cuz the actual ubuntu installation (wich is on my 2nd HD) installed grub on my 1st disk MBR and i dont like that cuz windows its not showing under de grub menu, so i decided to restore my MBR...

is there a way to easily install grub into the 2nd HD MBR??

Thanx in advance =)

---

### Post by Herman on 2006-10-08
Hello sosamv,
You can do that, just open a terminal and type 'sudo grub', to change it to a grub shell.
Then type 'find /boot/grub/stage1', and it should tell you '(hd1,0)', probably, by what you said in your post.
Whatever it says, that's the information you canuse for the next command, which is 'root (hd1,0)', (or whatever the first answer was).
To install Grub to your second disk's MBR, you type this, 'setup (hd1)', and Grub will install it's IPL in the first sector of your second hard disk (MBR), plus stage1_5 in the next 15 sectors.
When done, type 'quit', then 'exit'.
To see pictures of the whole process, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

You will need some kind of a special BIOS setting or a special boot manager to make the BIOS look at your MBR on your second hard disk though.

Regards, Herman :D

---

