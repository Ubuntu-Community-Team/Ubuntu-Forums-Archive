---
title: "Windows network drives"
date: 2005-05-12
forum: Absolute Beginner Talk
---

### Post by NiceGuy on 2005-05-12
Hi, I'm running Ubuntu on a network along side machines running Windows XP. My problem is that I can access their shared folders (by going to Places> Network Servers> Windows Network> etc. etc.) but not their shared network drives.  Can anyone tell me how to do this?

Thanks!

---

### Post by qstone on 2005-05-12
shared network drives should appear just like the shared folders.
Try this to see if it's a network problem or something related to Gnome network browser :
type in a console :
smbclient //nameofmyxpmachine/nameofshareddrive
If you get the 'smb>' prompt, then your network setup is fine, and curiosly this share does not show in Gnome. If you get an error, then maybe the name of the share is wrong (check it on xp : right click on the drive, properties, sharing)

If it's an "administrative share" (something like c$), it's the normal behaviour NOT to have it in Nautilus. Windows machines act exactly the same way...

Hope this helps.

---

### Post by NiceGuy on 2005-05-13
hurm... thats odd it only appears to be a problem on one machine. But unfortunately the guy whos machine it is has gone home for the weekend - I'll have to wait till he gets back - thanks anyway!

---

### Post by ThonyJ on 2006-04-12
I noticed yeasterday when i shared a folder on xp that if I had blanks in the sharename it didn't show up in ubuntu.

---

### Post by PriceChild on 2006-04-12
[quote=ThonyJ]I noticed yeasterday when i shared a folder on xp that if I had blanks in the sharename it didn't show up in ubuntu.[/quote]

I think that you should still be able to search for it in terminal using the above methods, placing "s around the name of folders with spaces.

---

### Post by Benji77 on 2006-09-21
woops

---

### Post by Iowan on 2006-09-21
> **NiceGuy said:**
> hurm... thats odd it only appears to be a problem on one machine. But unfortunately the guy whos machine it is has gone home for the weekend - I'll have to wait till he gets back - thanks anyway!
Wonder if that one machine had sharing disabled?

[edit] Oops, too.  Didn't notice the date on the rest of the posts.   I presume this got solved sometime within the last five months...

---

