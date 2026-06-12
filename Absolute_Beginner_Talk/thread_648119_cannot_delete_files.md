---
title: "cannot delete files"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by alenis on 2007-12-23
Hello
I have two files in my .Trash folder that I cannot delete. Their names are:

FWDPE~T_.EML
PEDCO~#8.EML

I suspect the problem lies in their strange names. I tried both as normal user and root user to no avail.
Can anybody help?
Thanks
Alessandro

---

### Post by BluePlum on 2007-12-23
PEDCo sounds bad...

---

### Post by ray bot on 2007-12-23
What exactly happens when you try to delete them?

---

### Post by alenis on 2007-12-23
Hi  ray bot
when I try to empty therecycle bin nothing happens.
Trying to delete the files from gnome I get a dialog box telling me

 Error "File not found" while deleting "/media/na...PE~T_.EML.EML".

However, double clicking on the file from nautilus opens it!

From the terminal, trying 

rm ped*

I get

 cannot remove `ped*': No such file or directory

I tried both as normal user and as root.

---

### Post by lgambett on 2007-12-23
pay attention to uppercase / lowercase, it is different !

---

### Post by AndyCooll on 2007-12-23
From a terminal try the following:
```
rm -rf $HOME/.Trash/*
```

And if that doesn't work try:
```
sudo rm -rf $HOME/.Trash/*
```

:cool:

---

### Post by bumanie on 2007-12-23
In terminal type gksudo nautilus 
Then find your way to the trash and should be able to delete the files.
Be careful what you delete as it is irretrievable

---

### Post by brett611 on 2007-12-26
bumanie - thanks -- that did it for me.  BTW - what is the plain english description/explanation of what "gk" does in front of sudo?  I've never seen that mentioned

thx

---

### Post by seventhc on 2007-12-26
> **brett611 said:**
> bumanie - thanks -- that did it for me.  BTW - what is the plain english description/explanation of what "gk" does in front of sudo?  I've never seen that mentioned

thx
From what I can tell if you do 'sudo' you enter your password in the terminal, when you put 'gksudo' then you get a pop up to log in at ( a log in gui). From my experience they both will work I think it's more preference more than anything but then again if I am wrong please somebody correct me.

---

### Post by jonmartin on 2007-12-26
> **alenis said:**
> 

rm ped*

I get

 cannot remove `ped*': No such file or directory


Filesystem is case sensitive, the filename starts with PED ... so no go ...

---

### Post by AndyCooll on 2007-12-26
> **brett611 said:**
> bumanie - thanks -- that did it for me.  BTW - what is the plain english description/explanation of what "gk" does in front of sudo?  I've never seen that mentioned

thx

This is a good explanation: [Running sudo graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

:cool:

---

### Post by alenis on 2007-12-26
Actually, I typed the names in upper case, so the problem is something else. I forgot to mention that the files are stored on a NAS bo. can the problem be connected to some peculiarity of the samba driver?

---

