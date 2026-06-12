---
title: "How do we install .tar.gz/.rpm archive appz in ubtuntu ?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by rajeshgovindan on 2006-09-16
How do we install .tar.gz/.rpm archive appz in ubtuntu ? Pleae tell in detail(coz am a super n00b)

Thanx in adavnce

---

### Post by deadgobby on 2006-09-16
First check Synaptic first to see if the program you wish is there. Here is a couple of links to book mark.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
 Very easy step by step intructions on installing from source.
Gobby

---

### Post by mixmaster on 2006-09-16
To install a tar.gz archive, you need to unpack it with tar.

The command tar -xzvf <archive-name> will unpack it.  However, you need to know where to put it and that information should be provided with the archive.

To install an .rpm you an either use the alien command to convert it into a deb and then install it as normal, or you can install the rpm directly using the rpm package manager.  Both alien and rpm can be downloaded and installed using the synpatic package manager (from the System->administration menu).

Using the rpm package manager directly is easier but it may complain about missing dependencies.  I believe the option --nodep will bypass this checking (I don't have it installed on this machine to check).  Using alien will keep the Ubuntu package manager happy but is not guaranteed to always work.  

It is difficult to give a detailed answer to this question as there are so many things that can happen when using packages not specifically prepared for Ubuntu.  If you are genuinely a complete noob I would stick to Ubuntu  stuff until you have a bit more experience, or ask about specific packages if there is something you have to have and it is not in the correct form.

---

### Post by 3rdalbum on 2006-09-16
Don't use the rpm command. If you must use an RPM file, convert it to a .deb first with alien.

---

### Post by Anduu on 2006-09-16
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

