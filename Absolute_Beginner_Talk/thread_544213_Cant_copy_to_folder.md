---
title: "Cant copy to folder"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Faud on 2007-09-06
Hello, Im new to ubuntu. Love it so far.
I found some really cool glass themes from gnomelook. I opened the file and then I found the usr/share/icon folder. I went to copy the folder from the download and it said that it couldnt copy it because i didnt have the rights.
Im the only one that uses this computer and it didnt give me an option to enter a password or anything

Faud

---

### Post by BaffledMollusc on 2007-09-06
> **Faud said:**
> Hello, Im new to ubuntu. Love it so far.
I found some really cool glass themes from gnomelook. I opened the file and then I found the usr/share/icon folder. I went to copy the folder from the download and it said that it couldnt copy it because i didnt have the rights.
Im the only one that uses this computer and it didnt give me an option to enter a password or anything

Faud
Linux is different from Windows in that by default your account doesn't have administrator rights. For security reasons, you only have the right to write to files and directories that live under your own home directory, i.e. /home/username.

You can of course write to other directories if you want to, but there's an extra step to make you think about whether what you're doing is *really* what you want to be doing.

One way to do it is if you open up a terminal window (Applications->Accesories->Terminal) and type "gksu nautilus" you will get a file browser that is running with administrative privileges. Essentially it means you're running the file browser under sudo.

---

### Post by Sensenseppl on 2007-09-06
In case it is a package (like tar, tar.gz, ...) you might want to try to unpack it first.
If you can't unpack it, type
```
sudo file-roller
```
into your console, which opens the archiving program with the permissions you need. Then you should be able to unpack it.

---

### Post by hyper_ch on 2007-09-06
.tar.gz files can easily be extracted from the terminal:

```

tar xvfz file.tar.gz

```

---

### Post by Perfect Storm on 2007-09-06
Use the Theme installer under System --> Preferences tab to install the downloaded theme. No need to mess with your system.

---

