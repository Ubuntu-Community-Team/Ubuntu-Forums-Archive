---
title: "remote control (agian)"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jeffhills on 2008-02-02
please help! I have spent hous trying to get this working. I am working through the remote section of installing Hauppauge Nova 500T. Everything works as planned, ie card works , ir is detected when
dmeseg | grep DVB
Only a few of the buttons are detected with irw

How do you install needed driver dev/input?
The guide givesthe correct lircd.conf file, How do you install this!!?

Sorry if this is basic, but all of the other instuctions are blow by blow, then it all goes wrong.
please help I have worked through everything else, but I am stuck now
Jeff

---

### Post by markd on 2008-02-05
This is just a regular file in /etc/lircd/lircd.conf

You can edit it (as root via sudo) with your favourite editor, or copy a new version of it to that location.  Have a look at the lirc section on this link:

[http://parker1.co.uk/mythtv_ubuntu2.php]("http://parker1.co.uk/mythtv_ubuntu2.php")

---

