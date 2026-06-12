---
title: "how do i install thunderbird?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Stromham on 2006-06-28
hey i downloaded the taraball and i extracted it into my home directory, how do i install it? i have tried many things but i cannot figure out how to install it.

---

### Post by aysiu on 2006-06-28
You don't need to download a tarball. Just paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install mozilla-thunderbird
``` Alternatively--if you prefer Mozilla's Thunderbird to Ubuntu's Thunderbird, you can use [this installation script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Thunderbird_1.5).

You may want to read this, too--it basically sums up how to install software in Ubuntu:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by hod139 on 2006-06-28
There is no need to download thunderbird from their website, it exists already as a package in the ubuntu repositories.  To install, simply click on applications-->Add/Remove 
and search for thunderbird (It is in the Internet section.)
Then select it and apply the changes.  Simple as that.

Most software you want to install can be done this way.  Either through the add/remove tool or though synaptic (System-->Administration-->Synaptic)

Edit:  I'm too slow

---

### Post by shoot2kill on 2006-06-28
have you tried 
> sudo aptitude install mozilla-thunderbird

---

### Post by Stromham on 2006-06-28
thanks aysiu your a lifesaver, always helpful ;)

---

