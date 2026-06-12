---
title: "n00b problems in 6.10"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Wandering Cloud on 2007-01-24
Firstly, getting the freaking .run files to work!!! For some reason, when every I double click on them, it loads up the text editor. I have tried to get it to run in several other applications, including using my very limited knowledge of the command line, to to avail. How on earth do you get them working.

Second, for some really odd reason, Ubuntu is quite happy to tell me that there is no wireless network. This is even though I have full and proper access to the Internet and to the shared documents on the windows computers in my network.

Third, the fonts are *damn ugly*. This might have something to do with the very poor ati drivers I have running atm, so I'm not so worried about this after I take my own crack at installing the ati driver that is currently enclosed in a .run file  :angry.

---

### Post by Bachstelze on 2007-01-24
Instructions about installing your ATi drivers are [here](https://help.ubuntu.com/community/BinaryDriverHowto).

Good luck :)

---

### Post by stiankarlsen on 2007-01-24
You need to lighten up a bit, take it easy. :wink:

---

### Post by Canis familiaris on 2007-01-24
> **Wandering Cloud said:**
> Firstly, getting the freaking .run files to work!!! For some reason, when every I double click on them, it loads up the text editor. I have tried to get it to run in several other applications, including using my very limited knowledge of the command line, to to avail. How on earth do you get them working.
This might have something to do with the very poor ati drivers I have running atm, so I'm not so worried about this after I take my own crack at installing the ati driver that is currently enclosed in a .run file  :angry.
These are usually executable files you have to run them in terminal.
Go to Terminal and browse to the installation folder (cd is for changing directory, ls is for listing files)
and execute the file:

```
user@pc:~/instfolder$ ./executable.run

```

---

### Post by Wandering Cloud on 2007-01-24
> **stiankarlsen said:**
> You need to lighten up a bit, take it easy. :wink: Yeah, I probably should.

---

### Post by Wandering Cloud on 2007-01-24
> **Anurag_panda said:**
> These are usually executable files you have to run them in terminal.
Go to Terminal and browse to the installation folder (cd is for changing directory, ls is for listing files)
and execute the file:

```
user@pc:~/instfolder$ ./executable.run

```
So which parts of that command do I have to edit in order to get it working? I know what to do with user@pc and what the replace ´executable.run' with, but that does n´t seem to be working. What else do I have to do?

Oh, and does anyone have any idea how to fix the false reporting of being unable to find a wireless network? its been rather annoying.

---

### Post by Pobega on 2007-01-24
Well, first you have to chmod your file.> chmod +x executable.run
Then you have to execute your file.> ./executable.run

And that's all there is to running a .run file, as far as I know.

---

### Post by Wandering Cloud on 2007-01-26
Does anyone have any idea how to fix my networking problem? Because otherwise, I'll see if anyone elsewhere knows how to fix this.

---

