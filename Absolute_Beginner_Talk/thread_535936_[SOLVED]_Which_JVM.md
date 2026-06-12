---
title: "[SOLVED] Which JVM?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-08-27
I'm a bit confused about the JVM to use for Ubuntu. I am under the impression that the official JVM cannot be used on any GNU/Linux systems. How do I go about getting a JVM? I can't find it in add/remove programs. Also, if there are more than 1 JVM available, which is the best to use?

---

### Post by steve.horsley on 2007-08-27
By default, an open source java VM is installed.However, it's not as fast as the Sun VMs, and some juava programs just don't work in it. 

The repositories contain both Sun java 5 and Sun java 6 VMs. I would suggest you go for version 6 myself. Start Synaptic (Systam->Administration->Synaptic) and search for **sun-java6-jre**. Mark this for installation and apply. You may also want sun-java6-plugin which is the plugin to firefox, I think.

---

