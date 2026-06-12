---
title: "Where's the registry?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by 56seeker on 2007-05-04
Silly question, I know Linux doesn't have one!

But how do I know uninstalled software is really gone?

On a Windows box; after running the uninstaller, I'd do a search in program files, user/app data and maybe in Windows/temp and as a last step I'd do a search and delete in the Windows registry to clean up.

How does one ensure a clean uninstall in Ubuntu?

I've been playing (unsuccessfully) with Wine recently. However, although I've since uninstalled Wine, there's "bits" of it all over the place.

Are there configuration any files I need to clean up? For instance, there's still a Wine program group on the start menu, although Wine it's self is long gone. I can hide this group in preferences, but I don't want to hide it, I want it gone!

Thanks :)

---

### Post by srt5 on 2007-05-04
If your using Synaptic package manager, then you can right click on installed packages and select 'completely remove package', which I believe removes configuration files as well as the actually binaries. If your still in doubt you could always open up a terminal and type:

```
locate programName
```

for instance

```
locate wine
```

this should print out a list of where the files which relate to that command/program are stored within your filesystem so you could go through and manually remove them.

Hope this helps somewhat :)

---

### Post by ubnewbie2 on 2007-05-04
srt5 had some good advice, but I just wanted to say, that linux programs tend to keep their configuration in conf files which are just text files.  These tend to be of 2 types.  System wide ones, mostly found in /etc, and user ones, often to overide or modify the systems settings. User ones are mostly kept in the user's home directory, often in directories, or filenames that start with a leading dot, '.' to make them hidden.

---

### Post by MrKlean on 2007-05-04
Thanks to a fellow Ububtu'er .. I use  " sudo gnome-search-tool" . I do a search on the filename I'm looking for... and highlight and delete.  BE CAREFUL... you can delete anything from here !!! But you should only find the locations of the filename you're looking for...DON'T MISPELL!!    LOL!!

---

### Post by use a name on 2007-05-04
In synaptic you can choose to remove completely. If you only remove, your settings will remain untouched in your home folder.

If you have your home folder on a separate partition and use it from another linux install, be careful, the package may still be installed in the other install, but missing its settings if you completely remove the package. The other way around: you only have to setup packages from one install and they'll work on both the same (if installed on both). Adding the same package to the other install later on will in most cases (all cases? anyone to confirm/defeat?) not overwrite your settings.

---

### Post by 3rdalbum on 2007-05-04
If you really want to know for sure that every last scrap of the program will leave, open Synaptic, search for the program, right-click it and go to Properties; then click on the Installed Files tab.

Copy and paste the list into a new text document. Now uninstall the program. Afterwards, you can check for yourself if all the files are gone (no need to worry about directories, only files). This can be done from the terminal; type "file " and then paste in the filepath, e.g.:

[CODE]file /usr/share/myprogram/prefs.conf
/usr/share/myprogram/prefs.conf: ERROR: cannot open `/etc/somethingnas' (No such file or directory)

---

### Post by 56seeker on 2007-05-05
Some great info here; thanks a lot! :)

---

