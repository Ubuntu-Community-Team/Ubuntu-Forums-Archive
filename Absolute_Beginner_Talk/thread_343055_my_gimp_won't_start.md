---
title: "my gimp won't start"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-01-20
I just installed ubuntu 6.06 last night tried out all the new software and when i got to gimp it hangs up. it gets to a point where it says querying new plugins xsane and stops. what should i do

---

### Post by mssever on 2007-01-21
Open up a terminal window, type [FONT=Courier New][COLOR=Green]gimp[/COLOR][/FONT], and see if any error messages show up. If so, post them here.

---

### Post by rusty4r on 2007-01-21
no error messages were displayed

---

### Post by %hMa@?b&lt;C on 2007-01-21
> **rusty4r said:**
> no error messages were displayed
well, what is displayed?

---

### Post by rusty4r on 2007-01-21
nothing, after i typed in gimp the square came up in the middle of the screen that says the gimp 2.2 it has the orange progress bar at the bottom and when it gets to "Querying new plugins: xsane" it stops. and nothing ever comes up in the terminal window where i typed gimp

---

### Post by rusty4r on 2007-01-21
isnt xsane just the plug in for a scanner if so i dont have one hooked up to this machine so should i just uninstall xsane and try again

---

### Post by mssever on 2007-01-21
It couldn't hurt to uninstall xsane...

Also, post the result of this: ```
gimp; echo "Exit status is $?"
```

By the way, does it hang and do nothing, or does it exit? If it hangs, type gnome-system-monitor in another terminal and see if the CPU is pegged.

I've never heard of such a problem before...

---

### Post by rusty4r on 2007-01-21
Nothing ever shows up in the terminal window.

I moved to another workspace, opened another terminal and typed:

> gimp; echo "Exit status is $?"

The exact same thing happened in that workspace:

the square came up in the middle of the screen that says the gimp 2.2 it has the orange progress bar at the bottom and when it gets to "Querying new plugins: xsane" it stops. and nothing ever comes up in the terminal window.

I started the system monitor and it shows gimp to be sleeping, but Xsane is "uninterruptible" but with no (0)  cpu usage.

---

### Post by rusty4r on 2007-02-17
bump

---

### Post by spetras73 on 2007-03-25
bump!!

---

### Post by matchstich on 2007-05-01
i am having the same problem

gimp starts, gets to searching for plugins,
and at xscanimage  it hangs. 

xsane does the same also

epson 1200 perfection

worked just fine till that last xsane update

i did the gnome-system-monitor while i had gimp searching 
for plugins,

and it showed xsanimage sleeping.

and cpu was at 7%

---

### Post by Nuafite on 2007-05-09
Go to System/Administration/Synaptic Package Manager. 

Do a search for 'sane'.

Highlight 'sane' and mark for Reinstallation. 
Apply. 

I think your Gimp should now launch without any problem.  Fingers crossed!

---

### Post by matchstich on 2007-05-09
i did what you posted but the option for reinstall  is greyed out.

all i can do is remove sane or completely remove sane .

guess i could try removing and re install.
thanks

---

### Post by Zyppora on 2007-05-12
I seem to have had the same problem.
Gimp 2.2 on Feisty Fawn. Tried reinstalling Xsane, didn't work. Sane wasn't installed and I wasn't anywhere near considering it.

After uninstalling xsane and xsane-common from Synaptic, Gimp ran fine. I don't need them coz my computer doesn't have a scanner attached I guess.

Hope this helps anyone.

PS. I don't know if there'll be any other problems complaining about xsane not being installed anymore :/

---

### Post by yogibear214 on 2007-05-14
I have the same problem. I'm afraid to uninstall xsane, because when I instruct synaptic to do so, it comes up with a box saying "ubuntu-desktop" will also be installed, an idea which I don't really like the prospect of. Any help? I don't have a scanner plugged into my computer.

---

