---
title: "Drivel Blogger blues"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by aseneca on 2006-08-22
Anyone familiar with usins drivel with blogger.  I'm using the gmail/blogger configuration.  I keep getting the username/password mismatch error.  However, I have been able to login manually using the same information without a hang up (manually directly from the site).

I've tried several other applications which support blog entry posting.. no luck....

aseneca.blogger.com nothing works (drivel, gnome, blogtk)
aseneca.livejournal.com -- works (drivel, gnome, blogtk)

jason](*,)

---

### Post by bestiarosa on 2007-08-07
Late for the party but probably the server name is wrong. If you're using blogger, it's: [http://www.blogger.com/api/RPC2](http://www.blogger.com/api/RPC2)

Good luck!

---

### Post by kg6gfq on 2007-09-12
Currently drivel does not support the new blogger with the google-account-based login.  I've read that the SVN version has it, but I've also read that recent SVN versions are broken.  BloGTK supports the login system, I believe, but does not use the Atom API for posting and thus you cannot enter post titles.  You might try the gnome-blog applet, but I think it's minimalistic.  

I'm actually planning to use Thunderbird:  Set it to receive entries via the RSS reader and send new ones to the special address provided with your blogger account.  It lacks editing capabilities, though.  Good luck finding something that works for you!

---

### Post by sageb1 on 2008-01-06
both blogtk and gnome-blog applet cannot post titles like you are at the keyboard, probably because users can only create titles live.

i'd like to believe it is connected indirectly to the "live" test using the image showing the 5+ character "password".  I don't think there is anything to distinguish the title when either the tk tool or the applet post it, probably through a mail-like handler.

does this mean email to blog also cannot post a title correctly??

---

### Post by Cyberponcho on 2008-04-01
> **bestiarosa said:**
> Late for the party but probably the server name is wrong. If you're using blogger, it's: [http://www.blogger.com/api/RPC2](http://www.blogger.com/api/RPC2)

Good luck!

Thanks, this solved my problem, i couldn_#t figure out which server name to use, thank you very much :)

---

### Post by gcastell on 2008-04-20
One tool you might want to try too, is Petrus:

[http://petrus-blogger.peterp.org/](http://petrus-blogger.peterp.org/)

---

### Post by quinnten83 on 2008-06-17
Has anybody gotten this working right?
I can connect using the API address, but whenever I try to send a post, i get an error message that it couldn't connect to the server.
Also when I look into my older posts, I only see the maintenance messages that blogger posts, not my own blog.

---

