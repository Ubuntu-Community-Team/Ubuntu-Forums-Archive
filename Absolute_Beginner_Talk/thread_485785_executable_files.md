---
title: "executable files"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-06-27
Hi,

I have a C program, when I compile the program executable file is generated. I attached this executable file to my email and downloaded it to a separate location on my computer.I tried running this file and I get a warning cannot open the file. I tried opening it using sudo command also but it does not work.

Can somebody help me on how to run executables ??


thanks

---

### Post by Seisen on 2007-06-27
What is the extension at the end of the file?

---

### Post by bluezapper on 2007-06-27
there is no extension, but in the properties it shows as executable file.

---

### Post by Nekiruhs on 2007-06-27
> **bluezapper said:**
> there is no extension, but in the properties it shows as executable file.
Does it have executable permissions? Try ```
chmod +x /path/to/file

```

---

### Post by bluezapper on 2007-06-27
nothing happens when I execute that command. It return me back to the command line without any output.

---

### Post by bluezapper on 2007-06-27
chmod u+rwx filename solved my problem. thanks.

---

