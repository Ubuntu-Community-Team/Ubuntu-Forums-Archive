---
title: "how to configure evolution mail for a hotmail account"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by singetak on 2006-08-30
i have a hotmail email i need configirations for a hotmail account 
the recieving server type.....
and sending email ....:-k

---

### Post by Abstract on 2006-08-30
I am unsure if Microsoft allow Pop3 email, which is what you need. If you look around on the Hotmail website you need to find something along the lines of POP3 details, Outlook Configuration or External email client help. If you come back with the details I can help you.

---

### Post by mejy on 2006-08-30
Unfortunately, Microsoft made changes to the hotmail service about a year ago so that E-Mail apps can't access hotmail without using hacks (that is, through POP 3). To my knowledge, the easiest such hack is to install thunderbird (sudo apt-get install thunderbird) and then use the webmail extension: [http://webmail.mozdev.org/](http://webmail.mozdev.org/).

---

### Post by singetak on 2006-08-30
THANKS I THINK WILL DO THAT AND REPORT BACK
BUT NOT TODAY I THINK TOMOROW I HAVE THINGS TO DO :cool: 
;)

---

### Post by halitech on 2006-08-30
they used to but unless you are paying for the advanced account, they don't allow it any longer

---

### Post by tagra123 on 2006-08-30
Gotmail works great and you don't need to rent your email address from MSN or hotmail

[http://linux.cudeso.be/linuxdoc/gotmail.php](http://linux.cudeso.be/linuxdoc/gotmail.php)

I went one step farther and set up a gmail account.

I let gotmail forward all of my emails to gmail (google mail works with thunderbird and evolution)


The script above is not all that hard to get working. If I remember correctly there are a couple of other packages that gotmail needs (use apt-get or synaptic to download and install them)

I have ours to run every 15 minutes with a cronjob

Heres an example cronjob in one of my posts:

[http://ubuntuforums.org/showthread.php?t=240326](http://ubuntuforums.org/showthread.php?t=240326)

---

