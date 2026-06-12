---
title: "queries about permissions, and copying"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by kwyjibo on 2006-04-16
right, i have an icon folder i want to put in the icon directory, why am i getting the below error when trying to do it?  anything obvious?

> rmorgan@Richard:~$ sudo cp /home/rmorgan/Desktop/d3a-icons /usr/share/icons/
Password:
cp: omitting directory `/home/rmorgan/Desktop/d3a-icons'
rmorgan@Richard:~$


while on this, is there a way of using the file browser gui to change permissions on folders.  for instance i'm browsing and i want to right click, properties and add me to the write section just by ticking, cant do this at the moment as it's greyed out... and it is a bit of a hassle having to open a terminal and chmod or do all stuff as sudo?

---

### Post by kwyjibo on 2006-04-16
think i just found this out

i just did sudo nautilus in a terminal and that seemed to let me do what i wanted.  That best practice?

---

### Post by siminone on 2006-04-16
I wouldn't recommend it unless it was absolutely neccessary.

The best practise has to be to find out why you are getting files in your home folder that you don't even have permission even to view. It sounds like an installation problem.

---

### Post by htinn on 2006-04-16
Probably not a good idea, actually. Anyway, what you probably should do is this:

sudo cp -r /home/rmorgan/Desktop/d3a-icons /usr/share/icons/

---

### Post by Mustard on 2006-04-16
You might need to use the recursive option, -r .  The manual can be found with this command..

```
man cp
```

Just mucking around with a test on my system I think it would be something like this...

```
sudo cp -ir /home/rmorgan/Desktop/d3a-icons/ /usr/share/icons/
#I've included the -i option to make it interactive
#that way you can confirm each step with 
#a yes or no answer
```

The command you used 'sudo nautilus' should actually be used like this..

```
gksudo nautilus
```

It not really a good idea to be changing the permissions on system files.

---

### Post by kwyjibo on 2006-04-16
thanks a lot.  I have set the file permissions back and created myself a link to run gksudo if i have to copy stuff and dont wanna use terminal.  i'll go look, but quicky what is the difference between setting it to gksudo rather than sudo, they both seem to run it the same way?

---

### Post by siminone on 2006-04-16
gksudo is a gnome front-end for sudo so you can setup 'launchers' in desktop to run programs as root.

---

### Post by dunomous on 2006-04-28
If copying a folder from my windows partition, before I do so, I'd like to know if I can go ahead and set properties/permissions, to allow access without root. if I must do so after copying the folder, that's fine. Either way, I apparently am not gleaning that information out well if it's already in this thread.

---

