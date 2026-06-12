---
title: "What is a chroot? and how can I use it on my 64 bit machine?"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Killerbird on 2006-01-14
Hello, I'm having trouble with installing wine and people and the internet is telling me that I can't install it because there is no 64 bit version of wine yet or something like this.  Im told using chroot is a way to get around this problem or something, but I have no idea what that is.  If any one can give me a hand it would be much appreciated :)

Thanks!

---

### Post by kakashi on 2006-01-14
chroot is a rudimentry computer seperation. what happens is that in a chroot enviorment the / becomes the directory you specify. so only the stuff accessible is the one under that / not the ones under a reall /.

for your problem, who knows maybe you can but i doubt it cuz the kernel is still the same.

ps. i thought this after wirtiinh the above reply. 
[SIZE=7]
[/SIZE]

---

### Post by Hallavej on 2006-01-14
[QUOTE=Killerbird]Hello, I'm having trouble with installing wine and people and the internet is telling me that I can't install it because there is no 64 bit version of wine yet or something like this.  Im told using chroot is a way to get around this problem or something, but I have no idea what that is.  If any one can give me a hand it would be much appreciated :)

Thanks![/QUOTE]

There is a howto here:
[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot)
It is for hoary, so replace hoary with breezy everywhere. It lets you install a 32-bit file system and any 32-bit program including wine. But if wine is the only 32-bit program that you need, then maybe chroot is overkill.
32-bit wine works in ubuntu 64 bit. Just download the .deb and install it with:
dpkg -i --force-architecture the_file.deb

---

