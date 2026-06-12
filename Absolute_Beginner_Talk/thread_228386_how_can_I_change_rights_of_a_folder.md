---
title: "how can I change rights of a folder?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-08-03
Azureus wants rights for writing /opt/azureus. I can't change the rights, because I am not the root. How to start file browser as root or how to do this from the command line?
Anyway, I've been hoping to find a list of commands to use in terminal and have not found it yet. I don't even know copy or delete commands - is there a list like that anywhere?

---

### Post by BitTorrentBuddha on 2006-08-03
If you want to save things in /opt/azureus you should either run azureus as root or a simple workaround would be to create a symbolic link to it from a hidden directory in your home folder. ```
mkdir ~/.azureusfiles
sudo ln -t /home/(yourusername)/.azureusfiles /opt/azureus
```

---

### Post by 23meg on 2006-08-03
> **1002285 said:**
> Azureus wants rights for writing /opt/azureus. I can't change the rights, because I am not the root. How to start file browser as root or how to do this from the command line?
```
gksudo nautilus
```will give you a Nautilus running as root, with which you can change all permissions. The terminal command would be ```
sudo chmod +x /opt/azureus
```
> 
Anyway, I've been hoping to find a list of commands to use in terminal and have not found it yet. I don't even know copy or delete commands - is there a list like that anywhere?

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.linuxcommand.org](http://www.linuxcommand.org)

You'll also find the command "apropos" very useful.

---

### Post by ylixir on 2006-08-03
okay, i'll tell you how to start the file manager as root, if you promise not to do it....really there aren't very many good reasons for allowing a user account (even your own) write permissions to anything out of their own home folder. that being said, type the following in a terminal window to start the file manager as root (you'll have to enter your password):

> sudo nautilus

---

### Post by A2A on 2006-08-03
Open a terminal window, and type in the following "CD .." then type in "pwd", that will give you you current working directory. Continue doing a "CD .." untin the "pwd" command shows you are in the root folder, ie "someuser@somehost:/" 
Then type "CD opt" and then "CD Azureus". A "pwd" command would confirm that you are indeed in this directory.

Then type "sudo chmod Azereus 700" or whatever access level you might want to grant the directory.  You will need to enter your password.

Hope this helps,
A2A

---

### Post by BitTorrentBuddha on 2006-08-03
I think he wants to write downloaded files there, not run azureus, as that would be located in /opt/azureus/azureus.

---

### Post by 1002285 on 2006-08-03
Thanks for your answers, at least I could get the rights right now. Which doesn't yet mean I will understan how azureus actually works. bittorrent clients are much more complicated to install in Linux than they are in Windows. But I'll try some of them for some more time.

---

