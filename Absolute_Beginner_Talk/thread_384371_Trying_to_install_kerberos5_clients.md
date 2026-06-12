---
title: "Trying to install kerberos5 clients"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jackal242 on 2007-03-14
# apt-get install krb5-clients
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  krb5-clients: Depends: libkrb53 (= 1.4.3-9ubuntu1) but 1.4.3-9ubuntu1.1 is to be installed
E: Broken packages

-----

How do I work around this?  I already have libkrb53 installed!

--force-yes doesn't work.

---

### Post by jackal242 on 2007-03-14
> 

The following packages have unmet dependencies:
  krb5-clients: Depends: libkrb53 (= 1.4.3-9ubuntu1) but 1.4.3-9ubuntu1.1 is to be installed
E: Broken packages



So that's the real problem. how do you work around this?  when i look at the libkrb53 i have installed it says it provides:

Provides: 
1.4.3-9ubuntu1.1 - 
1.4.3-9ubuntu1 - 


So I don't get it.

---

### Post by jackal242 on 2007-03-14
Solved it:
  
# sudo aptitude install libkrb53=1.4.3-9ubuntu1 -f
 
# sudo apt-get -f install krb5-clients

---

