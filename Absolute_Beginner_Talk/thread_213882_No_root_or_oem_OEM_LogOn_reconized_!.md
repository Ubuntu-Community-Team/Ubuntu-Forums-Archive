---
title: "No root or oem OEM LogOn reconized !"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-07-11
Tryed'

root oem OEM

none accepted. Did a reinstall without a reformat of /home
just / and swap,

can log into my account find
which root should have the same password right!

Thanks any help is always appreciated ](*,)

---

### Post by Kilz on 2006-07-11
> **orb9220 said:**
> Tryed'

root oem OEM

none accepted. Did a reinstall without a reformat of /home
just / and swap,

can log into my account find
which root should have the same password right!

Thanks any help is always appreciated ](*,)
[Root is not setup by default]("https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29"). Its not really needed and can be a security risk. If you need a gui to move files around you could use 
```
gksudo nautilus
```

---

### Post by orb9220 on 2006-07-11
I du do that with sudo.

but on my first install with same cd I ended up with a root account with the same password as my orb account.

What if my orb goes tit's up and I need to get into a root gui to fix things and no I am not going to even try to remember the 12 dozen commands with the two dozen flags to get things done.

I am sorry I just 1) Hate to type
                  2) Never can find commands that I have wrote down.

The cli maybe powerful but the gui is much easier to look and run things than typing in esotoric meangiless to human thinking type commands.

I do it when I have no other choice.

---

### Post by Kilz on 2006-07-11
> **orb9220 said:**
> I du do that with sudo.

but on my first install with same cd I ended up with a root account with the same password as my orb account.

What if my orb goes tit's up and I need to get into a root gui to fix things and no I am not going to even try to remember the 12 dozen commands with the two dozen flags to get things done.

I am sorry I just 1) Hate to type
                  2) Never can find commands that I have wrote down.

The cli maybe powerful but the gui is much easier to look and run things than typing in esotoric meangiless to human thinking type commands.

I do it when I have no other choice.

I know what you mean, I used the Alacarte menu editor to add the gksudo nautilus command to my System > Adminastration menu. What that command dose is opens up the Nautilus file manager as root with a few clicks.

---

### Post by orb9220 on 2006-07-11
Easier is to drag naughtlus to panel so its right there.

Then right click properties and add sudo there!

---

