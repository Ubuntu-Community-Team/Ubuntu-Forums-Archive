---
title: "How do I fix my password"
date: 2014-11-07
forum: Apple Hardware Users
---

### Post by jacatone on 2014-11-07
I'm using Lubuntu 12.04 on my Powerbook G4. I did something and screwed up my password and now I keep getting wrong password, try again. Is there anyway to fix this if I'm root?

---

### Post by TheFu on 2014-11-07
As root, use the passwd command to change the password for the other userid.

# passwd {userid}

---

### Post by jacatone on 2014-11-07
I can't become root because it's asking for my password which is screwed up.

---

### Post by slickymaster on 2014-11-07
To reset your Ubuntu user account password: [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by TheFu on 2014-11-07
> **jacatone said:**
> I can't become root because it's asking for my password which is screwed up.

> **jacatone said:**
> Is there anyway to fix this if I'm root?

Your first post says you are root, hence my answer.
howtogeek has an article on resetting passwords using 2 different methods. LiveCD is probably a little harder than booting into recovery mode. They can explain things better than me.

---

