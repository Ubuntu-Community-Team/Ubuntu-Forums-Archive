---
title: "So green if I was more stupid you could water me"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Midgetprawn on 2008-02-15
Newbie of the week installed Ubuntu 7.10 onto his laptop with an admin password and now it won't let me login. It worked first time but now I am left wallowing in the quagmire of despair. I thought I could reinstall but the screen goes all stripey when I try to run the live CD. Is there a way through this?

Only water once a week and keep in the shade:popcorn:

---

### Post by oldb0y on 2008-02-15
What do you mean? You are not able to boot up from CD/DVD-rom?

---

### Post by Vitamin-Carrot on 2008-02-15
*grabs water can*

have ya made any major changes tot he OS when you did login?

otherwise just boot off the live cd

---

### Post by Midgetprawn on 2008-02-15
Nope cannot rerun live CD as the system appears to hang or crash despite loading from this disc originally.

Water until the compost is wet to the touch

---

### Post by jken146 on 2008-02-15
When you installed, you chose a user name and a password.  Use those two pieces of information to log in.  If you can't remember them, don't worry.  There are some steps you can take to recover:

1.  Reboot into Recovery Mode (you select this from the GRUB menu).

2.  If you can't remember your user name, type ```
ls /home
``` to find out what it is.

3.  Change your password.  Remember that user names and passwords are case-sensitive.  Type ```
passwd yourUserName
``` replacing yourUserName with whatever it is.  When it asks you for a password, just type it in.  You won't see anything, but type anyway and press Enter.

4.  Reboot the computer.  ```
reboot
```

---

### Post by Midgetprawn on 2008-02-15
Ah the sweet smell of success. It is coming up roses. I am writing down these important words now and sticking them where I will see them.

Sound of hammer as nails driven into fore head

Feed me Seymour

---

### Post by jken146 on 2008-02-15
You're welcome :)

---

