---
title: "Program will not launch"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by swoskow on 2007-07-23
I cannot launch one of the programs (gtkpod) from the Applications menu. It was working fine then I went to use it today and it will not launch. I can launch from terminal using sudo gtkpod. I did search the threads and found one that mentions launching from the terminal and reading output so I did and I got this message 

"Parse error reading prefs: London, England Segmentation fault (core dumped)". 

I searched but could not find anything I understood that could fix it. I did try uninstalling and reinstalling but the same thing happened. FYI - I am using Feisty and gtkpod aac. Any help is very appreciated.en

---

### Post by asmoore82 on 2007-07-23
move gtkpod's personalized settings to a backup location ...
open a terminal and ...

```
~$ cd
~$ mkdir .backups
~$ mv .*pod* .backups/
```

now when you run gtkpod again, it should be as if you've never used it before

(someone please correct me if my reg. ex. won't catch gtkpod's folder, more than likely it's '~/.gtkpod' )

---

### Post by swoskow on 2007-07-23
It worked - thanks so much.  As usual simple when you know what you are doing.  FYI - just in case anyone else has the problem and you are new to Ubuntu (I am fairly new but I know some of the idiosyncrasies of Ubuntu).  This method creates a backup file of your gtkpod settings in a file in the Home folder (not "your" home folder but "the" folder named Home).   The .backup folder (at least for me) cannot be viewed unless you mark show hidden files in the view menu.  When you do that you will see the folder and the files just in case you need them again.

Just out of curiosity why does this happen and how can I avoid it in the future?

Again, thanks so much for your help.

---

### Post by swoskow on 2007-07-23
"(someone please correct me if my reg. ex. won't catch gtkpod's folder, more than likely it's '~/.gtkpod' ) "

FYI - you are correct - the local folder is .gtkpod. (Again for newbies you have to mark "show hidden files" to view this.

---

### Post by asmoore82 on 2007-07-24
:guitar:rock on!

Either gtkpod exit-ed uncleanly and didn't save its settings right or there is some bug in gtkpod that causes it to trash its settings ...

but this situation is one of the reasons I can't stand Winders and Mac OS X  ... 
it's so beautiful when you know where and how software will go about saving its config data ... and NEVER in system folders!!!

*NIX ~ multiuser from the ground up and never looking back.

---

