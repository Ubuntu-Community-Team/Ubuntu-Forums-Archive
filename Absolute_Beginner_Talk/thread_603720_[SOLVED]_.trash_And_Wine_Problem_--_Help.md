---
title: "[SOLVED] /.trash And Wine Problem -- Help"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by averagebeatboy on 2007-11-05
Hi everyone,
I am using Gutsy Ribbon 7.10.  I installed Wine (I do not have Windows installed) thinking I could run Quake II just under Wine with no Windows.
I, after a few attempts, removed wine and all the Quake entries I could find via Synaptic.
Here's the problem now:
My trash bin is full when I try to empty it I get the following message:  "Removing item 1 of 7311" underneath it says "Removing "file." And the message stays there and does nothing. when I open the Trash through a file browser "trash": it has a folder called games and another folder called .wine.
I cannot delete them from the folder yet the Permissions are set as mine. If I highlight the folder games and hit the delete key on my keyboard here is the error message: "Error while deleting  "/home/bae...mega.tmp" cannot be deleted because you do not have Permissions to modify its parent folder.  Skip Cancel Retry are my options.
I have another Trash directory /.Trash same content folders "game .wine"
I have tried everything under the sun that my knowledge of Ubuntu can think of and, I cannot solve this.  Could someone please try to help me?
I have already read the links, the board containg a trash problem where the icon was full but the folder empty and a couple of others to no avail. Please, please help!

Cheers,

Averagebeatboy

---

### Post by milton1 on 2007-11-05
```
cd ~/.Trash

sudo rm -rf *
```

this will remove everything in the .Trash folder recursively. Be careful; make sure you have not accidentally deleted your entire .wine folder!

---

### Post by Beggar on 2007-11-05
For the record, you want to run,

```
sudo rm -rf ~/.Trash/*
```

Miltons code does work, but it leaves open the possibility that you could wipe out your entire hard drive on accident if used improperly. (what if they did cs instead of cd, didnt notice and then ran rm -rf *? Ill give you a hint *boom*)

In regards to the OP, I dont think milton answered the real problem, if you have a folder "foo", which you dont have write permissions for, and you have a file inside that folder "bar", which you have all permissions for, you wont be able to delete "bar". In order to remove a file from "foo", or add a file to "foo", you need write permissions for "foo", not for "bar".

---

### Post by averagebeatboy on 2007-11-05
Begger you are good buddy, really really good!
Popped code  sudo rm -rf ~/.Trash/*
asked for password blinked for a little while. And then returned to its usual self. Trash icon emptied as did the contents of directory /.Trash 
Question:  rm stands for remove?
what are the switches -rf and what do they do?
Thanks again a tremendous job!

Cheers,

Averagebeatboy

---

### Post by averagebeatboy on 2007-11-05
THIS IS NOW SOLVED HOW DO i MARK IT AS SO?

Cheers,

Averagebeatboy

---

### Post by Dr Small on 2007-11-05
Thread Tools > Mark as Solved

---

### Post by dfreer on 2007-11-05
From the manual for rm
```

       -f, --force
              ignore nonexistent files, never prompt
       -r, -R, --recursive
              remove directories and their contents recursively

```

rm does indeed stand for remove, although with normal usage it won't remove a directory. Using the -r switch will remove the directory, and all of the files/folders within that directory. Generally, I find the trash can doesn't empty because it contains a file that you do not have the permission to delete, which is why using *sudo rm -rf* will make sure to get delete it.

---

