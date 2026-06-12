---
title: "How can I shut down My X server"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by appeltje on 2007-05-22
I've just started using ubuntu (7), and I've learned some so far. Now I want to install the Nvidia drivers, did everything it wanted, downloaded it to my desktop.

First I just ran it into a terminal console, it said, u need root. So I ran it into a terminal console with: 

// sudo sh NVIDIA-(blablabla).run

Then it said Xserver running. So then I started looking on the internet, and found out there are run levels, and everything below ctrl+alt+F3 uses no Xserver. UHm...not true, even ctrl+alt+F1 still says Im using Xserver which I obviously need to shut down to install the drivers. I read in some other thread some other guy had succeeded with the ctr+alt+F1 thingie.  Then I read somewhere u can kill it with ctrl+alt+backspace, then I get the black screen but I cant enter any data. Other thing I read was "init 3" (which I think is just the same as ctrl+alt+F3).  When I do that using the sudo command:

// sudo init 3 

It basically returns nothing like a 'succeeded' message or anything else to tell me something has changed. And when I try again, the installer tells me Xserver is still running.

So I thought it must be that my run levels are different from everyone else's (although I have a clean install and modified nothing sofar). I read somewhere u can configure ur run levels in etc/inittab. I dont have such a map, but I do have a map much alike (init.rx or something like that) But when I open that map, it looks like total chaos to me

pls help xD

---

### Post by Bachstelze on 2007-05-22
```
sudo /etc/init.d/gdm stop
```

---

### Post by brim4brim on 2007-05-22
When I had to install drivers using the CLI, I just restarted and used the recovery option as it doesn't start X server and then you can run the installer.

---

### Post by Bachstelze on 2007-05-22
Nice try but the NVIDIA installer will refuse to run in single-user ;)

---

### Post by appeltje on 2007-05-22
ah, cool thanks alot, that worked xD

nvidia still wont install but at least I got something new to work with now; a man needs some diversion, if anyone wouldnt mind saving me this diversion (:P), this is the error Im getting:


EDIT: nvm all that, this link:[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) , worked fine

---

### Post by dcquence on 2007-12-17
Well I was having the same issue.  Now I used the sudo /etc/init.d/gdm stop command and that does seem to kill the x server however now that takes me to a just black window and no commands will do anything and I am forced to do a hard reboot.

I am starting to think ubuntu is not my desired choice of linux builds and may just give debian a try as ubuntu seems to be buggy as all hell for me.

---

### Post by PmDematagoda on 2007-12-17
When you kill the X-server press Ctrl+Alt+F1 to move to a terminal.

---

