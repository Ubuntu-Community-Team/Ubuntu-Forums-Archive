---
title: "ubuntu 6.10 snag"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by doug41 on 2007-03-10
I have just installed ubuntu 6.10 and all went well. At least I thought so till I went to login. Won't accept my password. I revisited that section and entered a new password and still no luck! So now I would like to know how to rectify this issue. I am a total ubuntu newb. I used the oem install. I would really appreciate any tips to fix this problem.

---

### Post by Crooksey on 2007-03-10
Have you tried all posible passwords/usernames..

If so boot into the failsafe kernel.

From the command line run

```

# passwd <username>

```  

To change it.

e.g.

```

# passwd crooksey
New Unix Password:
Repeat Password:
Password Updated Successfully

```

---

### Post by Patrick K on 2007-03-10
Passwords are case sensitive. Make sure the caps lock is off (or on, if that is how you entered it).

---

