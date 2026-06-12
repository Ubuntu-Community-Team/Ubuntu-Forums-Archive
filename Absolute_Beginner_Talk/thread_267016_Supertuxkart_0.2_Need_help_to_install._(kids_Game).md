---
title: "Supertuxkart 0.2 Need help to install. (kids Game)"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-09-28
Hi all,
i have the original tuxkart game, my 4 year old loves it.
Now i've found the successor to it,except i don't know how to install it.
As far as i can see it's not to find with synaptic, so i've downloaded it from the site. [http://supertuxkart.berlios.de](http://supertuxkart.berlios.de)

Normally i'd use either of the following...
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)  (What has happend to this site???)
or
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

But i can't find an answer there.
The Ubuntu forums don't give me much idea either (not with my searches - depends obviously on knowing exactly what to look for)

I've included a screenie of what i have downloade, any help will be greatly appreciated by both father and son!
Cheers.

---

### Post by Perfect Storm on 2006-09-28
```
cd && cd Desktop/supertuxkart-0.2
sh run_game.sh
```

---

### Post by stoer on 2006-09-28
> **Artificial Intelligence said:**
> ```
cd && cd Desktop/supertuxkart-0.2
sh run_game.sh
```

Hey Thanks!
That works a treat; is this installing the game or just running it from location?
Any chance you could tell me how to add this to the "Games" menu - I can type the code but my son needs to be able to "point and click".

---

### Post by Perfect Storm on 2006-09-28
I don't know, I havn't tried it. But I could see there was a running script on your screenshot.

Try see if it runs or install the game.

---

### Post by stoer on 2006-09-28
run_game.sh

As far as i see it "runs" and doesn't install,
but if it runs, can't i link to "run_game.sh", adding this as a shortcut to my Games dir?

---

### Post by Perfect Storm on 2006-09-28
<double post>

---

### Post by Perfect Storm on 2006-09-28
You might need making a script for it, but first try making a launcher for it in the applications tab games.

The command to put in the launcher is
```
sh /home/<username>/bla/bla/bla/run_game.sh
```

Edit: You might want to put supertuxkart folder somewhere else than the Desktop.
I usually hides away under .Games in the home folder (/home/<username>/.Games) the . (full stop) infront a file or folder makes it hidden.

---

### Post by stoer on 2006-09-28
> **Artificial Intelligence said:**
> You might need making a script for it, but first try making a launcher for it in the applications tab games.

The command to put in the launcher is
```
sh /home/<username>/bla/bla/bla/run_game.sh
```

Edit: You might want to put supertuxkart folder somewhere else than the Desktop.
I usually hides away under .Games in the home folder (/home/<username>/.Games) the . (full stop) infront a file or folder makes it hidden.


Hm, tried that.
Made directory .Games and then

```
steve@laptop:~$ /home/steve/.Games/supertuxkart-0.2/run_game.sh
/home/steve/.Games/supertuxkart-0.2/run_game.sh: line 1: bin/supertuxkart: No such file or directory
```

That's
 sh /home/<username>/bla/bla/bla/run_game.sh

 sh /home/steve/.Games/supertuxkart-0.2/run_game.sh  ????

---

### Post by Perfect Storm on 2006-09-28
Aye, if it does not work you have to make a script for it.

edit
> 
```


steve@laptop:~$ /home/steve/.Games/supertuxkart-0.2/run_game.sh /home/steve/.Games/supertuxkart-0.2/run_game.sh: line 1: bin/supertuxkart: No such file or directory
```

you forgot sh infront of the command.

---

### Post by stoer on 2006-09-28
> **Artificial Intelligence said:**
> Aye, if it does not work you have to make a script for it.

edit


you forgot sh infront of the command.

Sorry, didn't forget the sh in the command line just in my reply :(

steve@laptop:~$ sh /home/steve/.Games/supertuxkart-0.2/run_game.sh
/home/steve/.Games/supertuxkart-0.2/run_game.sh: line 1: bin/supertuxkart: No such file or directory

---

### Post by Perfect Storm on 2006-09-28
Okay. Lets try this:

```
cd /home/steve/.Games/supertuxkart-0.2
nano StartSuperTuxKart.sh

```

add the following:

[b]#!/bin/bash

cd /home/steve/.Games/supertuxkart-0.2
sh run_game.sh[/b]


save <ctrl> + <o> and exit <ctrl> + <x>

back to terminal:
```
chmod +x StartSuperTuxKart.sh
sudo nano /usr/share/applications/supertuxkart.desktop
```

add following;

[b][Desktop Entry]
Name=SuperTuxKart
Comment=Racer game for kids
Exec=sh /home/steve/.Games/supertuxkart-0.2/StartSuperTuxKart.sh
Icon=
Terminal=false
Type=Application
Categories=Application;Game;
[/b]

save and exit.

The game can now be launched from application tab ---> Games

---

### Post by stoer on 2006-09-28
That's got it!!

Can't thank you enough for the help, really appreciate it.

Cheers

steve.

---

### Post by Perfect Storm on 2006-09-28
If you are interested in more games check: [http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)

---

### Post by stoer on 2006-09-28
Always interested, thanks :)

---

