---
title: "Ok no one would help with the flash issue so......"
date: 2012-11-28
forum: Any Other OS
---

### Post by Gh0zt36 on 2012-11-28
I installed mint 13 on another drive VOILA flash works. Ok 

So now I want to transer all my media from ubuntu drive on external to the mint drive and I went to home folder then user folder but the user folder is empty . 

Can mint only see so far into another drive? is there an app to make my content pics , music ect discoverable ?

---

### Post by MythosLegend on 2012-11-28
Mint should be able to see it. You may have to be root in order to see the folder (maybe some chroot and stuff). If you deleted files, then photorec is the app to recover them.

---

### Post by Gh0zt36 on 2012-11-28
No they are still there . I just booted into ubuntu and everything is as was . Its just empty when I go into  /home/joe/ from mint looking into ubuntu .  You're saying I may need to be root in mint to see the files in ubuntu ?

---

### Post by Gh0zt36 on 2012-11-28
Also I encrypted my home folder when I installed mint 13  how do I set that up to be accessed from ubuntu ?

---

### Post by mastablasta on 2012-11-29
> **Gh0zt36 said:**
> No they are still there . I just booted into ubuntu and everything is as was . Its just empty when I go into /home/joe/ from mint looking into ubuntu . You're saying I may need to be root in mint to see the files in ubuntu ?
 
you could try that - use 
 
gksu nautilus 
 
in mint to get nautilus to be root and then try poking at ubuntu disk again.

---

### Post by Elfy on 2012-11-29
*Thread moved to **Other OS/Distro Talk**.*

---

