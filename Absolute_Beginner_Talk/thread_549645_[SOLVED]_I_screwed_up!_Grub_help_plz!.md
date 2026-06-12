---
title: "[SOLVED] I screwed up! Grub help plz!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by rugbydazzla4 on 2007-09-12
OK.  I got new shiny vista laptop, and wanted to linux it up and did so, dual bootign with grub, forwhatever reason i decided to get rid of linux. so i just when to the hard drive manager in vista nad deleted the linux partitions and gave all the free space back to my windows vista C drive

now however, whenever i restart the computer, grub still loads and givs me "Grub error 22"

HELP PLEASE!

---

### Post by wjp.reg on 2007-09-12
You need to fix the MBR..

[How to fix the MBR]("http://support.microsoft.com/kb/927392")

Don't worry, be happy!!  :-)

---

### Post by rugbydazzla4 on 2007-09-12
I dont have a windows installation disk, it just came preinstalled :S

---

### Post by wjp.reg on 2007-09-12
Cool..

How about an XP CD??

If you have another computer check out and download [Super Grub Disk]("http://supergrub.forjamari.linex.org/")

cheers!!

---

### Post by raja on 2007-09-12
Of course your MBR is overwritten and you have to repair it. If you had it backed up, you can restore it. If not you need to repair it with the Vista cd - see [this]("http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html") for an example. 
If you dont have an install cd, another option is to try something like Supergrub that can boot various os' - dont know if it works with vista. 
As a temporary measure another thing that may work is to use the Ubuntu live cd and choose 'Boot from first hard drive' in the initial options to boot into Vista.

---

### Post by rugbydazzla4 on 2007-09-12
Thank you v much for your help

Downloaded and burn the super grub disk

i will give it try shortly

could another option be two reinstall linux using the live cd?

---

### Post by wjp.reg on 2007-09-12
sure.

---

### Post by rugbydazzla4 on 2007-09-12
ok, ive booted up using super grub cd, but beign an absolute beginner i dont have a clue what to do. can any one advise me please?

---

### Post by rugbydazzla4 on 2007-09-12
hey guys! thanks for all your help, i was in an absolute panic, used the grub ccd and some quick learning / gues work and got it all hunky dory again.

Thank you very much

---

### Post by Paul133 on 2007-09-12
Please mark the thread as solved. Go to thread tools -> Mark thread as solved. Thanks.

---

