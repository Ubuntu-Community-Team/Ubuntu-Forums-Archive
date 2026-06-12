---
title: "Why as admin for interesting applications?"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by mathew.chacko on 2006-02-07
Why we need run as administrator to use some of the application properly? 
like; Kino, K3B, Eclipse (to add plugins) etc.

To capture DVs
> sudo kino

To create VCDs or write on to DVDs
> sudo k3b

To add plugins to development tool:
> sudo eclipse

Or is there any other way which I may not be knowing?

---

### Post by Kapre on 2006-02-07
[QUOTE=mathew.chacko]Why we need run as administrator to use some of the application properly? 
like; Kino, K3B, Eclipse (to add plugins) etc.

To capture DVs


To create VCDs or write on to DVDs


To add plugins to development tool:


Or is there any other way which I may not be knowing?[/QUOTE]

matthew - try to check your permissions (and check if your account has admin abilities). maybe when you set it up you dont have enough permissions. Also, try making a shortcut of it on your apps list.

K

---

### Post by kaamos on 2006-02-07
The first one could be solved with a "sudo chmod 777 /dev/XXX".

The second one I have never encountered, but I use gnomebaker.

The third.. well, it's the same thing for nvu extensions and a lot of stuff. The apps are made to be installed per user, so I guess the permission model does not really fit in.

---

