---
title: "Thunderbird is not working after being updated"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by bprof on 2007-05-04
Hi, 

I have installed thunderbird 1.5 using SPM and then I used this command 

bash ~/Desktop/installnewthunderbird.sh -install

to update to version 2, but now I'm unable to start it when I click start it shows a message starting thunderbird but nothing happened, I tried ctrl-alt-backspace to restart gnome and the system halted I have shut it down manually and then restarted it, but still thunderbird is not working.

Any help please?

Thanks!

---

### Post by Seisen on 2007-05-04
You can try this

[https://help.ubuntu.com/community/ThunderbirdNewVersion]("https://help.ubuntu.com/community/ThunderbirdNewVersion")

---

### Post by nanotube on 2007-05-04
you should have posted in the subforum for the [ubuntuzilla scripts]("http://ubuntuforums.org/forumdisplay.php?f=251"), like the instructions in the script say.

to figure out what's wrong, please open a terminal, and run command
```
thunderbird
```
and copy and post any output that it generates in the terminal in here.

---

### Post by bprof on 2007-05-04
Thanks guys for your replies.

Seisen, I was in that page and after I read Automated script to install the newest Thunderbird section I visited Ubuntuzilla and got the instructions on how to use the script from there.

nanotube, here is what I got after running thunderbird:

Segmentation fault (core dumped)

---

### Post by nanotube on 2007-05-04
> **bprof said:**
> Thanks guys for your replies.

Seisen, I was in that page and after I read Automated script to install the newest Thunderbird section I visited Ubuntuzilla and got the instructions on how to use the script from there.

nanotube, here is what I got after running thunderbird:

Segmentation fault (core dumped)

ah i see... are you by any chance using SCIM? try nunning either of the following commands to start thunderbird:
```
export GTK_IM_MODULE=scim-bridge; thunderbird
export GTK_IM_MODULE=xim; thunderbird
```

see also this thread in the ubuntuzilla forum about the same (?) problem: [http://ubuntuforums.org/showthread.php?t=423521](http://ubuntuforums.org/showthread.php?t=423521)

please report whether that works... :)

---

### Post by bprof on 2007-05-04
Thank you nanotube.

Yes I'm using scim. I've tried the following and it worked:

```
export GTK_IM_MODULE=scim-bridge; thunderbird
```

But this means that each time I want to run thunderbird I have to type the above line, correct?

IS there away to make it work from applications-->internet-->thunderbird

Thanks

---

### Post by nanotube on 2007-05-04
well, you have two choices. one - uninstall scim. :) but since you are using it, i assume you want it. :)

otherwise, just edit the shortcut in your applications menu to point to a shellscript, that contains the following lines:
```
#!/bin/bash
export GTK_IM_MODULE=scim-bridge
thunderbird
```
take that shellscript, save it in a text file in your home dir, something like "thunderbirdstarter.sh", change its permissions to executable, with command:
```
chmod u+x thunderbirdstarter.sh
```
then, start the menu editor, and go edit the shortcut properties to point to 
```
/home/yourusernamegoeshere/thunderbirdstarter.sh
```

then, when you click on your shortcut, tb should start.

let me know if you have any problems, and please report if it works as advertised. :)

---

### Post by bprof on 2007-05-04
Thanks a lot!

Now I can click on the panel to start thunderbird\

Just a note:

it worked after I added sudo to the command:

```
sudo /home/yourusernamegoeshere/thunderbirdstarter.sh
```

Thanks for your help,

---

### Post by nanotube on 2007-05-05
what happened when you didn't use sudo? it didn't work?
it's generally not a great idea to run apps with sudo on a regular basis - that's why your user is a "regular user" and not root, in the first place.

what happens if you run ```
/home/yourusernamegoeshere/thunderbirdstarter.sh
``` from a terminal (when it doesn't have sudo in it)? does it show any errors? does thunderbird start?

---

