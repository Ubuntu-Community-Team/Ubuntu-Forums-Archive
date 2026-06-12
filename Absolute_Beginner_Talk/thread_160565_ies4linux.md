---
title: "ies4linux"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by csk on 2006-04-15
hi all 
with regards to being able to run internet explorer in ububtu i read this from the howto guide 

[http://www.ubuntuforums.org/showthread.php?t=132508&highlight=ies4linux](http://www.ubuntuforums.org/showthread.php?t=132508&highlight=ies4linux)

i got all the steps done but after i extracted it, ran from termnial, chose 1 from teh screen that came up and all the installation process, nothing happend. where do i access the internet explorer from?

thanks in advance
csk

---

### Post by MartinJ on 2006-04-15
There is a simple script which gets IE up and running.  It should be in /home/username/bin.

I use "~/bin/ie6" at a terminal to start it.

---

### Post by csk on 2006-04-15
i tried doing that and all i got was 
"sudo: /home/chetan/bin/ie6: command not found
"
i tried to reinstall it from the extracted file to no avail

---

### Post by Qrk on 2006-04-15
Go to your home directory (using nautilus) and verify that you have a "bin" folder there. Open it and make sure ie6 is listed.

To execute it, ***DON'T*** use sudo. Just type:

```
/home/chetan/bin/ie6
```

into the terminal.

You can also double click on the ie6 file and select "run"

---

### Post by wolfee on 2006-04-16
or when you open your folder where .wine is suppose to be you can "select" "show hidden files" from "view" section. Then go to .wine driv_c program files and select you ie and run it by clicking the exe file!

---

### Post by csk on 2006-04-16
Qrk - in my bin folder there is no ie6 icon. have i messed up my installation?

wolfee - could you please be more specific cause i am really really new to this. i think my wine is configed cause everytime i press winecfg it says 
"wine: creating configuration directory '/home/chetan/.wine'..."
get a screen with wine cfg things. when i go to the directory u told me there is nothing in the program files folder (even after i do unhide). is my wine properly configed?

---

### Post by hentaidan on 2006-04-16
AFAIK, ies4linux installs into **~/.ies4linux** (notice the dot).

Try typing that into nautilus and see if anything comes up.

---

### Post by wolfee on 2006-04-16
wolfee - could you please be more specific cause i am really really new to this. i think my wine is configed cause everytime i press winecfg it says 
"wine: creating configuration directory '/home/chetan/.wine'..."
get a screen with wine cfg things. when i go to the directory u told me there is nothing in the program files folder (even after i do unhide). is my wine properly configed?[/QUOTE]
 

Ok.. click on your home folder icon, then in the upper left corner of the window you will see the word "view" click on it and look for "show hidden files" option click on it so that there is a check mark next to it. After you have done this scroll down till yo find the folder .wine click on it you will see 2 folders click on the "drive_c" folder. Then you will see 2 folders click on the "programs" folder this is where wine stores all your installed windows programs!! To delete or "uninstall" Just right click on one and select "move to trash":shock:

---

### Post by csk on 2006-04-16
[QUOTE=hentaidan]AFAIK, ies4linux installs into **~/.ies4linux** (notice the dot).

Try typing that into nautilus and see if anything comes up.[/QUOTE]

i just get "bash: /home/chetan/.ies4linux: is a directory"

wolfee - there are is nothing in my program files folder. (i have unhide everything)

---

### Post by wolfee on 2006-04-16
then it's not installed. try installing it again, also when I installed I got shortcuts on my desktop

---

### Post by hentaidan on 2006-04-17
[QUOTE=csk]i just get "bash: /home/chetan/.ies4linux: is a directory"[/QUOTE]

Look in your home directory for .ies4linux (make sure hidden files are showing). This is where ies4linux installs Internet Explorer, NOT in the .wine directory.

You should see directories like: ie55 ie5 ie6. If you do, open them up to "drive_c/Program Files/Internet Explorer" and you should see IEXPLORE.EXE

I'm attaching the scripts that were installed with my ies4linux:
[LIST=1]
[*]download the attachment
[*]right click on ie.zip
[*]click "extract here"
[*]left click on one (3 diff scripts for the 3 versions hopefully installed)
[*]click "run in terminal"
[/LIST]

---

