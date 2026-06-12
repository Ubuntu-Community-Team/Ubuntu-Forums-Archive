---
title: "Custom Launcher for Command line app doesn't stay open."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by fpwind on 2007-09-01
I've been using Ubuntu for about 2 years now but I feel really stupid on this one.  I'm trying to create a launcher for a command line program.  mp3wrap.  It works great by the way.
I've tried Rt clicking and creating a launcher - changing the type to Application in Terminal and setting the command as mp3wrap.  I've also tried this using the full path to the app.
Unfortunately after clicking the launcher I never get anything.  I think the terminal may be opening really fast and then closing before I can interact with it.  
Thanks for the help

---

### Post by shearn89 on 2007-09-01
does the app work fine when you open a terminal and then run it? If so, its probs to do with the launcher. Try creating a new gnome-terminal profile, and somewhere in the preferences there is a box saying "hold terminal open after finish" or something similar. Then put this in the launcher (it should work):
```

gnome-terminal --window-with-profile=XXXXXX -e <command>

```
and uncheck the box saying "run in terminal".

Post any probs here - i know i've had a few teething troubles with similar stuff...

---

### Post by fpwind on 2007-09-01
Thanks for the reply.
The program runs just fine if I manually open the terminal.
I created a new profile and tried your command.  I just get the terminal window opening with nothing in it. Not even a command prompt.  Under the new profile i also tried  the setting Hold terminal open -- When a command exits.  No dice. Also in Feisty I don't have the check box for "run in terminal" when creating a launcher. Its now in the drop down under type.  I've tried it both ways.
Any Ideas's

thanks again

---

### Post by banewman on 2007-09-01
A trick I use is to create a panel launcher then right click - click properties and check the command. I use this to add launchers to gdesklets starterbar.

---

### Post by fpwind on 2007-09-01
I've done that and it doesn't change anything.

---

### Post by shearn89 on 2007-09-02
Does it say anything? I sometimes get an error saying "unable to create child process"?

---

### Post by twistadias on 2008-04-09
Hi I created a custom launcher for matlab 2008. the program works fine but the terminal stays open at the same time. is there any way I can hide the terminal or close it while still keeping matlab open

---

### Post by twistadias on 2008-04-11
bump

---

