---
title: "permissions on different harddrive"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by capty99 on 2007-04-26
okay, i have a smallish hard drive i use for my os installs.
then i have a 400 gig and another 350 gig that i use as media holders,
i do alot of rearranging, renaming etc... on these and its getting to be a pain to not be able to do that real easily because of permissions.
is there not a way to just open these up to let me change whatever i want?

---

### Post by lepz on 2007-04-26
gksudo nautilus

---

### Post by Ecthelion on 2007-04-26
> **lepz said:**
> gksudo nautilus

... and then just right-click on the folder where the drive is mounted, click properties, permissions and change them to whatever you want :-)

---

### Post by capty99 on 2007-04-26
yeah, i did gksudo nautilus,
and i can get the root file browser window,
but my media drive does not show up.
it does if i am in my regular user file browser,
but not in root.

that make sense?

does it have to be mounted for the root user?and how do i do that?
thanks for the help

---

### Post by Ecthelion on 2007-04-27
> **capty99 said:**
> yeah, i did gksudo nautilus,
and i can get the root file browser window,
but my media drive does not show up.
it does if i am in my regular user file browser,
but not in root.

that make sense?

does it have to be mounted for the root user?and how do i do that?
thanks for the help

If it's mounted then the root user should see it.
in fact, when you mount things manually, you have to be root to do it.

Please post the output of this:
```
cat /etc/fstab
```

---

### Post by kakalaky on 2007-04-27
you can use the terminal to do this easily.  For instance, say you have a dir under /home/yourusername called stuff and you want any user to be able to do whateverwith it and everything in it:

```
chmod -R 777 ~/stuff
```

for more detail on how this works:

```
man chmod
```

---

### Post by Ecthelion on 2007-04-27
Noooo!

Never give people the idea to use a chmod -R without an extended explanation of the risk bound to this command!
(don't forget we are in the beginner area here)

Using a chmod -R on, for example, your home dir may give you multiple errors everywhere, and doing it in any system dir can entirely break your system!
So please only use it when you know what you do!

(I've once misused it and had to reinstall, so I know what I'm talking about)

...Well now the warning has been given, it might be the easiest way to settle this here, but for the exact command, please give us the name of the mount point, and the content of your fstab...

btw, giving all your files the 777 permissions is useless and never a good idea because of security issues...

---

### Post by kakalaky on 2007-04-27
hence the reference to man and the explanation that the example will allow anyone to do anything.

---

