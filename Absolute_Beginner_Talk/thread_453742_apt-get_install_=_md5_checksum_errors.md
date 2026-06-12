---
title: "apt-get install = md5 checksum errors"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by takayuki on 2007-05-24
hi,

i'm in Japan so my repos in my sources.list all start with jp.ubuntu...  i've just installed xubuntu and while installing new software from the repos i've been getting alot of md5 checksum errors.

i just tried to install amarok.  it took about an hour to download everything, then it said it couldn't get one package b/c of a md5 checksum error.  so i did a 

[php]sudo apt-get update --fix-missing.[/php]now what is my next move installing amarok?  (i'm a dummy and didn't write down the package with the md5 checksum error).  when i did

[php]sudo apt-get install amarok.[/php]it acted like it wanted to install everything again. 

thanks for any advice.

regards,

takayuki

---

### Post by Happy_Man on 2007-05-24
That's because it does... if there is an md5sum error, it won't install ANYTHING.

---

### Post by takayuki on 2007-05-24
Happy_man,

thanks for the reply.

is it ok to change my repos from jp... to us....?  should I?

if i get another checksum error, what should i do?  how do i get around it?

is it ok to change from apt-get to aptitude after having used apt-get for a few days?

thanks,

takayuki

---

### Post by bobplano on 2007-05-24
apt-get and aptitude are interchangeable except aptitude keeps track of dependencies better. why don't you just try ubuntu servers instead of using us servers? they probably are essentially in the same place but the ubuntu servers might be more reliable

---

### Post by PriceChild on 2007-05-24
If I were you I would do```
sudo apt-get clean
```to clean your cache of packages.```
sudo apt-get -f install
```to check everything's currently ok. Then ```
sudo apt-get install amarok
```to re-download the packages and try again.

---

### Post by takayuki on 2007-05-26
Pricechild and Bobplano,

thanks for the input.

i changed the repos to ubuntu...

i also did Pricechild's apt-get commands...

and Amarok went in without a hitch.



takayuki

---

