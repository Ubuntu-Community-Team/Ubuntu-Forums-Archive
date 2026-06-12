---
title: "How to launch app not in app menu?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by catlett on 2006-03-19
I am following this how to to install opera web browser...[https://wiki.ubuntu.com/OperaBrowser...](https://wiki.ubuntu.com/OperaBrowser...)The terminal returned a messege that Opera was installed and had the newest version(I did both examples in the how to. The 2nd one used synaptic and then had me update synaptic. This is how I got the message "already installed. Newest version. No update.") The how to said I could launch Opera from applications<internet. Opera is not listed there. If an app is installed will it always appear in the application menu? Is there a way to launch without app<internet? When I do a search I only find the Opera deb package that I downloaded from the Opera website. Does Ubuntu have something equivalent to windows Progrfam Files? I only know windows so I'm lost. If this was windows I would just got to C: program files/Opera. Then I could double click the exe. file and launch. If I wanted a shortcut on the desktop I would right-click drag it to desktop and choose `create shortcut here'. Is there a Ubuntu/Gnome equivalent  that procedure?

---

### Post by woedend on 2006-03-19
it should be there, if its not try running "killall gnome-panel"  from terminal or rebooting and see if its there.  If still not showing up, the easiest thing is to go to places->search, type the name of the file in question(in this case "opera"), and make it look in "file system", not just the whole folder.  Whichever ones appear in /usr/bin  or /usr/sbin  are normally executable, in which case you would push alt+f2 and type in the name you just found, or to make things easy create a launcher button linked to it.

---

### Post by catlett on 2006-03-19
I found the menu editor and did "new entry". I believe I browsed to the file to launch opera...usr/bin/opera. But the new entry does not come up in the application menu when I click applications<internet. Am I missing a step when adding? I am in menu editor. I highlighted internet. This brought up the selection that is in the app<internet section. I clicked new entry. Browsed to usr/bin/opera. Wrote a comment and clicked OK. Am I doing something wrong? (probably everything:confused: )

---

### Post by tuxcantfly on 2006-03-19
Alt-F2 to bring up run command, type opera. It should run

---

### Post by catlett on 2006-03-19
Reboot worked. But now I get this ....Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not locate plug-in 'libnpp.so'.
This executable is included in the install package.


Could not locate plug-in executable 'operamotifwrapper'.
This executable is included in the install package.

Plug-in path
(Path can be modified in Preferences dialog)....
When they say "plugin path can be modified in Preferences dialog" do they mean from within Opera? Am I trying to make a path to the plugins folder? Thank you for the quick and helpful replies. Ubuntu has already given me more advice and help in 2 weeks than my father did my whole life:p .

---

### Post by tuxcantfly on 2006-03-19
sudo apt-get install lesstif2

will get you the motif library opera needs

---

### Post by catlett on 2006-03-19
I ran..sudo apt-get install lesstif2..It ran a bunch of lines (building dependency tree etc.) When I shut down and restarted Opera I got the same message about plugins. Do I have to alter the path? When I tried to alter the path I couldn't find the Opera folder. The filesystem is very confusing to me. I don't yet get the logic and flow of it's setup.

---

### Post by tuxcantfly on 2006-03-19
how about you try installing opera this way:

download opera at
[http://www.opera.com/download/get.pl?id=27593&location=15&nothanks=yes&sub=marine](http://www.opera.com/download/get.pl?id=27593&location=15&nothanks=yes&sub=marine)

Get alien:

sudo apt-get install alien

Then convert the downloaded deb to rpm:

sudo alien -R /path/to/operaversion.deb

It should generate some rpm file, then convert it back:

sudo alien /path/to/operaversion.rpm

It should generate another deb file. Install it:

sudo dpkg -i /path/to/operanewversion.deb

then run opera from the command prompt and see what happens

---

### Post by ncappel1 on 2006-03-19
Also, if you just open up a terminal and type in the name of the program yu want to use, it should start up. just open the terminal and type "Opera"

---

### Post by catlett on 2006-03-19
I got Opera to launch after reboot but a can't get any pug-ins to work. I keep getting the error message I posted. When I go to change the path I can't find the plug-ins they want.I can't get Java on any browser for that matter. I was hoping Easy Ubuntu would take care of it but it didn't.

---

### Post by catlett on 2006-03-19
Finally took the easy the easy way out. Someone pointed me to Automatix. Done deal. I now not only have Opera and all it's plug-ins but am upgraded to Firefox 1.5 and it's plug-ins. Thanks for all your help. Hopefully I can sweim on my own for a whiole. Regards

---

### Post by dvarsam on 2006-03-20
Hello !!!

Recently, I had the same concerns like you...

If you want a step-by-step solution, visit this Forum's _**Article#**_**:** 145991

---

### Post by catlett on 2006-03-20
Thanks.

---

