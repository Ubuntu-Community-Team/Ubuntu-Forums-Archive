---
title: "How do i run things in the terminal"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-06-26
/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\ the title says it all

---

### Post by deadgobby on 2007-06-26
What do you mean? If you want to run a program. Oh lets say Bzflag for example. Just type in 
bzflag
 No caps.  So if you want to run a program just use the name with out caps and off it goes. 
Gobby

---

### Post by MoxJet on 2007-06-26
Can you be a bit more specific, like what kind of things?

But usually you just write the program and press enter. If you want it to run the the background you append an &

```

moxjet@ubuntu$: firefox &

```

---

### Post by honda on 2007-06-26
Or if you want to run a program, script or anything executable in the 'current directory', ie where you are, then you type ./programname
Without the ./ in front programname is probably not found because because the folder you are in is probably not searched (depending on where you are, of course, your home folder is not searched)

---

### Post by alienexplorers on 2007-06-26
To run something with the root command just enter gksudo in front of the command.

---

### Post by PlatinumPlus on 2007-06-26
So if I compile a c program I can just type 

                            
                                          ./a.out

---

### Post by Golyadkin on 2007-06-26
Yes, if that is the output of the program after compiling and linking.
You can also compile like this:
> 
gcc -o helloWorld hello.c
./helloWord


---

### Post by Spydax on 2007-06-26
Also if it's of any assistance as I was confused to pieces with this, and it's amazingly overlooked here - look in the top left of your screen - click applications --> accessories --> Terminal   --   And there you go, your terminal window.  Seems easy once you know it, but I overlooked it and kept doing ALT+F2 for a terminal window.  It was useless.

---

### Post by testube_babies on 2007-06-26
> **Spydax said:**
> Also if it's of any assistance as I was confused to pieces with this, and it's amazingly overlooked here - look in the top left of your screen - click applications --> accessories --> Terminal   --   And there you go, your terminal window.  Seems easy once you know it, but I overlooked it and kept doing ALT+F2 for a terminal window.  It was useless.

Even better: ```
sudo apt-get install nautilus-open-terminal
``` and you can open a terminal from your right-click menu.

---

### Post by davie668 on 2007-06-26
> **Vismund Cygnus said:**
> OK, there's the solution I've found:

set "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base"

Here's the reference: [Audio Left Channel Problem]("http://forums.nvidia.com/lofiversion/index.php?t18109.html")

How do you go about doing this?
This will hopefully relieve my ears!

---

### Post by davie668 on 2007-06-26
Got it sorted but if anyon else is interested here's how...

> **rpw said:**
> If this is the solution (can't tell at this point), you have to do the following:

1) Open the file "/etc/modprobe.d/alsa-base" with sudo
=> sudo gedit /etc/modprobe.d/alsa-base

2) At the end of the file you will find some entries begining with "option ...". There you can write the needed entry
=> options snd-hda-intel position_fix=1 model=3stack

3) After saving the file you can let the system reload the modules, but due to brain failure I can not remember the command to do this ;-) What will work - of course - is a reboot of the system, so the modules will get loaded.

Regards,

rpw

---

### Post by Golyadkin on 2007-06-27
> **testube_babies said:**
> Even better: ```
sudo apt-get install nautilus-open-terminal
``` and you can open a terminal from your right-click menu.

And just for completness sake, my preference is adding the terminal to the panel. Rightclick "Applications > Accessories > Terminal" and select "Add this launcher to panel".

---

### Post by swoll1980 on 2007-06-27
/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\ how did you do that?

---

### Post by Golyadkin on 2007-06-27
How did who do what?

If you refer to my post, it says so. I move the mouse to the top left of the screen (I am using Ubuntu GNOME, just like you) and left-click on "Applications" then move to "Accessories" and move the mouse down to "Terminal". I rightclick on that line and select "Add this launcher to panel". Then the icon shows up in the panel ("menu bar") at the top of the screen.

---

### Post by swoll1980 on 2007-06-27
How did you do this "/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\ " Theres no keyboard charicter for that
very strange stuff.

---

### Post by testube_babies on 2007-06-28
it's a slash / and a backslash \

/\/\/\/.wow.\/\/\/\

---

