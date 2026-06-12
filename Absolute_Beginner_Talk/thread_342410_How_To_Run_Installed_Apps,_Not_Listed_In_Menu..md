---
title: "How To Run Installed Apps, Not Listed In Menu."
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by 7mm on 2007-01-20
HI There EveryOne, I'm Using Kubuntu 6.10 As My Secondery OS (Still New To Linux) As Windows Is My Priority. I've Used "Adept Manager" For Software Updates & Installation & It Worked Very Well Form Me. Downloaded Apps "Firefox" & "GnuCash" Listed In Menu While "ClamAV" & "Jabber" Didn't ](*,) . How Do I Get Them In The Menu & If I Can't, Is There a Possible Way To Get Them Started? Please Help!

---

### Post by ewankho on 2007-01-20
You can run them from the terminal if you know the program name.

---

### Post by riven0 on 2007-01-20
Whenever an app isn't listed in the menu bar, you can try through the terminal. So if you installed opera, for example, just go to the terminal and type:

> opera

And it should come up.

---

### Post by silence.hr on 2007-01-20
wrong post. sorry.

---

### Post by Sef on 2007-01-20
Alt + F2 and type in the name of the app.  Note: It is case sensitive, so Firefox and firefox are not the same.

---

### Post by ewankho on 2007-01-20
In KDE I right click on the K menu thing (kinda like the start menu in Windows) and then select Menu Editor. You can then manually add your application in the Menu Editor.

---

### Post by 7mm on 2007-01-20
> **ewankho said:**
> In KDE I right click on the K menu thing (kinda like the start menu in Windows) and then select Menu Editor. You can then manually add your application in the Menu Editor.

Thanx Bro, Thought Before It But Just Don't Know The Programe Installation Folder (Possib'ly Where All of Them Are Installed). Can Any One Show Me The Location.

I've Tried To Run ClamAV From Terminal By Typing [clamav, Clamav, CalmAV], But Non of Them Worked. Please Help!

---

### Post by RomeReactor on 2007-01-20
Hi. To know what options ClamAV gives you, type in a terminal:

```
man clamscan
```

Let's say your home directory is named "User", and you want to scan it, but NOT it's subfolders (something like "My Music" or "Pictures"), just the files located there. Then you do:

```
clamscan /home/User
```

Scanning a single file called "file.txt" in "/home/User":

```
clamscan /home/User/file.txt
```

If you do want to scan your home folder AND it's subfolders, then:

```
clamscan -r /home/User
```

This is done from the terminal because ClamAV is a text mode antivirus; you can, however, install a graphical interface called clamtk. Look for it in Adept or:

```
sudo apt-get install clamtk
```

---

### Post by hatchetman82 on 2007-01-20
it looks to me like you can add / remove programs from the menu by running System --> Preferences --> Menu layout.
by default it has 2 menus to edit - Applications and System (the menu through which you invoked this application).

---

### Post by 7mm on 2007-01-20
Thank You "RomeReactor". That's Good Enough Virus Scanner Info For Novice Like Me. I've Downloaded The [clamtk] With [Adept Manager] & It's Working. Thanx :D . But My Problem Isn't Just The Virus Scanner. Any Downloaded & Installed Programe Can Be Executes EZ'ly. Can Anyone Show Us?

---

### Post by 7mm on 2007-01-20
For a Linux Fresher, Am I Demanding Too Much?:(

---

### Post by 7mm on 2007-09-02
Ohh....Well..............I Guess I Did, Sorry Folks!

---

### Post by RomeReactor on 2007-09-02
Do you mean to run them from the terminal? usually you just type the command name in and press enter; for example, to open **firefox** from the terminal and see if it leaves any error messages there, you type:
```
firefox
```
if you want to open firefox and leave the terminal free so you can do something else with it, you type the command followed by a space and an ampersand (**&**):
```
firefox &
```
to know what command line options you have with a certain application, you call the manual page for that program:
```
man firefox
```
to exit the manual page, press **Q**.

If you have problems with a specific application, please post back.

---

