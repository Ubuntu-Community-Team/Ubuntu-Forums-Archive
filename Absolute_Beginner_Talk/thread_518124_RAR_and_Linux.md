---
title: "RAR and Linux"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by CrashintoDMB on 2007-08-05
I'm looking for a program that will unpack .rar files. I'm not sure what programs on the internet are decent programs.

---

### Post by Tomosaur on 2007-08-05
> **CrashintoDMB said:**
> I'm looking for a program that will unpack .rar files. I'm not sure what programs on the internet are decent programs.

Open up the Synaptic Package Manager and search for '.rar'. You should find various programs to do what you need.

---

### Post by Majorix on 2007-08-05
```
sudo apt-get install rar
```
```
sudo apt-get install unrar
```

They will do the job for you. You can then right click a rar file and say "extract here".

Welcome to Ubuntu!

---

### Post by CrashintoDMB on 2007-08-05
after i get it from the package manager is there a code i need to enter to get it working?

---

### Post by Majorix on 2007-08-05
No they work automatically. Just install them using the code I typed in.

---

### Post by Tomosaur on 2007-08-05
> **CrashintoDMB said:**
> after i get it from the package manager is there a code i need to enter to get it working?

Those commands will set up and install the software so you don't need to do anything else. You should just be able to open the .rar file through the GUI like you would any other file.

If the option to extract the file doesn't come up, then you should be able to extract the file through the command line. Open up a terminal and type 'man unrar' to learn how to do so.

---

### Post by sailor.nir on 2007-08-08
I installed rar and unrar and can now work with them.
The web page says registration is needed after 40 days. It mostly talks about WinRAR, though, and only mentions rar a couple times. Does the linux pkg require registration or payment?
Also, I'm wondering about the p7zip-full package. The description in Synaptic says it inlcludes rar format, but I had it installed before the rar package and file-roller still couldn't said about rar files that "format is not supported". What gives?

---

