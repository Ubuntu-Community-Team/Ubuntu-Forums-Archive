---
title: "[SOLVED] User Accounts on Server"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by HornedBeast on 2008-01-18
I am trying to create a system where by there is a server; and for an easy example, 10 client machines.

I would like to have the database of users on the server, so, whichever machine the user  logs in to, it checks the username and password against the server rather than the local client machine. I would also like all the 'home' directories to reside on the server too, so whatever settings username "A" has, will be the same on whichever client machine they login on. This would make backups simpler.

Is this possible using Ubuntu-Server and Ubuntu-Desktop? Or is there a smililar solution using a certain package?

Any ideas or solutions would be apreciated. Thank-you kindly.

Andy

---

### Post by stump138 on 2008-01-18
Yes this is possible. However, it takes some setup.  In order to accomplish what you are looking for you need the following packages.

[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

[openldap]("https://help.ubuntu.com/community/OpenLDAPServer?highlight=%28openldap%29")

[autofs]("https://help.ubuntu.com/community/Autofs")

If you need more to get started, post away as each of these topics are pretty heavy unto themselves.  Good luck!

---

### Post by HornedBeast on 2008-01-18
Thank-you for your quick response. Are there any quick and simple guides on the internet about setting this system up that you know off?

Is there any basic information about what those packages do? Because the links supplied don't seem to work and a simple google search didn't bring up a huge amount of help.

Cheers again.

Andy

---

### Post by hyper_ch on 2008-01-18
if you go even a step further you may want a thin client setup:

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

### Post by stump138 on 2008-01-18
NFS is for file sharing, openldap is for user authentication and information,and autofs-ldap takes care of automounting those home directories.  There is a great amount of information available on each of these topics.  As far as a all-in-one guide there might be one or two.  As I said before these topics can get pretty heavy.

I would start with NFS, that way you can start with basic file shares and then move into open-ldap. After you get users authenticating via PAM, you start working on automounts :)

here is the original links so you can try these:
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

[https://help.ubuntu.com/community/OpenLDAPServer]("https://help.ubuntu.com/community/OpenLDAPServer")

[https://help.ubuntu.com/community/AutofsLDAP]("https://help.ubuntu.com/community/AutofsLDAP")

---

### Post by HornedBeast on 2008-01-18
Thank you very much for your response. I assume this is the only way of doing it? Time to setup a testing server and client laptop to try it with me thinks. 

I'll let you know how I get on...

If anyone has any complete guides or if there are any other easier ways of creating a similar system (I liked the ThinClient idea) then that would be apreciated too.

Cheers to everyone thats helped me so far!

(I love this community!!!!!) :guitar:

---

### Post by stump138 on 2008-01-18
I've used this approach and the thin client approach.  I've even used them in conjunction,  It really depends on what setup you are trying to achieve.  I have multiple thin-client servers, but i still need authentication and file shares from centralized locations,

I'm sure there are probably other methods to do these things such as kerberos.  The one hyper-ch and I listed are proabably just the most common.

---

### Post by HornedBeast on 2008-01-18
For the time being the system only needs to be over a local network. However, being in the music industry we may have "troops" out in diffrent countries that need to access this system. Are the two methods suggested capable of working over the internet? Via VPN or natively?

Andy

---

### Post by hyper_ch on 2008-01-18
thin client setup is not recommended over the internet at transfer rates aren't that great...

Over the net I'd just remote mount a folders over ssh. That is fairly simple... but leave login authorization et al. be part of the local computer...

---

### Post by HornedBeast on 2008-01-18
That seemed to be the best option. Locally in the office have a user account system on the server so any machine you login to, its YOUR settings and file (your Home folder)... But when out on the road, have laptops pre-setup for automatically logging into the system and give it access to the files they need.

I assume this is what u are suggesting?

---

### Post by stump138 on 2008-01-18
There really isn't much as far as options go to do what you want from remote locations "seamlessly."  As far as your LAN is concerned, you could setup a laptop to authenticate inside your building to a server, and also be able to access a localized account on the road.  As far as file sync'ing, you are going to have use a solution like ssh like Hyper_ch suggests.

---

### Post by HornedBeast on 2008-01-18
Ok...well, for a start... I think ill try the LDAP and NFS option as suggested first as this seems to be fairly robust and certainly not beyond me to setup. This would sort out all my needs locally.

For remote logins, Im sure I could create a web based solution for people out on the road, so if we send ppl out with XP laptops for example. They can just login from any browser, or an internet cafe for example.

But the local stuff is by far the most important. And having seemless logins on any machine so it looks like your on your own desktop all the time is a fairly handy product for me. Makes backing up really simple too, as its only one server to backup which contains all the data. I could also use 'fetchmail' to setup an IMAP solution for all the emails too.

Configure the server with a RAID-1 and bobs your uncle.

Sounds like a fresh plan :)

Cheers guys!

---

