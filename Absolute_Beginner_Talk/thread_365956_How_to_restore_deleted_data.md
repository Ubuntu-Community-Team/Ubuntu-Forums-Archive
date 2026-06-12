---
title: "How to restore deleted data"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rodrigo666 on 2007-02-20
Greetings,

okay, here is the deal, someone of my family accidentally deleted my "themes" directory where I used to store and save all of my wallpapers, icons ant GTK themes. Well I really want that stuff back, since some of my wallpapers will be extremely hard to find again.

So, in Windows, I know a couple of software that restore deleted data even if they are not in the trash, but in Ubuntu/Linux, I don't know any, can someone help me out?

Plus, there is some way I can protect all my directories with "read-only" permission to another users?

Thanks in advance.

---

### Post by Tomosaur on 2007-02-20
It depends on how it was deleted. If they used the 'rm' command - you may as well just give up now. If, however - they deleted it through the GUI, then it may still be hanging around in the Trash can.

Yes - you can protect your files. If you want to do it through the GUI, then just open up the directory where the file/folder is, select properties, then permissions, and just set it to whatever permissions you want.

If you want to do it through the command line - then open up the terminal, and type:
```

chmod 700 /path/to/my/file

```

This will stop anyone but you reading, writing, or executing that file. You can also hide files by renaming it so it has a . in front, for example:
my_file.txt : not hidden
.my_file.txt : hidden

---

### Post by rodrigo666 on 2007-02-20
These are not good news, but thanks.

I believe the one who deleted my directory used "shift + delete" in it.

Thanks for your patience.

---

### Post by Tomosaur on 2007-02-20
Hmm, never used that method before. If they did it from their own log in, then just check their Trash can to see if it's there. If they did it on your username, then check your own trash. There may well be recovery software available, but I don't know of anything reliable.

---

### Post by fidolip on 2007-02-20
Try here:

[http://applications.linux.com/applications/06/10/30/1652211.shtml?tid=47](http://applications.linux.com/applications/06/10/30/1652211.shtml?tid=47)

---

