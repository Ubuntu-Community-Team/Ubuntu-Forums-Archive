---
title: "A Few questions"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by 3guk on 2005-10-17
Hi Guys,

Im brand new to linux understood windows XP pretty well but due to instability issues have decided I want to try linux.

Now i have a few programs I would like to install and azeurues being one of them, my question is what is the program files directory ? Is there a place where its best to put stuff ?

Also in the applications bar at the top I have under internet gaim listed twice as i updated the old version that was shipped with Ubuntu. Is there anyway to remove them as it does not seem as simple as right clicking.

ALso how come everything seems to be owned by root ? It seems I can not modify much as I have gone to make new folders adn I do not have the perms.

Can anyone explain a bit ?

Please :)

---

### Post by Ampersand on 2005-10-17
There isn't really a program files equivalent. The executables generally go to one of the bin folders (usr/bin, usr/share/bin &c). However, most programs can just be installed from the apt repositories using apt-get or synaptic. Make sure you've got the universe and multiverse repositories enabled and check to see whether the software you want is available there first. See this wiki page for more details: [https://wiki.ubuntu.com/SoftwareManagement](https://wiki.ubuntu.com/SoftwareManagement). Programs that aren't here may have to be compiled from source, and will be copied to the appropriate folders during the installation. I don't think you'll have to copy programs to other directories manually.

For menu editing, install Smeg (available in synaptic). You can also right click on the menu bar and go to 'edit menus'.

With regards to your last question, most of the folders outside the /home directory is owned by root. You can edit files from the terminal using 'sudo' before commands, you can also open a file manager with administrator priveleges using 'sudo nautilus'.

---

