---
title: "Compiling from Source, &quot;no makefile found&quot;"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by thenovices on 2007-07-21
Hi,

I am somewhat new to Ubuntu, but I have already read several threads and tutorials on how to compile from source, but I just can't seem to install this program.  All the tutorials just tell you to do 

./configure
make
sudo make install

but the problem with the program i found is that it doesn't even come with a configure file.  When I try to do make, it says "No targets specified and no makefile found.  Stop." 

If you'd like to be really helpful, you can download the program from here [http://www.stevens-bradfield.com/MahJong/Linux/]("http://www.stevens-bradfield.com/MahJong/Linux/")

If you're wondering why I insist on installing this program rather than the ones in Synaptic, its because this game is different from the ones on Synaptic.  I don't really feel like explaining in detail, I hope some of you can understand what I mean.  I havent really been able to find any other similar programs on the web.  

I have a suspicion that 3 of the files are actually just plain executable files, but there is some weird lock symbol near the icon.  Either way, when I double-click on the icon, nothing happens.

Any help would be greatly appreciated. Thank you!

---

### Post by tbroderick on 2007-07-21
You download a binary. It's ready to run no compiling needs. Open a terminal and type;
```

./pathto/xmj

```

---

### Post by thenovices on 2007-07-21
wow i spent hours searching on how to run this program.

thank you so much for you help

but why can't i just double-click the icon?  this game is for my grandpa, and i'm not sure he would be able to run the program from the terminal every time.  Is there anyways to create something that would automatically type in that command in the terminal, so that all my grandpa has to do is double-click on it?

---

### Post by grishenko2000 on 2007-07-21
you can always create a launcher on the desktop or in the panels.
right click on desktop click Create Launcher.
then type ./pathto/xmj in the Command: line

---

### Post by thenovices on 2007-07-21
umm... now when I try to start a game, it says that server failed to start, and in the terminal it says 

sh: mj-server: not found

I am guessing this means that the program xmj can't find the other program mj-server, so its not working.  I remember that in the README it says to copy the 3 binaries to another folder, do you think that might be the reason?
From the README: 
```
"Unpack the distribution, and cd into the distribution directory.

Just copy the three binaries
 mj-server
 mj-player
 xmj
into your chosen directory. If you don't have GTK+, then see above.

The user documentation is  use.txt  and  rules.txt ; put these in
an appropriate place. 

Alternatively, or as well, copy the man pages  xmj.1, mj-server.1,
mj-player.1  to the appropriate man directory (e.g. /usr/local/man/man1).

Make sure that the binary directory is in your PATH; in particular,
if you run from the source directory, you need to have it in your 
PATH either explicitly or as . ."
```

---

### Post by nitro_n2o on 2007-07-21
Yes, you have to copy the three files in some folder...

---

### Post by thenovices on 2007-07-21
well I just copied the 3 files, and I am getting the same problem
```

Make sure that the binary directory is in your PATH; in particular,
if you run from the source directory, you need to have it in your 
PATH either explicitly or as . ."
```

what does this mean?  Does it mean i have to copy the 3 files in a specific place?

---

### Post by nitro_n2o on 2007-07-21
Do you have GTK installed?

---

### Post by use a name on 2007-07-21
Ok, tried it myself: you've got to add the folder you unpacked the files to to your $PATH (it's an environment variable, telling which folders to look in for executables). Use this guide: [http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)

WARNING: NEVER EVER add . (the folder '.', denoting your current folder) or $HOME (if you tend to save 'files' there) to you $PATH. This will allow malicious scripts with the same name as normal commands (eg. ls) to be executed, without explicitly specifying you want to.

I had to change the port the server listens to to something else as the port was in use, then it worked. (Well I don't understand the game, but that's something else...)

---

### Post by thenovices on 2007-07-21
okay before I enter in the command, I'd like to double check it.
would it be:

PATH=$PATH:~/Mahjong

I couldn't understand the rest of the jargon about $HOME so I don't really know if that stuff is important or not.

---

### Post by use a name on 2007-07-21
Yes, that'll work.

About the $HOME thing: that would add your homefolder to $PATH, allowing any script in there to be executed from anywhere, and without explicitly stating that you want THAT scripot to be run. The same holds for ~ as well, but since you're adding a subfolder of ~ you're safe (only the scripts inside that folder can be executed from anywhere).

To clarify a bit more: suppose someone writes a malicious script called ls, you save it to your home folder and you've got $HOME or ~ in your $PATH, then every time you type ls in a terminal, this script may be called (I'm not sure what determines which of the available ls commands is actually executed, but if it's just the first one found, then you are in big trouble if $HOME is at the beginning of your $PATH...) The same holds for . which maps to the current folder. If that's in your path, and you're in a folder with a malicious script with the same name as a common command, then that one might be executed.
If you want to execute some script in some folder which is not in your $PATH, you'll have to make explicit that you want that script to run, either by typing the full path, or going to that folder and typing ./nameofthescript. (Hence ./configure.) That's why a script called ls for example will normally not get executed. ;)

---

### Post by thenovices on 2007-07-22
okay the game worked!  thanks for everybody's help!

but I have to type in PATH=$PATH:~/Mahjong everytime, and its annoying.  How do i save the PATH thingy?  or can i make a launcher that launches two lines of code?

---

