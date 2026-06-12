---
title: "My homework has...disappeared?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by 05rutterb on 2008-04-20
Ok, i saved my homework on my memory stick (i did it on open office office word processor)
then i took my memory out, put it back in, tried to open the file and it said this:

"The filename "Jamie oliver newspaper report.doc" indicates that this file is of type "Word document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

What do i do to get it back/open it?  i tried opening it with word processor but it didnt work!
please help as this homework is due in tommorow! :(

---

### Post by ugm6hr on 2008-04-20
Did you unmount / eject the USB stick before removing it?

---

### Post by frup on 2008-04-20
When you saved it did you choose to actually save it as a word document or did you just give it the file extension .doc? If .doc wasn't the file extension, what did you give it?

---

### Post by stinger30au on 2008-04-20
> **ugm6hr said:**
> Did you unmount / eject the USB stick before removing it?


learn something new here.

how do you do that???

---

### Post by lswest on 2008-04-20
right-click the icon on the desktop for your USB stick and choose "eject" or "unmount" (the phrasing varies).  Then it will probably tell you that it's writing changes to the disk, and then it will tell you when it's safe to remove the hardware.  Similar to Window's "safely remove hardware".

---

### Post by PmDematagoda on 2008-04-20
> **stinger30au said:**
> learn something new here.

how do you do that???

You can just right-click on the USB drive icon and press "Unmount volume".

---

### Post by T-Virus on 2008-04-20
Or execute:

```

umount /media/usbflash

```

In case if USB is mounted at **/media/usbflash** folder. It may also require root access.

---

### Post by IanW on 2008-04-20
Frup is probably right here. Try opening the file with Gedit (Accesories/Text Editor).

---

### Post by sailor2001 on 2008-04-20
if you have open office installed, it should read ' docs'

---

### Post by raydeen on 2008-04-20
I'm betting what happened was that the document wasn't entirely written to the drive. Even though you hit Save and directed it to the USB drive, it may not have been written at that moment. ALWAYS unmount the drive before removing it. If the data hadn't yet been written, it will be when you give it the unmount/eject command. This has something to do with the OS (Win, Mac and Linux) scheduling when the actual data writing will occur. Sometimes it doesn't happen right away depending on what other processes are occurring.

---

### Post by 05rutterb on 2008-04-20
ok, to answer all your questions, i didnt know you had to eject the usb, so im guessing all the data is gone.
opening it in text editor doesnt work and neither does opening it as a doc
thanks for all your help

---

### Post by iSplicer on 2008-04-20
> **05rutterb said:**
> ok, to answer all your questions, i didnt know you had to eject the usb, so im guessing all the data is gone.
opening it in text editor doesnt work and neither does opening it as a doc
thanks for all your help

Atleast you learned a lesson =)

---

### Post by ugm6hr on 2008-04-20
Does OpenOffice autosave somewhere?

I don't know - but a recent-ish version may still be in atemp file somewhere (unless you have rebooted since then).

---

