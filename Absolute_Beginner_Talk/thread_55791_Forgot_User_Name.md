---
title: "Forgot User Name"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by Grinok on 2005-08-10
Hello retard here and I installed Ubuntu a couple weeks ago and I have since forgotten what I used as name to loggin.   Is there a way to find out the user names  without being to loggin?  thanks

---

### Post by Lord Illidan on 2005-08-10
Use the live cd to browse the contents of /home

There should be a folder with your name..though if you forgot the password, can't help you much there...

---

### Post by Grinok on 2005-08-10
Thanks for fast responce is there a way to do it without Live cd as all I have is full isntall cd?

---

### Post by Lord Illidan on 2005-08-10
If you have Windows, you can install a tool called ext2fs and browse the Linux partition..
Or you can boot Ubuntu failsafe..

There should be an option below the default Ubuntu option in the Grub Menu..

You will be logged in as root in the console.

Then type

```

cd /home
ls
```

And it should give you your username.. I hope you remember your password.

---

### Post by heimo on 2005-08-10
Boot Ubuntu CD, check under /home/ or in file /etc/passwd. If you need to reset password, you can chroot and passwd - erhm... Can't explain it. It's quite simple and this should be enough to explain it (even though this is for gentoo):
[http://gentoo-wiki.com/HOWTO_Reset_a_Lost_Root_Password]("http://gentoo-wiki.com/HOWTO_Reset_a_Lost_Root_Password")

EDIT: Oh boy, am I slow today! ;)

---

### Post by Grinok on 2005-08-10
Thanks guys found my evil user name :}

---

### Post by jeremy on 2005-08-10
[QUOTE=Grinok]Thanks guys found my evil user name :}[/QUOTE]
 Tell us, then when you next forget it all you will need to do is search the forums!!??

---

### Post by weasel fierce on 2005-08-10
It would be rather funny, if the user name was actually his own name :)

---

