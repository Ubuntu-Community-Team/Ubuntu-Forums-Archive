---
title: "Backup installed programs."
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-11-22
Is there a way to make a list of all the installed programs in synaptic, somehow turn that into a script that you could double click and allow a new install to install all those programs/dependencies or their equivalents?

---

### Post by overdrank on 2007-11-22
> **Trzone said:**
> Is there a way to make a list of all the installed programs in synaptic, somehow turn that into a script that you could double click and allow a new install to install all those programs/dependencies or their equivalents?

Hi if you go to synaptic manger and under file, generate package download script and then save the file. :)

---

### Post by Paul820 on 2007-11-22
AptOnCD: [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/") You can download it from the repos, i just put the link there so you can decide if that is what you are looking for.

---

### Post by Trzone on 2007-11-22
I was thinking more of the lines of, something i could save that in case i needed to reinstall, then it'd be able to restore me back to all my programs but this is interesting thanks

---

### Post by OffAxis on 2007-11-22
How about sbackup?
```
sudo apt-get install sbackup
```

It's more along the lines of traditional backup software, but works pretty well. It also has a gui interface.

---

### Post by Trzone on 2007-11-23
Hmm, what's the command or the gui for sbackup?

---

