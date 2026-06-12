---
title: "Error to open file with vim!!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by jaywee on 2007-05-13
I set gvim as my preferred text editor,but when I left click a file to open with gvim, error comes across:
```
 Error detected while processing BufReadCmd Auto commands for "file://*";
E37:no write since last change 
```

but when I open gvim first, open a file as File-Open,everything is OK! 
wondering thing! hope someone could help me!!

---

### Post by jaywee on 2007-05-13
no one could help me ??

---

### Post by Metacarpal on 2007-05-13
I installed the vim-gnome package and tested this.  I received a similar error the first time I opened the file.

After closing gvim, I went into the directory the file was in (in this case, my home directory) and viewed hidden files with ctrl+h
This revealed the existence of a temp file for the script I had tried to open.  Check to see if you have one.  It'll start with a period and end with swp, such as:
.scriptname.sh.swp

I deleted the .swp file, and afterward gvim was able to open the regular file normally.  Give that a try.

Still, sounds like a bug in gvim.  If your problem persists, you should report the bug on bugs.ubuntu.com

---

### Post by jaywee on 2007-05-13
Thanks but still it doesn't work, maybe as your word, this is the bug of vim

---

### Post by shangouet on 2007-07-11
It seems that GVIM bugs when the filename is passed on command line as a URL :

$ gvim file:///home/shangouet/.bashrc

This produces the following :

Erreur détectée en traitant Autocommandes BufReadCmd pour "file://*" :
E37: Modifications non enregistrées (ajoutez ! pour passer outre) 

I tried to specify %F instead of %U in /home/shangouet/.local/share/applications/gvim-usercustom.desktop
but this is useless.

Finally, typing :e in vim after the error message allows us to edit the file normally,
but this problem is annoying.

---

