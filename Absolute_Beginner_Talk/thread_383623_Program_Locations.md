---
title: "Program Locations?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-13
Where are programs installed on Linux? Is there a specific folder, like Program Files on Windows? And how do I tell which program is which?

---

### Post by lamalex on 2007-03-13
they are not stored per se in any one spot. the binary for the program is in a /bin folder, configurations and other things are often in /etc or /opt. Really depends on the program.

---

### Post by 23meg on 2007-03-13
To figure out where files from a certain package are installed, right click the package in Synaptic, click "Properties" and go to the "Installed Files" tab.

The executable binaries usually go to /usr/bin or /usr/local/bin. The rest of the required files are scattered all over the filesystem.

---

### Post by jabeez on 2007-03-13
usually in /usr/bin, and the name is usually the name of the program, but look in /usr/bin for a similar name and type it into a terminal and it should run.

---

### Post by 23meg on 2007-03-13
> **Iamalex said:**
> they are not stored per se in any one spot. the binary for the program is in a /bin folder, configurations and other things are often in /etc or /opt. Really depends on the program.

New programs are almost never installed in /bin. It's reserved for the shell and basic set of system commands that can be needed to rescue the system.

---

