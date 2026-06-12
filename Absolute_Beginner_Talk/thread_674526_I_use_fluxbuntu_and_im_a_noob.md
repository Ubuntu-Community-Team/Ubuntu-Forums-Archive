---
title: "I use fluxbuntu and im a noob"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Draken2910 on 2008-01-21
I have recently picked up on this thing called ubuntu because of my friend. My being totally new at decided to check it out i was like hey pretty cool OS. Unfortunatly for me it didn work the grub would not work correctly. So I moved on come to realize that there is still hope. I got my self into fluxbuntu. Those that are familiar with it i need you help. I need to know how to install .deb files. When I double click a .deb file this comes up (No run action specified for files of this type (application/x-deb) - you can set a run action by choosing `Set Run Action' from the File menu, or you can just drag the file to an application.) So any input would be awesome. Then I come across my next problem. Im looking in the repositories section on Fluxbuntu and im lost im wondering weither or not there is a way to make it look like ubuntus repositories section. Because I dont know how to change the sources, so i cant download anything :confused: please help me.

---

### Post by sumguy231 on 2008-01-21
You can install .deb files from the command line like so:
```
sudo dpkg -i packagename.deb
```
Ubuntu uses a utility called Gdebi for installing .deb files so you could install that and then tell whatever file manager you're using to open .deb files with it.

I don't know what package manager Fluxbuntu uses but you can edit the file /etc/apt/sources.list to add/remove repositories. You will need to edit it with admin privileges.

---

### Post by CupofDice on 2008-01-21
To edit your sources.list, type in the terminal

sudo gedit /etc/apt/sources.list.

Remove the # sign from the beginning of the urls that start with " deb [http://soonsoon](http://soonsoon) "
Do not remove the # sign from the instructions.

Or you can type " sudo synaptic" in the terminal, and go to settings/repositories to check the repositories (though I seem to be missing them in synaptic). 

If you have a deb called " comix.deb " , the command would be-

sudo dpkg -i comix.deb

Make sure you are in the same folder as the deb. Us the "cd" command to move around. To remove it use- 

sudo apt-get remove comix.deb

You can also edit your right click menu in ~/.fluxbox with the menu file in ~/.fluxbox/menu as in

gedit ~/.fluxbox/menu.

The fluxbox config files are pretty easy to understand.

---

### Post by Draken2910 on 2008-01-21
i tryed the sudo but it gave me this error (Status Database Area is Locked by another Process). I just need to know how to make my .deb files extract, my friend that uses ubuntu has already figured out a program or something for it now all he has to do is double click on the file and it installs perfectly

The sources i have figured out how to use now.

---

### Post by Draken2910 on 2008-01-21
i have figured it out thank you all great community love it:lolflag:

---

