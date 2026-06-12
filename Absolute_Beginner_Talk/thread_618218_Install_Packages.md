---
title: "Install Packages"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-20
I am using Ubuntu 7.10
On the subject of installing  style or class files in my home directory (as per the Ubuntu Doc.page) I made a sub-directory in my home directory called 'mylatex'

However when I try to export as suggested I get the following:

bernard@bernard-desktop:~$ export TEXINPUTS= ~/mylatex/

bash: export: `/home/bernard/mylatex/': not a valid identifier

bernard@bernard-desktop:~$ 


Any ideas on this please.


Thanks


Bernard

---

### Post by conjur3r on 2007-11-20
I'm not sure what you are trying accomplish but the command you have there is simply setting an environment variable TEXINPUTS to equal /home/bernard/mylatex/.  When doing this, make sure there is NO space after the = sign.

To verify that the environment variable was set up properly, try echoing before and after setting it (note the $ sign):

# echo $TEXINPUTS

---

### Post by bern1939 on 2007-11-20
Many Thanks
Just using it to put my packages into.

Bernard

---

