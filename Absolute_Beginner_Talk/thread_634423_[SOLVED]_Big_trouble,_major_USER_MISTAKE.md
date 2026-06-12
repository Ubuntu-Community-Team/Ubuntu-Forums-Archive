---
title: "[SOLVED] Big trouble, major USER MISTAKE"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by hvac3901 on 2007-12-07
NOW i have some real trouble.

I erased my xserver file, I mistook it for part of the files i loaded to make the VGA port work. I am stuck at the black screen wihtout GUI, and i am kinda screwed at this point without help.

I have my disk, but i do not run windows and do not have a windows partition, My disk aparently only boots in the windows enviroment.

So my fellow ubuntu users, what happens when someone screws up this bad like i did? is there a repair option out there for CD's some manner of recovery? I think this will generate some interesting answers

I unfortunately do not know how to open my internet (wireless) from the command line, sooo. I find myself eagerly waiting for some help

By the way, my mock DOS promt (dr dos) is in GERMAN any help with a translation would help too.

---

### Post by aktiwers on 2007-12-07
Don't worry.. just type:
 ```
sudo dpkg-reconfigure xserver-xorg
```

And then:
```
startx
```

All fixed :)

---

### Post by hvac3901 on 2007-12-07
xserver-xorg is not installed anymore. I really worked hard to delete it. 
Not knowing that xserver was a little different than the xorg stuff i loaded.

---

### Post by aktiwers on 2007-12-07
Is your computer connected to the internet?

Then:
```
sudo apt-get install xserver-xorg
```

And then try:
```
startx
```If that dont work, you will have to run the 
```
sudo dpkg-reconfigure xserver-xorg
```before the startx command

---

### Post by hvac3901 on 2007-12-07
no not currently i will wait until i go home to hardwire it, and then do as you say. Thanks i'll post an update later.

---

### Post by hvac3901 on 2007-12-07
hey thanks for the help. it worked out, and i am back to where i wanted to be. i had to go the long route and reconfigure the whole Xserver stuff.. Thanks alot for your timely and spot on help.

---

### Post by RandyNose on 2007-12-07
> **aktiwers said:**
> Don't worry.. just type:
 ```
sudo dpkg-reconfigure xserver-xorg
```

And then:
```
startx
```

All fixed :)

Wow! That's some good stuff Maynard!  You rock! 

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

I had farted around with the graphic card settings on my Toshiba Laptop, and had munged the settings, and of course, there isn't a simple Graphical or text "restore" function with ubuntu like there is with XP.  So.. I was left hanging at a command line... So, I ran the settings,   you suggested. There's a whole bunch more questions than with a simple install. But it seems to have killed Beryl or what ever was munging up screen writes.  No Wobbly windows or special effects please, I just need things to work!


BUT

The program that I was having problems with, in WINE now works when it goes to draw the screen.  As the original thing that I had tried to do was figure out how to kill the fancy screens stuff...


In a round about way, I fixed the problem.  So I just might be able to run my Linux machine, and put my XP machine on the back burner, as it's had it's share of abuse over the last three years in my Big truck.  The powersupply is dying, the hinges are starting to go...   But getting trucking map software that I like to use,  hadn't worked.  ..... and I could just drone on and on...  :)

---

