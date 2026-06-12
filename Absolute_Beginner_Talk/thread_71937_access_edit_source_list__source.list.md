---
title: "access edit source list  source.list"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by onihr on 2005-10-04
What's the most efficient and effective way to edit and most importantly accessing the source.list. 
 I'm trying to add a repository and I need to make changes to it if I could only find a way to find and edit the source.list. 

 Where do I go: Konq? Konsole? 
 What do I type? 
 
 FYI,  Ubuntu forum seems to get more hits than the kubuntu at the moment and for something that's so easy I'm sure someone can quickly assist.
I checked the kumbuntu unnoffcial guide on adding repositories(because that's what I'm trying to do) and it does not specify exactly in dummie terms how to access the source list so I can edit it.
I

I'm new to kubuntu and I've never used anything other than windows. There's no heading back now(my choice) so please help and reply

---

### Post by Mustard on 2005-10-04
I would think in command line you type..
```
sudo gedit /etc/apt/sources.list

(edit:your using KDE so you probably wont have gedit)
```

You could substitute whatever editor you usually use instead of gedit. 


You could edit in the terminal with

```
sudo nano /etc/apt/sources.list
```

---

### Post by Ampersand on 2005-10-04
You can either open konsole and run 'sudo nano' followed by the file you want to edit (eg 'sudo nano /etc/apt/sources.list'), or run 'kdesu kwrite' and use 'file - open' as usual.

---

### Post by loupy on 2005-10-04
It sounds like you are running Kubuntu and may not have gedit.  If that does not work from a terminal try:

sudo kate /etc/apt/sources.list

---

### Post by BoyOfDestiny on 2005-10-04
[QUOTE=onihr]What's the most efficient and effective way to edit and most importantly accessing the source.list. 
I'm trying to add a repository and I need to make changes to it if I could only find a way to find and edit the source.list. 
Where do I go: Konq? Konsole? 
What do I type? 
FYI,  Ubuntu forum seems to get more hits than the kubuntu at the moment and for something that's so easy I'm sure someone can quickly assist.
I checked the kumbuntu unnoffcial guide on adding repositories(because that's what I'm trying to do) and it does not specify exactly in dummie terms how to access the source list so I can edit it.
I
I'm new to kubuntu and I've never used anything other than windows. There's no heading back now(my choice) so please help and reply[/QUOTE]
sudo gedit /etc/apt/sources.list
or use kate instead of gedit?
anyway for the basic stuff, remove the # infront of the deb blah blah universe to enable it 
(putting #on a line is a comment, and is ignored by apt-get, etc)
If you want even more apps, on the lines that contain universe, write multiverse next to it. If synaptic or anything complains, just go and undo the change...

---

### Post by onihr on 2005-10-05
thanks to all for the rapid response and great support. I will use the following:

 sudo kwrite /etc/apt/sources.list 

  sudo nano /etc/apt/sources.list

I'll have to learn how to use the commands in the nano method within the terminal. 

thanks again

---

