---
title: "How to turn the trackpad on/off with a button?"
date: 2015-12-27
forum: Apple Hardware Users
---

### Post by Zorgoth on 2015-12-27
On my old computer (an ASUS), there were buttons to turn the trackpad on and off, which was very useful because I'm apt to accidentally click on things when I don't want to, and sometimes I'm in a program like emacs where I don't really need a mouse anyway.

Is there a way to bind keys in Ubuntu on a Macbook Pro Retina 11,2 so that the trackpad will turn off? Is it possibly just a matter of finding the name of the right media key and mapping it to something else?

FYI I am using the mtrack drivers.

---

### Post by Zorgoth on 2015-12-27
Here's the solution I came up with for now:

Run

```
echo "pointer = 0 0 0 4 5 0 0 0 0 0 0 0" ~/.togglebuttons
```

and then make a script called ~/.toggleclicks containing the lines

```

#!/bin/bash
xmodmap ~/.togglebuttons
S1="pointer = 0 0 0 4 5 0 0 0 0 0 0 0"
S2=`grep pointer ~/.togglebuttons`
if [ "$S1" = "$S2" ];
then echo "pointer = 1  2 3 4 5 6 7 8 9 10 11 12" > ~/.togglebuttons;
else echo "$S1" > ~/.togglebuttons;
fi
```

Run 

```
chmod +x ~/.toggleclicks
```

and you can then bind the command to a key combination as a standard keyboard shortcut from CCSM. Oddly, the Keyboard shortcuts application doesn't seem to execute it correctly, though a terminal or CCSM's keyboard shortcuts do.

This still permits scrolling. To disable scrolling as well, just replace the 4 and 5 with zeroes in the definition of S1 and the initial echo statement.

---

