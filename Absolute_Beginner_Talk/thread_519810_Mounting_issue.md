---
title: "Mounting issue"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by StarscreamUK on 2007-08-07
Hello fellas, I love this forum, a few searches and replies to my other questions and I'm already flying along.


I do have a niggle though


How do i auto bind a directory at boot?

i tried adding a session and giving it the command 

sudo mount --bind /media/disk/PICS /private/my_pics

works in the terminal, but not as a session command.....

any ideas please?

---

### Post by Jimmyfj on 2007-08-07
The reason that it's not working after turning on your computer is that you haven't added your root password as called in the command. Don't know if you can do that - Im pretty newbie myself.

---

### Post by iver2435 on 2007-08-07
The key to gettting a volume to "auto-mount" lies with the /etc/fstab file 

This file tells Ubuntu what drives to mount and where.

Read up on the man page and documentation for it, but it's pretty straight-forward.

---

### Post by Inxsible on 2007-08-07
> **StarscreamUK said:**
> Hello fellas, I love this forum, a few searches and replies to my other questions and I'm already flying along.


I do have a niggle though


How do i auto bind a directory at boot?

i tried adding a session and giving it the command 

sudo mount --bind /media/disk/PICS /private/my_pics

works in the terminal, but not as a session command.....

any ideas please?

if its an external drive, you can mount it using pmount. Look at the link in my signature for it.

if its an internal drive, you will need to modify your fstab like suggested.

post the contents here and we can help you out.

```
cat /etc/fstab
```

---

### Post by StarscreamUK on 2007-08-07
i dont think i made myself clear lol

its an external drive and it mounts fine

but on powering on machien i want to bind a dir. so i can go /private/my_pics

rather than /media/disk/PICS

i can do it by opening a terminal and doing sudo bind etc

surely i can automate this to make my life lazier?

---

### Post by Noz Candy on 2008-05-07
[http://www.vinno.net/linux/server/chroot-mount-trick](http://www.vinno.net/linux/server/chroot-mount-trick)

I found it in: [http://ubuntuforums.org/showthread.php?t=363388&highlight=auto+mount+--bind](http://ubuntuforums.org/showthread.php?t=363388&highlight=auto+mount+--bind)

It works for me.

---

### Post by scubanator87 on 2008-05-07
> **StarscreamUK said:**
> i dont think i made myself clear lol

its an external drive and it mounts fine

but on powering on machien i want to bind a dir. so i can go /private/my_pics

rather than /media/disk/PICS

i can do it by opening a terminal and doing sudo bind etc

surely i can automate this to make my life lazier?
Well in *nix systems, everything is a file including folders. So things like /dev/sdb1 is a file as is /media/disk/my-pics 

you should be able to add something to your fstab as suggested to make it work and you should still be able to use the --bind option.

Just for curiosity, why would you want to make a specific folder mount elsewhere? security? or just to make it one less click to access? cause if its the latter you could always just add a shortcut to from the desktop or ad a favorite in the nautalis/gnome menu?

---

