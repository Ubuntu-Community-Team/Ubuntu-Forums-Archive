---
title: "Songs in windows drive in amarok"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by JJFO on 2007-04-01
All my music is on my windows drive, I can access it and it plays fine, but how can I add my songs to my Amarok collection?

---

### Post by DoorGunner on 2007-04-01
make sure you have your

settings>Configure Amarok>Collections and select sqlite or mysql whatever is appropriate for your set up. 

I have my music located on a separate vfat partition. It seems that it takes amarok a long time to build the collection when I first moved it there. Eventually it will show up. I dont know why it does this but it will work.

---

### Post by JJFO on 2007-04-01
It was already on SQLite, and i switched it to MySQL, but I have no idea what this means and I have to connect to something. How can I set this up?

---

### Post by DoorGunner on 2007-04-01
Im not sure if you already have mysql for something already. you would need to go into phpmyadmin and setup an amarok instance then just use your regular password and username for mysql to allow amarok to store data.

SQLite is ok too and much simpler. If you switch it back to SQLite you will have your content. It just may take a bit of time.....

As well i was just wondering if your Tools>Script Manager>general if your cover copy is swithced on to run
also check to see that > Lyrics Lyric is set to run as well.

If the scripts arent there just go to the add more scripts and load them up.

That will ensure you have stuff to add to SQLite

---

