---
title: "installing 4 ubuntu desktops"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-08-05
i want to use 3 desktops that are supported by ubuntu
i-e gnome,kubuntu, and edubuntu

i have cd of gnome and i khave requested kubuntu and edubuntu cds.
i know i can install kubuntu and edubuntu desktops from internet using gnome desktop.but what if i have three cds of all desktops ,can i install them in a single partition with 3 or 4 GB of size?can i do that?if yes then how? .that is i have only one linux with 3 desktops.

---

### Post by reacocard on 2006-08-05
no need to use the cds. everything you need is in the repos. for KDE:
```
sudo apt-get install kubuntu-desktop
```
for XFCE:
```
sudo apt-get install xubuntu-desktop
```

---

### Post by u04f061 on 2006-08-05
> **reacocard said:**
> no need to use the cds. everything you need is in the repos. for KDE:
```
sudo apt-get install kubuntu-desktop
```
for XFCE:
```
sudo apt-get install xubuntu-desktop
```

my dear i have mestioned in my post that i know i can install them from repository and i can't do this because my proxy server is blocking files having extentions tar.gz and files with large size. that is why i started this thread to know about ?

---

### Post by sapo on 2006-08-05
yes you can.

You just have to mount the cd and add the cd as a repository in the sources.list or synaptic.

After that just type:

sudo apt-get install whatever-desktop

---

### Post by u04f061 on 2006-08-05
> **sapo said:**
> yes you can.

You just have to mount the cd and add the cd as a repository in the sources.list or synaptic.

After that just type:

sudo apt-get install whatever-desktop

i don't know how to mount or add cd to repository.plz tell me about this.

thanks for your nice reply

---

### Post by sapo on 2006-08-05
Its very easy, just open the Synaptic Package manager its on the Administration menu.

then you click on Settings -> repositories -> Add CDROM

The cdrom will be mounted when you insert it in the drive.. so dont mind about it ;)

---

### Post by u04f061 on 2006-08-05
isn't there any way of doing this using command line because i use command line normally.however your reply has solved my trouble.
thanks

---

### Post by ColdDeath on 2006-08-05
You can just add a cdrom repository to the list manually, but the GUI makes it easier.

---

### Post by u04f061 on 2006-08-05
> **ColdDeath said:**
> You can just add a cdrom repository to the list manually, but the GUI makes it easier.

what should i write in sources.list file?just i should type cdrome or something else.plz mention

---

### Post by Jagot on 2006-08-05
> **u04f061 said:**
> isn't there any way of doing this using command line because i use command line normally.

With the CD in the drive:

```
sudo apt-cdrom add
```

Then you'll need to update.

---

