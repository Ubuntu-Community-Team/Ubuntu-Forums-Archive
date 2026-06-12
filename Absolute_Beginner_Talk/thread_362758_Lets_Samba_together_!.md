---
title: "Lets Samba together !"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-02-16
Got Samba turned on (was already part of ubuntu it seems) loaded up a shared folder or two , called "Problem Child" (the space isn't going to cause a problem is it ? ) dumped some mp3's in it, hit the button on my kvm switch to move to the windows xp machine , and start searching the network. 
   Xp see's it , but wants a user id and pass. The only user id / pass I know is the one I use to log onto ubunto , and it doesn't work  ? 

   Going the reverse route , I set up a shared folder on xp , and then realized I didn't have any Linux tools to go find it , even though I knew the folders ip address (192.168.2.1  ... we're all in behind that same tiny belkin router) 

A few hints would be nice.  :)
:popcorn:

---

### Post by dbbolton on 2007-02-16
go to "places > connect to server"

enter just the name of your windows computer in the first field, and the name of the shared folder in the "share" field. NOT the path to it.

you might also try setting up a common account with windows and linux- i.e. exact same username and password.

---

### Post by koconnor100 on 2007-02-16
Like two ships , passing in the night ... 

both computers can see each other ...but they just don't quite communicate. They both find the MSHOME network, they both find themselves and the other computer on it , and then they both fail to see any shared items at all. Oh they see their own shared items ... but they don't see shared items on the other side ... Windows demands a user id / pass and won't take the ubutuntu log on , and ubuntu just doesn't see anything at all on the windows server. 

Time to find a quick and dirty linux ftp server. This samba business just isn't working out.

---

