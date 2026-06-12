---
title: "Where to begin, NAS, Print, file, web, media server...?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by ToxicDoctor on 2007-01-11
For the first time on a forum, I can declare myself to be a complete and utter NooB!!! Ok, so yes, Im aware of, but have never seen or used any non windows/dos based os before now... my only saving grace, is im IT literate, being a PC Support/Network Engineer, albeit in a windows based environment....

I was guided in this direction after google-ing for NAS solutions, and from other forums... after discovering that affordable home NAS solutions were, quite frankly... very poor performers  -  although they offered some cool features.  As I have plenty of spare pc parts, I have decided to put them to use building a more customised solution...

What I would like, however, is some/all of the fuctionality of the dedicated NAS devices, most of which, seem to run on linux based code... so it seemed an obvious choice, a linux based pc/server... but I need pointing in the right direction.

Several of the NAS devices I was looking at all share the same functionality:

Multimedia Station
Download Station
Mirror Station
Disaster Recovery 
Web Server
Printer Server
File Server
FTP Server ed. 
Backup Server 

Now from what reading I have done over the last day or two, can most, if not all of these functions be developed using ubuntu??

Would I be best off starting with the desktop (more user friendly, gui, may be easier to pickup the basics)? or would the server version be the only platform to go for  -  and jump in at the deep end??? 

Any advice, tips, starting points would be greatly appreciated... I feel this is a project to get stuck in to, but Im not expecting an overnight solution!!!

Thanks

---

### Post by jvc26 on 2007-01-11
You could put the server on and then add a desktop environment (a light one) which wont use too much resources but will give you a GUI to work with and get used to. For instance you could put on the xubuntu desktop via an install:
```

sudo apt-get install xubuntu-desktop

```
If it throws back something about repositories or packages not found then you can take a peek on:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
About adding extra repositories, then try again.
That will give you the Xubuntu desktop which should allow you to have a GUI to do some things with. Then at a later date should you no longer want the desktop you can merely go:
```

sudo apt-get remove xubuntu-desktop
**or**
sudo apt-get --purge remove xubuntu-desktop

```
To remove it and leave you with just the server terminal line.

Il

---

### Post by ToxicDoctor on 2007-01-11
Thanks for the advice... it was late last night when I got server installed, and I do remember browsing some threads telling me exactly that.. but as you point out, I was getting similar errors, despite doing an online update from the command line...

Just one thing, is all of the functionality Im looking for qvailable through ubunto?? Just so that I know im on the right path, even if it is likely to be a long and winding one for me!!!

Still, its something to get my teeth into..!!

Thankyou

---

