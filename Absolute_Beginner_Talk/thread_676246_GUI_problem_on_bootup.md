---
title: "GUI problem on bootup"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by tkn4everb on 2008-01-23
Hey guys,

Yesterday we installed ubuntu and everything was fine, but today at bootup it loaded a bunch of text on screen it said it could load the GUI then it went to another screen asking to install something called a "dide" or something like that and it said their was none found.

how can this be fixed?

---

### Post by tkn4everb on 2008-01-23
[IMG]http://i228.photobucket.com/albums/ee37/MichaelRyannH/Picture11.jpg[/IMG]

[IMG]http://i228.photobucket.com/albums/ee37/MichaelRyannH/Picture12.jpg[/IMG]

[IMG]http://i228.photobucket.com/albums/ee37/MichaelRyannH/Picture9.jpg[/IMG]


These are the errors that we get instead of Ubuntu loading up.

---

### Post by tkn4everb on 2008-01-23
bumpppppppp.

---

### Post by mikeyphi on 2008-01-23
Go through the boot again - when you get to the message about 'failed to start the X server' enter the 'Yes' option. you will be presented with a long list of text with questions - accept the default option each time.

At the end - if you are left with an input sign ($)
enter startx

---

### Post by tkn4everb on 2008-01-23
thanks we will try and post our results

---

### Post by tkn4everb on 2008-01-23
nothing :(

and switch the 2nd and 3rd images around.

after that screen it takes us back to the first screen but lets us input commands. I tried typing in startx but nothing happened.

---

### Post by mikeyphi on 2008-01-24
> **tkn4everb said:**
> nothing :(

and switch the 2nd and 3rd images around.

after that screen it takes us back to the first screen but lets us input commands. I tried typing in startx but nothing happened.

OK - in that case at the command prompt enter this:
sudo dpkg-reconfigure xserver-xorg

accept all the default options - unless you know better!!

Then, when that bit's done and you are back at the command prompt - enter
startx

---

### Post by LeAstrale on 2008-01-24
after reconfiguring X here is a couple of useful commands from CLI:

*sudo /etc/init.d/gdm restart* "this one restarts the Gnome Display Manager"
*sudo /etc/init.d/kdm restart* "this one restarts the K Display Manager (for KDE users)"
*telinit 3* "when starting in recovery mode this will start up the computer like if you had pressed the normal boot in grub"
*telinit 1* "this will take you into a similar enviroment like the recovery option in GRUB, however, to be root type *sudo -s*"

---

### Post by tkn4everb on 2008-01-24
Thanks,we will try it out!

---

### Post by LeAstrale on 2008-01-28
any news? did it work oout for you?

---

### Post by tkn4everb on 2008-01-28
I havent been at his house since then, but the next time I talk to him ill let you know.

---

### Post by tkn4everb on 2008-01-29
Kay, this is the friend.

I rebooted my computer to go into Ubuntu, went back to the black screen and entered the command.

Commands aren't working at all.

It didn't do anything with the commands I gave it.
"sudo dpkg-reconfigure xserver-xorg"

---

### Post by PmDematagoda on 2008-01-29
Actually you should not enter the command on the black screen but you should switch to a terminal by pressing Ctrl+Alt+F1, once you switch to the terminal, kill the X-Server using:-
```
sudo /etc/init.d/gdm stop
```

Then execute:-
```
sudo dpkg-reconfigure xserver-xorg
```

---

