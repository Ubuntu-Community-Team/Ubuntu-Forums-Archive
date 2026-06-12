---
title: "avg scanning problem ?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-07-23
ok, so ive just had to re-install fiesty (i really should stop messing) and ive got to the point i want to install avg (i know i dont really need it) so i make sure all the dependacies are met and go ahead with the installation, which goes fine.
but when i came to running a scan nothing happened, that is to say that when i click test nothing happens, no window opens no nothing :confused: now ive always installed avg the same way and this is the first time it didnt work.
cheers in advance for any help.

---

### Post by gn2 on 2007-07-23
More trouble than it's worth, get rid of it.

Relax, breathe deeply and repeat after me: 

Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 


Aaaahhhhh that's better now isn't it?

---

### Post by techno-mole on 2007-07-23
agreed linus isnt windows, but i do have it networked with 2 other pc's that are running windows.
the points was not that i dont need an avg for ubuntu, the pont was more what has gone wrong ? why out of the other times ive installed it did it not install correctly ?
i have worked out though that it is actually working, that is to say i can run commands from terminal, as in avgscan and so on, its the gui thats not installed correctly, strange.
cheers.

this is the output frm terminal when i try to run a test using the avg gui.

```

avggui: /opt/grisoft/avggui/prog/messagebox.py:25: WARNING: License type is FREE.
Traceback (most recent call last):
  File "/opt/grisoft/avggui/prog/mainview.py", line 175, in __test_item_run_cb
    select_window = select.CSelect()
  File "/opt/grisoft/avggui/prog/select.py", line 23, in __init__
    self.__select_view = fsh.CView([os.path.expanduser("~")], False, True)
  File "/opt/grisoft/avggui/prog/fsh.py", line 744, in __init__
    self.model = CStore(pathnames, selected, expand, w_message)
  File "/opt/grisoft/avggui/prog/fsh.py", line 349, in __init__
    self.add_pathname(pathname, selected, expand, w_message)
  File "/opt/grisoft/avggui/prog/fsh.py", line 568, in add_pathname
    self.expand(self.get_iter_root())
  File "/opt/grisoft/avggui/prog/fsh.py", line 419, in expand
    entries = self.dir_entries.get_entries(pathname) 
  File "/opt/grisoft/avggui/prog/fsh.py", line 145, in get_entries
    self.__logger.warn(detail)
  File "/opt/grisoft/avggui/prog/logger.py", line 125, in warn
    self.__log(WARN, format, args)
  File "/opt/grisoft/avggui/prog/logger.py", line 85, in __log
    msg = format.encode(sysinfo.CLocaleInfo().get_value('console_encoding'))
AttributeError: 'exceptions.OSError' object has no attribute 'encode'

```

---

### Post by gn2 on 2007-07-23
Surely the Windows boxes should protect themselves?

---

### Post by por100pre1 on 2007-07-23
> **techno-mole said:**
> ok, so ive just had to re-install fiesty (i really should stop messing) and ive got to the point i want to install avg (i know i dont really need it) so i make sure all the dependacies are met and go ahead with the installation, which goes fine.
but when i came to running a scan nothing happened, that is to say that when i click test nothing happens, no window opens no nothing :confused: now ive always installed avg the same way and this is the first time it didnt work.
cheers in advance for any help.

AVG for Debian is not working well. Uninstall it and use avast! or F-Prot with [XFProt]("http://web.tiscali.it/sharp/xfprot/") instead. It's not a bad idea to check your files for viruses.

---

### Post by A*p on 2007-07-23
> **gn2 said:**
> More trouble than it's worth, get rid of it.

Relax, breathe deeply and repeat after me: 

Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 
Linux isn't Windows 


Aaaahhhhh that's better now isn't it?

I second that.

Numerous installs, numerous distro's, over past 5 years with 0 virus scanners, 0 viruses, visiting the occasional dodgey site ;) resulting in 0 problems and near perfect uptime, damn them power cuts :mad:

Just get into the habit of backups, set a cron job today :)

---

### Post by techno-mole on 2007-07-23
interesting, maybe its something with one of the updates ? ive never had trouble until today, and you would have thought that a clean install would be ok.
the windows pc's do protect themselves, but there have been reports of people running wine who have managed to also get windows viruses to run under wine, so i thought id protect my system, and also it stops me sending a virus over to one of the windows systems with out knowing it.
still its a puzzle why all of a sudden it doesnt want to work.
cheers
ps - i back everything up twice, once on an external drive and then again onto cd/dvd disc.

---

### Post by por100pre1 on 2007-07-23
> **techno-mole said:**
>  ...and also it stops me sending a virus over to one of the windows systems with out knowing it. 

I agree with you. **The fact that your Linux system is harder to break, doesn't mean it has to be a cesspool for Windows viruses.**

---

### Post by asmoore82 on 2007-07-23
_ANYONE_ who would write AntiVirus for Linux does _NOT_ understand Linux enough to write _ANYTHING_ for it.

and yet some may wonder why the AV for Linux does not work correctly ... :lolflag:

---

