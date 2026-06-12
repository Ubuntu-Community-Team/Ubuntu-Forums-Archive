---
title: "Networking Woes- How to do it right?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2007-01-06
I wanted to share folders between my two computers. So I right clicked share folders and I receive a pop up message telling me I needed to install nfs or samba. No Problem , i hit ok and downloaded packages and dependencies for both.

Now I right click the folder I want to share, I asks me what I want to share it through. 
Windows networks (SMB)
Unix Networks (NFS)

Seeing how both computers are running Linux I chose Unix Network (NFS). I then hit Add and get another window asking me to choose allowed hosts. I can choose to:
Specify Host Name
Specify IP address
Specify Network

This is where I am lost. I am looking to just share my comics, videos, picture and Download folders between two computers. I want be able take content from my desktop and copy it over to my laptop and vise versa. What do these mean? I don't want to start doing something without knowing what I am doing. Which setting do I use, how do I keep my home network secure and what really best for my setup.

Thanks, network the two together is the last obstacle on having everything setup right in Linux.

---

### Post by Sasa_Ivanovic on 2007-01-06
type 
```

cat /etc/hosts

```
and use the info from there to fill in the blanks.

---

### Post by redDEADresolve on 2007-01-06
Thats that useful info, but I wanted to know how and why of what I'm doing. I don't know how to use the content of: 
```
cat /etc/hosts
```

---

### Post by eekbot on 2007-01-06
i recommend you specify by the IP address and then you type the IP of the computer you want to connect to.  usually, it's something like 192.168.0.x.

i'm not sure about specifying the network option, but specifying the host is telling your computer to look for your other computer's name and then find the associated IP of that computer.

hope that helps.

---

### Post by redDEADresolve on 2007-01-06
ok I type the ip address of the computer i will connect to, is this the most secure method?

---

### Post by redDEADresolve on 2007-01-06
ok i tried entering the ip address, the folder now says shared but i can't access. how do i do this and can anyone give me help on what i'm supposed to be doing

---

### Post by eekbot on 2007-01-06
how are your computers connected together?  if they are directly connected, you need a crossover cable.  if you have something in the middle (such as a router), then you can use regular ethernet cables.

after you have the computers sharing with each other, you go to something like "places -> network servers" (sorry, i can't remember off the top of my head and i'm on a windows pc right now).

if that doesn't help, here's another thread that could be of assistance:
[http://ubuntuforums.org/showthread.php?t=315962](http://ubuntuforums.org/showthread.php?t=315962)

good luck, and i hope that helps some.

---

### Post by redDEADresolve on 2007-01-06
my two computers are wireless. i have them both setup and connecting to the internet perfectly through my wireless router.

---

### Post by redDEADresolve on 2007-01-07
Still looking for help. I want to learn what these options mean as well as how to use them.

I don't want you to just hand me a fish, teach me how to fish.

---

### Post by scrooge_74 on 2007-01-17
Try this go to places>conect to server pick the connection you want (you can use SSH, if you install ssh server) and give the info for user, the folder to connect and you are practically done
then click on the link in your desktop give the password of the user on the other machine and you should be connected

---

### Post by redDEADresolve on 2007-01-17
i finally figured it out thanks for your help

---

