---
title: "America's Army Install Help"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by lilro on 2007-05-23
i tried to install this game using:

```
 1. su

then type root password at prompt 2.

/path/to/armyops250linux.run

where /path/to/ is the path to the directory which contains the armyops250linux.run file

**I GET STUCK HERE.**

3. Follow the onscreen prompts to accept the EULA and otherwise

4. Run

armyops 
```

but i get permission denied. i searched on how to login as root, i did that, and it still said permission denied. can someone please help me?

---

### Post by wormser on 2007-05-23
It is better practice to use **sudo** or **gksudo** (for graphical apps) instead of logging in as root.  Try putting sudo infront of the command then type your password.

---

### Post by WalmartSniperLX on 2007-05-23
I did it this way: Assuming the .run is in the home dir just do this. If not then cd to the path it is in.
```

cd to the dir the .run is
sudo sh armyops250linux.run

```

Then after it is installed (just hit the defaults) run it using:
```

armyops

```

---

### Post by lilro on 2007-05-23
thanks you guys i got it now. i love this forum people respond nice and quick:D:D

---

### Post by AZzKikR on 2007-05-23
Use sudo or gksudo please. su lets you stay in as root on your current shell session until you type 'exit'. It can be very dangerous if you forget that you are still super user.

$ sudo ./armyops250linux.run

should do the trick just fine. armyops250linux.run should be in your current directory when typed like this.

---

