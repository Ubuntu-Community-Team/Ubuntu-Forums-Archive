---
title: "Ruuning an exe from home directory"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-16
Hello,

I have an exe located in my home directory but I can't get to run it as it says "Command not found". I tried copying the file to the bin directory but it reports that I don't have permissions to do so. Please help...  Anyone ?

---

### Post by Stickymaddness on 2007-04-16
You can't run .exe's in linux! 

You need an emulator like wine to be able to do this!

---

### Post by Terl on 2007-04-16
What is it exactly you are trying to run?  Can you give the name of the program?  The more info we have the easier and faster it is to help :)   Is it really an .exe?

---

### Post by justleen on 2007-04-16
if you are reffering to executable files, try putting a ./ in front of the file name.
Without it, it will look in the PATH for the file, not in the actual dir.

if its a shell script you can use   sh to execute it.
```
 # sh filename.sh 
```

copy it with ```
 sudo cp file1 /usr/bin/ 
``` to your bin dir.

---

### Post by slayerboy on 2007-04-16
It looks like you are trying to run a Windows program.  Are you trying to install something?

In order to use Windows programs you can try to use a program called WINE.

If you open up a terminal you can type

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install wine
```

Now that we have WINE installed (and assuming the program you are trying to run IS in your home directory), you can type:

```
cd /home/<insert your username here>/
wine <insert program name here>.exe
```

It will most likely show a bunch of errors or warnings before it runs the program, if it does at all.  A LOT of programs won't work using WINE, and some will.

---

### Post by justleen on 2007-04-16
i dont think hes trying to run a windows .exe file people :)

running an .exe file from the cmdline will output something different again..

---

### Post by Joseaa on 2007-04-16
Sorry about the confusion. I'm a recent convert to linux so a big  n00b. 

Earlier I used to run the .exe version of a particular file in window but now I want to run the executable version of the same file in Linux. Adding ./ in front of the filename did the trick.. Thanks for the info :)

---

