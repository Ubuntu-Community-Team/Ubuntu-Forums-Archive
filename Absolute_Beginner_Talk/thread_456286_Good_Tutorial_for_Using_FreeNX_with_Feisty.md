---
title: "Good Tutorial for Using FreeNX with Feisty"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-27
Ive looked around the forums and found tutorial for setting up freenx with warty and hoary.  Im interested in using freenx with feisty.  Are the steps still the same, or is there something different I should do???

---

### Post by Marsolin on 2007-05-27
It's not a tutorial, but [here]("http://blogs.ubuntu-nl.org/dennis/2007/04/29/freenx-for-feisty/") is a blog entry I ran across with links to [FreeNX]("http://linuxappfinder.com/package/freenx") packages for Feisty.

---

### Post by kevdog on 2007-05-27
Ok, so I adjusted the sources.list and then installed freenx with aptitude.  Now what???

Any other reference I should be using to get the server up and going??

---

### Post by Marsolin on 2007-05-27
[This]("http://www.linux-tip.net/cms/content/view/298/26/") tutorial is for Debian Etch, but it should still help show you what to do.

---

### Post by kevdog on 2007-05-28
I definitely need help.  I installed the freenx server from seaveas repositories along with nx client.  I have ensured I can ssh to localhost without a problem.  To the nxserver I added my own username and password with the following commands. 

sudo nxserver --adduser <username> 
sudo nxserver --passwd <username>
sudo nxserver --restart

I can confirm that the server is up and running and my name is in the database.  Within my .ssh directory I now have a file called authorized_keys2.  (Could this be the source of the problem??? With only ssh I have a file called authorized_keys not authorized_keys2!).

Anyway I fire up the client
/usr/NX/bin/nxclient &

I configure it to use SSL encryption of all traffic.
I look at my key -- its a dsa private key -- I dont remember making this key, but oh well.

I push connect an I get



NX> 203 NXSSH running with pid: 8381
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Shouldnt the user be something else than nx, or maybe Im totally wrong on this one!!!

What should I try now!

---

