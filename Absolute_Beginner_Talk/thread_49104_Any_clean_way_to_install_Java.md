---
title: "Any clean way to install Java?"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by stellaNera on 2005-07-15
Hello all,

I have been reading lots of posts on how to install Java, and also note on the WIki, but  trying what it is suggested it does not work from me.

Also, lets add that I am not a Linux person, and most of the times I am not quite sure what a certain command is doing.

I have my Linx-java....bin file from Sun. 

I followed all the other instructions one of them is

```
make-jpkg jdk-1_5_0_01-linux-i586.bin
```

but I get a command not found. 

I will happy to provide more info on my newly installed Linux if needed.

Thanks.

---

### Post by stellaNera on 2005-07-15
... I just tryied using the Ubuntu update Manager, selecting the appropriate repository for java and I got the following...

```
ftp://ubuntujava.yimports.com/binary/Release.gpg: PASS failed, server said: Login incorrect.
ftp://ubuntujava.yimports.com/source/Release.gpg: PASS failed, server said: Login incorrect.
ftp://ubuntujava.yimports.com/binary/Packages.gz: PASS failed, server said: Login incorrect.
ftp://ubuntujava.yimports.com/source/Sources.gz: PASS failed, server said: Login incorrect.
``` 

... I am running out of ideas :)    :roll: 

Thanks

---

### Post by Knome_fan on 2005-07-15
Hi,
I think the easieast way would be to use the sun java environments provided by the backports project.

To do that, simply modify your /etc/apt/sources.list as described here (the Backport lines are the important ones in this case):
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

and then install java:
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

I think that should be it.

Have fun!  :grin:

---

### Post by jiyuu0 on 2005-07-15
have you tried this?

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

remember to do this first before doing the above
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

EDIT: replied same time as the guy above :) only slower by the seconds :(

---

### Post by stellaNera on 2005-07-20
Hi there,

sorry I got caught up with work stuff... 

Thanks for the advice, I will give it a try and let u know.

Seems easy enough.  :)

---

