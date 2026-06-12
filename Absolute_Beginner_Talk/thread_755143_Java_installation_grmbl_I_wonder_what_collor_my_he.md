---
title: "Java installation grmbl I wonder what collor my hear is"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by friartuck on 2008-04-14
Trying for some time now to get Java started

used the following;

broedertuck@ubuntu-desktop:/root$ sudo apt-get update 
broedertuck@ubuntu-desktop:/root$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6plugin
broedertuck@ubuntu-desktop:/root$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not installable
                 Depends: libstdc++5 but it is not installable
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
E: Broken packages
broedertuck@ubuntu-desktop:/root$ 
broedertuck@ubuntu-desktop:/root$ 


Anyone know some more about this.

---

### Post by forrestcupp on 2008-04-14
Go to System->Administration->Software Sources and in the Ubuntu Software tab make sure all of the boxes are checked.  Then try again.

---

### Post by friartuck on 2008-04-14
isn't this the same as sudo apt-get install ubuntu-restricted-extras ?

---

### Post by forrestcupp on 2008-04-14
No.  ubuntu-restricted-extras installs much more than just java.  It doesn't matter anyway.  Neither the restricted-extras nor sun-java are in the main supported repository.  You need to enable universe and multiverse for either one you do.

Did you try what I said earlier?

---

### Post by friartuck on 2008-04-14
I think you solved my problem thnks

---

### Post by friartuck on 2008-04-14
I did what you told me and starting to believe there is for sure better support than any other software program available,
Java is installed .-)

Thanks buddy

---

