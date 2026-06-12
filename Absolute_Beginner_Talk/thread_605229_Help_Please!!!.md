---
title: "Help Please!!!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-11-06
Today when I went into Ubuntu, I got a message at login saing that I needed to change my home folder permissions to 644. Bo problem, I type in:


sudo chmod -R 644 ./


And then everything stopped working. How do I fix this using Recovery mode???

---

### Post by Dr Small on 2007-11-06
Bah, I have been through this 50 times or so.
Give me a couple of minutes and I'll dig up the solution.

---

### Post by Dr Small on 2007-11-06
Try this:
[http://ubuntuforums.org/showpost.php?p=2035142&postcount=13](http://ubuntuforums.org/showpost.php?p=2035142&postcount=13)

And this one:
[http://ubuntuforums.org/showthread.php?t=535555](http://ubuntuforums.org/showthread.php?t=535555)

---

### Post by shamushand on 2007-11-06
Lol, you I see I'm not the only one who's locked himself out of his own desktop. Trying your solution right now... :)

---

### Post by Dr Small on 2007-11-06
> **shamushand said:**
> Lol, you I see I'm not the only one who's locked himself out of his own desktop. Trying your solution right now... :)
Yeah, I have done it, my sister has done it, my friends have done it... So, I get used to it after awhile. I need to add one of those links to my bookmarks :| :p

---

### Post by shamushand on 2007-11-06
Didn't work... When I try to log in, I just get a message saying my session only lasted less than 10 seconds because Gnome couldn't write to the home directory. Failsafe doesn't work either. What are the commands that I have to type in recovery mode? Do I need to put 'sudo' before them? :confused:

---

### Post by Dr Small on 2007-11-06
You shouldn't have to.
Post here exactly what you tried.

---

### Post by Evil Wayz on 2007-11-06
Out of curiosity if a failsafe session works, what do you do then?

---

### Post by shamushand on 2007-11-06
First I tried:

```
sudo chown shamus /home/shamus
sudo chmod 755 /home/shamus
sudo rm -rf /home/shamus/.dmrc
```

Didn't work, so I tried:

```
sudo chmod 644 /home/shamus/.dmrc
sudo chown shamus /home/shamus/.dmrc
sudo chmod 755 /home/shamus
sudo chown shamus /home/shamus
```

Didn't work either. What do I do... :(

---

### Post by shamushand on 2007-11-07
Please! Help me! :(

---

### Post by underdog512 on 2007-11-07
Probably the easiest thing to do at this point would be to use recovery mode to create a user account and make sure you give it all the super user rights.  

then just transfer the files from your old home folder into the new home folder and delete the old user account.

hope this helps!! If it doesn't we will be here.

---

