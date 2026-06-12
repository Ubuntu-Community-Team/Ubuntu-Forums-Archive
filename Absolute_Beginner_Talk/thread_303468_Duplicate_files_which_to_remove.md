---
title: "Duplicate files: which to remove?"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by neocortex on 2006-11-20
Hello!
I have noticed same files in:
/usr/share/applications/
and
/usr/share/app-install/desktop/
They are all of *.desktop type.
Why is that? Can I remove one of them? Which one?

Thanks!

---

### Post by Jussi Kukkonen on 2006-11-20
First, they may be just symbolic links -- have you checked?

Second, desktop files are quite small, there's probably no real advantage in removing them.

Third, you shouldn't go removing system files,  that's what package management is for. You can even break package management if you do so, thus making upgrading the OS quite difficult.... If you are really sure that there are files that aren't necessary, open a bug in launchpad.net.

---

### Post by tubasoldier on 2006-11-20
> **Jussi Kukkonen said:**
> Third, you shouldn't go removing system files,  that's what package management is for. You can even break package management if you do so, thus making upgrading the OS quite difficult.... If you are really sure that there are files that aren't necessary, open a bug in launchpad.net.

Since this is posted under the Absolute Beginner Talk, I would recommend not removing any files you didn't put there yourself. Running around your system deleting files will undoubtedly put you back in here asking for help on how to get your system working again. If you see two desktop Icons for the same program then you could remove one off of your desktop, sure. But what you are talking about requires root/sudo access and should not be done unless you really know what you are doing.

If you are seriously that worried about disk space then go pick up a new hard drive.

---

### Post by CatKiller on 2006-11-20
> **neocortex said:**
> Hello!
I have noticed same files in:
/usr/share/applications/
and
/usr/share/app-install/desktop/
They are all of *.desktop type.
Why is that? Can I remove one of them? Which one?

No. I believe that one set is for programs you have installed, and the other is used for entries in the Add/Remove application.

There are probably thousands of .desktop files on your computer. They are the standard launcher configuration type - more information [here]("http://www.freedesktop.org/wiki/Standards_2fdesktop_2dentry_2dspec").

It's a mindset that surprises me - I used to hear it now and then in the Windows world too - "I deleted some files because I didn't know what they did, and now my computer doesn't work". Generally files are created for a purpose, even if you don't know what that purpose is.

Welcome to the community.

---

### Post by neocortex on 2006-11-21
OK, I shall not delete them :)
They are not symbolic links, and there is another one with some duplicates:
$HOME/.local/share/applications/
There are my locals, which I had added via Alacarte.

Petar

---

