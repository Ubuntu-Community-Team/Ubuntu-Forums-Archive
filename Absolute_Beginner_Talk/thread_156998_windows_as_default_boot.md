---
title: "windows as default boot"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by boodeey on 2006-04-08
hi ... my name's boodeey and i'm newbie .... on linux, specially ubuntu
i already try mandriva and suse .... and i have no problem to change default boot between windows xp and ubuntu
but now, .... i have difficulty to change my default boot .... it's always ubuntu as the default ....

please help ..........
thank's .........................

---

### Post by taurus on 2006-04-08
If you want to change the default, you need to edit your /boot/grub/menu.lst.  Open a terminal by clicking Applications -> Accessories -> Terminal.  Now, type
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak <-- making a backup copy
sudo gedit /boot/grub/menu.lst

```
Then, count to see which number is the entry for your XP.  Let's assume that your XP is the fourth entry (there are three title's before the one for XP), then at near the top, change the default value from 0 (currently) to 3...  Save it and reboot!

---

### Post by sYs^ on 2006-04-08
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by boodeey on 2006-04-09
thank's man ..........

i'm very hate linux before, i have to install 1 dvd of suse and mandriva ..... but when my friend give me 1 simple installation CD and i try it .... it some kinda "african magic" magnitize me .................

i feel so interest with ubuntu ..........

i request a shipped cd from the website ..... how you guy get money to produce it???

thank's ................

---

### Post by trent dillman on 2006-04-09
Boodeey, welcome to Ubuntu! I'm sorry you didn't like Linux before, but I feel your pain...Mandrake and Suse were the first 2 I used, too (except I had also used Knoppix). Knoppix was the one I liked best, so I went with Debian. I didn't like the 'old' packages, so here I am!

---

