---
title: "Obscure Message from Update Manager"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by baekeland on 2007-04-27
Hi,

Recently I resolved a problem I was having with Services.List.  Once I solved the problem I am now getting this error message.  If I am not mistaken, I think the message is telling me to update my links for updates for Feisty 7.04.  Here is the message I just need to know is there an easy correction to this and where would I procure new repositories?

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

Then these repositories are listed:

[http://archive,ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive,ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2:](http://archive,ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2:](http://archive,ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2:](http://archive,ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2:](http://archive,ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'archive,ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release:) Unable to find expected entry  updates/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive,ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive,ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive,ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive,ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Could not resolve 'archive,ubuntu.com'
[http://archive,ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive,ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Could not resolve 'archive,ubuntu.com'


Any help as usual is greatly appreciated.  I also noticed that after the word "archive" there seems to be a comma rather than a period which I think should be there.

Thanks,

Bill  ):P )

---

### Post by Kobalt on 2007-04-27
Can you please post us your sources.list file : ```
cat /etc/apt/sources.list
```

---

### Post by Seisen on 2007-04-27
You are right it need to be a period instead of a comma. Change that and then it should work.

---

### Post by psyke83 on 2007-04-27
Hi,

It seems your sources.list file was corrupted somehow. You need to edit the file and replace every occurrence of "archive,ubuntu.com" with "archive.ubuntu.com".

OR (I'm not sure if it works with Dapper) move "/etc/apt/sources.list" to "/etc/apt/sources.list.bak", open up Synaptic, go to Tools/Repositories, and then place a checkmark in all entries on the "Ubuntu Software" and "Updates" tabs.

---

### Post by baekeland on 2007-04-27
> **Kobalt said:**
> Can you please post us your sources.list file : ```
cat /etc/apt/sources.list
```

Here is my latest sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates universe

#AUTOMATIX REPOS END
#deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)
#deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org)
#[http://ubuntu.beryl-project.org/root@1upine.me.uk.gpg](http://ubuntu.beryl-project.org/root@1upine.me.uk.gpg) -0 - | sudo apt-key add -
# Trevino's Beryl-SVN Ububtu Repository
 # GPG key: 81836ebf




deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive,ubuntu.com/ubuntu/](http://archive,ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted


Thanks,

Bikll

---

### Post by baekeland on 2007-04-27
Thanks very kindly guys.  I will give your suggestions a try.  :) :)

---

### Post by Kobalt on 2007-04-27
You do have a line that have a , instead of a . : > deb [http://archive,ubuntu.com/ubuntu/](http://archive,ubuntu.com/ubuntu/) dapper universe main restricted multiverse

---

### Post by psyke83 on 2007-04-27
baekeland,

If you look at the first entry in your sources.list, it's pointing to feisty-updates... you can expect programs to break if you leave that there, as your system will try to upgrade packages from Feisty's repository which probably won't work on Dapper.

My advice is to use this list here, it's clean and complete: [http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)

---

