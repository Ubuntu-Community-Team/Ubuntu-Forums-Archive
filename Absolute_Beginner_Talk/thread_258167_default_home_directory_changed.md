---
title: "default home directory changed?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-15
for some reason when ever i open konsole i dont start at my home directory i start in ~/.cairo-dock 

i think it has to do with this script i run at start up.

cd ~/.cairo-dock
./cairo-dock --no-glitz --no-background&

can you tell me how to set it so when i open konsole i start in my home directory?

Thanks

---

### Post by skierkegaard on 2006-09-15
add cd ~ to the end of that script, then you will start in your home dir.

---

### Post by jinxjinx on 2006-09-16
#!/bin/bash
cd ~/.cairo-dock
./cairo-dock --no-glitz --no-background&
cd ~


sadly...no worky.

thanks for the reply.

---

### Post by skierkegaard on 2006-09-16
Can you type env at the command line? it should print out your environment variables.  I suspect your HOME variable is set to that .cairo dir.
my HOME is like this in env:

HOME=/home/chris

Hope this helps.

---

### Post by jinxjinx on 2006-09-18
awesome. now if i could only figure out how to edit that file...

---

### Post by Brunellus on 2006-09-18
> **jinxjinx said:**
> awesome. now if i could only figure out how to edit that file...
edit which file?

if it's a config file, it's just text, whereupon you can edit it in the Text Editor of Your Choice (TM) (I use vim), provided you have the necessary permissions.

---

### Post by jinxjinx on 2006-09-18
thats the question: which file?
all i know is that when i typ env i see whats in it...

---

