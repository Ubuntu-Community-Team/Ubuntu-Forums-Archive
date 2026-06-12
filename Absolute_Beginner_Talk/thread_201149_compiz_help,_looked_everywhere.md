---
title: "compiz help, looked everywhere"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-06-21
Ok, fresh install of dapper,
Add all repositories (universe, multiverse, etc)
install linux-686 package
install all upgrades
nvidia graphics install as described in the [wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") which seems to work ok
follow instructions for xgl/compiz install as in the [wiki]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz?highlight=%28compiz%29"), up to the section "Getting Compiz to Run"
at this point I use Method A and run:
richard@Akira:~$         gnome-window-decorator
(gnome-window-decorator:7401): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

hmmm. if I then run:
richard@Akira:~$ compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water &
[1] 7962
richard@Akira:~$ compiz.real: No composite extension

Really not sure whats going on here, any help/advice would be warmly welcomed

---

