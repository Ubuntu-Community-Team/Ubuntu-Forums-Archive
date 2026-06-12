---
title: "Back with a new problem."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by kitcecil on 2008-01-31
So I reinstalled Ubuntu to fix my "bash: /dev/null: Permission Denied" error and it worked, but now as I login, I'm hanging at this screen where all I have is:

cecil@ubuntu~$:

I've read things about the startx command, but it gives me another error saying that the server is already active, or something to that effect. How would I bring up the ubuntu desktop?

Thanks in advance!

---

### Post by yabbadabbadont on 2008-01-31
What happens if you run:
```
sudo /etc/init.d/gdm restart
```

---

### Post by kitcecil on 2008-01-31
My screen goes black. Completely.

---

### Post by yabbadabbadont on 2008-01-31
OK, sounds like the same issue that many Gutsy users are having.  Unfortunately, I don't know the solution.  (Or I would be a hero on the forums :D)  Try hitting Control-Alt-F1 to see if you can get to a text console.

---

### Post by kitcecil on 2008-01-31
Yes, it takes me back to login screen where I am able to try logging in once more. Suggestion?

---

### Post by yabbadabbadont on 2008-01-31
Read through the (many) "Gutsy black screen" threads to see if there are any potential solutions.  Not a good suggestion, but the best that I have to offer currently.  :(

---

### Post by legend2440 on 2008-01-31
Boot Ubuntu in Recovery Mode and execute:-
Code:

dpkg-reconfigure -phigh xserver-xorg

After the X-Server has been set to defaults reboot the system using:-
Code:

reboot

Note:- Booting Ubuntu in Recovery Mode means that you are immediately brought to a Command Line Interface or terminal.

---

