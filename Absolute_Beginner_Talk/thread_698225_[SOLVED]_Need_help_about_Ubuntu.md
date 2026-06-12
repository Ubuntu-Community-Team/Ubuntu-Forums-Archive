---
title: "[SOLVED] Need help about Ubuntu"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-02-16
Hi.
Yesterday i install Ubuntu.Every thing is working fine.

Some basis questions to ask here.

I want to format all the drives one by one while installing Ubuntu.How i can i do that.
I know something about manual partition.

Another WHY its necessary to have internet connection for Ubuntu to install software packages.
.exe extension i dont think work in this system.
If i have no internet then how can i install most common softwares.

Thanks
Arif

---

### Post by oldb0y on 2008-02-16
> **mmarif4u said:**
> Hi.
I want to format all the drives one by one while installing Ubuntu. How i can i do that.
I know something about manual partition.

Do you want to make Ubuntu use your entire HD?

---

### Post by hackle577 on 2008-02-16
> **mmarif4u said:**
> .exe extension i dont think work in this system.
If i have no internet then how can i install most common softwares.

You are correct, .exe files do not work natively in Ubuntu, or in any flavor of Linux I know of. However, you can try to get them to work via [Wine]("http://www.winehq.org/"), but not all programs are compatible or 100% functional.

To install software without a connection, you'll want to use another computer to download the .deb files of the software you want, put those on some sort of flash drive or other portable memory, copy them over to your system, and then run them.

---

### Post by mmarif4u on 2008-02-16
@oldB0y
I have 2 partition on 160GB drive.i want it to make it 3 with complete formating them.

@hackle577
It mean i have to download Wine and install,rite.
.deb files mean for the current software i am downloading.i mean like .exe it will be .deb. for example mplayer.deb

Ok i will download files and put in flash drive and then where to copy files in HDD.
i am newbie plz bear with me.
Thank you.

---

### Post by oldb0y on 2008-02-16
Boot up using the Live CD, then use gParted in that session to partition as you please.

---

### Post by hackle577 on 2008-02-16
> **mmarif4u said:**
> @hackle577
It mean i have to download Wine and install, rite.
.deb files mean for the current software i am downloading.i mean like .exe it will be .deb. for example mplayer.deb

To run Windows programs, Wine may be needed. However, you should probably check to see if the Windows programs don't have some as good (or better!) alternatives written specifically for Linux.

Yes, .deb files are basically the Linux equivalent of Window's .exe files. So if you wanted to download a game, the .deb file might look something like: SuperTux-1.3.deb.

---

### Post by mmarif4u on 2008-02-16
@hackle577
> Ok i will download files and put in flash drive and then where to copy files in HDD.
Where i have to copy that files from flash drive to HDD.

.deb file i have to run directly OR from terminal using some command.

---

### Post by hackle577 on 2008-02-16
You can just run .deb files directly by double-clicking them. It doesn't matter where you put them, as the program is installed to the directory it needs to be in automatically. When it's done, you can delete the .deb file.

---

### Post by mmarif4u on 2008-02-16
@hackle577
thanks for ur information.
1 last question.
WHICH one is the latest version of Linux based GUI OS.

---

### Post by hackle577 on 2008-02-16
7.10 (Gutsy Gibbon) is the latest version of Ubuntu.

---

