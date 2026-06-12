---
title: "Sessions"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-07-16
I want to create a script the executes the following commands and can be called by the command "cairo-dock"

```

cd /opt/cairo-dock
make clean
make
./cairo-dock --no-glitz

```

I want to place a command in sessions called "cairo-dock" that executes a file that run's those commands. Any help would be appreciated :)

---

### Post by charles.g.moore on 2007-07-16
> **amrclutch1 said:**
> I want to create a script the executes the following commands and can be called by the command "cairo-dock"

```

cd /opt/cairo-dock
make clean
make
./cairo-dock --no-glitz

```

I want to place a command in sessions called "cairo-dock" that executes a file that run's those commands. Any help would be appreciated :)

Try this:

Fire up a terminal
make a dir in your home folder called scripts
cd into scripts
sudo vim *the name you want to call the script*
type this:

#!/bin/bash
*commands you want executed in order of execution*


save and close

sudo chmod +x *name of your script*

now you should be able to launch it by typing ./*name of your script*

then you can place the path to the script (including the ./) in your sessions menu



I know there is an easier way but I think that should do it.

The only prob. may have to do with the order of your commands...

---

### Post by MiCovran on 2007-07-16
If you want to be able to run it by just typing "cairo-dock", then you can copy the script to the "/usr/bin".
```
sudo cp cairo-dock /usr/bin
```

---

### Post by charles.g.moore on 2007-07-16
> **MiCovran said:**
> If you want to be able to run it by just typing "cairo-dock", then you can copy the script to the "/usr/bin".
```
sudo cp cairo-dock /usr/bin
```

Very nice, I learn something new every day...

---

### Post by amrclutch1 on 2007-07-16
thanks! I love linux :D

---

### Post by charles.g.moore on 2007-07-16
> **amrclutch1 said:**
> thanks! I love linux :D

I'm glad it worked for you...

---

### Post by amrclutch1 on 2007-07-16
So am I :)

---

