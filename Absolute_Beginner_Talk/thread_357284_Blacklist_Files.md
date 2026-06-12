---
title: "Blacklist Files?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by akao79 on 2007-02-09
I'm working through some wireless network problems and one possible solution involves adding a [blacklist file]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortege3500").  What's the process involved to either create new blacklist files or append new info to existing ones? 

Thanks in advance.

---

### Post by dannyboy79 on 2007-02-09
the link you posted pretty much says it all.

To get wifi to work again I had to disable the hostap drivers after upgrading from Breezy to Dapper, by creating a file /etc/modprobe.d/blacklist-orinoco containing: 

blacklist hostap
blacklist hostap_cs

so you should do a search to see if this file already exists on your system. open nautilus by typing in the terminal
gksudo nautilus
when it opens you have root privalages so be VERY CAREFULL!!!!!
now go to the /etc/modprobe.d/ folder. within it you should see a file called blacklist and maybe some others like blacklist-scanner etc etc.
so now just create a new file called blacklist-orinoco and simply paste in what he is telling you to paste in there
blacklist hostap
blacklist hostap_cs

and that's it. now don't forget to close nautilus out of root privalages. if you're not sure how to create a file while in nautilus, then shut down nautilus and go back to the terminal. first you'll want to cd to the /etc/modprobe.d/ directory and then type in sudo gedit blacklist-orinoco (or you can use kate or whatever editor you like) then simply type it in exactly how you see it above.
blacklist hostap
blacklist hostap_cs

save it and close it. then do a restart on your computer and that should work. at least according to the guy anyway. good luck

---

