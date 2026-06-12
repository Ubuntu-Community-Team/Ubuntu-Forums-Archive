---
title: "Cannot install software"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by antharr on 2006-11-24
I am having a problem installing software. I am using Synaptic and have also tried using command line. I get the following error messages:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.24ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.24ubuntu2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/gcj-4.1-base_4.1.0-1ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/gcj-4.1-base_4.1.0-1ubuntu8_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/libgcj-common_4.1.0-1ubuntu8_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/libgcj-common_4.1.0-1ubuntu8_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/libgcj7_4.1.0-1ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/libgcj7_4.1.0-1ubuntu8_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/gij-4.1_4.1.0-1ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/gij-4.1_4.1.0-1ubuntu8_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/libgcj7-jar_4.1.0-1ubuntu8_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.1/libgcj7-jar_4.1.0-1ubuntu8_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnucrypto-java/libgnucrypto-java_2.0.1-4ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnucrypto-java/libgnucrypto-java_2.0.1-4ubuntu1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libj/libjessie-java/libjessie-java_1.0.1-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libj/libjessie-java/libjessie-java_1.0.1-1ubuntu1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


Here is my source.list file also:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://getautomatix.com/apt](http://getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END


Any help is appreciated. Thanks

---

### Post by antharr on 2006-11-24
Okay I feel stupid now. I see where the universe entries are not supported by Ubuntu. I am guessing I need to uncomment the entries stated.

---

### Post by PartisanEntity on 2006-11-24
Is this a recent installation? Are you connected to the internet directly or through a proxy?

---

### Post by antharr on 2006-11-24
I am connected directly to the internet. I installed some software earlier today. Things went wrong when using Automatix.

---

### Post by PartisanEntity on 2006-11-24
Did you install something like anon proxy?

---

### Post by antharr on 2006-11-24
Yes I did.

---

### Post by PartisanEntity on 2006-11-24
If you enter some lines from the error message you received you will notice many threads with the same problem.

I have not found a solution, only a removal will allow the download of updates again it seems.

Good luck :)

---

### Post by antharr on 2006-11-24
Removing anon proxy and a restart did the trick. Thanks for your help. 
I am very impressed with the support on this forum. If things keep going at this rate, I will never use Windows unless it is for class or work. Thanks a million.

---

