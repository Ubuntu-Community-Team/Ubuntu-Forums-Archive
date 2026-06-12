---
title: "cannot unmount volume"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-11-25
i need help :( every time i eject/unmount an USB (drive/mp3 player), an error message "Cannot unmount volume" with details "Cannot remove directory" will appear i tried this one liner

> sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

 i found in another post but it still wont work it just changed the right click menu entry from 'eject' to 'unmount' i still get the same error message.


any help will be greatly appreciated thanx!

---

### Post by ubukool on 2007-11-25
Maybe your volume is being used by another program, such as your soundfile playing software like Amarok, XMMS, etc. in which case you would have to exit the program first before it will allow you to unmount the volume.

If you go into the terminal and type:

sudo umount /[volume name]

it should unmount if it isn't being used by any program.

---

### Post by Vic! on 2007-11-25
it says its not found when i try to sudo umount /v    (v) is the name

---

### Post by Bothered on 2007-11-25
The volume name needs to be prefixed with /dev, e.g. "/dev/[volume]"

---

### Post by Vic! on 2007-11-25
how do i change the prefix so that when i right click it it ejects it properly

---

### Post by Vic! on 2007-11-25
ok actually it worked when i typed this > sudo umount /media/v how do i make that the command that is given when i rightclick the icon and choose unmount volume


thanx  guys!

---

### Post by Vic! on 2007-11-25
?? help... lol

---

### Post by ubukool on 2007-11-25
I can't help you with that, sorry.  I had a problem with some DVDs not automatically mounting so I had to manually mount and unmount them using the terminal commands, so maybe you could do the same?  It's not perfect but at least you've got a workaround :)

---

