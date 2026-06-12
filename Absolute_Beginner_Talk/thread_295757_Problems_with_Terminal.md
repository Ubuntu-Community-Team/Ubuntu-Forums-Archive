---
title: "Problems with Terminal"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Malink on 2006-11-08
When I load the terminal program it pops up then shuts down right away. I havnt done anything differnt than when it was working. Also I have the 64 bit version incase that makes a differnce. Thanks

---

### Post by kernco on 2006-11-08
Try opening Synaptic Package Manager and reinstalling the gnome-terminal package.  If you press ctrl-alt-F2, do you get a working command line? (Press ctrl-alt-F6 to get back to Gnome).

---

### Post by davidleeroth2006 on 2006-11-09
I get the same problem! I can access a terminal by ctrl+alt+f3
But how do I restore my terminal?

---

### Post by professor_chaos on 2006-11-09
To try and catch any errors to trace the problem, can you....

from tty1 (ie ctrl+alt+F1) or other.

type ```
gnome-terminal --display=:0
```

this is assuming that gdm is on :0


what happens?

---

### Post by davidleeroth2006 on 2006-11-09
No that didn't work! 
unable to locate theme engine in path,,,, is what I get

---

### Post by professor_chaos on 2006-11-09
Perhaps that error is meaningful.
To start I would try switching themes. Or then reinstalling themes.

Although if your theme was hosed, I wouldn't think you would get any windows. :-k 

Perhaps reinstalling gnome-terminal.

Sorry, I can't be more help, but these are the things I would try. Good luck.

---

### Post by davidleeroth2006 on 2006-11-09
The reason its messed up is because I was playing around with the look of the terminal, but I can't remember how I did it!!!
I think I should re-install the terminal
Could you please tell me how to? ;)

---

### Post by professor_chaos on 2006-11-09
gnome-terminal is the package you want to reinstall.

your can open synaptic package manager and using the search button search for and choose to reinstall "gnome-terminal"

or from the command-line (tty1, etc)

type 
```
sudo apt-get install --reinstall gnome-terminal
```

---

### Post by davidleeroth2006 on 2006-11-09
before you posted I tried 
sudo apt-get --reinstall install gnome-terminal gnome-terminal-data
this didn't work, the terminal still pops up then disapears

I have tried your method and I get this message:
Invalid operation gnome-terminal

---

### Post by professor_chaos on 2006-11-09
Or maybe your profile settings are screwed and you should try wiping/moving them.

they are in 
 ~/.gconf/apps/gnome-terminal/profiles/*

---

### Post by professor_chaos on 2006-11-09
> **davidleeroth2006 said:**
> before you posted I tried 
sudo apt-get --reinstall install gnome-terminal gnome-terminal-data
this didn't work, the terminal still pops up then disapears

I have tried your method and I get this message:
Invalid operation gnome-terminal

it not
```
sudo apt-get --reinstall install gnome-terminal gnome-terminal-data
```

its

```
sudo apt-get install --reinstall gnome-terminal gnome-terminal-data
```

---

### Post by davidleeroth2006 on 2006-11-09
I appologise i am new to ubuntu! how do you move the files?

---

### Post by davidleeroth2006 on 2006-11-09
I just tried the command you just gave 
sudo apt-get install --reinstall gnome-terminal gnome-terminal-data
and it still wont work :(

---

### Post by professor_chaos on 2006-11-09
the gui way is 

open nautilus (this is the file browser thing)
ie. Menu-Bar -> Places -> Home Folder

Then click on the view menu.
Choose to show hidden files and folders

then navigate the path I posted. 

You can then cut and paste these somewhere else. You may need to log out and login to get the changes to take effect.

---

### Post by blendmaster on 2006-11-09
> I appologise i am new to ubuntu! how do you move the files?


The terminal way to do it is by using the mv or cp commands.

e.g.

```
sudo mv <file1> <destination folder>
sudo cp <file2> <destination folder or file to overwrite>
```

The difference between mv and cp is mv moves it to the destination, while cp will copy it.

Thought I'd spread the wisdom of the terminal!

---

### Post by kerry_s on 2006-11-09
You use synaptic to reinstall it, but i'm sure there's nothing wrong with the terminal. Open nautilus and enable show hidden files, go here .gconf/apps/gnome-terminal/ and delete the settings you messed up.

---

### Post by davidleeroth2006 on 2006-11-09
> **davidleeroth2006 said:**
> I just tried the command you just gave 
sudo apt-get install --reinstall gnome-terminal gnome-terminal-data
and it still wont work :(

:D  IT WORKS

THANK YOU:p :KS

---

