---
title: "i need to delete something in Wine"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-16
I have installed something and it is now in the Program Files in Wine. It isn't working and I need to delete it, only I don't know how. Its not in the FAQ's on the Wine website, I already checked.

---

### Post by bswilson on 2006-10-16
> **voodoonirvana said:**
> I have installed something and it is now in the Program Files in Wine. It isn't working and I need to delete it, only I don't know how. Its not in the FAQ's on the Wine website, I already checked.

You can just delete the files from the **Program Files** folder.  Remember that this folder is in a hidden subdirectory of your home directory.  In the Terminal, run this command:

```
$ nautilus ~/.wine/drive_c/Program\ Files &
```

Then delete what you want.

---

### Post by voodoonirvana on 2006-10-16
> **bswilson said:**
> You can just delete the files from the **Program Files** folder.  Remember that this folder is in a hidden subdirectory of your home directory.  In the Terminal, run this command:

```
$ nautilus ~/.wine/drive_c/Program\ Files &
```

Then delete what you want.

Yeah, I have figured out how to get into the Program Files and how to navigate around. But What would the command be to delete specific files/programs/documents?

---

### Post by podunk on 2006-10-16
```
uninstaller
```

[http://www.pclinuxonline.com/wiki/ConfiguringWine](http://www.pclinuxonline.com/wiki/ConfiguringWine)

---

### Post by bswilson on 2006-10-16
**Podunk** is right, use the _uninstaller_ that probably came with the tool you installed under **wine**.  It should be in the folder where the Windows program was installed.  

Using my directions to launch **nautilus**, heck, I say just right-click the folder of your app and send it to the Trash...

---

### Post by podunk on 2006-10-16
If you type in 
uninstaller

it brings up a GUI of all your apps installed under wine.

I *think* this is sort of like the winduhs registration database - and we all know what happens when you start deleting folders without using the Add/Remove Programs tool
(the same thing that happens when you *do* use the Add Remove thingy - the registry getrs corrupt and you get to reinstall it twice a year.) :-D

podunk
If Bill Gates got a nickle everytime windows crashed - wait! He already has!

---

