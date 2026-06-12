---
title: "I changed a setting I shouldn't have and broke Ubuntu (Help)"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Krusader3z on 2007-09-01
I was trying to change my home directory through the GUI (Administration -> Users) and when I did change it and reboot i got an error telling me 

"User's $HOME/.dmrc file is being ignored. "

I looked at some threads regarding this issue but I still couldnt figure out what to do. I am able to Ctrl+Alt+F2 and login to a command prompt. 
Anyone?

---

### Post by banewman on 2007-09-01
Try this as a start - never had to myself - at the command prompt type - gksu users-admin . That should bring the GUI for users & groups up so you can undo the wrong.:)

---

### Post by kellemes on 2007-09-01
[https://answers.launchpad.net/ubuntu/+question/7296]("https://answers.launchpad.net/ubuntu/+question/7296")

---

### Post by Krusader3z on 2007-09-01
Hmm. I tried both suggestions so far. The first suggestion didnt work because the application was unable to launch and the second one that redirected me to a link telling me to do this

sudo chmod 700 /home/mike

failed to solve the problem. I should add that after the first error comes up another box appears telling me "Your session only lasted less than 10 seconds. If you have noy logged out yourself, this could me that there is some installation problem or that you may be out of diskspace"

I am most certainly not out of diskspace..

---

### Post by Skrynesaver on 2007-09-01
when you log in at the command prompt and 
```

cat ~/.dmrc
ls -l ~/.dmrc

```
do you own the file
is it readable and writeable by you only
does it contain something like the following
```

[Desktop]
Session=gnome

```

---

### Post by Krusader3z on 2007-09-01
If it helps, what i did was change my default (i think) directory from /home/mike to just /

---

### Post by forestpixie on 2007-09-01
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

I followed this when I had the same problem

---

### Post by Krusader3z on 2007-09-01
When I do 

cat ~/.dmrc

it says " cat: //.dmrc: No such file or directory"

I did this both at / and /home/mike

---

### Post by Krusader3z on 2007-09-01
FORESTPIXIE

I followed those instructions already and nothing changed. I am still getting the 644 error followed by an error telling me that my session lasted less than 10 seconds.

---

### Post by Krusader3z on 2007-09-01
Thank you everyone for the suggestions. I think i'm going to do a reinstall (I could use the practice anyways)

---

