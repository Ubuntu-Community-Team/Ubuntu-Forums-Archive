---
title: "How do I find &amp; install . . . . . . ."
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-30
I am very new to Ubuntu (and to Linux).  I am attempting to install my first program.  Coming from Windows I feel that the first program that I add should be an antivirus.  On another thread someone suggested "clamav".

I opened System > Administration > Synaptic Package Manager.
I searched for clamav on the list and did not find it.

Will Synaptic Package Manager search Web sources for software, or do I need to first locate the program on-line?  If it will search the Web for a program, how do I do so?  If I have to find the program on-line where do I download the program to once I find it?

Is clamav a good choice for antivirus?

Thank you.

babel .

---

### Post by mostwanted on 2006-04-30
You don't need anti-virus on Linux.

And try enabling extra repositories:

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

---

### Post by gingermark on 2006-04-30
AVG is a nice anti-virus - and has a guide here: [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php) should show you the different ways of installing software.

---

### Post by Nikusan on 2006-04-30
[QUOTE=babel]I am very new to Ubuntu (and to Linux).  I am attempting to install my first program.  Coming from Windows I feel that the first program that I add should be an antivirus.  On another thread someone suggested "clamav".

I opened System > Administration > Synaptic Package Manager.
I searched for clamav on the list and did not find it.

Will Synaptic Package Manager search Web sources for software, or do I need to first locate the program on-line?  If it will search the Web for a program, how do I do so?  If I have to find the program on-line where do I download the program to once I find it?

Is clamav a good choice for antivirus?

Thank you.

babel .[/QUOTE]

clamav is in universe
go to settings > repositories in synaptic and enable universe.
However, you probably don't need it ;)

---

### Post by babel on 2006-04-30
[QUOTE=mostwanted]You don't need anti-virus on Linux.

And try enabling extra repositories:

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)[/QUOTE]
Others have given me the same advice.
I will probably look for a different type of software to install.

Thanks for the information on other repositories.

babel .

---

### Post by babel on 2006-04-30
Thanks for the advice & links, gingermark & Nikusan.

---

### Post by AnRuaRi on 2006-04-30
Viri are not common on Linux systems.
this is for several reasons.

1 programs need explicit permission to run. & you must be Root to install anything. Viri therefore cant install themselves.

2 to date only 2 known viri have ever been written for Unix based systems

3 Most antivirus scanners search for Windows viruses. This is usefull on *NIX servers acting as web oe email servers. That's the main reason they exist.

It's more important to have a firewall.

---

