---
title: "[SOLVED] .text~ files?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
These files tend to show up after I save a file in gedit. They're not a bother on Ubuntu, but they're especially annoying whenever I burn a data CD and open it on a Windows machine. What function do they serve?

---

### Post by nonewmsgs on 2007-09-01
> **boiiinnnnnnnnnnnnnnnnggg said:**
> These files tend to show up after I save a file in gedit. They're not a bother on Ubuntu, but they're especially annoying whenever I burn a data CD and open it on a Windows machine. What function do they serve?

um what?

---

### Post by yabbadabbadont on 2007-09-01
They are the automatic backup that gedit makes everytime you save a file.  There is an option somewhere in the preferences to turn it off.

---

### Post by apetresc on 2007-09-01
Those are Gedit's (and vim's, and emac's, etc) swap files, for recovery and things. I believe Gedit has an option to disable them. Vim certainly does, it's ```
:set noswapfile
```

---

### Post by rsambuca on 2007-09-01
I think those are backups of a text file you edited.

EDIT:  I must be typing s l o w l y tonight.

---

### Post by yabbadabbadont on 2007-09-01
Too slow guys...  :D

---

### Post by CowzRule on 2007-09-01
Here's the option to turn it off

---

### Post by nonewmsgs on 2007-09-01
ok i guessed they were backup files but what's he talking about with the cd under windows?

---

### Post by apetresc on 2007-09-01
> **nonewmsgs said:**
> ok i guessed they were backup files but what's he talking about with the cd under windows?

By default, these ~ files are hidden under Linux, but not under Windows. So if you burn a CD containing a folder of text files in Linux, and you open it in Windows, you will suddenly see all the ~ files, which you normally wouldn't.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-02
If I were to suddenly shut off my computer while working on a .text file, would these files allow me to recover the data, and, if I disable them, would it prevent me from recovering?

---

### Post by apetresc on 2007-09-02
> **boiiinnnnnnnnnnnnnnnnggg said:**
> If I were to suddenly shut off my computer while working on a .text file, would these files allow me to recover the data, and, if I disable them, would it prevent me from recovering?

Yes, that's correct on both counts. It may be easier for you to just do a ```
 rm *~
``` before you burn a CD, to get rid of all of them, and let Gedit use them the rest of the time.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-02
Wow, I didn't know you could use wildcards with "rm"--thank you!

---

### Post by apetresc on 2007-09-02
> **boiiinnnnnnnnnnnnnnnnggg said:**
> Wow, I didn't know you could use wildcards with "rm"--thank you!

Wildcards are bash built-ins, they are evaluated by the shell before it ever gets passed to the command. In that sense, wildcards work with *anything*. (Or at least, anything that can take multiple files as command-line arguments)

Learn something new every day :)

---

### Post by dwhitney67 on 2007-09-02
If you use 'vi', then yes you could recover.  I am not sure about gedit and emacs, or whatever else is out there... heck, I've know s/w developers to use MS Word to write code; I wouldn't be half surprised if someone uses Open Office.

'vi' does not leave temp files lingering around like other editors.  The temp file is created during the 'vi' session, and if/when the vi session is terminated normally, then the temp file is automatically removed.

---

### Post by Celegorm on 2007-09-02
> **boiiinnnnnnnnnnnnnnnnggg said:**
> Wow, I didn't know you could use wildcards with "rm"--thank you!

Just a reminder- always be very careful using rm with wildcards, as rm deletes things permanently. A good trick I saw someone mention elsewhere is to try the command first with ls instead of rm just to make sure it's going to affect only the files you want it to and not erase something important on accident.

---

### Post by dwhitney67 on 2007-09-02
> **Celegorm said:**
> Just a reminder- always be very careful using rm with wildcards, as rm deletes things permanently. A good trick I saw someone mention elsewhere is to try the command first with ls instead of rm just to make sure it's going to affect only the files you want it to and not erase something important on accident.

Another easier trick is to alias the 'rm' command to always use the 'i' option.  In other words:

[FONT="Courier New"]alias rm='\rm -i'[/FONT]

Slap that into your ~/.bashrc file or other file that is sourced when you login.  Each attempt to remove a file will force the operator to confirm the action.

To avoid the hassle of these confirmations, one can apply the '-f' option:

[FONT="Courier New"]$ rm -f file[/FONT]

---

### Post by SPr on 2007-09-02
> **dwhitney67 said:**
> Another easier trick is to alias the 'rm' command to always use the 'i' option.  In other words:

[FONT="Courier New"]alias rm='\rm -i'[/FONT]

Slap that into your ~/.bashrc file or other file that is sourced when you login.  Each attempt to remove a file will force the operator to confirm the action.

To avoid the hassle of these confirmations, one can apply the '-f' option:

[FONT="Courier New"]$ rm -f file[/FONT]

Thanks for this excellent tip :) Works a treat. I'll still replace rm with ls first just to check but this is belt and braces. rm can be dangerous and needs treating with as much caution as possible.

---

### Post by Zootropo on 2007-09-02
Gedit should really have an option to select a directory to write all backup files too
[https://blueprints.launchpad.net/gedit/+spec/gedit-backup-directory](https://blueprints.launchpad.net/gedit/+spec/gedit-backup-directory)

---

