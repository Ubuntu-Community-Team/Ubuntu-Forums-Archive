---
title: "Updates And Automatix"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Merlin Whitewolf on 2006-06-27
Over the last several days, I have gotten the message that an update is available. I click on the button to see what is available, and "Automatix new version 6.2-4-6.06 dapper1 (size 31.0k)" is always there. The first time it appeared, I clicked to install and it proceeded to run the install. Fine. But that was 4 days ago. I log on about twice a day, and the same update is always there. If I click on install or check, I always get this message --

'The following problems were found on your system -
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper 
Release: the following signatures were invalid: BADSIG 18B52FE3521A9C7C Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>'

As I understand it, this constant repeat of an update and a problem message has something to do with the key. Is that correct? Do I need to get a new gpg key for the new version of Automatix? If so, how? Please.
I like the automatic notification of available updates, but having the same one show up at each logon is wearing. :( 

-Merlin

---

### Post by Burgresso on 2006-10-20
Yea, this is happening to me too. I wonder how to fix it?

---

### Post by dbd on 2006-10-20
Hmmm, just a guess, but you could try to update using the command line to install the updates, then you may be given the option to update without even having the correct signature.

Try:
> sudo apt-get update
followed by:
> sudo apt-get upgrade

---

### Post by arnieboy on 2006-10-21
> **Merlin Whitewolf said:**
> Over the last several days, I have gotten the message that an update is available. I click on the button to see what is available, and "Automatix new version 6.2-4-6.06 dapper1 (size 31.0k)" is always there. The first time it appeared, I clicked to install and it proceeded to run the install. Fine. But that was 4 days ago. I log on about twice a day, and the same update is always there. If I click on install or check, I always get this message --

'The following problems were found on your system -
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper 
Release: the following signatures were invalid: BADSIG 18B52FE3521A9C7C Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>'

As I understand it, this constant repeat of an update and a problem message has something to do with the key. Is that correct? Do I need to get a new gpg key for the new version of Automatix? If so, how? Please.
I like the automatic notification of available updates, but having the same one show up at each logon is wearing. :( 

-Merlin

try doing the following:
```
sudo apt-get remove automatix
sudo apt-get install automatix2
```

---

### Post by tubasoldier on 2006-10-21
Arnie, 

 Thanks for all the work with AutoMatix. It sure makes setting up an Ubuntu system slicker than snot. However, after I use it I always just remove it. I have noticed that it does get upgraded quite often. I would rather not upgrade a program I use to simply set up my system how I like it. Other than that Automatix is great. Keep up the good work!

---

### Post by rlozano on 2006-10-21
are you using dapper or edgy?

automatix is close to end of life. the error your getting is the key error for automatix. 

it might be worth for you upgrading to automtix2 to fix the error.

follow this link and hope it will help you..

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

