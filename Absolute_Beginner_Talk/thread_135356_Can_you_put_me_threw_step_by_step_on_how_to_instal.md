---
title: "Can you put me threw step by step on how to install applications on ubuntu."
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by YellowHat on 2006-02-23
How? I'm having so much trouble installing just flasplayer. I extracted it made a directory and typed in what I told it and it said no such filename or directory.

---

### Post by taurus on 2006-02-23
Did you remember to put ./ in front of the file you tried to execute???  Otherwise, use automatix to install some extra stuff for your Breezy then.

---

### Post by Madpilot on 2006-02-23
[QUOTE=YellowHat]How? I'm having so much trouble installing just flasplayer. I extracted it made a directory and typed in what I told it and it said no such filename or directory.[/QUOTE]

Try the Flash instructions [here]("https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b").

Also, note that the Linux terminal is case-sensitive. If you're trying to change to a directory called "Documents", typing "cd documents" will NOT work... it has to match the case of the directory or file you're trying to use!

---

### Post by procras on 2006-02-23
Check the file permissions for the file you are trying to execute

For example in a terminal type
$ ls -l file_you_are_trying_to_execute
(Where $ is the shell prompt)
Or
Right click the file, go to properties and select the permissions tab.

It must be executable, you should see an x in the field, otherwise you cannot execute it.

Sometimes the file is executable but your shell will not execute things in the current working directory unless you try to run them as
$ ./file_you_want_to_execute

If the file you are trying to execute is a shell script then you can just send it to the shell by
$ sh file_you_want_to_execute.

If this does not help send more information please.

---

### Post by dvarsam on 2006-02-23
read my Tutorial on this Forum's "Customization Tips & Tricks" Page, article #; 134914

---

### Post by Sutekh on 2006-02-23
And to throw more into the mix... but seriously this is a great link

[Installing Software in Ubuntu - by ]("http://www.psychocats.net/linux/installingsoftware.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

