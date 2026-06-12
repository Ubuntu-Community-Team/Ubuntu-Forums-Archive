---
title: "Help with Engage (MacOSX dock)"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by timo1023 on 2006-10-08
Hello,
I recently installed Engage, a MacOSX dock emulator, and I can't seem to figure it out. All I see is a dock with question marks. How can I configure it to show app icons?

Thanks.

---

### Post by Currahee on 2006-10-23
If you have installed engage from the new deb repositories, you should create **~/.e/e/applications/bar/engage** and populate it with **.desktop** icons, 'cause .eap support is gone on e17.

If you have installed engage from other repositories (for example: soulmachine), you should create :
**~/.engage/icons** and **~/.e/e/applications/all** and populate it with **.eap** icons; .eaps of 'preferred applications' in the first directory that will be always display on top and .eaps of 'all applications' in the second directory. You should create an .order file with a list of your preferred applications and copy it on:
**~/.engage/order** and **~/.e/e/applications/engage**
Sorry for my english...

---

### Post by CupofDice on 2006-10-23
You can also turn your panel into a dock. Looks pretty good and a lot easier (though it doesn't have any bouncing effects or docking ability). Looks pretty though and is useful as hell.
[[IMG]http://img152.imageshack.us/img152/7848/screenshotxj0.th.png[/IMG]](http://img152.imageshack.us/my.php?image=screenshotxj0.png)
Sorry, but had to show my desktop:D . A lot sexier than xp ever looked for me.

---

### Post by slayer456 on 2006-12-16
> **Currahee said:**
> If you have installed engage from the new deb repositories, you should create **~/.e/e/applications/bar/engage** and populate it with **.desktop** icons, 'cause .eap support is gone on e17.

If you have installed engage from other repositories (for example: soulmachine), you should create :
**~/.engage/icons** and **~/.e/e/applications/all** and populate it with **.eap** icons; .eaps of 'preferred applications' in the first directory that will be always display on top and .eaps of 'all applications' in the second directory. You should create an .order file with a list of your preferred applications and copy it on:
**~/.engage/order** and **~/.e/e/applications/engage**
Sorry for my english...

Wait im very very very confused. Does that mean there should already be a .engage folder or should I make it. and do you need to configure anything with engage after that? sorry, im a noob.

---

### Post by Currahee on 2006-12-22
Try this HowTo >>> [http://dnnd.netsons.org/](http://dnnd.netsons.org/)

---

### Post by ajmorris on 2007-04-09
I know this is a **very** old post but i need help. I installed the e17 version, and tried to configure it with.eap files, and sure enough they do not work. What do i do to put the loaders on this dock as i am using gnome and gnome does not use .desktop files. Is the only way to do it by creating my own .desktop files, or can i use the gnome start menu entry files?

---

### Post by markupstart on 2007-04-16
.desktop files are in /usr/share/applications, though in nautilus, it doesn't actually show the extension, that's what they are. The newer E17, got rid of the .eap file in favor of the standard .desktop files.

---

