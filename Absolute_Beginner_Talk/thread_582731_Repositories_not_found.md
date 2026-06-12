---
title: "Repositories not found"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by oneinchpixel on 2007-10-20
I'm having some trouble with a new install of Gutsy (Ubuntu 7.10) 

I can install fine, infact, clearly this is the best Ubuntu build ever, however...

I can't seem to connect to any of the repositories around the globe. 

I'm in Australia and I know that they can be a little slower to update the repositories locally, but even the main repositories seem to be down. 

Hell I've even tried to use others from USA, the UK and Korea, all that bring back that the repositories for the AU locality are not found. 

The other interesting thing I am finding is that when I install 7.10 it can't seem to find anything when scanning the mirror at 82% (clearly a small issue, as when I do an update it finds the security updates).

Oh and here is the kicker, and I think the major issue I'm having, for some reason, Ubuntu 7.10 is dropping my router connection to the internet. My router is not USB it is a standard ethernet router that connects to the web. 

I can still use firefox, so I know the connection is active and live, but I think that there might be a problem with Ubuntu being able to port through the router to connect to the repositories.

Any thoughts?

---

### Post by TheWizzard on 2007-10-20
please post the output of
```
cat /etc/apt/sources.list
```

---

### Post by 001100 on 2007-10-20
ok try reinstalling gusty again with an internet connection if you installed when it was relesed teh servers wre overloaded try again thats what I had to do

---

