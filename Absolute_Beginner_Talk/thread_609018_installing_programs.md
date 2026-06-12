---
title: "installing programs"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Anti-thesisofreason on 2007-11-10
I recently downloaded a installer for a game dangerdeep-0.3.0-linux-installer.bin

I'm running Ubuntu 7.04.
My question is how do I install this program and where should I put it?

Thanks ahead of time!

---

### Post by matthewcraig on 2007-11-10
You probably want to stick to installing applications through the Synaptic package manager.  There are lots of applications there including games.  If you have to download and run a 3rd-party installer, then you risk your system with the code the developer gives you.  Therefore, work with that developer on how to install their application, but also encourage them to work with the Ubuntu community to add their package to Synaptic.

---

### Post by Maestro23 on 2007-11-10
Installing Software:
Installing Anything: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Psychocats Page: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

For a .bin (Make sure you are in the directory you downloaded the file to):

> sudo chmod +x filename.bin

./filename.bin

---

### Post by Anti-thesisofreason on 2007-11-12
Thanks guys' for your help. I tried each one of your solutions but to no avail. I know I'm doing something wrong with the chmod command. I'll figure it out eventually.

I know this thread hasn't been solved how do I mark it so no one needs to reply any longer???

Thanks!

---

### Post by Maestro23 on 2007-11-12
> **Anti-thesisofreason said:**
> Thanks guys' for your help. I tried each one of your solutions but to no avail. I know I'm doing something wrong with the chmod command. I'll figure it out eventually.

I know this thread hasn't been solved how do I mark it so no one needs to reply any longer???

Thanks!

Make sure you are spacing correctly in the command line.

Must be in the directory that you downloaded the file to. If it was your Desktop:

cd ~/Desktop


sudo (sp) chmod (sp) +x (sp) filename.bin

To mark this SOLVED, use the TRHEAD TOOLS.

*Remember linux is Case Sensitive.

---

