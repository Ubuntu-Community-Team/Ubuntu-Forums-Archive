---
title: "Cna't install Antidote RX, which is an executable file type"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by thinkpeace on 2007-12-28
I am trying to install a French language dictionary and spell check program.  It says it will run in Linux, but when I put the disk in, it just opens the disk so I can browse it.  When double click the installation program in the linux part of the disk, nothing happens.  If I right-click it, it says it wants to open it with Wine, which is that windows emulator thing.  Is this right?  What other program should I try it with?
thanks for the help

---

### Post by tech9 on 2007-12-28
how are you trying to execute it through wine?

---

### Post by thinkpeace on 2007-12-28
I'm double-clicking the install program, and nothing happens.  WHen I right-click the program, it says "open with wine", and then "open with another program", etc.  I assumed that meant that me double clicking the program would start it with wine.  if not, then that's fine, but it still won't open.

---

### Post by taurus on 2007-12-28
Try to run it from a terminal.  First, make sure you have changed to the right directory where that executable file is before you run it.  I assume your CDROM is mounted to /media/cdrom0, 

Applications -> Accessories -> Terminal
```
cd /media/cdrom0
./**filename**
```

---

### Post by thinkpeace on 2007-12-30
Thank you for the help, but no dice.

I entered what you said in the terminal, and I even went one futher and went into the folder on the cd where the install file is: /media/cdrom0/Linux
all that came up fine, but when I enter the file name, it says there is no file or folder.  The file is named "Installe Antidote" when I look at it in the cd folder.  I enterd it that way, with a _ between the words, and with .exe behind it. nothing.

Anything else I should try?

---

### Post by taurus on 2007-12-30
The name of the file that you want to install ends with .exe?  Then, you need to use wine to install it.

Can you post the output of this command in the directory that you want to install it?

```
ls -la
```

---

