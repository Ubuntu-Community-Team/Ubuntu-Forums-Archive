---
title: "Trash Can on KDE desktop"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-09-23
Hi,
It's a silly question, I know, but I can' get the Trash Icon on the KDE desktop.
My basic installation is Ubuntu 6.06 64 Bit architecture and additionally  I installed KDE desktop.
Can somebody give me a hint what to do?

---

### Post by Minyaliel on 2006-09-23
The trash should be sitting right on the bottom right by the clock/ date thing... it does so by default. If it doesn't, that would be rather strange, but you can add it by right- clicking the panel and go to "add applet", I think you'll find it there.

---

### Post by claydoh on 2006-09-23
If you want to put a trash icon on your *desktop* rather than having on the taskbar, you can create one by right-clicking on your desktop, select "Create new - Text File", and name it whatever you like. Then open that file and paste the following into it, and save:
```

[Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Icon=trashcan_full
Name=Trash
Type=Link
URL=trash:/

```

---

### Post by Cariboo1938 on 2006-09-24
Thanks to Minyaliel and claydoh,
in fact the trash can   was NOT in the taskbar!
But anyway  I chose the "add applet" version Minyaliel suggested and it worked fine. Case closed...thanks again
Cariboo

---

### Post by Cariboo1938 on 2006-09-24
> **claydoh said:**
> If you want to put a trash icon on your *desktop* rather than having on the taskbar, you can create one by right-clicking on your desktop, select "Create new - Text File", and name it whatever you like. Then open that file and paste the following into it, and save:
```

[Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Icon=trashcan_full
Name=Trash
Type=Link
URL=trash:/

```I created the file...what would be the next step...???

---

### Post by aysiu on 2006-09-24
There is no next step. Once you create that file on your desktop, that should be it.

The file should be named trash.desktop

---

### Post by rama on 2006-10-29
I m quite sure that there is a way to add the trash icon on the desktop from a menu somewhere but I ve wasted the past 30 minutes looking for it!

---

### Post by nikkolas on 2006-11-15
Saving the file as trash.desktop should fix your trash icon problem

---

### Post by unreal on 2006-12-22
> **nikkolas said:**
> Saving the file as trash.desktop should fix your trash icon problem


Works wonderfully! Thank you Nikkolas!

---

### Post by msak007 on 2006-12-22
I know this issue's been resolved as you've already added the Kicker applet and you were advised on how to create the link to the trash can, but if you're still looking for an alternative for your Desktop you can check out [this]("http://www.kde-look.org/content/show.php?content=39184") SuperKaramba trash applet.

---

