---
title: "[SOLVED] Printing problem with localhost"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by hps on 2008-01-21
I have installed a Samsung 2010 printer on the computer my wife uses.  However every time she go's to print she has to select the printer from a list.   When I use System/Printer to set it up as the default printer It tells me a Password is required and asks for the password for localhost.   I enter the password that she uses to log on to Ubuntu and it tells me that the password is incorrect.
Any Ideas on how to solve this problem.

I must say that installing the printer was a piece of cake as it was installed right away with no problems untill we went to set it as default, however the old printer that never worked with the system is still on the list of printers. Any ideas on how to delete the old one from the list.

Thanks for any advice

jp

---

### Post by PeterJS on 2008-01-21
Is her account in the lpadmin or admin groups?

---

### Post by hps on 2008-01-21
Sorry very new to this. I do not know which she is.  How would I find out.

---

### Post by PeterJS on 2008-01-21
To find out what groups she's in run:
```

groups *username*

```
To add a user to new groups:
```

sudo usermod -a -G *GROUP_NAME* *username*

```
The admin group grants sudo access for access to general administrative functions. lpadmin is the group for administrating local printers.

---

### Post by hps on 2008-01-21
Thanks she was not in the lpadmin group I added her to it and it worked like a charm.  Thanks for the quick help. All you guys and girls deserve a great big thank you from new users like myself for the time and effort you put into building Ubuntu and helping othres.
Thanks again, now how do I list this as solved?

---

### Post by PeterJS on 2008-01-21
Mark as solved is up in the thread tools drop down above the first post.

---

### Post by msjulie on 2008-01-24
Hello PeterJS:

Adding me and my partner into the **lpadmin** did the trick.  Now I have a default for all seven accounts that prints *gray scale* by default--save on color cartridge use!

Thank you.
Julie

---

