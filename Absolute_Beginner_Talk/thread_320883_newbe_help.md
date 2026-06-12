---
title: "newbe help"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by troll380 on 2006-12-18
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
what is this error and how do i fix it 
i am a new user

---

### Post by NeoLithium on 2006-12-18
It just means that one of the packages wasn't set up right, so it's asking you to just run the command to allow it to be reconfigured for your system. In a terminal, just run what it tells you: ```
sudo dpkg --configure -a
```

---

### Post by troll380 on 2006-12-18
ok i ithink its working  relly slow it seems to be downloading a new file

---

### Post by NeoLithium on 2006-12-18
Well, if you were running an update after a fresh install, or getting a big package, it can take a while, depending on the connection, but I wouldn't worry about it; once you have all of your software installed that you might want, updates are generally quick.

---

### Post by troll380 on 2006-12-18
ok it is takimg a loog time im on a fast conetion ie cable
i am new  to  this op  sys so fare it looks good
 but im haveing   a case of newbe blues
as i can use other opsys and im tired of that  one  thats every where
so now in need to find some p2p software that will work with this opsys 
any hints?
thanks

---

### Post by NeoLithium on 2006-12-18
Well, I use frostwire, works good for me, when I dont' opt for torrents.  It should be in the repositories, so you can just ```
sudo aptitude install frostwire
```

---

### Post by troll380 on 2006-12-18
ok it is on a 5.5m download this is taking for ever is there a faster server?

---

### Post by troll380 on 2006-12-18
we are looking at 2 hours or more

---

### Post by NeoLithium on 2006-12-18
5.5MB isn't that big of a download; by default when you installed ubuntu, it would have set up to download from mirrors that are close to your actual location; so you really shouldn't be getting that slow of a speed...

It might just be the servers are busy with other people downloading as well, just have a bit of patience, sometimes even the fastest servers get bogged with downloads from people and go slow for a little while.

---

