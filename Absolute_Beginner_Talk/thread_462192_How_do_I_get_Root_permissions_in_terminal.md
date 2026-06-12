---
title: "How do I get Root permissions in terminal?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-02
Hi,
I'm trying to inspect and start my ekpd in order to get my printer running. I've tried '/etc/ekpdrc' and /etc/rc.d/init.d/ekpd start (this command structure may apply more to red hat)...

I'm a newbie at coding so please be as specifc as you can. Many Thanks, Frank B.

---

### Post by floke on 2007-06-02
sudo

---

### Post by h0ax on 2007-06-02
there are many ways to get root

the main way is typing "sudo" then the command
so "sudo vi /etc/ekpdrc" or replace vi with whatever command line text editor you'd prefer.

also you can run gksudo on an application if you'd like a GUI version.

---

### Post by Brightbelt on 2007-06-02
Thanks for responding. I should have mentioned that I've already tried sudo,...Thanks, Frank B.

---

### Post by locke.dragon on 2007-06-02
```

sudo -i

```

is the easiest way.  most of the time

```

gksudo nautilus

```

works better tho.

EDIT: woops.  made the stupid mistake of answering before reading the question.  :P  -smacks self in face-

---

### Post by Brightbelt on 2007-06-02
The 'vi' made the difference. Thanks !! Frank B.

---

### Post by ncappel1 on 2007-06-02
here's a great page from the ubuntu wiki regarding everything sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Brightbelt on 2007-06-02
Thanks, that is a very good resource,...Frank B.

---

### Post by zero244 on 2007-06-02
sudo -s
will put you in the root folder as well.
I like the way Ubuntu handles super user. You cant login and stay loged in as Root......it times out after about 15 minutes.
Now I suppose theoretically if something attacked or invaded your machine during that 15 minutes you could be vulnerable.

---

