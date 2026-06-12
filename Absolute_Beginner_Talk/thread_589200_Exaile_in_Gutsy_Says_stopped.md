---
title: "Exaile in Gutsy Says stopped"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-10-24
I  like streaming radio in Exaile and it was fine in Feisty. Now when I open it there is no list of music type or stations and Exaile says it is stopped. When I click on the radio streams folder nothing happens.:)

---

### Post by rosswmcgee on 2007-10-24
I have since been able to get Exaile working in 7.10 upgrade machine by adding a plug in. However in the new install, after adding the same plugin, I can go as far as selecting a radio shout cast/ Americana for instance/Blues/ but when I select a station Exaile goes to it but then Exaile freezes up and will not play. Looking for an Exaile solution.

---

### Post by realvz on 2007-10-24
try removing exaile and reinstalling....

dont forget to run these commands before your reinstall
sudo apt-get remove
sudo apt-get autoremove
sudo apt-get clean

---

### Post by rosswmcgee on 2007-10-24
I have removed and re- installed but not with those commands/will give it a try/thanks

---

### Post by rosswmcgee on 2007-10-24
Same problem Exaile freezes up and will not play streams/I did note that the sudo apt-get clean/command did not seem to do anything/ also when I re-installed a previously selected
stream was there as well as the previous plug ins.

---

### Post by Neovos on 2007-10-25
When I upgraded to 7.10, my exaile never froze, it just didn't play anything in my library. I'd hit play and it would just stay at 0:00/7:10 or so. But the extra terminal lines for reinstall did the trick for me. Thanks realvz.

---

### Post by rosswmcgee on 2007-10-27
Still wondering why Exaile works fine in my Gutsy upgrade but will not play in the clean install. It does every correct except the final result is no music playing. I did the removal did 
the terminal exercise.

---

### Post by rosswmcgee on 2007-10-30
Fixed it by installing Gstreamers

---

### Post by chadlongstaff on 2007-11-28
I didn't find reinstalling exaile useful in resolving this problem; even installing 0.2.11 didn't help. However I did notice I could play local files. /etc/init.d/mt-daap restart on the server (also gutsy) fixed it.

---

