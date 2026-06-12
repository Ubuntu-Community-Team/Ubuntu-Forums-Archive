---
title: "two simple commands"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-27
hi, can you show me two commands please?

the first one is make this file:
/usr/local/bin/rhkunter.sh

and the second is delete this folder:
/usr/local/kbitdefender

i tried:
sudo delete /usr/local/kbitdefender

but as usual there's no such command. thanks

---

### Post by Remmelas on 2005-11-27
Not sure what you mean by 'make this file', so I can't offer specific help but as to the second folder, if you really really want to delete the folder, and everything in it, and i mean 'really' want to, the command would be ```
rm -rf /usr/local/kbitdefender
```
keep in mind that it's a brute force attack.  rm=remove -rf=recursive/force, so it will forcibly and recursively remove that folder from the filesystem.

---

### Post by amohanty on 2005-11-27
the first one is make this file:
/usr/local/bin/rhkunter.sh

Did you want to run this file?
If so just type /usr/local/bin/rhkunter.sh at the command prompt and press enter and that should do it.

HTH
AM

---

### Post by michael_salcher on 2005-11-27
if mean "make" as in "create", try

> vim /usr/local/bin/rhkunter.sh

or

> vi /usr/local/bin/rhkunter.sh

or basically

> texteditor filename

and in case you don't have enough permissions to create this file, append "sudo" to the command:

> sudo texteditor filename

---

### Post by Danielle on 2005-11-27
thanks for the help. i deleted the bitdefender folder, that was an empty folder i created eariler but didn't need in the end.

i'm trying to make this batch file:

#!/bin/bash
#
# Script to check RKHunter for updates and run Rkhunter
#
echo "Checking for updates first..."
sudo rkhunter --update

echo "Now we'll scan your system..."
sudo rkhunter --skip-keypress -c

sleep 5

and i want to save it to/as:
/usr/local/bin/rhkunter.sh

i tried what you said but i can't save it :( thanks for the help :cool:

---

### Post by amohanty on 2005-11-27
which ones of michael_salcher suggestion did you try?

AM

---

### Post by Danielle on 2005-11-27
[QUOTE=amohanty]which ones of michael_salcher suggestion did you try?

AM[/QUOTE]
the top two, i don't know how to save it #-o

---

### Post by amohanty on 2005-11-27
Once you have typed out all you want press the following keys in order:

ESC
wq
Enter


This will work with the first two.
HTH
AM

---

### Post by Danielle on 2005-11-27
[QUOTE=amohanty]Once you have typed out all you want press the following keys in order:

ESC
wq
Enter


This will work with the first two.
HTH
AM[/QUOTE]
excellant, thanks for the help :-D

---

