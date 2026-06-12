---
title: "Launcher command"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-26
Hi,
I just installed Neverwinter Nights (under /home/roubos/nwn) and I run the game with the ./nwn command.

I tried creating a launcher and in command browsing to the folder and file "nwn" (like I read in some posts), but it does not work.

I tried entering the following ./nwn "/home/roubos/nwn/nwn" I get permission denied

How should I create the command?

---

### Post by olejorgen on 2007-06-27
Have you tried just /home/roubos/nwn/nwn ? (Although I guess that what "browse" whould insert)

---

### Post by ROUBOS on 2007-06-27
OK
I created a script nwnlaunch.sh
with the following code:

#!/bin/bash
cd ~/nwn/
.nwn

then I did chmod +x nwlaunch.sh

Then I created a desktop launcher and pointer to the script.

Works fine :)

---

### Post by zanglang on 2007-06-27
Does your script look something like this? Make sure you've given your script executing priveledges ('chmod +x <file name>') or it might refuse to run.
```
#!/bin/bash
cd /home/roubos/nwn
./nwn
```

Edit: Oops, I see you've already solved it. :)

---

### Post by ROUBOS on 2007-06-27
Yes it works.
No thanks to me. I'm a noob. Thanks to this great community. I looked a lot through the forums but I was looking for a launcher. Did not know that I had to make a script and link to it.

Anyways it works fine now. Cheers for the help :)

---

### Post by olejorgen on 2007-06-27
Usually you don't need to make a script, but if the program requries that it's started from the resident directory you need to do it. I think gnome should add a "working directory" field in the launcher dialog. (and fill in the parent directory of the selected program)

But I guess that's "too much options". Lets reduce the confusion ^^

---

