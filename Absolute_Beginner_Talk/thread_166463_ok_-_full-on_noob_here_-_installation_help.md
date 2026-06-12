---
title: "ok - full-on noob here - installation help"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by surftrip on 2006-04-26
<linux noob alert>

I downloaded the .iso for kubuntu.  When I put it in my laptop, windows just opens an explorer window showing my iso file on the disk as just a file.

How can I get the Linux OS to boot?

</linux noob alert>

---

### Post by mostwanted on 2006-04-26
[QUOTE=surftrip]<linux noob alert>

I downloaded the .iso for kubuntu.  When I put it in my laptop, windows just opens an explorer window showing my iso file on the disk as just a file.

How can I get the Linux OS to boot?

</linux noob alert>[/QUOTE]

You need to actually burn the ISO to a CD and boot with that. Ubuntu is an operating system, not a Windows program.

Edit: My bad, think I misread your post. You need to burn your CD as a CD image or as an ISO. It should be available as an option in most burning programs. Simply burning a regular data CD won't work.

---

### Post by kbrown3074 on 2006-04-26
did you modify the bios to make sure the cd is the first boot device?

was the cd burnt as an image?  if it was burnt as a data cd, you could have problems...

---

### Post by surftrip on 2006-04-26
[QUOTE=kbrown3074]did you modify the bios to make sure the cd is the first boot device?

was the cd burnt as an image?  if it was burnt as a data cd, you could have problems...[/QUOTE]

Yes to all of your questions.  I burned with nero using the ISO tab.  The CD appears as having the file with a .iso extension.  I went into the BIOS and chose to have the CD-rom be the first first boot device; unfortunately, it still boots windows.

<sigh>

I realize Ubuntu is an Linux operating system and not a Windows app, but I was a little shakey on actually what it takes to get the ISO recognized as I do not work much with the file type.

---

### Post by junglemike on 2006-04-26
Looks to me like you burnt your iso just as regular file in data mode.
In nero you need to do the following:
Go to Menu->Recorder->Burn Image...

---

### Post by steve.horsley on 2006-04-26
I remember when I burned my first Linux installer CD a few years ago I used nero, and I used a menu somewhere that said to burn an **image** file. The word image is the important thing. Of course, recent versions may have different menu options. 

If windows a .iso file on the disk then it has not been burned as an image. If you succesfully burn the image file then the contents if you open the CD in windows will show quite a few files and folders. So your immediate problem is getting nero to burn the image.

---

### Post by surftrip on 2006-04-26
[QUOTE=junglemike]Looks to me like you burnt your iso just as regular file in data mode.
In nero you need to do the following:
Go to Menu->Recorder->Burn Image...[/QUOTE]

That was it.  What's weird is NERO has a ISO tab, but it functions just like dataCD.  I had to actuall;y go to the menu item Recorder:Burn Image to do it properly.

Thank you - what a great group of support folks.  I'll let ya know how I make out and share whatever I learn with other dopey fools like myself.

Cheers.

---

### Post by RobyX on 2006-04-26
I know a MUCH easier way. You can even use a DVD to burn it like I did :)

While in Windows download a program called ISORecorder, install it and then when it's done you right click you're .ISO file for linux you should see a new menu there that says something like "Burn CD" I dont remember exactly.

It will just burn with no questions asked and you can boot up from that CD.
Remember to change the BIOS Menus to make CD-ROM on first boot.

---

