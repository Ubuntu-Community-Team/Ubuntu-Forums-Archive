---
title: "Networking ubuntu to windows"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by mashtdi on 2006-03-07
Here is the equipment im using.  1 Unbutu box, 1 windows 2000 advanced server, 1 laptop with WinXP over wireless.

I have samba and swat installed
I can ping all the boxes.
It prompts me for the User/Pass for my windows 2k Server.  I enter my info correctly

Here's the problem:

Next, It prompts me for a User/Pass for my Unbutu box.  I enter in the info and it keeps poping up like my info is not correct.  

Am I doing something wrong?

---

### Post by TrendyDark on 2006-03-07
Try using "root" as the user name for the Ubuntu box. Although your password is the root password, your account is not.

---

### Post by mashtdi on 2006-03-07
Hmm, Still not working for me, it keeps giving me longin streens.....

---

### Post by racecat on 2006-03-07
Got to go to work now, but thought I'd take a minute. See the post entitled "Weird Samba Problem". It's probably on page 2 of this forum right now. Wait. Here's the link.
Stay tuned.

[http://ubuntuforums.org/showthread.php?t=137927](http://ubuntuforums.org/showthread.php?t=137927)

Bill

---

### Post by Sweet on 2006-03-07
[QUOTE=TrendyDark]Try using "root" as the user name for the Ubuntu box. Although your password is the root password, your account is not.[/QUOTE]


Ubuntu does not have a "root" account unless you personally create it, just clarifying :)

---

### Post by mashtdi on 2006-03-07
Yeah. I have enabled the Root account but for some reason it is not letting me log into my box.......Not that I know why i cant log into my box, since Im trying to reach another box.....???????

---

### Post by brentoboy on 2006-03-07
I think it wants your password so it can save this new windows username and password onto your keyring - for later use.

Is there an option to NOT save the username and password, maybe that will get you a step further, and we'll find out what is going on.

I havent done this in so long, i'm kind of shooting from the hip

---

### Post by LordBug on 2006-03-07
I had the same behavior.  Kept asking over and over for the login information.  I finally hit "cancel".  The login box vanished, and I had the Windows shares visible.  Might want to try that.

---

