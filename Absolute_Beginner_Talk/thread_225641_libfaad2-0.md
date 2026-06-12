---
title: "libfaad2-0"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-30
What is that?
that file or wwhat ever it is, never updates or upgrades.
Everytime i run update manager and what not, it says that won't upgrade

Can anyone help me out with this?

---

### Post by croak77 on 2006-07-30
MPEG-4 AAC audio codec.

---

### Post by IrishGangsta on 2006-07-30
alrite now i know what it is
But now, how can i update it, install it, or what ever i have to do?

---

### Post by croak77 on 2006-07-30
Can you post the message you are recieving from sudo apt-get update && sudo apt-get upgrade?

---

### Post by IrishGangsta on 2006-07-30
No need to see the whole thing right?

This is just the bottom of update where the error messages shows:

Reading package lists... Done
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems

---------------------------------------------------------------------------
And here is the bottom of upgrade:
The following packages have been kept back:
  libfaad2-0
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by croak77 on 2006-07-30
You might want to remove that entry from you sources.list. 

From the webpage:

"These packages are build (and sometimes tested ;) on a Debian sid/unstable system. It probably won't work with Ubuntu. Ubuntu is not Debian, it's now a completely different distribution."

If you want to keep it, you need to add the key if you haven't done so. Open a terminal and paste:

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
gpg --armor --export F00175CA | sudo apt-key add -

It might be wise not to use that repo. As it is not an Ubuntu repo.

---

### Post by IrishGangsta on 2006-07-30
well after running those commands
then i ran update, the update ran with no errors
then i did upgrade, but that one thing still didnt upgrade

So i went to my source list and I just commented it. Rather then delete it, I dont know if i'll ever need it again or something.


But thanx for your help

---

