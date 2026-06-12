---
title: "how 2 install download"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by pollock37 on 2007-03-31
nube-----------------------------------------------------------------------------
i was given ubuntu6.06 and installed on its own HD
i wanted to update the firefox browser to firefox 2.0.0.3
so i downloaded it from the firefox internet site its a tar.gz
file its on my desktop in its folder what do i need to do
to get it to install so i can use it as my browser .
i am new to ubuntu and am enjoying it also how can i 
run a xp HD and a ubuntu HD on the same puter and 
have a choice of whitch one boots .
thanks bob37 ----------------------------------------------------------------

---

### Post by Maestro23 on 2007-03-31
Some links that might help:

New Firefox version on Dapper: [https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29)

Installing in Ubuntu:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Good luck and welcome to Ubuntu.

---

### Post by InuyashaDuelist on 2007-03-31
Open up a terminal window and type in

```
sudo apt-get install firefox
```

---

### Post by zvacet on 2007-03-31
[http://www.mozilla.com/en-US/firefox/releases/1.5.html#install]("http://www.mozilla.com/en-US/firefox/releases/1.5.html#install")

Replace 1.5 with number of your version

---

### Post by confused57 on 2007-03-31
> **pollock37 said:**
> nube-----------------------------------------------------------------------------
i was given ubuntu6.06 and installed on its own HD
i wanted to update the firefox browser to firefox 2.0.0.3
so i downloaded it from the firefox internet site its a tar.gz
file its on my desktop in its folder what do i need to do
to get it to install so i can use it as my browser .
i am new to ubuntu and am enjoying it also how can i 
run a xp HD and a ubuntu HD on the same puter and 
have a choice of whitch one boots .
thanks bob37 ----------------------------------------------------------------

Here's a really easy way to install the newest Firefox:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox)

You should be able to add an entry to your menu.lst to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by 67GTA on 2007-03-31
I was trying to install firefox with psyhocats instructions and have hit a snag. It is asking me to select a number for my locale from a list that is not there. What number do I need for english? Here is the terminal: [ATTACH]28622[/ATTACH]

---

### Post by 67GTA on 2007-03-31
Anybody?

---

### Post by pollock37 on 2007-04-01
THANK  U ALL ------------------------------------------------------------------------------
for the in put
i went to [http://pykeylogger.sourceforge.net/w...d_o](http://pykeylogger.sourceforge.net/w...d_o) f_Firefox 
as per - confused 57 - input -  downloaded the script and
pasted in the terminal command lines it worked real good 
i also installed Thunderbird it was interesting watching the
download in the text format now working on Mplayer and a
Totem install
thanks again
blessings - bob37 -----------------------------------------------------------------------

---

### Post by pollock37 on 2007-04-01
i used number 10 
just type in    10    it will equal en US
thats what i did 
bob37

---

### Post by confused57 on 2007-04-01
> **pollock37 said:**
> THANK  U ALL ------------------------------------------------------------------------------
for the in put
i went to [http://pykeylogger.sourceforge.net/w...d_o](http://pykeylogger.sourceforge.net/w...d_o) f_Firefox 
as per - confused 57 - input -  downloaded the script and
pasted in the terminal command lines it worked real good 
i also installed Thunderbird it was interesting watching the
download in the text format now working on Mplayer and a
Totem install
thanks again
blessings - bob37 -----------------------------------------------------------------------

I've successfully used this script to install the newest Firefox on 3 separate Dapper installs...there's also directions for updating your Firefox,  I've updated from 2.0.0.1 > 2.0.0.2 > 2.0.0.3 using "gksudo firefox &" as described in nanotube's instructions.

---

