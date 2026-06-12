---
title: "wine directory"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Corey4666 on 2006-09-06
i installed mame32k under wine but i dont know where to put the roms into mame32k because i dont know how

---

### Post by Tomosaur on 2006-09-06
Your wine directory is by default in your home directory. It is hidden though, because it is called .wine (with the dot in front :))

So say your username is corey, the wine directory would be in:
/home/corey/.wine

And you would put your roms in:
/home/corey/.wine/drive_c/Program\ Files/mame32k/roms/

---

### Post by Corey4666 on 2006-09-06
i went to filesystem then home then corey4666 then i looked for .wine but didnt see it
you said it was hidden how to i view hidden folders? :confused:

---

### Post by Tomosaur on 2006-09-06
You should type 'ls -a'

---

### Post by Corey4666 on 2006-09-07
whats that do? i jus did it and it showed alot of .<name here> file's

---

### Post by Tomosaur on 2006-09-07
That lists the hidden files and folders. The dot is how you hide something in linux - any file or folder can be made hidden just by putting a dot in front of it.

If the .wine folder doesn't exist, just start wine and it will create one for you.

---

### Post by Bloch on 2006-09-07
You can also view the hiden files in nautilus (the normal file browser in ubuntu). Just ick the "show hidden files" in preferences.

---

### Post by msandersen on 2006-09-07
Control+h in Nautilus shows the hidden folders.
You don't need Wine to run a MAME frontend. There's XMAME for Linux.
I haven't tried MAME on Linux, but in Windows ROM files go in the ROM subdirectory. XMAME would have some Preferences for where ROM files are located. I expect you can put them where you want, then point XMAME to the directory.

---

### Post by Corey4666 on 2006-09-07
> **msandersen said:**
> Control+h in Nautilus shows the hidden folders.


thanks btw i use mame32k on windows because its online and the linux version isnt because kaillera hasent been made for linux "client" hasent been made the server has

---

### Post by jbumgar on 2006-09-07
It didn't work for me.

---

