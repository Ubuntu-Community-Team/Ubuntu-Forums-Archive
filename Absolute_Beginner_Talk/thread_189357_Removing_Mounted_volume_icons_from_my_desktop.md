---
title: "Removing Mounted volume icons from my desktop"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2006-06-05
How can I get rid of some of the mounted volume icons from my desktop **without** unmounting them?

---

### Post by Klaidas on 2006-06-05
Simply right click the icon and choose "Unmount" :)

---

### Post by FireFusion on 2006-06-05
Sorry I meant to say **without** unmounting them. Sorry about that.

---

### Post by FireFusion on 2006-06-05
Anyone?

---

### Post by mostwanted on 2006-06-05
Either run this command:

```
gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible false
```

Or open up gconf-editor and go to /apps/nautilus/desktop and uncheck the box outside the volumes_visible label.

---

### Post by bluenova on 2006-06-05
What I do is just use the nautilus bookmarks, easyest way is to do the 'connect to server' thing, then double-click the icon on the desktop to open it then 'Bookmarks > Add bookmark' then you can go and unmount the link on the desktop and you will still have the new icon in your places menu and in the nautilus side bar.

---

### Post by FireFusion on 2006-06-05
Thanks.

---

### Post by chmmr on 2006-07-08
When I try to unmount the volumes from my desktop, it says I need root access.  How do I do this sort of thing without sudo (ie it's not an app that one launches from the commandline)?

---

### Post by chmmr on 2006-07-08
Actually, I think I have a more specific request:

I have two NTFS volumes, which are currently auto-mounted and have icons on my desktop.  I would like to keep the volumes mounted so I can access them, but I don't want the icons.  I would, however, like to have icons for removable media and USB drives pop up on my desktop.  Is there any way to do this?

Relatedly, I tried setting "volumes_visible" to false in gconf-editor and nothing happened.

---

### Post by jamesford on 2006-07-08
my solution to this very problem is to hide the volumes i dont want visible on my desktop under a gdesklet, like the weather desklet

---

### Post by H Roark on 2006-07-28
> **mostwanted said:**
>  [...] run this command:

```
gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible false
```


I had been looking for this for quite a while. Thank you very much for the fix!

- Roark

---

