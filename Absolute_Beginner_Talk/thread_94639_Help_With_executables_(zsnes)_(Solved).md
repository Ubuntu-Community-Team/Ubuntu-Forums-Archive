---
title: "Help With executables (zsnes) (Solved)"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Sonic5688 on 2005-11-24
Hello. I'm very new (2 days) to Linux of any form and I was wondering how to use the executable files? I select to open them in a terminal, but the terminal pops up for a second then goes away and nothing else happens. What am I doing wrong? Thanks in advance, and have a happy Thanksgiving. :???:

---

### Post by steve.horsley on 2005-11-24
What kind of executable file are you having trouble with? A short-lived stript will open and closr the console vey quickly.

---

### Post by Sonic5688 on 2005-11-25
Well, I'm trying to get ZSNES, the SNES emulator, to run on Linux, but i have no idea how to do so.:confused:

---

### Post by Specialsauce on 2005-11-25
[QUOTE=Sonic5688]Well, I'm trying to get ZSNES, the SNES emulator, to run on Linux, but i have no idea how to do so.:confused:[/QUOTE]
if it is in .deb format, typpe 'sudo dpkg -i [name od .deb].deb' tp run it. if it is rpm or another package type, go to synaptic package manager, find 'alien' on the list, install it, and then use alien to convert the package you have to a .deb..... i think thats what you wanna know

---

### Post by aysiu on 2005-11-25
[QUOTE=Sonic5688]Well, I'm trying to get ZSNES, the SNES emulator, to run on Linux, but i have no idea how to do so.:confused:[/QUOTE] Forget about whatever you were trying to do before. If you downloaded something, just throw it in the trash--delete it.

Open up a terminal. 
In Hoary: Applications > System Tools > Terminal
In Breezy: Applications > Accesories > Terminal

Follow the directions in the first link in my sig.

Then type this in a terminal: ```
sudo apt-get update
sudo apt-get install zsnes
```

Then, it'll be installed. Once it's installed, find the .ROM files that you have for your Nintendo games, right-click them and select Properties, go to Open With, and add the command *zsnes* to the list of applications. Make sure it has a black circle next to it (not an empty circle).

---

### Post by Sonic5688 on 2005-11-25
You guys are going to beat me, but how do I know what the package is? What are package extensions? I'm terribly sorry for not knowing much before diving into Linux. Also, what kind of Linux is Ubuntu? I've seen stuff like Redhat, SuSE, and Mandrake, so what is Ubuntu?

---

### Post by sjh on 2005-11-25
[QUOTE=Sonic5688]You guys are going to beat me, but how do I know what the package is? What are package extensions? I'm terribly sorry for not knowing much before diving into Linux. Also, what kind of Linux is Ubuntu? I've seen stuff like Redhat, SuSE, and Mandrake, so what is Ubuntu?[/QUOTE]

Ubuntu is based on the Debian distribution.  I use Synaptic Package Manager to check package information.  It is the Gnome front end for the apt-get utility.  Highlighting a package in Synaptic gives a brief description of the package.  Aysiu's has links in his signature on repositories and installing software with Synaptic that can explain it better than I can.  Hope this will help.

SJH

---

### Post by almahtar on 2005-11-25
Ubuntu is a variant of Debian.  It isn't Mandrake, Redhat, Slackware, Fedora, BSD, etc... it's pretty much its own animal.  It's a heavily modified variant of Debian.

---

### Post by aysiu on 2005-11-25
[QUOTE=Sonic5688]You guys are going to beat me, but how do I know what the package is? What are package extensions? I'm terribly sorry for not knowing much before diving into Linux. Also, what kind of Linux is Ubuntu? I've seen stuff like Redhat, SuSE, and Mandrake, so what is Ubuntu?[/QUOTE] I'm glad people have answered your questions so quickly, but what do they have to do with your original question regarding zsnes? Did you get it working?

---

### Post by Sonic5688 on 2005-11-26
Yes, thank you so much. I've never been to a forum where I didn't get flammed for being ignorant of the object that the forums revolved around :) . Anyways, I'll definitly be hanging around these forums. Thanks for solving my problem, and thanks for answering my questions!

---

### Post by aysiu on 2005-11-26
[QUOTE=Sonic5688]Yes, thank you so much. I've never been to a forum where I didn't get flammed for being ignorant of the object that the forums revolved around :) . Anyways, I'll definitly be hanging around these forums. Thanks for solving my problem, and thanks for answering my questions![/QUOTE] The friendliness and helpfulness in these forums is the main reason I'm using Ubuntu and not some other distro. Glad it's working for you.

---

