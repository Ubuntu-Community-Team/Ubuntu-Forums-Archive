---
title: "Ctrl + T ?????"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Carl_Barks on 2008-01-01
I had a file of mine selected and I accidentaly pressed Ctrl + T (thought I was at mozilla)
and then *pop* the file dissapeared!
Is this a shortcut for delete like Shift+delete? If yes, can I retrieve the file? if not, where is my file?!

---

### Post by jimrz on 2008-01-01
just a guess, but have you looked in Trash

---

### Post by Carl_Barks on 2008-01-01
yep, already done that, they are not there

---

### Post by rfruth on 2008-01-01
What program was active when U ctrl-t'ed - any keyboard shortcuts setup :confused:

---

### Post by FuturePilot on 2008-01-01
I just tried this, and sure enough, it disappeared. But I found mine in the Trash. You might want to check your .Trash directory. Sometimes the Trash Applet lies.
It's hidden so press Ctrl+H in Nautilus to show hidden files.

---

### Post by Carl_Barks on 2008-01-01
nothing. and i created some empty folders and tried it on them too and the same thing happens. It seems to be setuped as a delete shortcut ... dunno

---

### Post by SOULRiDER on 2008-01-01
The file should be in your trash. Look for it there.
Alternatively you can do
```
sudo updatedb
locate <name_of_file>
```
That should show the location of the file.

---

### Post by RomeReactor on 2008-01-01
Hi. In Nautilus, go to "Edit->Preferences" and on the "Behavior"  tab make sure the last case ("Include a Delete command that bypasses Trash") is unchecked. Have you modified this file recently? open the folder where it used to be and press CTRL+H; see if there is a backup there (if the file was named **myfile**, the backup should be named **~myfile**. If it is there, just rename it to remove the dash.

Otherwise you could try to recover it by running the Live CD, mounting the harddrive and using an application such as [PhotoRec]("http://en.wikipedia.org/wiki/PhotoRec").

---

### Post by Carl_Barks on 2008-01-01
> **FuturePilot said:**
> I just tried this, and sure enough, it disappeared. But I found mine in the Trash. You might want to check your .Trash directory. Sometimes the Trash Applet lies.
It's hidden so press Ctrl+H in Nautilus to show hidden files.

It must be what you say, but we'll never find out cause i had emptied it a bit earlier! dumb me.
Never thought there would be hidden files INSIDE the trash :P 

Thnx anyway

---

### Post by bwtranch on 2008-01-01
Doubt it. Just go to Places -> Search for Files... enter File System. It can't be permanently deleted unless you were root.

---

