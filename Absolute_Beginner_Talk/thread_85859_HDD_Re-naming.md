---
title: "HDD Re-naming"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by Cufishing on 2005-11-03
Ok, I think I'm on my final install this time. I have all of my HDDs "mounted" on my desktop. They are all numbered and such hda1, 3,5,6,7,8, hdc1 etc. How can I dismount or unview the ones I don't want. Like hda1&3 which is WinXP and swap file. Hdc1 is my data back-up for C: WinXp.

Also, can I rename them into common names?
Like hda 5 or 6 is music. And the other 6 or 5 is pictures.
Then hda7 is movies. 'I think'.

---

### Post by Darrin on 2005-11-03
This should help you.
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by Cufishing on 2005-11-03
Thank You, that was almost a breeze.....

Any idea on re-naming them?

---

### Post by Darrin on 2005-11-03
Im assuming you would do the same steps as it showed in the instructions from the starter guide. Just instead of the name "windows" just name it something else and plug that in as in the example.
Im a newbie also. I did mine a few days ago and I think thats what I did.

---

### Post by tehwa on 2005-11-03
[QUOTE=Darrin]Im assuming you would do the same steps as it showed in the instructions from the starter guide. Just instead of the name "windows" just name it something else and plug that in as in the example.
Im a newbie also. I did mine a few days ago and I think thats what I did.[/QUOTE]
I just played around with this, apparently to get the label to read the name of the directory and give you a desktop icon, it needs to be mounted in the /media directory. It will give you an icon with the label being whatever the directory name is (/media/Cheese gives you a label "Cheese")

---

