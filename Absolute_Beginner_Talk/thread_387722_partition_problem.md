---
title: "partition problem"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-18
hey, i had xp and ubuntu but i deleted the partition drive where i had xp using gparted live cd.. but when i rebooted after the partition.. it was still there as dual boot.. what hapened.. is xp sitll in my system , if so, how do iget rid of it ?

---

### Post by HunkieChan on 2007-03-18
can anyone please help me ?

---

### Post by fuzzygenius on 2007-03-18
You still have the XP boot option in grub is all.  If you were to select that option, nothing would boot, since you have removed XP.  All there is to do now is to remove the boot entry for XP from grub's menu.  To do that, open a terminal, and put in
```
sudo gedit /boot/grub/menu.lst
```
Find the line that says ### END DEBIAN AUTOMAGIC KERNELS LIST and delete everything after that (which should be the entry for the divider between the Ubuntu boot options and XP, and the actual boot option for XP).  Then save and close.  Thats it, you're done!

---

### Post by dstew on 2007-03-18
What do you mean by "It was still there". Are you referring to the grub menu entry, to the partition, or to the Windows file system?

---

### Post by HunkieChan on 2007-03-18
> **dstew said:**
> What do you mean by "It was still there". Are you referring to the grub menu entry, to the partition, or to the Windows file system?

like there is option for me to go to ubuntu or xp, xp shouldnt be there since i deleted it.. and i wanted to make sure if it was deleted or not ..but i guess he solved it.. thanks

---

### Post by fuzzygenius on 2007-03-18
Yeah, I may have jumped to conclusions, but it sounded like you did exactly what I did earlier this week - deleted my XP partition, and then realized that grub's menu wouldn't change itself, and would have to be modified.  Glad to be helpful!

---

### Post by HunkieChan on 2007-03-18
> **fuzzygenius said:**
> Yeah, I may have jumped to conclusions, but it sounded like you did exactly what I did earlier this week - deleted my XP partition, and then realized that grub's menu wouldn't change itself, and would have to be modified.  Glad to be helpful!

so did you got rid of it ?

---

### Post by fuzzygenius on 2007-03-18
I sure did!  I left no entry for XP in the grub menu (the istructions I gave you) and I used GParted to delete the XP partition beforehand, as it appears you did already.

---

### Post by HunkieChan on 2007-03-18
> **fuzzygenius said:**
> I sure did!  I left no entry for XP in the grub menu (the istructions I gave you) and I used GParted to delete the XP partition beforehand, as it appears you did already.

oh your the one who game instruction.. so many users.. i thought your someone random in the same situation as i am, lol

---

