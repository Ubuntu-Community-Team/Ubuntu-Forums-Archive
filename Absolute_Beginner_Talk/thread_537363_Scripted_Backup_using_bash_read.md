---
title: "Scripted Backup using bash read"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by glope on 2007-08-28
Hi,

I currently have a laptop and an external HD. I travel with my laptop on occasion so it isnt always on. I decided i would like to get a script set up to run on cron that will basically run every few hours and ask if my HD is attached and if i would like to backup any changes.

I have written and tested the RSYNC component to the script. Im having problems with the read part of the code below.

> #!/bin/bash
#Backup script

read -p "Start backup? (Y/n)" status;
if [ $status=="Y" ];
then
rsync -a -v --exclude=.* /home/USER /media/External/backup;
elif [ $status=="n" ];
then
echo "Backup not ran"
fi

exit 0

It seems that no matter what is entered in the console, the code automatically proceeds as if the first IF condition has been met. 

Im unsure if its my read syntax or my conditionals but i know something isnt right, Any help greatly appreciated.

---

### Post by lloyd_b on 2007-08-28
Try:
```
if [ $status == "Y"]; then
```
Note space characters before and after the "==" (Yes, "bash" *is* that picky).

*edit* Why are you using "elif"?  Wouldn't it make more sense to use:
```
if [ $status == "Y"]; then
   .....
else
   echo "Not running backup"
fi
```

Lloyd B.

---

### Post by tekkenlord on 2007-08-28
I also think you need to change the first line to:

echo "Start backup(y/n)"; read status;

EDIT: Never mind me. Just tried your way and it works as well. Sorry...

---

### Post by glope on 2007-08-29
Hi Thanks for your help.

Had a play about with the conditional section and found that the syntax needed to be tweaked. The correct syntax was 

> read -p "Start backup? (Y/n)" status;
if [ $status = "Y" ]; then
...

Spacing was important as well. Thanks for your help

---

### Post by glope on 2007-08-29
Hey,

Got the functionality of the script working. My only problem is now that the crontab entry does not load a shell session to ask for and get a reply. Im guessing ive just missed a command at the top or something but i cant seem to find it.

Thanks

---

### Post by lloyd_b on 2007-08-29
> **glope said:**
> Hey,

Got the functionality of the script working. My only problem is now that the crontab entry does not load a shell session to ask for and get a reply. Im guessing ive just missed a command at the top or something but i cant seem to find it.

Thanks

I don't think it will be that easy.  In order to run the shell, it first has to invoke a terminal emulator(such as "xterm").  So a command like 
```
xterm -e "bash -c /home/mydir/myscript" 
```
will, from a terminal window, execute the "xterm" terminal emulator, and then run the script in that (using "bash").  

The problem is that the terminal emulator requires access to a "display", which I'm not sure is even accessible from cron.

If the script weren't interactive, then cron would be able to invoke the shell and run the script without needing the terminal emulator.  But because the script *is* interactive, the terminal emulator is required. 

Maybe somebody else will wander by with an idea on how to start a X process (like the terminal emulator) from within cron.

Lloyd B.

P.S. - you might consider opening up a new thread for this.  The original thread title involves shell script syntax, where now you're concerned about cron.  You'd have a better chance of somebody with the required knowledge spotting the thread with a title that fits the current issue.

---

