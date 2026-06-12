---
title: "synaptic package manager question.."
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by SpawnSC on 2006-07-31
ok on my laptop at work the one a friend got me me using with ubuntu on it and encouraged me to use it for my desktop at home has more packages listen in the manager then my desktop.

If you click on all on the laptop I have 18332 packages listed.  On my desktop at home I have 4403... thats a HUGE drop and I don't know if he did something to update the packages to show more or what anyone clue me in? I would ask him but his on vacation :mad:

---

### Post by Titus A Duxass on 2006-07-31
He probably has more repositories in his sources.list.
Edit your sources.list and remove the # from each line that looks like a URL.

---

### Post by DJ Scribblinni on 2006-07-31
More than likely he has enabled the extra repositories that are not enabled by default.  These would be found in the /etc/apt/sources.list  
And if you really want to you can just uncomment those extras by getting rid of the # sign in front of that line.  Do the update and poof, 18375 packages will be available.

---

### Post by SpawnSC on 2006-07-31
thanks that was it :) up to date now :KS

---

### Post by az on 2006-07-31
> **DJ Scribblinni said:**
> More than likely he has enabled the extra repositories that are not enabled by default.  These would be found in the /etc/apt/sources.list  
And if you really want to you can just uncomment those extras by getting rid of the # sign in front of that line.  Do the update and poof, 18375 packages will be available.

It's easier to just use synaptic to add the repositories.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by DJ Scribblinni on 2006-07-31
> It's easier to just use synaptic to add the repositories.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Sorry, I don't use Synaptic...  But I still knew that :^o

---

