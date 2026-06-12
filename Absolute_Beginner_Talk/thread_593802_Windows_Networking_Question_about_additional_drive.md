---
title: "Windows Networking Question about additional drives on system"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by FriscoZR on 2007-10-27
Hi All,

Through this long and drawn out learning process - I think I have most of my stuff working now.

I do have one question that remains.

When I look at my Ubuntu box over my Windows network, I still see remnants of my previous attemts - Not sure if this is a feature or something I need to clean up.

Anyway, I see the three folders that I have shared out and have the access that I want there.

The problem is I still see to icons for the drives 'disk' and 'disk-1'. This is puzzelling since I can seem to find no reference to them in the system anywhere - they are no longer showing up in the browser as before - after I manually mounted them anyway - now have that in the fstab and all seems to be right with the world.

So, how do I find and get rid of or hide these drive links from the network?

Thanks is advance for the help,
Matt

---

### Post by MaximusTG on 2007-10-27
I take it you right-clicked on the folders you wanted to share in Nautilus, and then chose samba to share them?
In that case, you should find reference to those shared folders, at the bottom of 

/etc/samba/smb.conf

---

### Post by FriscoZR on 2007-10-27
Found them right where stated. TYVM.
I'm guessing just removing those two entries by editing the files is acceptable?

---

### Post by FriscoZR on 2007-10-27
Yes that took care of it.
Thanks for the assist.

---

