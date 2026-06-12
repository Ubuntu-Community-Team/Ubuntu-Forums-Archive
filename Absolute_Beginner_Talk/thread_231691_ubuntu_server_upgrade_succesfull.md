---
title: "ubuntu server upgrade succesfull"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by dirkdekker on 2006-08-07
Hi, changed the file : sources.list in :

## Uncomment the following two lines to fetch updated software from the network
  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
  deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
  deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

 $ sudo apt-get upgrade 
and
 $ sudo apt-get dist-upgrade

After successfull upgrade ubuntu server version 5.10 breeze,
I like to know and see what upgrades are installed now.
And, do I have to uncommand the lines deb... again?

thanks for answering.

---

