---
title: "[SOLVED] I can only get internet with browser and not terminal"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by solitare on 2006-09-23
hi all...

this may be a weird one but here goes...
i am a newbie(ish) with a laptop and can connect to the internet (wireless) via my university log on. the only problem is it seems to be through the browser only.

to achieve this i've had to put proxy info into browser (mozilla) and when connected it goes to a default university screen where i have to log on (name/password). this is fine but when i use a terminal to do any 'sudo alt-get install....' stuff nothing happens. it looks like it's connected but stays on '0%' permanently. i have been to their help desk but, surprise surprise, they know diddly squat about linux. 

i guess i'm going to have to write something but what and where?

any clues??

   thanks...

---

### Post by bulldog on 2006-09-23
Well you could give **apt-get or aptitude** a chance :D

Could be you made a type error but you never know.......

---

### Post by Leeghoofd on 2006-09-23
Method 2.

This method uses the apt.conf file which is found in your /etc/apt/ directory. This method is useful if you only want apt-get (and not other applications) to use a http-proxy permanently.

Note:- On some installations there will be no apt-conf file set up. This procedure will either edit an existing apt-conf file or create a new apt-conf file.

sudo gedit /etc/apt/apt.conf

Add this line to your apt.conf file (substitute your details for yourproxyaddress and proxyport).

Acquire::http::Proxy "http://yourproxyaddress:proxyport";

Save the apt.conf file. 

for more information:
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

---

### Post by solitare on 2006-09-24
to bulldog.. yes, a typing error.. duh me!
 to leeghoofd.. ta, will try that but not in uni for a couple of days... will post later..
  cheers.

---

### Post by solitare on 2006-09-26
well that seemed to work for a while then i got

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

browser still working fine..   what did i do?

---

### Post by bulldog on 2006-09-26
> **solitare said:**
> well that seemed to work for a while then i got

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

browser still working fine..   what did i do?

What you did,I will never know,but it's possible another proces uses your /var/lib/dpkg/

Try later if it's persist or you could logout with ctrl alt backspace and log back in and see if you can do now.

---

### Post by JAwuku on 2006-09-26
> **solitare said:**
> well that seemed to work for a while then i got

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

browser still working fine..   what did i do?

This happens if you already have something like Synaptic, Adept or the updater running when you run apt-get, as both programs are accessing the same apt-get software database. Just close Synaptic and try again.

---

### Post by solitare on 2006-09-28
cheers all.... works a treet now

---

