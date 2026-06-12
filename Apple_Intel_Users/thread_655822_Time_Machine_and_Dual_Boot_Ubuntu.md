---
title: "Time Machine and Dual Boot Ubuntu"
date: 2008-01-01
forum: Apple Intel Users
---

### Post by changuito on 2008-01-01
I'm wondering if anyone might have any experience with Time Machine in Leopard on a dual boot ubuntu setup. I'm would like to use it to back up my internal drive, both mac and linux partitions, but I'm having issues. Essentially, there are directories of the linux partition that time machine just always ignores, even when i select to back up the entire partition. While time machine actually backs up most of the contents of the linux partition, the one main directory (possibly among others) which it ignores and does not back-up is /home (or in mac: /Volumes/Linux HD/home), where most of the action is. So, needless to say, it's really annoying. I've searched around but havent found anyone else with this issue. Most of the system directories are in the backup, like /bin, /etc, /usr, /var, ....  Totally annoying, right? It skips the ONE crucial directory in /. 

If you're interested in looking at this in more detail, I essentially describe my configuration in this post (but I dont think this is a FS configuration problem...)
[http://ubuntuforums.org/showthread.php?p=3795088#post3795088]("http://ubuntuforums.org/showthread.php?p=3795088#post3795088")
basically, i have neither partition journaled. i use both OSes with identical user numbers and user ids on both, so the permissions are seemingly seemless. There is the ext2fs layer in this, but that dosent seem to be the problem. I'm guessing there's some thing about time machine which is configured by default to ignore certain directories, but that seems ridiculous...  any thoughts??

i'm on a macbook pro with leopard and most things set up as per the macbook dual boot instructions.

Thanks.

---

### Post by RC Howe on 2008-01-01
You may want to check what directories Time Machine does not back up. It may be set to exclude that directory on Linux for some reason. System Preferences > Time Machine > Options.

---

### Post by changuito on 2008-01-04
Unfortunately, this is not the issue. I forgot to mention that i go and configure this the exact way i want, which shows that it will back up /Volumes/LINUX HD/home  but i does NOT do it and gives me no ouput that i'm aware of. 

 :(

---

