---
title: "Failure of Software Management System"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Carlton1 on 2007-01-22
I am new to Ubuntu, and everything was going well until....

On trying to run Add/Remove programs, the following error is shown;

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

On trying to get in to Synaptic Package manager, the following appears;

E: Type 'wget' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


This sounds serious, but everything else seems to be working fine.

Can anyone offer any suggestions?

Many thanks in advance.

Carlton.

---

### Post by mikewhatever on 2007-01-22
It looks like you need a new list of sources. Get one from here [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) but be aware of different Ubuntu versions. Back up first ```
cp /etc/apt/sources.list /etc/apt/sources.list_backup 
``` You can open your sources list in gedit ```
sudo gedit /etc/apt/sources.list
```
Save after updating/editing and run ```
sudo apt-get update
```

---

### Post by Carlton1 on 2007-01-22
Mike,

I'm not sure what I just did, but it certainly did the trick!

Many thanks for your help

Carlton.:guitar:

---

### Post by mikewhatever on 2007-01-22
I hope you've copied the new sources list and pasted it over the old one, then saved and updated.:D
By the way, since your old list was screwed anyway, there was no need to back it up. You should probably remove it ```
sudo rm /etc/apt/sources.list_backup
``` and then backup the new one ```
cp /etc/apt/sources.list /etc/apt/sources.list_backup 
```

---

