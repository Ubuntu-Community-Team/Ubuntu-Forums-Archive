---
title: "what do these commands mean??"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-12-05
hello,

ok while reading the help files i came accross some commands that i dont understand??

can some one plz help me clarify...

> $ sudo adduser USERNAME dip
 $ sudo adduser USERNAME dialout

gksudo gedit /etc/wvdial.conf

gksudo gedit $HOME/.wvdial.conf

gksudo gedit /etc/ppp/options



the only thing i recognize here is the sudo command?? which gives administrative permissions. right?


what are the rest.?

and what is gksudo??

what is gedit and why is there a location to a file after??

thx

---

### Post by GSF1200S on 2007-12-05
> **faraz_k86 said:**
> hello,

ok while reading the help files i came accross some commands that i dont understand??

can some one plz help me clarify...



the only thing i recognize here is the sudo command?? which gives administrative permissions. right?


what are the rest.?

and what is gksudo??

what is gedit and why is there a location to a file after??

thx

gksudo is like sudo, only for graphical applications. Yes, it is administrator permissions.

gedit is a basic text editor. If theres a file location afterwords, that means that gedit will open the file in that location.

Im not really sure what all those files do, but it should tell you that in the walkthrough...

---

### Post by rubicon on 2007-12-05
this two commands

sudo adduser faraz_k86 dip
sudo adduser faraz_k86 dialout

will add you in two groups: 'dip' and 'dialout'. What 'dip' group is about i don't know, but being in group 'dialout' makes you able to connect via modem (dialup).

wvdial.conf is file related to wvdial - console dialer program in Ubuntu, do 'man wvdial'.

---

