---
title: "Logon Screen (GDM/KDM) is distorted"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by TristanMike on 2006-01-13
Hi, I just converted my mom and installed Ubuntu on her computer. I have one big issue that if someone could help resolve would be greatly appreciated. Basically (and I've tried with Hoary and Breezy) the logon screen is distorted. When I log in, the desktop was also distorted but dropping the resolution to 1024x768 and refresh to 75 Hz has fixed the problem but I don't know how to apply those changes to the Logon screen. Can anyone help me with this please and if there is a difference between GDM and KDM let me know this as well.
Thank you in advance.
TristanMike

---

### Post by Dr. Nick on 2006-01-13
If you can mess up the gui with a high resoulition then I would reccomend removing it from your xorg.conf file. I dont know of a file that controls gdm/kdm res, I think it may just use the highest avaible in xorg.conf.

I could be wrong on that but its worth a try.

---

### Post by mustang on 2006-01-14
[QUOTE=Dr. Nick]If you can mess up the gui with a high resoulition then I would reccomend removing it from your xorg.conf file. I dont know of a file that controls gdm/kdm res, I think it may just use the highest avaible in xorg.conf.

I could be wrong on that but its worth a try.[/QUOTE]

Dr. Nick is right. Remove all the resolutions that are larger than the one you use (in this case, 1024x768 ). Then GDM will start at 1024x768.

---

### Post by TristanMike on 2006-01-14
That's what I thought, I'll give it a try, thanx.

---

