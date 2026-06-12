---
title: "How to make a start script for an application?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Dogfighter on 2007-08-14
well all i want is to make i script which starts a application so i dont need to browse into the directory every  time and execute it from there.
i hope u understand what i mean :)
tia!

---

### Post by bren on 2007-08-14
right click on the desktop and create a launcher.....
add a name and the command line (including path) to start your app
choose the icon and put it on the desktop

you can also make a script out of a simple text file 
have one line to call the app
make it executable chmod +x filename
add the script to a dir in your $PATH or add the dir where it is to to $PATH
now you can call the script from any terminal window

bren

---

### Post by Dogfighter on 2007-08-14
hmm, i must be doing something wrong.
in the command section ive added the path to the executable, but when i wanna start it, nothing happens. :(
also, does this work with wine?

---

### Post by nichipet on 2007-08-14
The method bren gave will work with any program. What did you enter in the Command field, Dogfighter? And what is the output of this:

```
whereis <the program you are trying to add>
```

---

### Post by Dogfighter on 2007-08-14
in the command field i just entered to whole path to the executable, in this case: /usr/local/games/Sauerbraten/sauerbraten_unix

and the whereis command does not return anything :confused:

---

### Post by Dogfighter on 2007-08-15
im still in need of help :)

---

### Post by jw5801 on 2007-08-15
What happens when you try to run the link?
Try to create a link using the command line to see if we can spot any errors there.
```
ln -s /usr/local/games/Sauerbraten/sauerbraten_unix ~/Desktop/Sauerbraten
```
Then try running the program from command line (ie. type in ~/Desktop... etc and press enter) and if that works try double clicking the icon on your desktop! Otherwise post the errors here and we'll try to fix.

---

### Post by scxtt on 2007-08-15
what happens if you hit Alt+F2 and enter **/usr/local/games/Sauerbraten/sauerbraten_unix** into the box that pops up?

---

### Post by Dogfighter on 2007-08-15
> **jw5801 said:**
> What happens when you try to run the link?
Try to create a link using the command line to see if we can spot any errors there.
```
ln -s /usr/local/games/Sauerbraten/sauerbraten_unix ~/Desktop/Sauerbraten
```
Then try running the program from command line (ie. type in ~/Desktop... etc and press enter) and if that works try double clicking the icon on your desktop! Otherwise post the errors here and we'll try to fix.

result:  ```
boosted@boosted-desktop:~/Desktop$ ./Sauerbraten 
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
```

> **scxtt said:**
> what happens if you hit Alt+F2 and enter **/usr/local/games/Sauerbraten/sauerbraten_unix** into the box that pops up?

nothing :confused:

the game works without problems when i browse into that directory manually, ive got everything installed what i need to run it.

---

### Post by jw5801 on 2007-08-15
That's very... odd...

What output do you get if you run the binary itself from the command line? ie ```
/usr/local/games/Sauerbraten/sauerbrate_unix
``` It could also be a permissions error... try running ```
sudo chmod a+x /usr/local/games/Sauerbraten/sauerbraten_unix
``` or even on the entire directory: ```
sudo chmod -R a+x /usr/local/games/Sauerbraten/
```

Try running the first command first, if that runs the program, then try the other two, otherwise post back here with what happens. One more thing: it isn't a shell script that you use to start the program is it? Try ```
sh ~/Desktop/Sauerbraten
``` and see what happens.

---

### Post by Dogfighter on 2007-08-15
the first (and last) cmd give me the same exact error.
ive already gave me full rights for my games folder, so that aint a problem.

---

### Post by jw5801 on 2007-08-15
hmm... Well whatever you're trying to run isn't executing itself. Another program is running it. Navigate to the file, right click on it and go to the "Open With" tab and see what's there. Then we'll need to make your launcher a call to that program.

---

### Post by Dogfighter on 2007-08-15
its a shellscript.

---

### Post by UnixAnt on 2007-08-15
> **Dogfighter said:**
> well all i want is to make i script which starts a application so i dont need to browse into the directory every  time and execute it from there.
i hope u understand what i mean :)
tia!

Hmmm, what about simply adding /usr/local/games/Sauerbraten/ to your path?  Theoretically you should just be able to open a terminal and enter sauerbrate_unix and the game will run.

Have you tried that?

---

### Post by jw5801 on 2007-08-15
If it's a shellscript then ```
sh /usr/local/games/Sauerbraten/sauerbraten_unix
``` should start the program. If that command works in terminal then creating a launcher with that command will work, or you can map it to a keyboard shortcut or whatever you want!

---

### Post by Dogfighter on 2007-08-15
nope i get the error again... :x

anyway, more important for me, does it work with wine? 
and if so, how?

---

### Post by jw5801 on 2007-08-15
Anything that you can run from command line you can run with a launcher. So yes, it will work with wine. To call to wine to run a program you'd simply type ```
wine *path_to_desired_program*
``` This game you're trying to run isn't normally run via wine by any chance is it? If it doesn't run with the sh command then it certainly isn't a shell script, and if it's a Windows file then you'd need to use wine to run it, ie. the command above.
Absolutely anything you want can be run from the command line, therefore a launcher can do pretty much anything provided you know how to tell it.

---

### Post by Dogfighter on 2007-08-15
err made a launcher for a win program, it does start then i get an error that it wouldnt be installed on a harddrive or something lol.

and no, sauerbraten is a *nix build, it works just fine when i navigate manually into the folder and start it from there (./sauerbraten_unix).

i have the feeling ubuntu just wanna have some fun with me and wants to make me work more :lolflag:

*EDIT* ive fixed the sauerbraten problem, there was an incorrect path in the shell script which caused that.

---

### Post by Jonk1967 on 2007-11-03
I started sauerbraten by creating a text file on my desktop containing the following code:


cd Desktop
cd sauerbraten
./sauerbraten_unix w1280 h1024

Im a complete linux noob so im probably doing somthing very weired here but it does seem to work. oh and make sure you change the file properties of sauerbraten_unix to Execute

when i double click the desktop icon i just select the run icon

---

### Post by jw5801 on 2007-11-03
That's not weird at all, although you can summarise the first two lines into one, and it's best to use absolute paths, not assume you'll be starting in your home directory. But that's all just good programming practise not a real issue!
```
cd /home/*your-username*/Desktop/sauerbraten/
./sauerbraten_unix w1280 h1024
```

---

### Post by thedarkdonut on 2007-11-07
As for me I edited the sauerbraten_unix shell file.  All I did was comment out the the SAUER_DIR=. line, uncommented #SAUER_DIR=/usr/local/sauerbraten, and edited it to point it to the actual folder that I have the sauerbraten folder place at.  So the top of my sauerbraten_unix shell file now looks like the following:

```

#!/bin/sh
# SAUER_DIR should refer to the directory in which Sauerbraten is placed.
#SAUER_DIR=~/sauerbraten
SAUER_DIR=/usr/local/games/sauerbraten
#SAUER_DIR=.

```

As for the launcher the command line I'm using is:
```

/usr/local/games/sauerbraten/sauerbraten_unix

```

Executed the launcher and it works fine for me.

---

