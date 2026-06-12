---
title: "booting pc, cannot connect to internet, had internet before"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by girlwithPc on 2005-08-03
I had (provider) established internet connection,but they told me each time i boot computer and begin to work i have to type in root terminal [ adsl-start]next line [ route add default gw 123.456.102... ppp] [ route del default gw 10.1.0. ethr0] , i did but nothing worked out :( why is that needed? how to connect now and how to make it to connect automaticly to internet?i have no clue why i have to type so much each time i boot pc and want to use internet ..at the end of work they told me to type [adsl-stop]...now im with no internet and any idea how to get it back  ](*,)

---

### Post by girlwithPc on 2005-08-03
No reply?Anyone? I don't have any clue how to start internet now..at least now , anyone can help?

---

### Post by az on 2005-08-03
It usually takes more than an hour to get an answer.


Use pppoeconf to set up adsl on your computer.  It should default to starting every time you boot...

sudo pppoeconf

---

