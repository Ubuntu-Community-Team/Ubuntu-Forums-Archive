---
title: "setting the date..."
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2006-11-15
hi,

im running a server with ubuntu 6.10 server edition.

Whenever i type date, i get a wrong day/date/month/year (its thinks its 1997!).

However i have no idea on earth how to set this thing.

How do i do it in ubuntu 6.10 server? date --set=111522172006 

doesnt work.

Whats the command? the help file says "string" which is oo soo specific...

---

### Post by 13ojo on 2006-11-15
ps i cant sudo anymore,

it says "timestamp too far in the future"

yay...

---

### Post by taurus on 2006-11-15
Reboot your machine and check in the BIOS to make sure you have the right date and time.  And if it does, then boot into recovery mode and see if both date and time are correct now.  If not, run

```
date 111509302006
```
where
11 = month
15 = day
09 = hour
30 = minute
2006 = year

---

### Post by jd65pl on 2006-11-15
Regarding your sudo problems see this page [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Ben Sprinkle on 2006-11-15
Just did this last night, do like this:
```

date --set="Tue Nov 15 21:21:00 2006"

```
Works great. :)

---

### Post by jd65pl on 2006-11-15
> **Goat Spirit said:**
> Just did this last night, do like this:
```

date --set="Tue Nov 15 21:21:00 2006"

```Works great. :)


Erm I think it may be wednesday 15th, well it is here lol!

---

### Post by Ben Sprinkle on 2006-11-15
Oh yes, I typed Tue because I did that last night for Nov 14, lol brains stuck on that date. :S

---

### Post by 13ojo on 2006-11-15
hmm its a server, with only ubuntu.

hence it has no screen or keyboard...

also "recovery mode" as listed in that link, didnt come up in the days when it did have one there.

plus i have to be sudo to change the day....

---

### Post by Ben Sprinkle on 2006-11-15
No screen or keyboard??? Are you mad?!

---

### Post by 13ojo on 2006-11-15
woohoo,

sudo -r now about ten times gave me the error then finaaly decided to reboot.

this reset the time to what it was, allowing me to sudo,

and goat spirits command helped :D yay.

---

### Post by 13ojo on 2006-11-15
its a server, its merely a proof of concept thing eg print servers etc.

yes friend i believe many servers would have no screen or keyboard. screen and keyboard seems pointless anyway, i get a terminal via SSH which is the same as id see on a screen and keyboard. :D

ps setting the date fixed the apt-get errors too

---

### Post by Ben Sprinkle on 2006-11-15
Your welcome anytime mate. :)

---

### Post by Ben Sprinkle on 2006-11-15
Are you remoting to the comp from another comp then?

---

### Post by 13ojo on 2006-11-15
yes i most certainly am SSH :D using putty from windows, or the terminal in linux.

has anyone heard of "QOSbalancer"? i was told its the program i want, but google yields nothing and ubuntu repositories dont have it.

(the whole date quest was headed towards this utility)

---

### Post by Ben Sprinkle on 2006-11-15
Now I understand why you have no screen or keyboard because of remoting. :)

---

