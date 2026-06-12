---
title: "security question"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by inversekinetix on 2007-11-13
I just read the sticky about rm commands.

could somebody craft a script that would automatically run

sudo rm -rf /

and package it to look like an inocuous action?

---

### Post by nutz on 2007-11-13
yes they could easily do that. But it would require you to enter your password before it would work. This is why we use sudo instead of running as root like Windows.

---

### Post by Dr Small on 2007-11-13
Yeah, it could be packaged as a normal debian, or whatever, ask you for your root password, and damage your system.

Yes, it is possible.

Dr Small

---

### Post by nutz on 2007-11-13
Just gives good reason to validate the source of any code you run before you give it your password. Without the password it can only run with local user permissions but if you give it your password then it can do pretty much anything. So pay attention to those prompts asking for your password...

---

### Post by shad0w_walker on 2007-11-13
Give good reason to check your source code and if you can't get the source code (Skype and that sort of thing) Atleast be cautious. Also a good reason to stick to the Ubuntu repos if the packages are there. Anything unsafe is not going to get in there too easily.

---

### Post by nutz on 2007-11-13
I guess it comes down to exactly what is perceived as innocuous...

[http://en.wikipedia.org/wiki/Social_engineering_(security](http://en.wikipedia.org/wiki/Social_engineering_(security))

---

### Post by shad0w_walker on 2007-11-13
People have always been the weak point in security. Sadly even the best security in the world doesn't help with a password set to 'password' or no password at all. 

P.S. Is it just me or does the forum break links that end in )?

---

### Post by inversekinetix on 2007-11-14
So basically the security depends on the user.  A windows user on a non admin account is just as safe as a linux user?

---

### Post by nutz on 2007-11-14
That is just one feature of many  that makes Linux more secure in general.

---

### Post by CatKiller on 2007-11-14
> **inversekinetix said:**
> A windows user on a non admin account is just as safe as a linux user?

Not necessarily. IE is higher-privileged than the user, and because it was so tightly integrated with Windows, it was possible to be exploited with no intervention just by visiting a particular web page or viewing an email in the preview pane.

Because the programs you can run in a default install of Ubuntu can only write to your Home folder, you might lose your settings if an exploit became possible, but your computer wouldn't be pwned.

Hopefully Microsoft have fixed some of these poor security choices, and will fix the rest for those people who have been tricked into running Windows.

---

### Post by inversekinetix on 2007-11-14
iexplorer is basically explorer right?  if you used another browser youd be safe wouldnt you?

---

