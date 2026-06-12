---
title: "Are .rar file OS dependant?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-04-09
I've received a .rar file from a Windows user. When I try to open it, I get "Archive type not supported". I've extracted it OK in Windows, but are Windows rar and Ubuntu rar different?

What other archive programs could I try in Ubuntu?

TIA

---

### Post by justin whitaker on 2007-04-09
> **freesitebuilder said:**
> I've received a .rar file from a Windows user. When I try to open it, I get "Archive type not supported". I've extracted it OK in Windows, but are Windows rar and Ubuntu rar different?

What other archive programs could I try in Ubuntu?

TIA

.rar are platform independent. If you are comfortable with the terminal, you can get rar by apt-get install rar.

There is also a port of 7z that handles rar files as well.

---

### Post by goonies on 2007-04-09
you can install either the program called rar, or the one called unrar (Yes, 2 different programs). Both do the same things.

once u have either of them you can right click and decompress rar files right through gnome like you do any other archive file.

---

### Post by zvacet on 2007-04-09
You opened it but it is not use for you because you uncompressed win exe.file.You have to install wine if you want to run that exe.

---

### Post by freesitebuilder on 2007-04-09
> **zvacet said:**
> You opened it but it is not use for you because you uncompressed win exe.file.You have to install wine if you want to run that exe.
It isn't a program, it's an Excel file - it opened OK in Calc when I'd extracted it in Windows.

---

### Post by freesitebuilder on 2007-04-09
That's odd - I've tried two other programs, and they don't like my .rar either! Must be something in the file - I can't possibly blame Ubuntu! :)

---

### Post by tonyr1988 on 2007-04-09
Did you try the rar or unrar programs in Synaptic? Did either one work? I installed unrar and all I have to do is right-click the *.rar file and select Extract Here. It works perfectly.

---

### Post by Lucifiel on 2007-04-09
Not sure if this will work for you but you can always try renaming .rar to .zip and see if it extracts successfully.

---

### Post by freesitebuilder on 2007-04-11
This gets stranger - I renamed, and it extracted OK. But the extracted folder is empty. Properties show "0 files, 2.3 Gb free".

---

### Post by 3rdalbum on 2007-04-11
Try installing the "unrar-nonfree" package. If your archive manager doesn't deal with it properly then, try using unrar from the command-line.

---

### Post by anaconda on 2007-04-11
Yep.. and if everyhing else fails you can install the windows program to wine... what was it called?? winrar?

---

