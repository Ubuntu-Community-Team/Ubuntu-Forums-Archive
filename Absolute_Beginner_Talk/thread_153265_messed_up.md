---
title: "messed up"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-03-31
OK! after a few posts trying to get 2nd HDD (with Mepis ) to be shown on the boot menu of master drive, I have messed up pretty badly. I am now in the position of not having the choice of booting into Ubuntu or XP. I can only boot into  XP. I think it may be I have to re install grub boot menu. How  do I do this?
Thanks

---

### Post by krusbjorn on 2006-03-31
Is there no entry for Ubuntu in the menu at all? If there is, what is the error message you get when selecting it? Give us details :)

---

### Post by Sbarton on 2006-03-31
[QUOTE=krusbjorn]Is there no entry for Ubuntu in the menu at all? If there is, what is the error message you get when selecting it? Give us details :)[/QUOTE]
None!

---

### Post by ferebee on 2006-03-31
[QUOTE=Sbarton]OK! after a few posts trying to get 2nd HDD (with Mepis ) to be shown on the boot menu of master drive, I have messed up pretty badly. I am now in the position of not having the choice of booting into Ubuntu or XP. I can only boot into  XP. I think it may be I have to re install grub boot menu. How  do I do this?
Thanks[/QUOTE]

If you can't get back into Ubuntu or Mepis on hdd you can use your
Mepis Live Cd to fix Grub.

Boot back into the Mepis LiveCd and log in as root, then click on 
Install Me. 
Go to the *Repair Installation* section in the menu in the sidebar
Under that there is the option * reinstall Grub bootloader*.
 
You'll need to reinstall it wherever you had put it when you installed Mepis, presumably in the MBR.

Were you using Grub from Ubuntu or Mepis?

---

