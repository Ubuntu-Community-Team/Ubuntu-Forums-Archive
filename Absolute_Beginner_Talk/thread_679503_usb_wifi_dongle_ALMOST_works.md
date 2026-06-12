---
title: "usb wifi dongle ALMOST works"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by pcrussell50 on 2008-01-27
it's a linksys as per [here]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775N09")

AND it all but works perfectly right out of the box in a fresh install of 7.10.  I can see all three of my unsecured wireless networks when I click on the "dual monitors" looking symbol near the upper right hand corner.  It shows their signal strengths and everything, and it beckons me to choose one.  The trouble is, when I select one, any one, it does that "circular thing" and never connects.

Searching on usb wifi dongles fails to reveal this particular problem.  I feel that I'm 99.9% there, but I'm darned if I can figure out the last step.

-Peter

---

### Post by Paul86fxr on 2008-01-27
I had the same problem, this is how I did it.
1>try 'connect to another wireless network'
2. when it asks for a name press x or y or something,doesnt matter,press connect.
3while its trying to find x, reselect the connection you wanted in the first place and it should connect, I have had the same thing many times and it seems to work.

Paul

---

### Post by Gone fishing on 2008-01-27
Id use the manual configuration, I've never had it not work although you might need to reboot before it comes up. Why are you using unsecured networks even a simple WEP encryption would be much better - I also seem to remember reading somewhere that connecting to an unsecured network can be a problem.

---

### Post by ugm6hr on 2008-01-27
> **pcrussell50 said:**
> it's a linksys as per [here]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775N09")


There are 4 revisions of this device.  So that link doesn't help.  I suspect it is Rev 4 you have, but this will help identify it:

```
lsusb -v
lshw -C network
```

If it is a Rev4 - this link will help: [http://ubuntuforums.org/showthread.php?p=4215254#post4215254](http://ubuntuforums.org/showthread.php?p=4215254#post4215254)

---

### Post by pcrussell50 on 2008-01-27
> **Paul86fxr said:**
> I had the same problem, this is how I did it.
1>try 'connect to another wireless network'
2. when it asks for a name press x or y or something,doesnt matter,press connect.
3while its trying to find x, reselect the connection you wanted in the first place and it should connect, I have had the same thing many times and it seems to work.

Paul

paul, 

i love this idea, but once i've complied with step 2, there is no way to comply with step 3 because i can't find the list of available networks while it's trying to connect to one.  am i missing something?

-peter

---

### Post by pcrussell50 on 2008-01-27
> **ugm6hr said:**
> There are 4 revisions of this device.  So that link doesn't help.  I suspect it is Rev 4 you have, but this will help identify it:

```
lsusb -v
lshw -C network
```

If it is a Rev4 - this link will help: [http://ubuntuforums.org/showthread.php?p=4215254#post4215254](http://ubuntuforums.org/showthread.php?p=4215254#post4215254)

Why yes, I do have rev4 :)

How about I follow your link and "meet" you over there?

-Peter

---

### Post by ugm6hr on 2008-01-27
> **pcrussell50 said:**
> Why yes, I do have rev4 :)

How about I follow your link and "meet" you over there?

-Peter

Going to be offline for a couple of hours, but I'm sure someone else will help til then :)

Maybe stick with your own thread, since boixter hasn't confirmed that it is solved for them, and it can get confusing having 2 people being advised in 1 thread at the same time.

But feel free to post on boixter's thread to let them know you're in the same situation... A problem shared and all that!

---

