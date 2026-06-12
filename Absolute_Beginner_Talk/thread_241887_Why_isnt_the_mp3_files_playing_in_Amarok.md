---
title: "Why isnt the mp3 files playing in Amarok?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2006-08-22
I just instaled Amarok with MYSql both for first time. But the problem is that when i try to play a song its just shufling along in the list not playing ](*,) wtf? im so tired now and i dont understand why the songs arent playing.... anyone know whats wrong? cant seem to find any questions anywhere else....

---

### Post by U5tabil on 2006-08-22
Ok i just found it out. maybe it will help others

[http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06](http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06)

---

### Post by cptjaben on 2006-08-23
Are other media players on your machine able to play .mp3's? It could be that you don't have a mp3 codec installed. I believe there is information regarding your codec [here.]("https://help.ubuntu.com/community/RestrictedFormats") Hope that helps.

---

### Post by U5tabil on 2006-08-23
if you read i got it to work :)

[http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06](http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06)

---

### Post by armware on 2006-08-23
i had the same problem, and running 
sudo apt-get install libmad0 libxine-extracodecs
did nothing for me, but your link did provide another solution that worked. i added:
deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main
to /etc/apt/sources.list
and ran:
sudo apt-get install amarok-xine
and it worked.

---