### Post by thinkpeace on 2007-12-30
andrew@andrew-laptop:~$ ls -la
total 31512
drwxr-xr-x  54 andrew andrew     4096 2007-12-30 16:48 .
drwxr-xr-x   4 root   root       4096 2007-12-27 01:19 ..
-rw-r--r--   1 root   root          0 2007-12-27 14:28 1
drwx------   3 andrew andrew     4096 2007-12-26 23:05 .adobe
-rw-r--r--   1 andrew andrew      144 2007-12-28 01:07 .audacity
drwxr-xr-x   2 andrew root       4096 2007-12-28 01:07 .automatix
drwxr-xr-x   5 andrew andrew     4096 2007-12-28 16:37 .avast
-rw-------   1 andrew andrew     2851 2007-12-30 16:16 .bash_history
-rw-r--r--   1 andrew andrew      220 2007-12-26 16:27 .bash_logout
-rw-r--r--   1 andrew andrew     2298 2007-12-26 16:27 .bashrc
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 14:39 bin
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 15:38 canon
drwx------   4 andrew andrew     4096 2007-12-26 22:06 .config
drwx------   2 andrew andrew     4096 2007-12-27 14:50 .cups
drwxr-xr-x   2 andrew andrew     4096 2007-12-28 16:51 Desktop
-rw-------   1 andrew andrew       26 2007-12-26 16:31 .dmrc
drwxr-xr-x   6 andrew andrew     4096 2007-12-27 17:24 Documentia
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 02:53 Downloads
-rw-------   1 andrew andrew       16 2007-12-26 16:32 .esd_auth
drwxr-xr-x   7 andrew andrew     4096 2007-12-28 17:31 .evolution
lrwxrwxrwx   1 andrew andrew       26 2007-12-26 16:27 Examples -> /usr/share/example-content
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 01:47 Finances
drwxr-xr-x   2 andrew andrew     4096 2007-12-26 16:32 .fontconfig
drwx------   3 andrew andrew     4096 2007-12-26 23:54 .gaim
drwx------   6 andrew andrew     4096 2007-12-30 15:45 .gconf
drwx------   2 andrew andrew     4096 2007-12-30 16:56 .gconfd
-rw-r-----   1 andrew andrew        0 2007-12-28 16:20 .gksu.lock
drwxr-xr-x   3 andrew andrew     4096 2007-12-26 16:32 .gnome
drwx------  14 andrew andrew     4096 2007-12-28 17:31 .gnome2
drwx------   3 andrew andrew     4096 2007-12-28 14:39 .gnome2_private
drwxr-xr-x   2 andrew andrew     4096 2007-12-28 14:35 .gpilotd
-rw-r--r--   1 andrew andrew        4 2007-12-30 15:46 .gpilotd.pid
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 17:08 .gstreamer-0.10
-rw-------   1 andrew andrew       43 2007-12-27 23:54 .gtk-bookmarks
-rw-r--r--   1 andrew andrew       88 2007-12-26 16:32 .gtkrc-1.2-gnome2
-rw-r--r--   1 andrew andrew 13516289 2007-12-27 14:56 gutenprint-5.0.1-1lsb3.1.i486.rpm
-rw-r--r--   1 root   root   14727976 2007-12-27 15:00 gutenprint_5.0.1-2_i386.deb
-rw-------   1 andrew andrew      346 2007-12-30 15:45 .ICEauthority
drwxr-xr-x   2 andrew andrew     4096 2007-12-28 14:51 .icons
drwxr-xr-x   5 andrew andrew     4096 2007-12-27 14:39 .ies4linux
drwxr-xr-x   7 andrew andrew     4096 2007-11-26 01:28 ies4linux-2.99.0
-rw-r--r--   1 andrew andrew   328987 2007-11-26 01:36 ies4linux-latest.tar.gz
drwxr-xr-x   3 andrew andrew     4096 2007-12-30 16:48 .java
drwxr-xr-x   3 andrew andrew     4096 2007-12-26 22:06 .local
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 12:23 LocalApps
drwxr-xr-x  17 andrew andrew     4096 2007-12-28 17:16 .lyrics
drwx------   3 andrew andrew     4096 2007-12-26 23:05 .macromedia
-rw-r--r--   1 andrew andrew     3156 2007-12-28 00:58 .mailcap
drwx------   3 andrew andrew     4096 2007-12-26 16:32 .metacity
drwxr-xr-x  18 andrew andrew     4096 2007-12-27 23:50 movies
drwx------   4 andrew andrew     4096 2007-12-26 23:05 .mozilla
drwxr-xr-x 274 andrew andrew    53248 2007-12-28 17:07 Music
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 01:48 MyFaves
drwx------   2 andrew andrew     4096 2007-12-28 14:37 MyPDA
drwxr-xr-x   2 andrew andrew     4096 2007-09-27 22:59 My Received Files
drwxr-xr-x   3 andrew andrew     4096 2007-12-16 15:29 MyWorks
drwxr-xr-x   3 andrew andrew     4096 2007-12-28 17:31 .nautilus
-rw-r--r--   1 andrew andrew   417792 2007-12-28 01:42 nautilus-debug-log.txt
-rw-r--r--   1 andrew andrew  2175928 2007-12-27 14:30 NoteTab_Setup.exe
drwx------   3 andrew andrew     4096 2007-12-26 22:23 .openoffice.org2
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 01:40 PDFs
drwxr-xr-x   3 andrew andrew     4096 2007-12-27 17:29 Photos
-rw-r--r--   1 andrew andrew       47 2007-12-27 11:58 .plan
-rw-r--r--   1 andrew andrew      566 2007-12-26 16:27 .profile
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 13:02 .qt
-rw-------   1 andrew andrew    34856 2007-12-28 01:50 .realplayerrc
-rw-------   1 andrew andrew     1062 2007-12-28 15:17 .recently-used
-rw-r--r--   1 andrew andrew    12176 2007-12-30 16:17 .recently-used.xbel
drwxr-xr-x   6 andrew andrew     4096 2007-12-28 15:47 Risk
drwx------   3 andrew andrew     4096 2007-12-27 13:13 .Skype
-rw-r--r--   1 andrew andrew        0 2007-12-26 16:32 .sudo_as_admin_successful
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 13:44 tarballs
drwxr-xr-x   4 andrew andrew     4096 2007-12-28 15:19 .themes
drwx------   4 andrew andrew     4096 2007-12-26 23:57 .thumbnails
drwx------   3 andrew andrew     4096 2007-12-30 16:14 .Trash
-rw-r--r--   1 andrew andrew     1076 2007-12-27 13:31 .tuxcards
-rw-r--r--   1 andrew andrew   310950 2007-12-27 13:23 tuxcards-1.2-1mdk.i586.rpm
-rw-r--r--   1 root   root     304314 2007-12-27 13:24 tuxcards_1.2-2_i386.deb
-rw-r--r--   1 andrew andrew    13650 2007-12-27 13:27 tuxcards_greeting
drwxr-xr-x   2 andrew andrew     4096 2007-12-26 23:34 .update-manager-core
drwx------   2 andrew andrew     4096 2007-12-26 16:32 .update-notifier
drwxr-xr-x   4 andrew andrew     4096 2007-12-30 15:52 .wine
-rw-------   1 andrew andrew      124 2007-12-30 15:45 .Xauthority
drwxr-xr-x   2 andrew andrew     4096 2007-12-27 17:54 .xine
-rw-r--r--   1 andrew andrew     4988 2007-12-30 16:21 .xsession-errors
andrew@andrew-laptop:~$ 

