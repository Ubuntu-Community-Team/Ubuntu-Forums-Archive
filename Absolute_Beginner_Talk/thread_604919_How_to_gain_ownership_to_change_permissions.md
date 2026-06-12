---
title: "How to gain ownership to change permissions?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by stork123 on 2007-11-06
i am trying to add a plugin to Azereus and to do so it tries to create a folder in the /usr/shared/azereus/plugins directory.
It fails after not being able to create this directory.

The issue takes me to a greater question as I learn how linux operates.
I have learned how to create directories using mkdir and learned about SUDO and SU commands.
But now I am having a hard time with permissions and CHMOD.

how do I change the permissions of this newly created directory so I can write to it?

More importantly, am I on the right track or is this an Azereus issue?

thanks
chris
baltimore, md

---

### Post by Dr Small on 2007-11-06
Why don't you just open nautilus as sudo and do all of the operations you need to as root ?
```
gksudo nautilus
```

;)

Dr Small

---

### Post by rudeboyskunk on 2007-11-06
If you are installing from commandline, type "sudo" right before any command.  This will allow you to install to anywhere in your system.

---

### Post by stork123 on 2007-11-06
HA!
done!
I guess all it took was for me to verbalize what I was trying to do!
chmod 700 and the newly created directory...

thanks

---

### Post by Dr Small on 2007-11-06
Yes, it really isn't as dark and difficult as Windows users visualize it as :p
Please remember to mark your thread as solved from Thread Tools, so other people will know to read your thread for a solution!

Dr Small

---

