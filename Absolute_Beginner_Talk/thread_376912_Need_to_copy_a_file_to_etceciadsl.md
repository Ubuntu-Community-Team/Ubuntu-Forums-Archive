---
title: "Need to copy a file to etc/eciadsl/"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by windozer on 2007-03-05
Please tell me how to do this.. 
I feel like I have to jump through hoops to do the simplest things in ubuntu! Whats wrong with right click copy right click paste [enter password]? :(

---

### Post by ardchoille42 on 2007-03-05
> **windozer said:**
> Please tell me how to do this.. 
I feel like I have to jump through hoops to do the simplest things in ubuntu! Whats wrong with right click copy right click paste [enter password]? :(

If you want a gui way to do that, open a terminal and run:

```

gksudo nautilus

```

That will launch a nautilus window with root privs. But, be careful with it.. root can do anything.

---

### Post by annda on 2007-03-05
i believe it's not a good idea to let users put some stuff in system directories unless they know what they are doing.

however, it IS very simple:
a) in the terminal type
 sudo mv path_to_your_file /etc/eciadsl

b) open nautilus as root by
 gksudo nautilus and copy and past if you prefer.(it just takes longer)

---

### Post by ardchoille42 on 2007-03-05
> **annda said:**
> i believe it's not a good idea to let users put some stuff in system directories unless they know what they are doing.

Well, that is a very good point.

---

### Post by windozer on 2007-03-05
Thanks, I will try your suggestions. I have to copy that file there to (hopefully) get my modem to work. 
Shouldn't it be easier than this though? How is a new user supposed to figure this stuff out without asking on a forum? I have had to do a lot of searching to even get as far as knowing I needed to download that file and I only discovered that by reading an obscure blog page I found via Google. More or less everything should be doable without the terminal in 2007, especially very basic stuff like copying files. And especially in an OS marketed as "Linux for human beings"! I must be an alien or something. :confused: 
> i believe it's not a good idea to let users put some stuff in system directories unless they know what they are doing.
It's my hard drive. The user should be able to do *anything* they want to their own files, at their own risk. It's like soviet russia "computer control you"..
[/rant]

---

### Post by annda on 2007-03-05
> **windozer said:**
>  It's like soviet russia 

sorry but i have to disagree. it's like linux. if you want to blow your system to pieces, you are welcome. nothing (except that little sudo or su command) will stop you. just do it because you want to, not because you are distracted by your cat and click somewhere by mistake.

other than that, you can really do most stuff using GUI. i put a launcher to my panel to quickly run nautilus as root so i sometimes can click away too :-) but usually the mouse is just too much hassle.

remember, you have a choice and can do it the way you like. and we are glad to help you avoid the console.

---

### Post by satx on 2007-12-09
All,

It is very easy to cut and paste in Ubuntu. For example, go to PLACES=>Home Folder, right click on file, do Edit Copy. Then go to Places=>(wherever), right click on blank space, Edit Paste.

SATX

---

