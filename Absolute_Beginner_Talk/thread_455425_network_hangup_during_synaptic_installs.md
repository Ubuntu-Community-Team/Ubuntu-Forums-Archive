---
title: "network hangup during synaptic installs"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-26
I've been having a problem recently that synaptic downloads often periodically hangup or time out.  While this happens, Firefox and other internet applications still maintain their connection.  If I restart the synaptic install and try again, it usually works for a few minutes and then hangs up again.  This isn't a good way to have to do things, especially since I jumped ship from OpenSUSE 10.2 specifically because of package manager problems.  Are any other users having these issues with synaptic?  Is there any way to fix this?

---

### Post by coffeecat on 2007-05-26
How long has this been going on for? If firefox and other internet-connected apps are maintaining connections OK, then this doesn't sound like a Synaptic problem at all. I've not experienced this. More likely is that the repository server you are connecting to is having problems, being maintained, or being overloaded. Hopefully this will be a temporary situation

Have a look in your /etc/apt/sources.list file to see which servers apt and Synaptic are using. It will vary depending on your geographical location, so if there is a server problem only some people will experience it. Once you have determined the server, suggest you do a forum search to see if anyone else is getting the same.

Or you could post the contents of sources.list and someone might comment, or you could think about changing your default servers.

---

### Post by paparucino on 2007-05-26
> **laptoplinux said:**
> Are any other users having these issues with synaptic?  Is there any way to fix this?
These problems are related to server. Try to change the repos.
Try using "the original". 
Edit your
```

su gedit /etc/apt/sources.list

```
and remove all country related informations. usually these are the first two letters after http://
And remove the point too :-)

---

### Post by ebe326 on 2007-05-26
I have been having the same problem. I've had problems on two different computers, one with ubuntu(wired desktop) and one with kubuntu(wireless laptop). So I know it's not just a synaptic or adept issue. I have also had problems downloading files through firefox. I have no problem at all just browsing the web though. There is another discussion about this on the kubuntu forums. Check out this link [http://kubuntuforums.net/forums/index.php?topic=3083292.0](http://kubuntuforums.net/forums/index.php?topic=3083292.0). I've tried playing around with DNS like the other post says but it hasn't helped. It has apparently helped others, but I'm not sure how DNS would have anything to do with this since it stalls in the middle of a download. I really don't know much about networking but I thought DNS only came into play at the beginning while name resolving. I also tried removing the country info in my sources list and I'm still having the problem. Whatever it is, I hope someone can figure it out because it prevents me from getting updates or downloading files. I will keep looking into this and reply back if I find anything out. 

david

---

