---
title: "mounting cdrom troubles"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Virtuous on 2007-02-15
I'm having troubles mounting a cdrom I type the command to mount and this is what I get.

mount /mnt/cdrom
mount: can't find /mnt/cdrom in /etc/fstab or /etc/mtab

Is there a way I can fix this? Thanks. :(

---

### Post by brazzmonkey on 2007-02-15
/mnt is barely used nowadays. check /media instead.

---

### Post by Virtuous on 2007-02-15
Thanks! I was able to install Starcraft through wine by using /media instead of /mnt.

Now I have another problem, When I try to play Starcraft it says that it cannot locate my disc so I typed:

# cd ~/.wine/dosdevices/
# ln -s /media/hdc d:

I was able to get into the dosdevices directory but after typing the last command nothing happened.

---

