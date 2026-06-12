---
title: "How do I 'create a file!"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Oddjob74 on 2007-03-27
I have found in the forums how to enable my wireless button LED on my HP Laptop. Unfortunately I don't know how to Create the file I need to give the command to as was said in the post! 

you edit or create the file /etc/modprobe.d/ipw2200

and inside the file needs to be

Code:

options ipw2200 led=1

Could someone pls tell me how to do this! Thanks in advance! :) :confused:

---

### Post by aysiu on 2007-03-27
Type or paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo nano /etc/modprobe.d/ipw2200
```

---

### Post by charles.g.moore on 2007-03-27
you could go to the directory from within the CLI
then gksudo ipw2200
type the stuff
save

---

### Post by Kobalt on 2007-03-27
Try this command line : 
```
gksudo gedit /etc/modprobe.d/ipw2200
```
It will open up the file with the text editor and you'll be able to modify it.

---

### Post by compmodder26 on 2007-03-27
Just type: "sudo gedit /etc/modprobe.d/ipw2200".  If the file already exists, it will allow you to edit it.  If it doesn't exist, when you choose to save your changes, it will create it for you.

---

### Post by Oddjob74 on 2007-03-27
> **aysiu said:**
> Type or paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo nano /etc/modprobe.d/ipw2200
```

Well I found that my wireless is actually an ipw3945. So when I input that in the way you showed I get:


install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
        /sbin/ipw3945d-$(uname -r) --quiet
remove  ipw3945 /sbin/ipw3945d-$(uname -r) --kill ; \
        /sbin/modprobe -r --ignore-remove ipw3945















                                [ Read 4 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

Baffled me!:confused:

---

### Post by Bachstelze on 2007-03-27
Ctrl+O, Enter, Ctrl+X.

---

### Post by Oddjob74 on 2007-03-27
Right Ihave tried every option given and they all in a roundabout way lead to the same details: 
         
           install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
	/sbin/ipw3945d-$(uname -r) --quiet
remove  ipw3945 /sbin/ipw3945d-$(uname -r) --kill ; \
	/sbin/modprobe -r --ignore-remove ipw3945


Now supposedly I have to enter: 
options ipw3945 led=1

to enable the LED! How do I do that.?!

I really am stuck guys and can't get my head round Ubuntu at the moment. And I thought I was quite quite experienced with PC's!! Well windows at least!!
  :confused: :confused: :confused:

---

### Post by ceeg on 2007-03-27
Can you provide a link to the guide you are attempting to follow?

---

### Post by Oddjob74 on 2007-03-27
> **ceeg said:**
> Can you provide a link to the guide you are attempting to follow?

It wasn't a guide but from another post which I can't find again! Just said:

you edit or create the file /etc/modprobe.d/ipw2200

and inside the file needs to be

Code:

options ipw2200 led=1

This is to try to get my LED light on my wireless button working! Petty, I know but its bugging me!

---

