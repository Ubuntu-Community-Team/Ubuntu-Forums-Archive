---
title: "[SOLVED] Launcher Problems"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Krydahl on 2007-07-25
I can't figure out what's going on with my launcher - despite reading a half dozen threads that all say the same thing.

I've created a simple bash script. It's in my bin. When I set up a custom launcher, instead of running the script it opens the file if I give it the full path name and doesn't find it at all if I just give the script name. I've set it to be executable, what am I missing? All the how tos I've seen suggest this should work fine.

Script runs ok from the command line.

---

### Post by wpshooter on 2007-07-25
I have had similar problems when trying to setup a launcher to run the ./qd command that shows the status of my folding-at-home work unit.

None of the suggestions that I received were able to help me setup a successfully launcher for running this command.

Hope someone can help us or maybe this is just not something that the launcher function is currently designed to do, maybe someone can confirm or deny this.

Thanks.

---

### Post by Krydahl on 2007-07-25
It certainly seems like it's designed to do this. I've read several "how tos" that seem to suggest you can - besides, what else is the custom option for. :(

Keeping my fingers crossed someone out there understands it. Otherwise after a week with Feisty I'm pretty happy.

---

### Post by Shazaam on 2007-07-25
Just a curious question. Did you right click the desktop to make your launcher? And did you check off "Run in terminal"?

---

### Post by shearn89 on 2007-07-25
if you've checked "run in terminal" and its still not working try
```
 gnome-terminal -x ./command
```

---

### Post by Krydahl on 2007-07-25
Ah! No, I'd selected file not run in terminal. Stupid boy. Thanks.

---

### Post by wpshooter on 2007-07-25
> **shearn89 said:**
> if you've checked "run in terminal" and its still not working try
```
 gnome-terminal -x ./command
```

This does NOT seem to work for me.  Am I correct that the command would be something like:

gnome-terminal -x ./home/home_name/foldingathome/CPU1/qd

What this does is quickly open a blank terminal and then immediately closes and comes back to the desktop from where the launcher was run.

Thanks.

---

### Post by Krydahl on 2007-07-26
Sorry wpshooter, if you've still got problems maybe I shouldn't have marked this as solved.

For me, I just needed to create the launcher from scratch, making sure that I set the box that defaults to 'application' to 'application in terminal'.

---

### Post by shearn89 on 2007-07-28
> **wpshooter said:**
> This does NOT seem to work for me.  Am I correct that the command would be something like:

gnome-terminal -x ./home/home_name/foldingathome/CPU1/qd

What this does is quickly open a blank terminal and then immediately closes and comes back to the desktop from where the launcher was run.

Thanks.

Yes - it should open a terminal, and run the command in it. Try replacing "home" and "home_name" with ~ (although it shouldn't really make a difference). You could try running a different command, just to check its not something with the syntax, and to see if it could be something to do with the script:
```
gnome-terminal -x top
```

---

