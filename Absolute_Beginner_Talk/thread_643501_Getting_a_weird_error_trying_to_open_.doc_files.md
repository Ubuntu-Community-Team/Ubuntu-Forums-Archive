---
title: "Getting a weird error trying to open .doc files"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-12-17
For some reason when I try to open a .doc it tells me: 

> The filename "resume -- Updated (Teaching).doc" indicates that this file is of type "Word document". The contents of the file indicate that the file is of type "RTF document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "RTF document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

I have both Openoffice.org and Abiword (I'd prefer using Abiword) installed.  For some reason I can't get .docs to open by double clicking them anymore.

---

### Post by wharp on 2007-12-17
Is it a specific doc file or any and all doc files?  The error message seems to indicate that its not actually a doc file.  Will it actually open the file and properly display its contents once you dismiss that dialog?

What happens if you rename the file to .rtf?

---

### Post by dmber on 2007-12-17
i can open abiword then open the file through abiword.

i think it happened from going back and forth between Ubuntu and OS X to be able to print.

---

### Post by wharp on 2007-12-17
What happens if you create a new .doc file in OOo or AbiWord?  Can you open that by double-clicking it?

---

### Post by dmber on 2007-12-18
ya.  i'm pretty sure it's my own fault from going back and forth between Ubuntu and OS X.

when i opened Abiword, then opened the file that was giving me trouble through Abiword, then saved-as a .doc, it opened fine by double-clicking the next time.

i'll mark the thread solved.

---

### Post by wharp on 2007-12-18
Well that really shouldn't cause problems one would think.  Out of curiosity, what programs are you using in OS X?

---

### Post by dmber on 2007-12-18
i think it was pages.

---

### Post by wharp on 2007-12-18
While I haven't used Pages, I know that it does some stuff that normal word processors don't do but I would think it would strip that out when saving in a different file type.  That might actually be a bug of some sort, but not having a mac myself I can't check to see.

---

### Post by kepardue on 2007-12-18
I'm a Mac user that's got a license of Pages.  If there's anything you'd like me to try for you, let me know and I'll certainly help where I can.  I export files from Pages and open them in NeoOffice all the time, and haven't had any problems transferring them to OOo on Ubuntu.

---

### Post by macogw on 2007-12-18
Rich Text Format is the format everybody's seen in Wordpad on Windows.  .doc is like rtf with a bunch of extra on top.  A lot of people who don't have Word or refuse to use it will write their stuff in Wordpad (because they know everything they need is in Wordpad and that Word is just unnecessary) and since they usually share those with Windows users and Windows ignores the file's built-in MIME-type, it believes the file extension when it says .doc.  Ubuntu reads MIME-types, so it knows the file is lying and warns you.  

That's also why you tend not to need file extensions on Ubuntu, but do on Windows.  If you have a file named README, Ubuntu goes "plain text? ok" and displays it in a text editor while Windows goes "omg there's no file extension!  *freak out* help! i dont know what to open it with!" and then you're just like "it's text.  stop being stupid, microsoft!"

---

