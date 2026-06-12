---
title: "alacarte editing help needed"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2007-03-09
So, I'm trying to edit alacarte to be able to play a game from the menu.  My game is located in /home/macleod/FretsOnFire.  Normally when I play the game I navigate to that directory using the terminal and then type "./FretsOnFire" to launch the game.  How would I write that in alacarte to be able to launch the game from the menu?  Thanks!

---

### Post by Perfect Storm on 2007-03-09
You need to make script.

```
nano RunFretsOnFire.sh
```

add:

[b]#! /bin/bash

cd /home/macleod/FretsOnFire

./FretsOnFire[/b]

Save and exit
```
chmod +x RunFretsOnFire.sh
```

Now point the launcher to the script file:
sh <distination>/RunFretsOnFire.sh

---

### Post by MakLeod on 2007-03-09
Awesome thanks.  I got a little hung up on what I actually put into alacarte.  If I put the .sh after the filename it wouldn't open, so I just took off the .sh and it worked great.  Thanks!

---

