---
title: "Help with running shell script"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-06-03
So I'm really new to shell scripts...as in, I don't know anything about them. But, I have one that I want to run that automatically runs wget and downloads a file to a certain spot. The script looks like this:

```
#!/bin/sh
wget --header="Cookie:cookieinfo" $1 -P /home/henry/torrents
```

I saved it in /usr/local/bin. But, whenever I try to run it by inputting get.sh, I'm told that I don't have permission, and when I try sudo get.sh, I'm told that there's no such command. How can I make it so that it works? Thanks.

---

### Post by yabbadabbadont on 2007-06-03
Try changing ```
#!/bin/sh
wget --header="Cookie:cookieinfo" $1 -P /home/henry/torrents
``` to ```
#!/bin/bash
wget --header="Cookie:cookieinfo" $1 -P /home/henry/torrents
``` then make sure that the script is executable after you have copied it to /usr/local/bin ```
sudo chmod 755 /usr/local/bin/get.sh
```

---

### Post by Crafty Kisses on 2007-06-03
> **yabbadabbadont said:**
> Try changing ```
#!/bin/sh
wget --header="Cookie:cookieinfo" $1 -P /home/henry/torrents
``` to ```
#!/bin/bash
wget --header="Cookie:cookieinfo" $1 -P /home/henry/torrents
``` then make sure that the script is executable after you have copied it to /usr/local/bin ```
sudo chmod 755 /usr/local/bin/get.sh
```

I got a question, do you need a program to make shellscript a .exe file, or can you do it through the  terminal.

---

### Post by yabbadabbadont on 2007-06-03
A shell script is just a series of, wait for it...... :D, shell commands that happen to have been saved in a text file for later execution.  It's the same as a *.bat file in DOS or Windows.  It is interpreted by the shell (/bin/bash in my example) when the user invokes it.  The last command I provided enables the executable permission on the script text file so that the user can simply type the name of the file and hit enter to run it.  (Just like with DOS batch files)  I hope this clears things up a bit.

---

### Post by Crafty Kisses on 2007-06-04
> **yabbadabbadont said:**
> A shell script is just a series of, wait for it...... :D, shell commands that happen to have been saved in a text file for later execution.  It's the same as a *.bat file in DOS or Windows.  It is interpreted by the shell (/bin/bash in my example) when the user invokes it.  The last command I provided enables the executable permission on the script text file so that the user can simply type the name of the file and hit enter to run it.  (Just like with DOS batch files)  I hope this clears things up a bit.

Haha.

---

