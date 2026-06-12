---
title: "Software Assiciation"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by farang on 2007-06-16
Hi,

I'd would like to know how to change the default software to be used in order to open files.

1.  The current setting of my Feisty is that .rm files are, by default, to be opened by Totem Movie Player.  I'd like to change the default  association of .rm to Real Player or MPlayer (already installed).  How could I achieve this?

2. I am using Greasemonkey on Firefox.  I have made a wrong move and configured the add-on to use "Run command - gedit" as the software to edit scripts.  Please help me undo this configuration.  I have reinstalled the add-on but the setting stays on.  I'd also appreciate help for locating the real "gedit" program when prompted to choose a text editor again.

Thank you VERY MUCH for your help!!!

Moderators, I apologise if my second question is not legitimate in this subforum.  Please let me know the appropriate forum.  I am going crazy scanning up and down the forums...

;)

---

### Post by Golyadkin on 2007-06-16
1.    Try "System > Preferences > Preffered Applications". 

2.   gedit is here:
> 
$ whereis gedit
gedit: /usr/bin/gedit /usr/X11R6/bin/gedit /usr/bin/X11/gedit /usr/share/man/man1/gedit.1.gz


---

### Post by Golyadkin on 2007-06-16
Also btw, you can change how firefox handles file types by going "Edit > Preferences > Content > Manage".

---

### Post by ajgreeny on 2007-06-16
You can also right click on the file in nautilus and chose the "Open with" option, making sure you also chose the "Always use this program for these files" or whatever the similar actual wording is.

---

### Post by Golyadkin on 2007-06-16
Yeah, just like in Windows, if you rightclick with the Shift key down.

---

### Post by farang on 2007-06-16
> **Golyadkin said:**
> 1.    Try "System > Preferences > Preffered Applications". 
The Preffered Applications panel shows two tabs; Internet and System.  I don't think this changes anything other than the browser and terminal emulator preferences.  ;( 

> **ajgreeny said:**
> You can also right click on the file in nautilus and chose the "Open with" option, making sure you also chose the "Always use this program for these files" or whatever the similar actual wording is.
Right-clicking the .rm file on desktop, right-clicking it in nautilus-opened desktop, right-clicking with shift down from both locations; they all fail to show "Always use whatever."
The context menu is like this;
Open with "Movie Player"
Open With 
[INDENT]Open with "MPlayer Movie Player"[/INDENT]
[INDENT]Open with "Real Player 10"[/INDENT]
[INDENT]Open with "VLC media player"[/INDENT]
[INDENT]Open with Other Application...[/INDENT]
Cut
Copy
etc., etc.

---

### Post by Golyadkin on 2007-06-16
Choose "Open with Other Application" and then choose the program you want to use. Then there is the option to "Always use ...." .

---

### Post by farang on 2007-06-16
> **Golyadkin said:**
> Choose "Open with Other Application" and then choose the program you want to use. Then there is the option to "Always use ...." .

An error is returned upon typing "realplayer" or "mplayer" or either with "sudo" in "Use a Custom Command" field of Open With panel;
**Could not add application**
Could not add application to the database

realplayer FILENAME
mplayer FILENAME
They both work fine from the terminal.

I am beginning to worry if my installation was really a big failure.....

---

### Post by Golyadkin on 2007-06-16
In the "Use custom command thing at the bottom, just type "realplayer" or "mplayer" without any filename.

---

### Post by farang on 2007-06-16
> **Golyadkin said:**
> In the "Use custom command thing at the bottom, just type "realplayer" or "mplayer" without any filename.

This was actually what I did when I got the error.  Sorry for the confusion.

---

### Post by feistyfirsttimer on 2007-06-16
> I am beginning to worry if my installation was really a big failure.....

Don't let a few teething problems put you off Ubuntu!  Most people who are used to how another OS works will experience some difficulties at first.  But you will discover how to do the stuff you want, and in no time you will be used to Ubuntu's setup.

---

### Post by farang on 2007-06-16
I realise there may be a clue in the Properties option (right click and at the very bottom) of the file I want to open with RealPlayer.

Properties panel says in Basic tab;
MIME type application/vnd.rn-realmedia

and in Open With tab;
&#9679; Movie Player
&#9675; MPlayer Movie Player
&#9675; RealPlayer 10
&#9675; VLC media Player
[In other words the tab is a list containing four applications, of which the first has the radio button marked.]

The problem is that I cannot make any change in the tab.

---

### Post by farang on 2007-06-16
> **Golyadkin said:**
> 1.    Try "System > Preferences > Preffered Applications". 

2.   gedit is here:

Thank you Golyadkin!

I have found out that the default text editor that Greasemonkey uses can be changed from FF "about:config."  There is, however, a problem selecting "gedit."

The following is the result of running "whereis gedit" in my system:
```
gedit: /usr/bin/gedit /usr/X11R6/bin/gedit /usr/bin/X11/gedit /usr/share/man/man1/gedit.1.gz

```
Does this mean that my system has [s]three[/s] sorry four files whose names contain "gedit"?  I am still wondering which of the three are the Linux equivalent of Windows .exe file for the text editor.

Thank you again.  :)

---

### Post by Golyadkin on 2007-06-16
You are welcome :)

That means that the binary for execution gedit (compare to Windows gedit.exe) is in three places on your computer. (As you can see, it is in 'bin' folders, with binaries. Binaries are compiled programs, like .exe files)

The last one is the compressed manual for the gedit program.

By the way, *whereis * doesn't just search in filename for "gedit" but it checks the standard binary directories for the speci     fied programs, printing out the paths of any it finds.

---

