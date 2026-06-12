---
title: "create custom app launcher"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by stainless_steel on 2008-03-30
hi,
Im trying to create a custom launcher for a program in a folder on my desktop. Im testing out the command in a terminal. when i cd  into the folder it works fine with ./FretsOnFire
but it doesnt work when i use the entire location: ~/Desktop/Fret*2/FretsOnFire
it just gives me this error:
```
exec: 3: ./FretsOnFire.bin: not found
```
(and i am certain that that is the correct location)

obviously a simple noob cmd line question.
can anyone help me out? 
-thanks

---

### Post by nvteighen on 2008-03-30
> **stainless_steel said:**
> hi,
Im trying to create a custom launcher for a program in a folder on my desktop. Im testing out the command in a terminal. when i cd  into the folder it works fine with ./FretsOnFire
but it doesnt work when i use the entire location: ~/Desktop/Fret*2/FretsOnFire
it just gives me this error:
```
exec: 3: ./FretsOnFire.bin: not found
```
(and i am certain that that is the correct location)

obviously a simple noob cmd line question.
can anyone help me out? 
-thanks

How is the file really called "FretsOnFire" or "FretsOnFire.bin"??

---

### Post by drs305 on 2008-03-30
For 'the entire location', try " /home/USERNAME/Desktop/Fret*2/FretsOnFire" .

---

### Post by stainless_steel on 2008-03-30
nope:
```

dave@dave-desktop:~$ /home/dave/Desktop/Fret*2/FretsOnFire
exec: 3: ./FretsOnFire.bin: not found
dave@dave-desktop:~$ 
```

---

### Post by bumanie on 2008-03-30
Not sure if this will work, but there is a start up manager under System -->
Administration --> Startup manager. You may be able to add your program through there.

---

### Post by stainless_steel on 2008-03-30
> **bumanie said:**
> Not sure if this will work, but there is a start up manager under System -->
Administration --> Startup manager. You may be able to add your program through there.
i dont want it to run at startup, im just trying to create a launcher on the toolbar or in the menu. (and theres nothing called "Startup Manager" under Administratoion.

---

### Post by bumanie on 2008-03-30
I'm at work at present so I can't check, but I think startup manager can be installed through synaptic if it is not already under the administration list.

---

### Post by drs305 on 2008-03-30
I loaded FretsOnFire via synaptic just to see what the launch command is.  The launcher I placed on my panel starts with the command "/usr/games/fretsonfire". So your issue may be just a capitalization one. Linux requires exact spelling/capitalization - i.e  Cats doesn't equal cats

The default install via synaptic put the files in the /usr/games/fretsonfire folder. If I simply type 'fretsonfire' it tries to launch, but the file IS found and executed. So I would guess you aren't using the correct capitalization (try fretsonfire) or the folder with the program is not where you think it is. On my computer, most of the files are in /usr/share/games/fretsonfire

Notes: Although my system tried to start the app, it wouldn't actually run (black screen) but I don't know what fretsonfire does or if my computer can run it. Also, after my install I could not find a fretsonfire.bin file.

Good luck.

---

### Post by stainless_steel on 2008-03-31
yeah, thats the way i was running it (through the standard synaptic install) but i downloaded a large mod pack that is on my desktop with its own execution file, which is how you have to launch if you want to play with the mod. just in case, i tried it lowercase even though the file to launch is with the uppercase

```
dave@dave-desktop:~$ /home/dave/Desktop/Fret*2/fretsonfire
bash: /home/dave/Desktop/Fret*2/fretsonfire: No such file or directory
dave@dave-desktop:~$ 
```

---

### Post by mcduck on 2008-03-31
If nothing else works, try creating a script to launch the game, and then point your launcher to that script:

```

#!/bin/sh

cd /home/dave/Desktop/Fret*2
./FretsOnFire.bin
```
(save the text as frets.sh or whatever you want, right-click and set it to be executable in the properties)

edit: BTW, is the directory really called "Fret*2"? In that case I recommend renaming it into something that doesn't contain any special characters.. If not, and you are just using the "*" as a wildcard, try using the real path instead.

---

### Post by stainless_steel on 2008-03-31
thanks! the script works great, and ive been meaning to figure out how to do that anyways.
and yes a i was using it as a wild card, and no, typing it all out didnt help any.
i'd still like to know why i couldnt launch from the cmd line with the full location though.

---

