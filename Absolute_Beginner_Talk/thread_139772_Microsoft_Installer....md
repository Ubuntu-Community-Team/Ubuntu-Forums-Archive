---
title: "Microsoft Installer..."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by WackToMack on 2006-03-04
How would one go about using a .msi file?  I know that it's a Microsoft Installer, but I really need the program it installs... is there anyway to use it?  I know Wine doesn't work, because I just tried it... Thanks in advance! :D

---

### Post by rfruth on 2006-03-04
ya can't use a msi file with breezy, just see what it does and convert it to Linux ;)

---

### Post by TrendyDark on 2006-03-04
What program is it? Maybe there is a Linux version or a program like it for Linux.

---

### Post by kaamos on 2006-03-04
You can use it in wine by getting the program that deals with .msis. Can't remember the name though so try google.

The syntax would then be something like "wine msinstaller.exe file.msi"

---

### Post by dtfinch on 2006-03-04
Wine supports .msi files. I like to grab the latest Wine rather than getting it from the repositories.

You can install winetools which will help you install a great number of real Windows components that Microsoft has available for download, which improves compatibility for when running programs that require more than what comes with Wine.

Sometimes, when a program still fails/refuses to install on Wine, I can install it on a Windows system, copy it over along with any dependencies, register its dll's (regsvr32), and add any necessary registry keys.

---

### Post by Mustard on 2006-03-04
[QUOTE=dtfinch]Wine supports .msi files. I like to grab the latest Wine rather than getting it from the repositories.

You can install winetools which will help you install a great number of real Windows components that Microsoft has available for download, which improves compatibility for when running programs that require more than what comes with Wine.

Sometimes, when a program still fails/refuses to install on Wine, I can install it on a Windows system, copy it over along with any dependencies, register its dll's (regsvr32), and add any necessary registry keys.[/QUOTE]

Hehehe..using wine seems to be an art form in itself.  We should have a whole forum section just for wine I think. :D

---

### Post by TrendyDark on 2006-03-04
Yeah, I tend to stray away from anything having to deal with Wine. Although, I would love to know how to install Photoshop CS2 over Wine, that would make my day.

---

