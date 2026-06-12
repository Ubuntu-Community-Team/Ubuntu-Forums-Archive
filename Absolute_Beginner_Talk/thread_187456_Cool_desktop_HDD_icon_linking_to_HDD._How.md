---
title: "Cool desktop HDD icon linking to HDD. How?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-03
Hi,

How do I add those cool desktop HDD icons so that they link to my 2 HDDs?

I need to know how to create a link on my desktop to my HDDs.

I need to know how to change the icons.

I have my "home" folder on my HDD but I have no idea how to do the same with my 2nd HDD, so that it too appears on the desktop.

Thanks.

---

### Post by BoneKracker on 2006-06-03
You can simply press the "up" button from your home directory
Or, they're right there under Places > Computer

**But** if you really want a cute disk on your desktop, all you have to do is:
Places > Computer
  (drag and drop each disk to desktop)
  (right-click > properties)
  (little box is the icon)
  (you can edit permissions to get rid of "read only" emblem -- they're just permissions for the link you created)

**Or** you can create a launcher on your desktop for nautilus (what you'd call "Windows Explorer"):
right-click on desktop > Create Launcher > 
(where it says "command", type "nautilus" (without the quotes))
name it what you want
pick the icon you want (there are other icons in other directories than the one it brings you to)

**Or** you can create a launcher on either panel for nautilus.
right-lick on panel
press "custom application launcher" (and do like above)

**Or** you can create a launcher on either panel for each drive:
right-click on panel
click plus
press "custom application launcher"
enter command "nautilus sda1" (subtitute appropriate partition name for sda1)
and do it again for second drive

**Or** you can create a drawer on either panel that contains the launchers for the two drives:
right click on panel
click plus
scroll down to "drawer" and click it
then right click on the drawer you created
click plus
and follow as you would for the two drive launchers on the panel

---

### Post by u.b.u.n.t.u on 2006-06-03
Thank you, BoneKracker.

---

### Post by BoneKracker on 2006-06-04
oh, and I didn't mention that if your disk is mounted by udev it magically shows up on the desktop (in other words, try commenting out the entry for your non-root disk in the /etc/fstab file and reboot).  if you can get by without any special options in fstab, then that's probably the simplest way

---

