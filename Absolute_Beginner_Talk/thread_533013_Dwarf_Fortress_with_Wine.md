---
title: "Dwarf Fortress with Wine"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-23
According to the Dwarf Fortress [wiki]("http://dwarf.lendemaindeveille.com/index.php/Frequently_Asked_Questions"),  it's possible to play Dwarf Fortress with Wine.  I have Wine installed, and the Dwarf Fortress zip file, but I can't figure out how to make it work.

Anyone out there know how to get it working?

---

### Post by Mr. Svinlesha on 2007-08-23
Bump.

---

### Post by shnastybiznastic on 2007-10-29
Alright, you need to unzip the file (right click and select 'extract here'), then just launch it from the commandline ('wine <path_to_executable>/dwarfort.exe')

It works for me in Gutsy as of the moment, and under both feisty and edgy.

---

### Post by Chuckaluphagus on 2007-11-08
*Edit: I found the fix, I should have read through more Wine-related documentation first.  DF runs fine if I open a terminal, change directories to where I have DF installed and run  "wine dwarfort.exe" from that directory.*

> **shnastybiznastic said:**
>  
It works for me in Gutsy as of the moment, and under both feisty and edgy.

That's odd, it isn't for me.  When I run it via Wine, the program first asks me if I want to run in fullscreen mode.  Whether I choose yes or no, it then gives me a popup window with this error:

"FATAL ERROR:
Main index file missing/corrupted.  The file "index" must be in the "data" folder.  Make sure DF decompressed its folders properly."

I did check the data folder, it contains a file called index.

I haven't changed any of the default settings in Wine (haven't had to); is there something in particular that I should have set or turned off in order for Dwarf Fortress to run?

---

### Post by feydreva on 2007-11-21
Same issue here...

---

### Post by Caiburn on 2007-11-24
You need to start the .exe in the directory where it resides (else it cannot find the path to it's data files). If you do that, it works (I am generating a world while typing this). :)

Cheers,

Caiburn

---

### Post by mtalexan on 2007-11-29
I can definitively say that just working from a fresh install of the latest wine and the unzipped files in a folder in my home directory, running wine one the exe file manifestly does not work.  This is true regardless of where the command is run from and how the path is provided to dwarfort.exe 

As a rough guess, I'd say it seems to be a problem with finding the location of the index file.  I'm guessing either the default path through wine isn't set correctly on a default install, or the system path wine uses to attempt to find the file isn't set correctly.

---

### Post by mtalexan on 2007-11-29
Well after looking into the problem a little more thoroughly it appears it's a difference in how the dwarf fortress zip file was unzipped.  Apparently the users that got it to work immediately, unzipped using a method that automatically set the file permissions correctly for them, while those that didn't get it working had the permissions set too restrictive by default.

THE FIX:
Go to the folder you unzipped your files into and type the following line, keeping in mind that it's case sensitive.:
```
sudo chmod -R 777 ./*
```

This will set the permissions of all the files in the directory tree so that all users can access them.  Apparently the issue was a lack of ability to read the data file since the permissions were set to disallow read, write, and execute for anyone except root.  I'll post again with a cleaned up set of full installation instructions in a moment.

---

### Post by mtalexan on 2007-11-29
To Install Dwarf Fortress II: Siege of Amorak
-----------------------------------------------------------------
*1)* Go to the [Dwarf Fortress website]("http://www.bay12games.com/dwarves/index.html") and download the zip file to your desktop.

*2)* Go to the [Wine HQ website]("http://www.winehq.org/site/download-deb") and follow the instructions (copy and paste the commands into a terminal window) for installing wine.  

*3)* Decide what directory you want to put the game in.  Unless you know what you're doing, just put it in your home directory by typing these commands in your terminal window, replacing "dwarfort_game_zip_file.zip" with the name of the zip file you downloaded.
```
cd ~
sudo mkdir dwarfort
cd dwarfort
sudo unzip ./Desktop/dwarfort_game_zip_file.zip -d=.
sudo chmod -R 777 ./*
```Keep in mind that everything is case sensitive, and the first time you use the sudo command you'll likely have to enter your password to temporarily gain root privledges.

*4) *Run the game with the commands:
```
cd ~/dwarfort
wine dwarfort.exe
```
NOTE: I have yet to find a way to get the game to successfully run when calling wine outside the directory containing dwarfort.exe. My "fix" was to write a brief script (see the commands for running the game) that took care of the two commands for me.

To add the game to your program menu:
------------------------------------------------------------
*1)* ```
PATH=/usr/games:"{$PATH}"
sudo touch /usr/games/dwarfort
sudo chmod 755 /usr/games/dwarfort
sudo printf "cd ~/dwarfort\nwine dwarfort.exe\n" > /usr/games/dwarfort
```Looking at this set of commands briefly, we tell the system to add "/usr/games" as a place to automatically look whenever we give it a command, then we create a file called "dwarfort" in the /usr/games directory, change the permissions on the file so it can be used as a script by anyone, and then print two lines of commands to the file.  The end result is a script stored in the /usr/games directory that will automatically take you to the dwarfort directory, where your game is, and run it with wine, simply by typing the command "dwarfort" from the terminal at any point.

*2)* Now lets add the game to the application menu itself.  Go to **System->Preferences->Main Menu**.  In the window that opens, make sure "Games" in the right pane has a check in the box next to it, and then select the icon labeled "Games" in the left pane.  Click the "New Item" button on the right side of the window.  Type what you want the game to be called in your menu in the "Name" box, and then type "dwarfort" in the "Command" box.  Fill in whatever comments you like and select whatever icon you want by clicking the icon image on the left side.  Unfortunately there aren't any images that come with the game that can be used for icons so you'll have to select a generic one.  When you're done, click the "OK" button and it will return you to the previous window.  Look through the right pane list box to find the name of the game and make sure it both has a check by it and is located where you want it in the list.  When you're done, click "Close" and it should appear in your application menu.

3) Run the game by going to Application->Games and clicking on the name you gave the game in the list.

---

