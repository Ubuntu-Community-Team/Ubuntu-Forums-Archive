---
title: "Feeling lost - LAMP installation and config"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Oceanwatcher on 2007-03-17
First of all - I have been hacking various linux distros and freebsd before. But this is my first attempt at Ubuntu.

I really like the idea that everything should be locked down from the start to make installations secure. Kudos to the dev team for this!!

Here is my problem:

I am installing Ubuntu 6.10 server under WMWare 1.02. That part is easy enough.

During the install I am choosing LAMP. But when I try to point a browser to the server, there is nothing to connect to.

I tested ping to the IP. It answers. Tested ping to the server name. It answers and resolves. So the IP is correct, the DNS is set up correct (not done by me - I got the IP and name for the server and I am sure the IT dept know what they do :)   ).

I checked if there was any apache or apache2 under /etc and found nothing. So I do not think that LAMP was installed at all... Then what is the point of having to choose LAMP? I chose Ubuntu because it was supposed to be easy re: installation of LAMP and secure. So far I have verified the secure part. Can anyone help me so I do not loose to much hair scratching my head over this? :) 

Regards,

Oceanwatcher

---

### Post by bodhi.zazen on 2007-03-17
I do not have an answer for your question, but there are many guides available.

First there is a server forum : [http://www.ubuntuforums.org/forumdisplay.php?f=7](http://www.ubuntuforums.org/forumdisplay.php?f=7)

Guides : 

[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.ubuntuforums.org/showthread.php?&t=223805](http://www.ubuntuforums.org/showthread.php?&t=223805)

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by Oceanwatcher on 2007-03-17
Bodhi,

Thank you for your quick reply.

Yes, I have been looking at some of the guides. But they really do not answer my question of the LAMP choice. Why is it there if none of the -AMP products are beeing installed?

I just posted here because it is my first post, and it could be that I overlooked something so easy that I got kicked out of the server forum :) 

Do you think it would be ok to crosspost to the server forum? I would move it if I could, but reposting there and linking to it from this thread might be acceptable?

Regards,

Oceanwatcher

---

### Post by bodhi.zazen on 2007-03-17
Seems odd that AMP are not installed. If they are not, they should be easily installed via apt-get/aptitude ;)

It was my impression that the new "server" cd installed all that or that there was at least a LAMP option on the install menu.

I would agree with posting in the server forum as I think you will get a better response.

---

### Post by Oceanwatcher on 2007-03-17
This thread has been continued in the Servers&Security forum.

[http://www.ubuntuforums.org/showthread.php?t=386619](http://www.ubuntuforums.org/showthread.php?t=386619)

Please post any replies there.

Thank you,

Oceanwatcher

---

