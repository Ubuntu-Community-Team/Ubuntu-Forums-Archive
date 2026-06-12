---
title: "Problem with shell scripts I think"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by butterandguns on 2007-08-02
I just downloaded FretsOnFire and extracted it to a desktop folder.  I double click the FretsOn Fire Icon and it shows me a new window which asks if I want to Run in terminal, display, cancel, or run.  Neither Run in Terminal nor Run do anything.  I don't know if this is a problem specific to FoF or just a general problem with all shell scripts.

---

### Post by apswartz on 2007-08-03
First make sure the shell script is executable...
```
chmod +x *.sh
```
or
```
chmod +x nameofshellscript
```

---

### Post by butterandguns on 2007-08-03
chmod +x *.sh
chmod: cannot access `*.sh': No such file or directory

Okay.  So maybe it's not executable.  How am I supposed to make it work then?  The properties on the fiel say it is a shell script and it's the only thing that even looks executable in the folder.

---

### Post by apswartz on 2007-08-03
what is the name of the shell script?

```
chmod +x NameOfShellScript
```

Replace **NameOfShellScript** with the actual name of the shell script you want to make executable.

---

### Post by AnRa on 2007-08-03
You can use this packages from Debian:
 :arrow: [fretsonfire](http://http.us.debian.org/debian/pool/main/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb)
 :arrow: [fretsonfire-game](http://http.us.debian.org/debian/pool/main/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb)
 :arrow: [fretsonfire-songs-sectoid](http://http.us.debian.org/debian/pool/main/f/fretsonfire-songs-sectoid/fretsonfire-songs-sectoid_1.dfsg-1_all.deb)

---

### Post by butterandguns on 2007-08-03
Nothing seems to happen.
It just gives me a new Terminal Prompt

---

### Post by walkerk on 2007-08-03
in terminal move to your desktop (i presume this is where you downloaded it to..)
```
cd ~/Desktop
```

Make the script executable (presuming the name is FretsOnFire.sh)
```
chmod +x FretsOnFire.sh
```

Now install it..
```
./FretsOnFire.sh
```

---

### Post by butterandguns on 2007-08-03
Okay well it says that there is no such file as FretsOnFire.sh in that dirctory even though when I right click and check properties on the file it says that it is a shellscript.  Am I just asking the wrong question.  Maybe I should just ask how do I install FretsOnFire once I have it extracted.

---

### Post by walkerk on 2007-08-03
> **butterandguns said:**
> Okay well it says that there is no such file as FretsOnFire.sh in that dirctory even though when I right click and check properties on the file it says that it is a shellscript.  Am I just asking the wrong question.  Maybe I should just ask how do I install FretsOnFire once I have it extracted.

what is the filename?

---

### Post by butterandguns on 2007-08-03
It is FretsOnFire

---

### Post by walkerk on 2007-08-03
> **butterandguns said:**
> It is FretsOnFire

in a teminal move to the location you downloaded it to..

then:
```
chmod +x FretsOnFire
```

run it:
```
./FretsOnFire
```

---

### Post by apswartz on 2007-08-03
Then it is
```
chmod +x FretsOnFire
```

Type the filename exactly as it appears since Linux is case sensitive.

---

### Post by apswartz on 2007-08-03
First, what result does this give....
```
ls -l FretsOnFire
```

---

### Post by butterandguns on 2007-08-03
Next post

---

### Post by butterandguns on 2007-08-03
> **walkerk said:**
> in a teminal move to the location you downloaded it to..

then:
```
chmod +x FretsOnFire
```

run it:
```
./FretsOnFire
```

This shows this message
File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by walkerk on 2007-08-03
> **butterandguns said:**
> Doing This
"Re: Problem with shell scripts I think
Quote:
Originally Posted by butterandguns View Post
It is FretsOnFire
in a teminal move to the location you downloaded it to..

then:
Code:

chmod +x FretsOnFire

run it:
Code:

./FretsOnFire"

Reveals this 




File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Ok, it seems that the script is only used to start the game but you do not have a good install.. I would use one of the packages listed early in this thread to install the game..

---

### Post by butterandguns on 2007-08-03
> **apswartz said:**
> First, what result does this give....
```
ls -l FretsOnFire
```

Results
-rwxr-xr-x 1 sid sid 73 2007-04-14 06:32 FretsOnFire

---

### Post by apswartz on 2007-08-03
Try this...
```

sudo aptitude install libsdl1.2-all libsdl1.2-dev
```

to make sure you have libSDL installed.

---

### Post by butterandguns on 2007-08-03
> **walkerk said:**
> Ok, it seems that the script is only used to start the game but you do not have a good install.. I would use one of the packages listed early in this thread to install the game..

I havn't installed anything at all.  All I've done is downloaded and extracted.  The chmod commands seem to do nothing.

---

### Post by apswartz on 2007-08-03
In linux when a command works you usually get no feedback. On the other hand, if there is an error an error message is usually displayed.

The chmod seems to have work, because now the script is attempting to run and you got an error saying it couldn't find a library.

---

### Post by butterandguns on 2007-08-03
> **apswartz said:**
> Try this...
```

sudo aptitude install libsdl1.2-all libsdl1.2-dev
```

to make sure you have libSDL installed.

Did this.
Get the same error message as before
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by butterandguns on 2007-08-03
Anything else I can do?
Or can somebody give me some other script I can download to see if it is a general problem or just with this script?

---

### Post by apswartz on 2007-08-03
What does this return?
```
locate libSDL-1.2.so 
```

This is what I get...
```

alan@dell:~$ locate libSDL-1.2.so
/usr/lib/libSDL-1.2.so.0.11.0
/usr/lib/libSDL-1.2.so.0

```

---

### Post by apswartz on 2007-08-03
> **AnRa said:**
> You can use this packages from Debian:
 :arrow: [fretsonfire](http://http.us.debian.org/debian/pool/main/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb)
 :arrow: [fretsonfire-game](http://http.us.debian.org/debian/pool/main/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb)
 :arrow: [fretsonfire-songs-sectoid](http://http.us.debian.org/debian/pool/main/f/fretsonfire-songs-sectoid/fretsonfire-songs-sectoid_1.dfsg-1_all.deb)

I think I would go with AnRa's suggestion and try one of the packages he links to. (above)
Clarification
Or I guess all of them. Plus, any needed dependencies will be downloaded and installed for you.

---

### Post by butterandguns on 2007-08-03
> **apswartz said:**
> I think I would go with AnRa's suggestion and try one of the packages he links to. (above)
Clarification
Or I guess all of them. Plus, any needed dependencies will be downloaded and installed for you.

Making progress
I now have a FoF icon under games in applications.
I click on it and a black screen flashes for a couple of seconds and then nothing happens.

---

### Post by apswartz on 2007-08-03
You know, you may have better help from some FoF users. I found their forum here...
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=3](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=3)

Do let us know if they get you up and running.

---

