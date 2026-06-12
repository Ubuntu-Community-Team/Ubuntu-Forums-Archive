---
title: "Trouble saving modified menu.lst"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by KGH on 2006-12-15
I enter sudo gedit \boot\grub\menu.lst, enter my password, make the necessary changes click on save and reboot. On reboot I get the save boot file I attempted to change. I have saved the menu file closed the editor and terminal, reopen the file and the saved changes are there. Again on rebooting I get the old menu. Any suggestions?

---

### Post by aysiu on 2006-12-15
You've got your slashes facing the wrong way. Try this instead: ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by lingnoi on 2006-12-15
I think it should be

```
sudo gedit /boot/grub/menu.lst
```

In your post you said you tried "sudo gedit \boot\grub\menu.lst". 

Unless thats a typo?

---

### Post by KGH on 2006-12-15
That did the trick. I am a little surprise that I was able to use the backslash and open the file. 

Thank you very much

KGH

---

