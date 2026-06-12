---
title: "gpg: no valid openPGP data found"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-10-21
just did my second fresh install of fiesty.
following instructions on [www.psychocats.net/ubuntu/sources](www.psychocats.net/ubuntu/sources).
i entered 
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -0 - | sudo apt-key add -

or something like that as it was cut & paste.the output i get back is what is in title.

any help explained simply thanks

---

### Post by jon zendatta on 2007-10-21
also when i try /etc/apt/sources.list   i get permission denied.
otherwise could i manually enter repository addresses into software sources>third-party sources?

---

### Post by krazy1912 on 2007-12-08
bump

---

### Post by angelorohit on 2008-03-15
Hey, I think that the error message is because you are not a super user. Do it as:
sudo wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -0 - | sudo apt-key add -

---

### Post by kevdog on 2008-03-15
I think your syntax is wrong.  Just cut and paste this into the terminal -- It should be an O and not a 0 (zero):

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

and are you sure:
[http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)

Is the right link -- If you cut and paste this in a browser you simply get a web page, not a gpg key.  That is most likely the problem.


Correction -- think this is the link to get the gpg key
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) 

So your line should read:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

---

