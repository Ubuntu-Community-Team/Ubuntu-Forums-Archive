---
title: "Locking a folder with the  password"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-06-24
Hello,

I am interested how could I password-protect some of my folders in /home. these folders belong to me, as an user, but sometimes my friends ask me to let them use my lap and I would not like to give them access to all folders. 

Is it possible to make so, that when one tries to open folder, instead of opening, a notification window appears with request to enter password to proceed. That was my dream in windows, but never could do that there. Maybe it is possible in Linux?

Any ideas would be appreciated.

---

### Post by jfinkels on 2007-06-24
Look into 'gpg': [http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

Type :```
man gpg
```for more info.

---

### Post by O-pos on 2007-06-24
that means, it's impossible?

---

### Post by jfinkels on 2007-06-24
> **O-pos said:**
> that means, it's impossible?

No, it means follow the directions on the website whose link I posted above and read the man pages for more information. In brief, do the following:

To encrypt a file with a passphrase, type the following in the terminal:```
gpg -c myfile
```
and enter your desired passphrase twice.

To decrypt the file, type the following in the terminal:```
gpg myfile.gpg
```In order to decrypt the file to an output file with a different name, type the following in the terminal:```
gpg myfile.gpg -o mysecondfile
```

Let me know if you need anymore info.

---

### Post by Taliskerd on 2007-06-24
What I don't understand is WHY your friends have to use YOUR account when they borrow your computer.
That's just stupid.

Create another user and let them use that one instead -End of problem.
Or is there a (very good) reason your account have to be used?

---

### Post by punx45 on 2007-06-24
i agree.   add a new user for your friends, then just chmod your folders so that only you can read them.

---

### Post by jfinkels on 2007-06-24
> **Taliskerd said:**
> What I don't understand is WHY your friends have to use YOUR account when they borrow your computer.
That's just stupid.

Create another user and let them use that one instead -End of problem.
Or is there a (very good) reason your account have to be used?

This is equally as difficult. There's more than one way to skin a cat. Remember Taliskerd, we are all friends here.

---

### Post by Taliskerd on 2007-06-24
You're right my reply can be read as another 'silly you' -apologies where needed!

But the solution I advocate is the easier of the two;
[menubar] System - Administration - Users And Groups - Add User

Fill in the blanks (stop by in the forum whenever you find something that needs explaining) and you're done.

---

