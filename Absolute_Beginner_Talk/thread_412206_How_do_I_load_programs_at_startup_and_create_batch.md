---
title: "How do I load programs at startup and create batch type files?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by grs on 2007-04-17
I'm totally new to Linux Ubuntu.
I am using F@H and would like to know how to start it automatically when I log into Linux.

I would also like to know how to create/write a file which I can leave on the desktop and when I double-click on it it will open the Terminal and input a series of commands to the terminal? Similar it a batch file in Windows.

---

### Post by jerryrw on 2007-04-17
Batch files under Linux are generally called shell scripts and there are tons of sites that teach how to write them.  Other options that achieve the same results (generally) are perl and python.

---

### Post by grs on 2007-04-17
Someone told me a bit on how to make Shell Script files, but they didn't tell me everything. I was able to get it to open Terminal but not type in commands.
What program do I used to create a Shell Script file? I had used Gedit before.

What I would like the Shell Script file to do is the following:

Open the Terminal window
Then change directory to /folding/FAH
Then run the following command ./FAH504-Linux.exe -verbosity 9 -forceasm &

Can someone explain it to me please.

---

### Post by Tundro Walker on 2007-04-17
**Auto-Load Your Own Programs At Login...**

>  I am using F@H and would like to know how to start it automatically when I log into Linux.(SIDE NOTE: For Windows migraters, what he's asking about would normally be handled in MS Windows by adding execution lines to an AUTOEXEC.bat file which loads on boot, or entries in the user's MS Windows "Startup" folder, which loads when a user logs in.)

I'm sure someone will post about some Linux / Ubuntu .config file somewhere to do this, but the GUI method I found was...[LIST]
[*](Main Menu) > System > Preferences > Sessions > Startup Programs (tab)[/LIST]Click "Add", and type the command you want to auto-run at login, which can include switches and arguments.  

**EG:** Say you wanted apt-get to auto-update & upgrade everytime you logged in (which System Update handles, too, but just for the sake of argument..).  You'd create 2 entries, one for...

```
sudo apt-get update
```...and one for...

```
sudo apt-get dist-upgrade
```I don't over-use this.  I mostly use it to auto-start tilda (quake-style terminal), which I've come to rely upon greatly for all my console / terminal work, and sometimes conky, which I use as my system monitor when I'm testing stuff (otherwise I keep the conky entry disabled).

In Xubuntu, you can have it save your session.  So, just keep open whatever program you want ran, and when you log back in, it'll restore itself.

I'm sure there's a way in Kubuntu, but I'm not familiar with it enough to know how.

** Make a Shell Batch / Script File...**

You can use any text editor to make your shell script file (files that end with an .sh extension).[LIST]
[*]Gedit (Ubuntu-GNOME)
[*]Kate (Kubuntu-KDE)
[*]Mousepad (Xubuntu-XFCE)
[*]Vim, Nano (Terminal)
[*]etc, etc (everyone has their favorite, and there's so many to choose from)[/LIST]Open it up, and type in your commands to run.  Unlike MS Windows, where you'd simply hit "enter" to go to a new line and each new line counts as a new execution of the batch file, in a Linux .sh script file, you can chain commands together on the same line using "&&" or ";" EG:...

```
sudo apt-get update; apt-get upgrade
```...would run apt-get to update then upgrade afterwards.  Since both executions are executed together sequentially, the first "sudo" you type will be used for all subsequent commands chained to the first.

When you're done writing up your script, save the file as <whatever>.sh where ever you want it at.  The default script folder for Ubuntu would be in your home directory, in a folder called ".gnome2/nautilus-scripts/", but you can put it wherever you want.  The benefit of putting them in that default folder is that they'll appear in your right-click menu going forward...

Right-Click > Scripts > (Pick the one to run)

Using the auto-load procedure described above, you can have your script auto-run upon login by entering...

```
sudo sh /home/(your home)/.gnome2/nautilus-scripts/(your script).sh
```Everytime you login, it'll fire off.

And, of course, you can tie it to a desktop icon for quick execution, as follows...[LIST]
[*] right-click on your desktop
[*] "Create Launcher..."
[*] Choose "Application" type
[*] Pick an Icon
[*] Enter a Name
[*] Enter the command...[/LIST]```
sudo sh /home/(your home)/.gnome2/nautilus-scripts/(your script).sh
```...which is the same as the one getting it to auto-execute.

Save it, and you now have a desktop execution for your script.

**Using GRS' request as an example...**

>  What I would like the Shell Script file to do is the following:

Open the Terminal window
Then change directory to /folding/FAH
Then run the following command ./FAH504-Linux.exe -verbosity 9 -forceasmGRS' request is actually pretty easy, because you don't have to change folders first...you can just tell the command line the full path to find the file in that you want to executy...

```
sudo /folding/FAH/FAH504-Linux.exe -verbosity 9 -forceasm
```Note 1 -- that I removed the "./" part from his last command..."." is used to tell a folder to refer to itself.  His command "./FAH..." was basically saying "look in myself for the file and run it")

Note 2 -- GRS, don't mean to burst your bubble, but if that's a Windows .exe file, it won't run in Linux.

Anyways, with the commands typed into the text file, we'll save it to his home directory's default script folder, assuming that his home directory is "HelloKitty" :D...

```
/home/HelloKitty/.gnome2/nautilus-scripts/test.sh
```Now, we can right-click on the desktop and run it from the "Scripts" section, or we can create an "Application" launcher to execute it using the following for the command...

```
sh /home/HelloKitty/.gnome2/nautilus-scripts/test.sh
```Note 3 -- I had to use "sudo" in the example scripts I showed, because they involved apt-get, which has to be ran in super-user mode.  But if your script doesn't require super-user mode, you shouldn't have to "sudo" it.  Just start it with "sh" so the terminal executes it in shell.

Have fun!

---

### Post by jerryrw on 2007-04-18
Thats a great explanation.

I was going to add that you also need to put a shebang at the beginning of the script but I tested it and it looks like bash no longer requires it.  Learn something new every day.  But to run scripts in general and if you ever have to run them from other scripts or directly from the terminal you do have to give your scripts executable permissions.

```
chmod +x /path.to/myscript.sh
```

The (old) way of starting a shell script was to place:

```
#!/bin/sh
```

as the first line of the script

---

### Post by grs on 2007-04-19
Thanks for the advice, I give it a go when I get a chance.
As far as the .exe file, I have been using it for the last few days to start F@H and it works, I did have type something before the file would run but that was only once.

---

### Post by Kent84 on 2007-04-22
Hi,

Are you sure that scripts that require "sudo" can be placed via. the Gnome System->Session GUI? I've tried it for a script to disable my wireless at startup "/etc/acpi/asus-wireless.sh" but without success. It works fine when I put it in /etc/init.d/acpi-support but I didn't really want it hidden that deep. I don't see how by having "sudo" in the Gnome session start-up lets you enter your root password...

Thanks in advance...

---

### Post by Kent84 on 2007-04-30
My problem has been fixed now. The bash script file that I created myself needed to change it's permission changed to executable.

---

### Post by DrErling on 2008-07-01
Using kubuntu 8.04 and kaffeine, how could I have a movie autostart during startup of the computer?

I want this computer to play this movie on repeat until it is shut down.

I guess what I`m asking for is the "repeat" argument to complete the code I think will do the trick... ```
kaffeine -p -f test.mpeg
```

Am I totally off now, or pretty close?

DrE
Citizen of n00btown

---

