---
title: "First time linux'er : Mplayer install help"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by turkey on 2006-05-17
Ok i added multiverse etc and in the synaptic package manager i see mplayer and right click to mark for install.

It then says, those chosen action also affects other packages. the following changes are required in order to proceed. with a list of software to be installed, including libggi2, liblame0 and about 10 others. I click mark on that screen.

Then i get an error saying could not mark all packages for installation, the following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the prefrences.

Well they are all enabled? and theres nothing wrong with the net connection, can anyone help.

Oh by the way, this is the first time i have installed linux and this is the first piece of software i have ever tried to install

---

### Post by Nano Geek on 2006-05-17
In a command line, type```
sudo gedit /etc/apt/sources.list
```Enter your password, and make sure that all the lines where it says **deb** with a web address don't have a **#** and a space in front of them. After that save it and you should be able to install software.
By the way: Welcome to Ubuntu and the forums!=D>

---

### Post by khightower on 2006-05-17
Try adding the apps using System>Administration>Synaptic Package Manager.

This method sometimes helps with your problem.

---

### Post by louis_nichols on 2006-05-17
My experience was that GUI's aren't always the best way to do things. And especially when it comes to activating extra repos in synaptic this is true. Try these steps:

1. Backup the file we'll be editing, in case something goes wrong:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

2. Open it for editing as root:

sudo gedit /etc/apt/sources.list

3. Remove the character # in front of every line that starts witj deb or deb-src

4. Refresh in synaptic and try again

EDIT: completed the post. oops :)

---

### Post by turkey on 2006-05-17
man you guys are helpful, managed to get it working =D

but now that leads to another problem, how can i remove totem movie player from the system? if i remove it in the package manager it wants to remove loads of things with it!

or how do i set mplayer to be the default app for all video files

---

### Post by Nano Geek on 2006-05-17
You need to use Dapper Drake Beta to set your perferred video player.

---

### Post by turkey on 2006-05-17
could you be a bit more detailed with that, it may seem like 2nd language to you but im on another planet here!

---

### Post by Nano Geek on 2006-05-17
Sorry about that. Here's what I mean: Right now, the current version of Ubuntu is Ubuntu 5.10 (codenamed "Breezy Badger"), and they are also working on the next version, Ubuntu 6.06 (codenamed "Dapper Drake"). Ubuntu 5.10 comes with the GNOME desktop enviorment version 2.12, while 6.06 comes with Gnome 2.14 and the feture that allowes you to set your preferred media player is only in GNOME 2.14. I hope it's clearer to you now.

---

### Post by Nano Geek on 2006-05-18
Sorry, but I've checked around and there seem's to be no way to set another video player as your default. I'm going to keep looking for a way to uninstall Totem.

---

### Post by louis_nichols on 2006-05-18
[QUOTE=turkey]man you guys are helpful, managed to get it working =D

but now that leads to another problem, how can i remove totem movie player from the system? if i remove it in the package manager it wants to remove loads of things with it!

or how do i set mplayer to be the default app for all video files[/QUOTE]

In nautilus, just right-click on one avi file, select Properties from the menu, go to tab "open with" and choose your application of choice from there. You'll also have the option to add an executable, if the player you want to use isn't listed. Do this with one file for each extension you are interested in (mpeg, wmv etc)

I think the system reacts that way when you want to uninstall totem, because nauilus uses totem's engine to create thumbnails when listing directories with video files.

EDIT: I hope I understood correctly wht you meant by "default video player" and this is what you are looking to do.

EDIT2: I was wrong: nautilus doesn't need it, so uninstalling it is possible and quite safe. The only reason to keep it would be if, among those apps it says it needs to also remove alongside totem you see one you really need.

---

### Post by Nano Geek on 2006-05-18
I figured it out!!! Ok, to remove Totem type:```
sudo apt-get remove totem totem-xine
```Then enter your password, now open your file browser and right-click on one of your videos. On the menu, select: **Open With**>**Open with Other Application...**. When it shows a list of applications, click **Use a custom command** and type **mplayer**. Press enter, now any video you open should open in M-Player. Tell me if it works or not.

[Edit] Sorry louis nichols, I didn't see you post before I wrote this one.

---

