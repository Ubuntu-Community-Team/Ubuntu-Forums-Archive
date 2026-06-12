---
title: "aptitude update --&gt; without internet"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2005-11-10
hi
is there a way to create a local repository with a lot of deb files that i downloaded? then just type sudo aptitude update or install??

this is beacause at home i don't hava an internet connection but here at work i can download what i need... 

is there a way? or am asking to much?

thanks

---

### Post by raublekick on 2005-11-10
i believe you can load the debs on a CD and use that as a repository just like you can the Ubuntu CD. i can't give you much more info thatn that, but it's a step in the right direction.

---

### Post by nrwilk on 2005-11-10
yes you can do this.  You could even burn a DVD with a whole lot on it and use that.  Try just copying the address that is already listed in the sources.list file at the top which gives the address of the original install CD for use as a repository.  Just change the name of the disk to be used.

---

### Post by lreyes6 on 2005-11-11
last night i tryed with a cd (about 600 deb files) but i cant add it just like that... first of all aptitude toldme to do an apt-cdrom add ...... and when i did that it returns me a message that said that cant find the package list... :eek: 

so...

does anybody knows how to create that list????:confused: 

thanks

---

### Post by widjajayd on 2005-12-01
Please see this thread

[http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)

part
1. Created /opt/repo directory (could be the home directory)
2. Created the directory /opt/repo/binary (copied from Debian specs)
3. Copied all debs from my update from /var/cache/apt/archives to /opt/repo/binary
4. Executed dpkg-scanpackages like this:
# pwd
/opt/repo
# dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
5. Burned a CD with its contents

For use that in my standalone host, I did this:
# apt-cdrom add


you miss this part.
# dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz

---

