---
title: "Extracting .run extensions"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Efrum on 2006-12-14
G'day.

just installed ubuntu and found out about .run extensions. it was a video driver. questions is what do i do?

cheers,
Efrum

---

### Post by Bachstelze on 2006-12-14
Those .run files are most often shell scripts, run them with

```
sh /path/to/file.run
```

you will need superuser rights to install driver so add *sudo* before ;)

---

### Post by po0f on 2006-12-14
Efrum,

There are video drivers available in the repos, depending on what card you need drivers for.  And to directly answer your question:
```
[FONT="Courier New"]$ sudo bash /path/to/file.run[/FONT]
```

---

### Post by Efrum on 2006-12-14
NVIDIA-Linux-x86-1.0-9629-pkg1.run is the name of the file i want to run. its in directory home/user/downloads.

can someone help me further please?

cheers,
Efrum

---

### Post by po0f on 2006-12-14
Efrum,

If you don't know how to execute a run file, you really don't want to manually install your video drivers.

Search the forums, users have set up repos with more up-to-date binary drivers for NVIDIA cards.

---

