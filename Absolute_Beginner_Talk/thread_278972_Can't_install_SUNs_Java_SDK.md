---
title: "Can't install SUNs Java SDK"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by badam on 2006-10-17
Hello there

Is there anyone out there that has been able to install Sun's Java SDK?
I've been googling and found a couple of guides for this but they all require make-jpkg and other packages not available in the repository anymore.

Anyone got any ideas or maybe a link to a guide that acctually works?

---

### Post by deadgobby on 2006-10-17
I seem to find this in Synaptic. I did not install it, but check to see if you can find it there. It should solve depend probs.
Gobby

---

### Post by Tomosaur on 2006-10-17
I've got it and it works fine, here's how I did it:

Opened up Synaptic. Removed ALL java-related programs, including the JRE.
Go to Sun's JDK download page. Download JDK 5.0 Update 9.0 (get the one with netbeans if you want, but I don't like it). Get the self-extracting version (it's a .bin file).

Make the .bin file executable (chmod +x jdk*.bin)

Execute the file with sudo (sudo ./jdk*.bin)

Follow the on-screen instructions.

---

