---
title: "Theme Problem"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by uchihaitachi on 2008-03-04
I'm trying to install the Hardy Theme found here

[http://www.gnome-look.org/content/show.php?content=74045&forumpage=1&PHPSESSID=0391ed1b4a99dd2f08c995d3da62f1a4](http://www.gnome-look.org/content/show.php?content=74045&forumpage=1&PHPSESSID=0391ed1b4a99dd2f08c995d3da62f1a4)

However I'm unable to get the GTK theme to show up in the appearance controls customize. What can be the problem?

---

### Post by jan quark on 2008-03-04
depending which desktop environment you use the installation is different

this I have taken from the read me file

> INSTALLATION:
[B]
	*GTk theme
Install this packages:
§ sudo aptitude install gtk2-engines-murrine
then copy "Hardy-Mariux" in your /home/.themes directory
Go in System -> Preferences -> Appearance->Customize then select "Hardy-Mariux" to choose this gtk theme.
If you want sudo apps to run with Hardy-Mariux theme, just copy as sudo the Hardy-Mariux directory in your usr/share/themes directory.[/B]

        *Icons + Firefox Theme
To install the icons there are 2 ways:
1)Install the Tangerine.tar.tgz with Appearance Manager (System -> Preferences -> Appearance).
or
2)In terminal, run 
§ sudo apt-get install tangerine-icon-theme. Then Select in Appearance.

For the Firefox theme, run in terminal 
§ sudo apt-get install firefox-themes-ubuntu
then open Firefox->Tools->Add-ons then select Tangerine theme, then restart Firefox.

	*Wallpaper
Make a right clic on your Desktop, and enter in the menu "change your wallpaper", then search for the directory where you untarred Hardy-Mariux.

        *Emerald
Just double click on the file.

        *GDM Theme
Open System->Administration->Login Window
Go to "Local", clic Add, then select the tar.gz file, OK, then select Mariux Glossy Hardy.


	*Compiz Fusion Settings
Just open "Advanced Desktop Effects Settings"-> Preferences-> Profile-> Import 
then select "Mariux.profile" into the Hardy-Mariux/Compiz Fusion Settings directory

        *conky Theme
first install conky with
§ sudo apt-get install conky
then copy ".conkyrc" in your /home directory.
to make conky start, click Alt+F2 then execute the command "conky".
If you want conky to start on startup, just open System->Preferencies->Session then add a new startup program with "conky" in command.

        *Skydome
Open Advanced Desktop Effects Settings->Cube Desktop-> Appearance->Skydome then select the carina4.jpg file.

try the first installation option

---

### Post by sayakb on 2008-03-04
@OP
Looks like the theme has been removed..

---

### Post by uchihaitachi on 2008-03-04
I did try the first option.
No issues with installing the engine however the theme just doesn't appear in controls listing.

No issues with the icons or the GDM.

The theme was not removed when I last checked, the author is just hosting the file at deviantart instead.

---

### Post by sayakb on 2008-03-04
> **uchihaitachi said:**
> I did try the first option.
No issues with installing the engine however the theme just doesn't appear in controls listing.

No issues with the icons or the GDM.

The theme was not removed when I last checked, the author is just hosting the file at deviantart instead.

Please provide the deviantArt link when the author uploads it..

---

### Post by uchihaitachi on 2008-03-04
[http://www.deviantart.com/download/75628261/Hardy_Theme_by_MariuxV.gz](http://www.deviantart.com/download/75628261/Hardy_Theme_by_MariuxV.gz)

---

### Post by Stu09 on 2008-03-06
woops... edit

---

