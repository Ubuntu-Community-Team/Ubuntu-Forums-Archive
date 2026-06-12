---
title: "Help a noob add some repositories..."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-08-08
OK, so I can follow instructions reasonably well.  Nevertheless, I am keen to try out the newest version of Rhythmbox, which is available here:

[http://blog.blackdown.de/2007/06/01/rhythmbox-0110-for-ubuntu-feisty-fawn/](http://blog.blackdown.de/2007/06/01/rhythmbox-0110-for-ubuntu-feisty-fawn/)

I have figured out how to add the repositories, but I have NO idea what to do with the key thingie.  I'm sure this is quite simple, but I don't want to risk breaking things...

---

### Post by Bachstelze on 2007-08-08
Just as said :

```
wget http://blog.blackdown.de/static/gpg.asc -O - | sudo apt-key add -
```

---

### Post by limberlegs on 2007-08-09
Thanks for your help.  I managed to get it to work, but when I tried out the new rhythmbox, the playback was crackling and sound quality was really poor.  I've decided to just revert to the old rhythmbox for now, until everything is working properly with the new version.  I've removed the new repositories, but do I have to do anything to reverse the command that I used to get the key?

---

