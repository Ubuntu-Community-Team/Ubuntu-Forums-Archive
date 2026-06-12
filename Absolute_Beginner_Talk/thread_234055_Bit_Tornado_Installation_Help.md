---
title: "Bit Tornado Installation Help"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Tyrael_Odium on 2006-08-10
Ok guys, i am having some trouble installing a bit torrent client.
I went to the ubuntu dapper starter guide located at 
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
and i tried to install azurus and the error message i got was 

"E: Couldn't find package azureus" 

so i just decided to move down to bit tornado. I used the command apt-get install bittornado bittornado-gui and the error message i got that time was 

"Package bittornado-gui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bittornado-gui has no installation candidate"

could somebody please help me?

---

### Post by wvslkr on 2006-08-10
Both programs are in the repositories.  Azureus is in universe,probably Bittornado also.

Go back to the guide and see how to enable extra repositories.  Then fire up synaptic and do a search.  Once you enable the repositories they should show up. Mark to install then hit apply and you should be good to go.

Synaptic is under>System>Administration.  If you have trouble post back.
You can also enable repositories in synaptic under settings>repositories.

GL Have Fun.

---

