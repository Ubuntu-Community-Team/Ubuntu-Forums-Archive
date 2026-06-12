---
title: "Keyboard shortcuts to apps"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-02
Hi Folks
I prefer to use keyboard shortcuts to launch apps or urls rather than mouse clicks.
In Windows I made extensive use of WinKey for this purpose.
Now that I'm struggling my way through Ubuntu, I find System->Preferences->Keyboard Shortcuts and GConf-Editor->apps->Metacity->Keybinding Commands to be both very useful (the latter particularly) for fast launching of urls and those apps for which I know the path to the executable file.
However, I'm having great difficulty for most apps. For example, in Windows, I can use a shortcut to the path to scalc.exe to quickly launch the OOo spreadsheet.
But, in Ubuntu I have so far failed to find how to do this for the same thing.
Would appreciate any advice.

Thanks
Paul

---

### Post by exif on 2006-08-02
So long as the executable is in a bin folder that's listed in $PATH just the app name should launch.

Try using just the name of the executable. If it's not launching make sure the path of it is in $PATH

---

### Post by gogos on 2006-08-02
I have found xbindkeys to be more useful for shortcuts.  Its lets you pick the key combination and corresponding application to launch.  There is a graphical utility (believe its called xbindkeys-config) that allows you to easily create the mappings.

---

### Post by PaulFXH on 2006-08-02
Hi exif
Thanks for your reply.

```
Try using just the name of the executable. If it's not launching make sure the path of it is in $PATH
```

This was useful and I managed to find quite a few executables going through /usr/bin/ and clicking on files that looked interesting.
Nevertheless, for two apps that I particularly wanted to shortcut (OOo Calc and RythmBox) I found it easier to just place an icon on the desktop panel, click it and look in the command line of the properties box.

Paul

---

### Post by PaulFXH on 2006-08-02
Hi gogos

Thanks for your suggestion.
Certainly xbindkeys looks highly interesting and could even become useful once I figure out how to use it.
One drawback I found with this tool was that its three line manual sure doesn't give a lot away :) 
The manual, such as it is, strongly recommends using the GetKey button rather than specifying the desired key (which activity it says is reserved uniquely for experts).
However, every time I hit this button, the utility just disappeared.
Nevertheless, i certainly would like to know more.

Paul

---

### Post by gogos on 2006-08-02
Yes. it is correct that GetKey is easier to use.  Did you try clicking the "New" button at the bottom first?  You need to create an entry in the list before assigning keys and an action to it.

---

### Post by PaulFXH on 2006-08-03
Hi gogos

Would appreciate if you can help me to get this xbindkeys to work. I have not been able to make any progress since yesterday with this.

Here's what I'm doing:

1. I installed the xbindkeys package in Synaptic
2. Clicked on xbindkeys-config in /usr/bib/ to open dialog box.
3. Next, click on NEW button
4. In the NAMR box, enter OOo Calc
5. In the ACTION box, enter ooffice -calc
6. Click Run Action button and OOo spreadsheet opens (so everything looks good so far)
7. Click Get Key and box shuts down immediately with no messages and nothing achieved.

What am I forgetting?

Thanks
Paul

---

### Post by gogos on 2006-08-03
Can you post the output of the application when you run it please.    Open a terminal and execute:

```
xbindkeys-config > /home/<username>/xbindkeys_output.txt
```

Replace <username> so that it points to your home folder and this will create a file xbindkeys_output.txt with the output.  Either attach the file or just post the contents.

---

### Post by PaulFXH on 2006-08-03
Here's what I got when I opened this file:

open file: No such file or directory
xbindkeys: no process killed
Error : /home/paul/.xbindkeysrc not found or reading not allowed.
please, create one with 'xbindkeys --defaults > /home/paul/.xbindkeysrc'.
or, if you want scheme configuration style,
with 'xbindkeys --defaults-guile > /home/paul/.xbindkeysrc.scm'.
Segmentation fault

Paul

---

### Post by gogos on 2006-08-03
Ok looks like you don't have a configuration file set up, so try doing exactly what the application says.  In a terminal run:

```
xbindkeys --defaults > /home/paul/.xbindkeysrc
```

It looks like there are a few posts surrounding this in the xbindkeys project as well.

---

### Post by aysiu on 2006-08-03
> **PaulFXH said:**
> 
This was useful and I managed to find quite a few executables going through /usr/bin/ and clicking on files that looked interesting. No, you're missing the point--you don't need to know the path to the executable. You can just type the name of the program as the command. For example, you don't have to do ```
/usr/bin/nautilus
``` in order to launch Nautilus. You can just do ```
nautilus
``` The same is true in Windows if you use Win+R, you don't have to type ```
C:\Program Files\Mozilla Firefox\firefox.exe
``` You can just type ```
firefox
``` > Nevertheless, for two apps that I particularly wanted to shortcut (OOo Calc and RythmBox) I found it easier to just place an icon on the desktop panel, click it and look in the command line of the properties box. Same with those: the commands are ```
oocalc
``` and ```
rhythmbox
``` respectively. If you type the first few letters of a command in the terminal and press the **Tab** key twice, you'll see the available commands. For example: ```
 oo
oobase          ooffice         oomath          oowriter
oocalc          oofromtemplate  ooo-wrapper
oodraw          ooimpress       ooweb

```

---

### Post by PaulFXH on 2006-08-03
OK, now I've got it.
Very many thanks for your help

Paul

---

### Post by HAARP on 2006-08-09
I've got a questions regarding xbindkeys:
I use a ctrl+y to switch between my 2 screens. However, this seems to be overridden by games. I'd like to be able to force focus away from them.
Is there any uber-combination I can use that is guaranteed to work? ctrl+alt+f1 works inside games, ctrl+alt+y doesn't. So there must be a way to do this, even if I have to use low-level tools.

---

