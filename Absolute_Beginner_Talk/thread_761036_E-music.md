---
title: "E-music"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2008-04-20
I subscribe to E-music. I need a download manager for e-music that works in Ubuntu Hardy Heron. I have downloaded  emusicj, but can't seem to get it installed. I extracted it to my desktop.

---

### Post by SunnyRabbiera on 2008-04-20
what format does emusic use?

---

### Post by bgast1 on 2008-04-20
It uses .emp, whatever that is.  After the files are downloaded though I believe they are MP3, not sure though because they went away with my windows installation. This program also needs Java, not sure what to install from Synaptic.

---

### Post by SunnyRabbiera on 2008-04-20
hmm, well if they use their own proprietary format there might be nothing we can do for you...
try contacting the developers about if they will have linux support

---

### Post by cardinals_fan on 2008-04-20
I see that you've abandoned the Java thread. **Ignore that.  I'm losing my mind.**  I ask you again: did you try the eMusic Remote Beta from the [official site]("http://www.emusic.com/dlm/download.html")?  It also sounds like there is a Firefox extension that could do the job; again, check the official download site.

Here are some instructions to try: download the [official eMusic installer]("http://www.emusic.com/remote/1.0/emusicremote-linux-installer.bin").  Open a terminal and enter the following (each line is a seperate command):
```
cd Desktop/
sudo chmod a+x emusicremote-linux-installer.bin
./emusicremote-linux-installer.bin
```
Another tip: hitting tab in the terminal will autocomplete either a command or a file name.  For example, on the last step, just start typing the name (after ./) and hit tab.  If nothing happens, hit it twice for a list of all options.

---

### Post by trucker96 on 2008-06-21
Thanks Cardinals fan,
I just upgraded to 8.04 and couldn't get emusic/j to work either and didn't know the commands to install emusic remote.

---

### Post by nhenry on 2008-06-29
Open a terminal and enter the following commands...

Change to your home directory (or wherever you want to install it):
```
cd ~
```

Download the file using the wget command:
```
wget http://www.emusic.com/apps/dlm/emusic_linux_current.tar.gz
```

Extract the file using tar:
```
tar xvf emusic_linux_current.tar.gz 
```

Change directories to emusicdlm:
```
cd emusicdlm/
```

Launch the program!
```
./emusicdlm &
```

If you want to create a shortcut:
Go to the Desktop, right click and 'Create Launcher' or
Right click on 'Applications' menu and choose 'Edit Menus' navigate where you want it and click add Item.

For your 'Command', browse to te 'emusicdlm' folder and then choose the 'emusicdlm' file

---

