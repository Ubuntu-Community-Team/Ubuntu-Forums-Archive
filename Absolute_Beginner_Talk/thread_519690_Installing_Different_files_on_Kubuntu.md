---
title: "Installing Different files on Kubuntu"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by FireStorm102389 on 2007-08-07
Ok, well, I guess I can't really get to know linux if I don't ask important and useful questions about specifics on where I am having problems...so here goes...

Kubuntu 7.04 is the version I installed on my computer. I recently had lots of trouble trying to install things, untill I stated looking at things from a slightly different angle, because I was under the impression that U had to manually do everything in a terminal and there was no install...but im over that now...now the question is how do I get different files other than .deb files to show up for installation?...Kubuntu has no problem recognizing and installing . deb files, but when it comes to the other files there is no install option and it doesn't show up into any of the lists in adept manager.

.gz, .bz2, .rpm

and im sure there is another cuz it feels like im missing one, but either way...it doesn't give me an installl option and I was wondering how I would go about installing them if they don't show up in the adept manager or add/remove programs?...unless there is something im oing wrong or forgetting to do to make them shw up...PLZ some HELP me

I just want to know how to install them, and I really wanna know how to install a game called [Boson]("http://www.kde-apps.org/content/show.php/Boson?content=28633")

---

### Post by Inxsible on 2007-08-07
you can install rpm files by using alien to first convert them to .deb and then simply double clicking the new .deb file.

The tar.gz or tar.bz2 mostly have a three step process:

```
tar -xvzf *filename*
```Navigate to the extracted folder, then
```
make
sudo make install
``````
./configure
```

---

### Post by LaRoza on 2007-08-07
The first two formats are archives, like .zip, so you'll have to uncompress them to install.

The third format is an rpm, which would need to be converted to a deb. 

Most times, the site has instructions on installing an app, or the file has a READ_ME which explains it.

---

### Post by Nythain on 2007-08-07
ubuntu is debian based, wich is why it installs debs
rpm's can be converted to deb with software (above mentioned alien)
and things contained in a .gz or bz2 or any other zip compressed file are usually source code installations involving that newbie intimidating terminal method that scares so many away from linux

---

### Post by AlexenderReez on 2007-08-07
hm...deb is software package that already has been compiled to be installer in** deb**ian branches distributions....ubuntu/kubuntu is part if it...


tar.gz and tar.bz2 is software packages that provided by developers and you need manually compile it :)...most of the software you just need > ./configure && make && sudo make install

but it also depends on the dependency ...and how developer created it....so be sure to check its README text:)...for game i think it is obviously has difference installation steps as it is not a software but a game :)


i do believe you can get deb packages for that game...check out :---->


> [http://www.filewatcher.com/m/boson-base_0.9.1-3_i386.deb.2654004.0.0.html](http://www.filewatcher.com/m/boson-base_0.9.1-3_i386.deb.2654004.0.0.html)


and 

for other games -->

> [http://dir.filewatcher.com/d/Debian/m68k/games.0.0.htm](http://dir.filewatcher.com/d/Debian/m68k/games.0.0.htm)


to install deb package just double click it **after **install deb package installer

---

### Post by nichipet on 2007-08-07
Off-hand, anyone know of a GUI program that will handle compressed files and fully install them, at least if they follow the three-step process? Seems if it's just a few shell commands, it shouldn't be hard to put that in a GUI.

If there isn't one, anyone have a link to a tutorial for creating a GUI? I'll go ahead and look into creating the program if it doesn't exist.

---

### Post by Inxsible on 2007-08-07
> **nichipet said:**
> Off-hand, anyone know of a GUI program that will handle compressed files and fully install them, at least if they follow the three-step process? Seems if it's just a few shell commands, it shouldn't be hard to put that in a GUI.

If there isn't one, anyone have a link to a tutorial for creating a GUI? I'll go ahead and look into creating the program if it doesn't exist.
You could always create a shell script and simply double click it and supply the filename to the shell script as input. 

Trouble is, like it was noted earlier by AlexanderReez, that not all tar.gz and tar.bz2 have the same installation process and they sometimes differ depending upon the developer who has packaged it. So you cant really have a universal GUI for it.

---

### Post by ravenwere on 2007-08-07
As for boson - in the terminal type
```
sudo apt-get install boson
```

Boson is in the ubuntu repositories -not sure which one.
r

---

### Post by LaRoza on 2007-08-07
> **nichipet said:**
> Off-hand, anyone know of a GUI program that will handle compressed files and fully install them, at least if they follow the three-step process? Seems if it's just a few shell commands, it shouldn't be hard to put that in a GUI.

If there isn't one, anyone have a link to a tutorial for creating a GUI? I'll go ahead and look into creating the program if it doesn't exist.

7-Zip is a very good archive manage, it also has a Windows version. 

Installing varies from program to program, so there cannot be a universal method.

Creating a GUI? In what language?

---

### Post by Hospadar on 2007-08-07
for rpm files, you'll need to convert them to .deb's.  try doing a ```
man alien
``` for some info on how to use it.  you may need to install it (i'm not sure if it's in the default install) ```
sudo apt-get install alien
```  There are probably some gui tools to do this sort of conversion as well, but I'm not sure what they are, I'm pretty sure I can just double-click rpm's and it will convert them for me in gnome, I'm sure there is something similiar that will work for kde, maybe automatix?

After you convert it to a deb you should be able to install it the traditional route.

---

