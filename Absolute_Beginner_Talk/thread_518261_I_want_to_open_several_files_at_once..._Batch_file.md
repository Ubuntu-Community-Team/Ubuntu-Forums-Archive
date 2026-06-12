---
title: "I want to open several files at once... Batch file? Launcher? Alternative?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by YAOMTC on 2007-08-05
[COLOR="Gray"]I have several files that I want to open once pretty much every day. On Windows, I have simple batch files to do that... But how do I do it on Linux? Do I use a Launcher somehow, maybe with commas and/or quotes? Or is there some other way of going about this?[/COLOR]
[I'm going through the tutorial(s) at linuxcommand.org and learning to use the shell and make shell scripts. It could be a while before I get this figured out, but this tutorial is pretty thorough, so I should be fine.]

[COLOR="Silver"]And another question: Is there a faster way to open the terminal window, faster than Applications -> System Tools?[/COLOR]
[Answered.]

[COLOR="Silver"]And as another unrelated comment, I can never get Amarok or Rhythmbox to play my music. Only classic-skinned Winamp through Wine can I play my music. Weird...[/COLOR]
[COLOR="Gray"][I decided this is good enough. Classic Winamp is still nice.][/COLOR]
{[Wait, nevermind. XMMS is a bit better here.]}

---

### Post by kidcharles on 2007-08-05
On the terminal opening question, I have a launcher button right on my top panel. Under 'Applications->Accessories' right-click on 'Terminal' and choose 'Add this launcher to panel.' Then you can just click on that button to pull up a terminal. Even better, you can assign a shortcut key. Under 'System->Preferences->Keyboard Shortcuts' you can assign a key to pull up a terminal instantly (I just assigned mine to ctrl-t).

EDIT: Whoops, ctrl-t makes it hard to open up a new tab in Firefox! Well, you get the idea anyway...

---

### Post by kidcharles on 2007-08-05
What kind of files do you want to open?

---

### Post by Nekiruhs on 2007-08-05
> **YAOMTC said:**
> I have several files that I want to open once pretty much every day. On Windows, I have simple batch files to do that... But how do I do it on Linux? Do I use a Launcher somehow, maybe with commas and/or quotes? Or is there some other way of going about this?

And another question: Is there a faster way to open the terminal window, faster than Applications -> System Tools?

And as another unrelated comment, I can never get Amarok or Rhythmbox to play my music. Only classic-skinned Winamp through Wine can I play my music. Weird...
The Linux equivalent of batch files are shell scripts. Just make a text file and make the first line #!/bin/bash, then right click it, go to properties > permissions and make it executable. Then put your commands on the subsequent lines. The first line just tells what to run the file with. For command line arguments (like cp ARGUMENT ARGUMENT) $1 is the first argument $2 is the second one and so on. Variables can be assigned like Name = 'YAOMTC', then referenced like $Name. For more info go to linuxcommand.org and choose shell scripts.

Heres a sample of mine that I use to make new Python files, preformat them, and make them executable, then open them in my IDE.
```
#!/bin/bash
echo "+===================+"
echo "|  Newpy v. 1.0     |"
echo "+===================+"
touch ~/Programming/Python\ Programs/$1.py
echo "#!/usr/bin/env python" >> ~/Programming/Python\ Programs/$1.py
echo "#By Kyle Rush" >> ~/Programming/Python\ Programs/$1.py
echo "#$(date +"%x %r %Z")" >> ~/Programming/Python\ Programs/$1.py
echo "" >> ~/Programming/Python\ Programs/$1.py
echo "" >> ~/Programming/Python\ Programs/$1.py
echo "#        +-----------------------------------------------------------------------------+" >> ~/Programming/Python\ Programs/$1.py
echo "#        | GPL                                                                         |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | Copyright (c) K. Rush <mvrck5@gmail.com>                                    |" >> ~/Programming/Python\ Programs/$1.py
echo "#        |                                                                             |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | This program is free software; you can redistribute it and/or               |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | modify it under the terms of the GNU General Public License                 |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | as published by the Free Software Foundation; either version 2              |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | of the License, or (at your option) any later version.                      |" >> ~/Programming/Python\ Programs/$1.py
echo "#        |                                                                             |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | This program is distributed in the hope that it will be useful,             |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | but WITHOUT ANY WARRANTY; without even the implied warranty of              |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the               |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | GNU General Public License for more details.                                |" >> ~/Programming/Python\ Programs/$1.py
echo "#        |                                                                             |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | You should have received a copy of the GNU General Public License           |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | along with this program; if not, write to the Free Software                 |" >> ~/Programming/Python\ Programs/$1.py
echo "#        | Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA. |" >> ~/Programming/Python\ Programs/$1.py
echo "#        +-----------------------------------------------------------------------------+" >> ~/Programming/Python\ Programs/$1.py
echo "" >> ~/Programming/Python\ Programs/$1.py
echo "#End Header" >> ~/Programming/Python\ Programs/$1.py
echo "" >> ~/Programming/Python\ Programs/$1.py
chmod +x ~/Programming/Python\ Programs/$1.py
echo ""
echo "Type ~/Programming/Python\ Programs/$1.py to run program at another time."
echo ""
echo "Newpy end"
geany ~/Programming/Python\ Programs/$1.py
exit  0

```

And for your terminal question, I just went into keyboard shortcuts (System > Preferences > Keyboard Shortcuts) and made my windows key launch a terminal.

---

### Post by happyhamster on 2007-08-05
1. You could write a script to do that. For example, something as small as:

#!/bin/sh
	gedit text1 text2 text3 text4 text5

would open 5 different text-files with gedit. (Put the script in a text file called opentxt.sh or something like that, and you can run it with 'sh opentxt.sh') Anyway, don't know that much about scripting myself, but there's lots of info around. Just open a few random scripts and take a look around :)

