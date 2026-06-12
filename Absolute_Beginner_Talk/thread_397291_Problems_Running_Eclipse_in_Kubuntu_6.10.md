---
title: "Problems Running Eclipse in Kubuntu 6.10"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Nathan Malone on 2007-03-30
I am running Kubuntu 6.10, and tried to install Eclipse using the Adept Manager with the following packages (I intend to use the PDT plugin to develop PHP code in):

[LIST]
[*]eclipse
[*]eclipse-cdt
[*]eclipse-jdt
[*]eclipse-pde
[*]eclipse-platform
[*]eclipse-rcp
[*]eclipse-source
[/LIST]

It apparently installed correctly, and I can see the entry in Start > Development > Eclipse , but when I click on it, the "loading" icon appears in the bottom bar for 30 seconds, then it goes away, and nothing else happens. I'm not sure how to access any error messages via the command line that it may be generating, so I don't know how to get any additional information to help debug this, but this is a Kubuntu 6.10 installation.

I'm not sure if it matters, but I have the sun-java6-bin and sun-java6-jre packages installed.

Any help would be appreciated!

---

### Post by Nathan Malone on 2007-03-30
After doing some research, it appears that this bug has been documented at [https://launchpad.net/ubuntu/+source/eclipse/+bug/68385](https://launchpad.net/ubuntu/+source/eclipse/+bug/68385)

There is a fix there that involves editing the /usr/bin/eclipse file, and I am able to find the file, but I am not able to figure out how to edit it. In the past, I have been able to Right Click > Edit as Root those "root-only" files, but that link is not in the drop-down menu for this file, for some reason. Is there some other way I can edit the file?

---

### Post by Maestro23 on 2007-03-30
Open a terminal and use a text editor. Some examples:

> sudo kedit

sudo nano

sudo gedit


---

### Post by Nathan Malone on 2007-03-30
Thank you, that worked!

For future reference, if you use Kubuntu 6.10 (perhaps prior versions, as well), and are installing Eclipse, you might have to follow the instructions in the post at [https://launchpad.net/ubuntu/+source/eclipse/+bug/68385](https://launchpad.net/ubuntu/+source/eclipse/+bug/68385) to get it running. It should work without that patch in Feisty Fawn, though.

---

