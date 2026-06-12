---
title: "Converting MDF to ISO"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-05-06
Hello everyone,
Love ubuntu, but right now i am trying to install a windows game through wine and  there was many problems needless to say we found out the problem is that the CD was just too messed. So i downloaded a copy but it was *.MDF not *.iso i asked this same question in the IRC channel and i was told about MDF2ISO, downloaded it and now i am wondering how to get it working. IF someone knows of a easier program to use please give me a hint

---

### Post by starcraft.man on 2007-05-06
No problem, mdf2iso is an easy terminal program to use :)

Here is the basic formula:

```
mdf2iso --cue source destination
```

--cue tells the program to convert it to a cue bin format, you can also use toc if you want that format but bin is more standard.

Source is the original file, it should be for instance /home/user/Desktop/X.mdf

Destination is where you want the file to end up, if you want it on the desktop too just type in the same name and put a 2 on the end, /home/user/Desktop/X2.cue

user = your user name.

That should be it :) You can also type in mdf2iso to the terminal to get their reminder if you ever forget.

---

### Post by Robert98374 on 2007-05-06
Alright thanks for that. The funny thing is that its Starcraft that i was having the Issues with :-)

---

### Post by Robert98374 on 2007-05-06
i thought that it turns it into an ISO?

---

### Post by Robert98374 on 2007-05-06
i juat tried it just to see if it would work and its throwing up the error message 

robert@Bobby's Computer:~$ mdf2iso cue </home/oem/completed_torrents/star_trek_voyager_elite_force/eliteforce.mdf> [/home/oem/Desktop/eliteforce.cue]bash: [/home/oem/Desktop/eliteforce.cue]: No such file or directory
So i am totally lost at this point, i tried to check out the IRC channel for help but i didnt find the channel

---

### Post by starcraft.man on 2007-05-06
> **Robert98374 said:**
> i juat tried it just to see if it would work and its throwing up the error message 

robert@Bobby's Computer:~$ mdf2iso cue </home/oem/completed_torrents/star_trek_voyager_elite_force/eliteforce.mdf> [/home/oem/Desktop/eliteforce.cue]bash: [/home/oem/Desktop/eliteforce.cue]: No such file or directory
So i am totally lost at this point, i tried to check out the IRC channel for help but i didnt find the channel

take off the <> and [] those are only in the demo, you don't actually use them... you want this.
```

mdf2iso --cue /home/oem/completed_torrents/star_trek_voyager_elite_force/eliteforce.mdf /home/oem/Desktop/eliteforce.cue
```

That should do it... methinks, been a while since I converted an mdf, try it and tell me if ya get an error?

I should probably sign into the IRC channel from time to time, thanks for reminding me... :)

And, cue is similar enough to ISO that you can burn it with k3b or any other program. Or extract it if you like.

---

### Post by Robert98374 on 2007-05-06
it did it fine, lol but how do i make it into an ISO?

---

### Post by kpkeerthi on 2007-05-06
mdf2iso sourcefile.mdf target.iso

---

### Post by Robert98374 on 2007-05-06
thats was simple :-)

---

### Post by starcraft.man on 2007-05-06
> **Robert98374 said:**
> thats was simple :-)

ya, whupps, sorry I forgot to put iso on the end >.>

Anyway, have fun with your game now :)

---

### Post by Robert98374 on 2007-05-06
Yep will do now i need to move onto the second phase of getting it going :-)

---

