---
title: "[SOLVED] grub loading error"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by malty on 2007-10-21
I have winxp, then installed ubuntu fiesty, then suse10.2 to do a comparison. The boot window was susies. Did not like susie so I used acronis disc director in windows to remove the susie partition After shutdown and reboot 1 get the message "grub loading error stage 1.5 error 22". As I still have winxp intact, I know this because I can access it on my c drive via the ubuntu installation disc and I assume ubuntu is still there (now updated to gutsy) Win xp is on the original c drive, ubuntu is and susie was on another, 500g disc with 4 partitions. What to do please (can I simply reinstall ubuntu and would it find the exsisting ubuntu partition to overwrite ?)

---

### Post by mikeyphi on 2007-10-21
I think what caused the problem was that you deleted the last installed OS which is where the 'current' Grub menu was.
If you use the LiveCD you should be able to run 'update-grub'
Or you can do a further install - use manual option for partition and delete unwanted partitions before  you choose some free space for the new partitions ( / and swap). 
update-grub is part of the install process so should fix the prob!
Good luck!

---

### Post by malty on 2007-10-23
Thanks for reply, what I did....
Fixed XP mbr via install disc (Yukkkkk) how does that grinning dick get away with it ?
Downloaded & burnt 7.1 ISO
Used Acronis Discdirector to create new partition
Installed 7.1 number 2.
I am in the process of filling with goodies I will ditch 7.1 number 1 via Discdirector when ready.
My own fault, I should have delved further before I nuked Susie, delving in Linux is interesting but heavy on the Asprin ! , the reason for ditching Susie..it was turning my processor into swarf (can`t it recognise a swap file?)
As 7.1 number 2 has the boot loader can I use Discdirector to remove 7.1 Number 1 ?
More ramblings (from an old engineer who discoverer Unix in the late eighties via ProE)..The Ubuntu install is very good , except... how it names drives in its partitioning section, bears absolutely no relationship whatever to windows / Discdirector nomenclature and it should, very confusing, if you are a beginner.
Malty, older but wiser.

---

