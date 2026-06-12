---
title: "java runtime enviroment install to play yahoo games"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by jwftm33 on 2008-03-13
I need help install java on feisty fawn 7.04. I have have tried to run a terminal command and i am asked to put cd labeled feisty fawn 7.04 in the cdrom, which i do but the system doesn't see the cd.   I would appreciated any adive to get this working.

---

### Post by taurus on 2008-03-13
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.

Then run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by {BzF}~JOKesTER on 2008-03-13
Sure To Fix This Problem - Open Synaptic Package Manager {In Control Center}

And Click The "Settings" Tab At The Top And Select "Repositories" 

Now Click The "Ubuntu Software" Tab And Uncheck The Boxes Under "Installable From CDROM/DVD"

Now Hit "Close"

And In Synaptic Hit "Reload" {In The Top Left Corner}

Restart Your Computer And Run The Command To Install Java

Hope This Helps!!!!

If It Does Please Hit "Thank":):)

---

### Post by jwftm33 on 2008-03-13
Thank you Thank you worked. :KS:guitar:

---

