---
title: "File Conversion"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by dr_dirk on 2007-04-03
I am trying to get an HP 1020 printer installed under Edgy and it is giving me plenty of trouble which I'm seeking help of in another thread.  While following directions from one site I came across a command I didn't really know anything about nor could I make sense from it.  It says to convert a .img file to .dl but it is unclear just how to do so.

4. Convert and install the firmware file: sudo su arm2hpdl sihp1000.img &gt;  usr/share/foo2zjs/firmware/sihp1000.dl

Can anyone explain what exactly I'm supposed to do with this?  If it helps, the directions came from [http://64.233.167.104/search?q=cache:nClBuPVTpvkJ:digitalfreedom.uwc.ac.za/index.php%3Faction%3Dmakepdf%26userid%3D944060741%26module%3Dblog%26postid%3Dinit_7143_1167223185+hp+1020+ubuntu&hl=en&ct=clnk&cd=16&gl=us&client=firefox-a](http://64.233.167.104/search?q=cache:nClBuPVTpvkJ:digitalfreedom.uwc.ac.za/index.php%3Faction%3Dmakepdf%26userid%3D944060741%26module%3Dblog%26postid%3Dinit_7143_1167223185+hp+1020+ubuntu&hl=en&ct=clnk&cd=16&gl=us&client=firefox-a)

Thanks a lot.

Derek

---

### Post by renzokuken on 2007-04-03
"sudo" gives you superuser privileges

"arm2hpdl" is the utility/software that is actually doing the conversion

"sihp1000.img" is obviously your image file

"&gt" ..... dunno what this does probably just a flag

"usr/share/foo2zjs/firmware/sihp1000.dl" this bit is telling arm2hpdl to put the file into the /usr/share/foo2zjs/firmware folder once it is converted

all you need to do is copy and paste this command into a terminal

---

### Post by dr_dirk on 2007-04-03
Thanks for the explanation.  The main part that confused me was "&gt;".  Of course Terminal didn't like the semicolon nor did it like "&gt".  I'll try it without &gt and see what happens.

---

### Post by raptor2552 on 2007-04-03
Was this copied from the web page? My thought is &gt; should be the greater than symbol > without the ; which would send the output of .img to .dl (maybe)??

Maybe the command should be: **sudo su arm2hpdl sihp1000.img > usr/share/foo2zjs/firmware/sihp1000.dl**

I have no idea why it tells you to do a **sudo su** since **sudo** alone should give you all the permissions you need.

Have fun

---

### Post by renzokuken on 2007-04-04
raptor2552 is right, the gt; bit is simply some html code for a certain symbol. for whatever reason that webpage isnt rendering properly and you are seeing all the html mixed in with the actual text

personally i would have thought the correct command should be

```
sudo arm2hpdl sihp1000.img /usr/share/foo2zjs/firmware/sihp1000.dl
```

---

