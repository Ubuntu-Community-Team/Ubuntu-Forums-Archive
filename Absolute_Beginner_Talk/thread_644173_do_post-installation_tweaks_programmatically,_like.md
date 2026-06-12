---
title: "do post-installation tweaks programmatically, like through .reg in XP?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by bokl on 2007-12-18
Hi community,
I'm very slowly moving to Ubuntu. During the (very long) transition I keep alternating between Ubuntu and Windows XP on my laptop. This means I tend to install and re-install these operating systems fairly regularly. I now want suggestions on how to carry out multiple post-installation settings and tweaks programmatically in Ubuntu. 

(Let me here state: Please refrain from suggesting possible virtualization, disc imaging or multiboot solutions in this thread. I WANT to keep re-installing and have one single OS at a time. Let's just presuppose that I have my reasons and leave it at that.)

Ok then, now back to my question. In In Win XP I've for most of my post-installation settings found their registry entries and can thereby do the settings programmatically by running a .reg file. Easy! I now want something similar in Ubuntu. Here is a list of such settings that I want to make programmatically:

File browser > edit > pref > views: view new = list view
File browser > edit > pref > views: show hidden
File browser > edit > pref > display: date = YYYY-MM-DD format
system > adm > login win > accessability > sounds = disable
system > adm > login win > security > enable auto login (for the only account I have created)
system > pref > sound > sounds > uncheck: play system sounds
system > pref > sound > system beep > uncheck
system > pref > mouse > touchpad > uncheck: tap to click
system > pref > windows > check: select when mouse over... & raise selected after interval (0,5 sec)
system > pref > main menu > pref: check: control center
system > pref > keyboard shortcuts: Run a terminal ---> WIN+T
toolbar > deskbar > preferences > uncheck: web searches
tray clock > pref > type: 24 hour

I want this for two reasons. First, to save me some time. Second, I also simply want to learn how such stuff works in Ubuntu.

So any help with any of the things above would be great. Any general information on how these kinds of settings are stored in Ubuntu, and how to find and modify them, would also be great.

---

### Post by hyper_ch on 2007-12-18
just copy back the config files of the according prorgrams.

Either the are in ~/ or in /etc depending on if they are system wide services or user specific programs. There's just tons of hidden folders in your home folder ( ~/ )

---

### Post by seamushc on 2007-12-18
you could write a script too :/  sounds like a PITA though.  I would just copy over the config files.

---

### Post by bokl on 2007-12-18
hyper_ch: 
Well to start from the top of my list, I don't find the config file for "File browser".
There's no "file system>etc>file browser" folder. I don't know what " ~/" means.

Anyway, copying an entire config file sounds risky to my newbie ears. :-k I want a solution that is relatively stable for new ubuntu  versions. Imagine I do the tweaks for application A under 7.04 and then save its config file (if I find it). After I later install 7.10 it seems risky to overwrite the new default with that old config since the new default config for 7.10 may contain updated lines (not related to my tweak) that I do want to keep. So it seems better to have a way to change only the settings above and nothing else, right?

seamushc: well for Win XP there are many, many sites that list a lot of such .reg tweaks in easily accessible format. So it's mostly just to look up and copy the ones I want into a text file, save it as .reg and then run it. I guess I hoped that something similar would be available for Ubuntu. 

all: 
If you two or someone else could instruct me in some more detail on how to find and then change the first setting in the list above programmatically through a script then maybe I'll be able to sort out the rest myself, based on your example.

---

### Post by bokl on 2007-12-18
Ok, I found one:
(first, "~/" seems to mean the path to the active user accounts folder, i.e. "file system/home/[account name]" )

"~/.gconf/desktop/gnome/file_views/%gconf.xml" contains this:

> <?xml version="1.0"?>
<gconf>
        <entry name="show_backup_files" mtime="1198020608" type="bool" value="false">
        </entry>
        <entry name="show_hidden_files" mtime="1198020608" type="bool" value="false">
        </entry>
</gconf>
If I do File browser > edit > pref > views: show hidden through the GUI, the above value changes to "true".

So one found, the rest to go. Next question: how do I change these values from false to true programmatically through a script?

**edit:**
searching some more for solutions, I find Gconf-editor  ( [http://en.wikipedia.org/wiki/Gconf-editor](http://en.wikipedia.org/wiki/Gconf-editor) ; [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) ). It sounds somewhat functionally similar to what I'm used to with the registry or perhaps tweak UI in Win XP. There also seems to be some sort of commandline tool for Gconf control. Can anyone give me some pointers on all that? Can Gconf-editor help me to programmatically do the settings, perhaps by generating/exporting the needed commands to a script somehow?

**edit2:**
Getting the hang of it now! :-) Here are notes for myself:
Gconf-editor and gconftool are built in. So I can run Gconf-editor just by opening a Run box (ALT+F2) and typing "Gconf-editor". In it, I can find for example the file view settings under "/desktop/gnome/file_views/". The individual keys and their values are then shown in the right window, for example show_backup_files with an unchecked box (=false). right clicking on a key name and doing "edit" shows a window where the key type is shown (in this case boolean). Then I have all I need to change the value programmatically through gconftool.

Gconftool runs from a terminal. gconftool --help displays the syntax. What I need for the example above is something of the format:

gconftool --set [key name] [new value] --type=[key type]

specifically:  
gconftool --set /desktop/gnome/file_views/show_backup_files true --type=bool

running the above command in a terminal changes the setting! Cool! :-) And the command for the other file_views key is:
gconftool --set /desktop/gnome/file_views/show_hidden_files true --type=bool

The strategy would now be to look up key names, key types and desired values for all the things in my list above, make gconftool commands out of them, and then put those commands in a script. I make the script like this:
1. create an empty text file. Paste the commands, one per line. 
2. save the file as some_wanted_name.sh
3. in a terminal, run: sudo chmod +x [path to script folder]/some_wanted_name.sh 
(That makes the script executable. Reminder: to get the full path to a file, select it then do CTRL+C, then paste the path in the terminal window through CTRL+ALT+V)
4. double-click the script, choose run

I will post here again if I finish this. Feedback is welcome in the meantime. Ideally, someone has of course already done all this and can just post a list of specific working gconftool commands. Or if there even is some way to within Gconf-editor export some made changes to such a list of commands.

---

### Post by bokl on 2007-12-19
I now have these:

gconftool --set /apps/nautilus/preferences/default_folder_viewer list_view --type=string
gconftool --set /desktop/gnome/file_views/show_backup_files true --type=bool
gconftool --set /desktop/gnome/file_views/show_hidden_files true --type=bool
gconftool --set /apps/nautilus/preferences/date_format iso --type=string

gconftool --set /desktop/gnome/sound/event_sounds false --type=bool

gconftool --set /desktop/gnome/peripherals/mouse/tap_to_click false --type=bool

gconftool --set /apps/panel/applets/clock_screen0/prefs/format 24-hour --type=string

I did not find keys for the ones below. Any ideas on how their configs are stored?
system > adm > login win > security > enable auto login (for the only account I have created)
system > pref > sound > system beep > uncheck
system > pref > windows > check: select when mouse over... & raise selected after interval (0,5 sec)
system > pref > main menu > pref: check: control center
system > pref > keyboard shortcuts: Run a terminal ---> WIN+T
toolbar > deskbar > preferences > uncheck: web searches

---

### Post by eldragon on 2007-12-19
i would just keep a different partition for /home, and have a script to backup anything you might have changed outside your home ( most stuff in /etc)

then have that same script do apt-get install whatever you installed that isnt default.

that would even keep your background :D

---

### Post by weblordpepe on 2007-12-19
I don't actually have anything to contribute. I just wanted to see what *programmitically* meant.

---