2. Right-click the terminal entry in the accessories menu, and you can then choose to add a launcher to desktop or panel. You could also try a package like "nautilus-open-terminal" (search Synaptic) to be able to open a terminal with a mouse-click.

3. Do you have multiple sound-cards (or USB-speakers perhaps?)

---

### Post by bogolisk on 2007-08-05
> **YAOMTC said:**
> I have several files that I want to open once pretty much every day. On Windows, I have simple batch files to do that... But how do I do it on Linux? Do I use a Launcher somehow, maybe with commas and/or quotes? Or is there some other way of going about this?


You can a shell script for that. In Debian based systems such as ubuntu, "see blah.xyz" (example "see myfile.pdf", "see my_file.txt", etc)  usually open the file(s) in the appropriate application.
> 

And another question: Is there a faster way to open the terminal window, faster than Applications -> System Tools?



nautilus-open-terminal (in gnome) might be what you want. Or you can GConf editor to bind gnome-terminal to a key.

> 

And as another unrelated comment, I can never get Amarok or Rhythmbox to play my music. Only classic-skinned Winamp through Wine can I play my music. Weird...

open the mixer (gmix or kmix) and check if any channels got muted. There're many sound backends in linux (esd, arts, alsa, oss.) launch winecfg to see what sound backend does wine use. Check if the other tools (amarok or rhythmbox) use the same thing.

---

### Post by wesley_of_course on 2007-08-05
Yakuake comes to mind and you can set a key , f12 is default , when hit a terminal pops open or drag a terminal off the menu and park it on your screen.

---

### Post by YAOMTC on 2007-08-05
Alright, Nekiruhs, I decided to go through the tutorial at linuxcommand.org. I figure if I'll be using Linux, I should know how to use the terminal. Thanks for the suggestion! :)

---

### Post by asmoore82 on 2007-08-05
if you like Winamp, check out XMMS.

---

### Post by YAOMTC on 2007-08-05
I tried XMMS, and thought the interface was too dark, and the controls too small...

But after trying it a bit more, I decided I could get used to it. After all, Winamp's volume control doesn't seem to work, and XMMS's does.

---

### Post by YAOMTC on 2007-08-07
I figured it out.

```
#!/bin/bash

cd /home/chris/Various_Stuff/Gaia_Online/TNBoG_PFBS
ooffice -calc tnbog_signers.ods
ooffice -calc pfbs_signers.ods
gedit repeatsigner.txt
```

---

