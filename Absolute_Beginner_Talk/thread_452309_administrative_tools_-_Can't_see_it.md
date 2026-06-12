---
title: "administrative tools - Can't see it"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by BrianClinton on 2007-05-23
I can't seem to get the administrative tools menu to show up under System.  I don't know why obviously. I am using the default user account that's created when I installed UBUNTU 6.06.  I have looked through softtware manager and honestly there's so much stuff in there I am afraid to just install something that looks like it could be the one.  Why can't I see it?  Is it permissions, Installation, or simply bug?

---

### Post by aysiu on 2007-05-23
It could be a bug. I've seen one other user who was also missing certain items in the administration section of the System menu.

---

### Post by stuffedinaninbox on 2007-09-09
I am having a similar issue.... I used to be able to see the Admin. Tools menu, but when I was adjusting some things for the other menus, i did *something* and now it's gone...

I remember accidentally clicking on somehting or other, but I have a talent for doing things without knowing i did them. 


Any suggestions?? Even if someone has a list of the programs found in administrative tools i can recreate the menu. I was more wondering if there is a place where the menu is saved

---

### Post by schorsch on 2007-09-09
Are you still member of the admin group? What is the output of
```
id
```

---

### Post by stuffedinaninbox on 2007-09-09
it returns with....

> uid=1000(holotone) gid=1000(holotone) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(holotone)


---

### Post by zveroboy on 2007-09-27
I am using 7.04 distro and this worked for me:
You have probably tried this already, but just in case:
right-click on the menu panel and select 'Edit Menus', which should bring up menu editor.  Check/select all the menu items you need.  Then just press 'Close' and you are done.  You might have to restart the session for changes to take place.  (e.g. log out and log back in).

I hope this helps.:)

---