this is what came up from that command

I don't necessarily know that it is .exe
The file name is "Installe Antidote", exactly like that.  When I right-click and go to properties, it says
Type: executable
MIME Type: application/x-executable

I was thinking windows I think when I said .exe = executable.

It must be able to run in Lin ux, as there is a specific Linux folder on the install disk, and the box says it will run with Linux.  THe only thing is I am running Feisty Fawn, but this program is from 2006

Thanks

---

### Post by doorknob60 on 2007-12-30
Try navigating to the folder that the file is in with a terminal and typing "./Installe\ Antidote" without quites

---

### Post by taurus on 2007-12-30
I don't want to see the list from your $HOME directory.  I want to see it from the CD where you plan to install that "Installe Antidote".  So, do you know where you CDROM has been mounted to?  Can you change directory to where it is and run that command again?

```
cd /media/cdrom0/Linux
ls -la
```

or

```
ls -la /media/cdrom0/Linux
```

---

### Post by thinkpeace on 2007-12-31
total 152138
dr-xr-xr-x 1 root root      2048 2006-09-12 15:46 .
dr-xr-xr-x 1 root root      2048 2006-09-12 17:31 ..
dr-xr-xr-x 1 root root      2048 2006-09-12 15:46 Documentation
-r-xr-xr-x 1 root root 155782190 2006-09-10 11:03 Installe Antidote

sorry. got confused.  THis is what comes up in the terminal for the cdrom "linux" folder.

also, I did what was suggested and typed: "./Installe\ Antidote"
and I got the bash telling me permission was denied.  I think that is important, isn't it.  How do I change that?

Thanks for all the help

---

### Post by tech9 on 2008-01-02
sorry for the delay, was out for the Holidays...

try changing directories to the file 

example 

cd /media/cdrom0

then 

wine "name of exe"

---

### Post by thinkpeace on 2008-01-03
But then I would have to run it through wine.  The program is supposed to integrate itself into open office so that everytime it opens, this program is there.  it doesn't sound like wine is what I am looking for.  Also, the installation instructions say nothing about having to use wine.

---

### Post by thinkpeace on 2008-01-05
I got it to work.  I contacted the makers of the software.  All I had to do was copy it to the desktop, then change permissions on the files inside.  seems so simple now.  oh well. thanks for all the help.  I guess we all start off as beginners.

---

### Post by fca_neo on 2008-02-17
An easier way to install antidote is to:
[LIST=1]
[*]Open the terminal program (konsole in my case)
[*]browse to the installation folder ```
cd /media/cdromXX/Linux/
```
[*]run the installation executable with root permissions ```
sudo ./Installe_Antidote_RX_v4_Linux
```
[*]Follow the installation steps (chose the dpkg installation for Ubuntu)
[*]That's it, you're done
[/LIST]

BTW, Antidote has a native Linux version (since it is written using Qt) so it doesn't require wine.

---

