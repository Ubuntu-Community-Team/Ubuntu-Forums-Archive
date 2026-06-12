---
title: "Please help with boot menu."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-06
iI successfully installed Ubuntu 7.10 and when I was prompted to restart I did. once my machine had powered back up I chose to start windows as i nedded to change some settings, but now when I restart my laptop there is no bott menu so I cant choose to boot Ubuntu! Please help as I am getting driven up the wall!

---

### Post by taurus on 2008-01-06
You mean when you turn on your machine, it boots directory into windows?  What happens when you press Esc when you first turn on your machine?  Do you see GRUB menu then?

---

### Post by Fraser from Scotland on 2008-01-06
When I press Escape it asks me If I want to boot the CD/DVD drive or the HDD, I really dont know why.

---

### Post by Fraser from Scotland on 2008-01-06
I will try again and see if it works this time.

---

### Post by taurus on 2008-01-06
So on the first reboot after you installed Gutsy, you got GRUB menu and you picked to boot windows.  Then, your laptop boots directly into windows since then?  What did you change in windows?  Did you happen to run the fixmbr thing?

By the way, you have to wait for your laptop to finish reading the BIOS first before you want to press Esc to bring up GRUB menu, if GRUB is still in MBR.

---

### Post by Fraser from Scotland on 2008-01-06
Yeah, after Gutsy was finished installing i re-booted then the GRUB menu came up and i chose windows and it botts directly to windows every time. When i press escape it gives me 2 options to boot from
1. ATAPI CD/DVD Drive
2. NOTEBOOK hard drive

neither makes a difference, i dont even know what it is booting.
I dont know what fixmbr is and i was only changing my password and my account settings.

---

### Post by Fraser from Scotland on 2008-01-06
Can someone solve this? I really dont know what to do. :(

---

### Post by taurus on 2008-01-06
If Gutsy is till on your machine and somehow you removed GRUB from MBR, then you just need to reinstall it so you can boot into Gutsy.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by Fraser from Scotland on 2008-01-06
Thank you!! it worked and I'm now dual-booting Gutsy and XP. :)

---

