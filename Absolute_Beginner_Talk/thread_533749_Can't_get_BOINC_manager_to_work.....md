---
title: "Can't get BOINC manager to work...."
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by the.dark.lord on 2007-08-24
When I click attach to project, the following error comes up:

> BOINC Manager is not currently connected to a BOINC client.
Please use the 'File\Select Computer...' menu option to connect up to a BOINC client.
To connect up to your local computer please use 'localhost' as the host name.

Help anyone?

---

### Post by oldos2er on 2007-08-24
If you go to 'Advanced,' 'Select computer...,' and type 'localhost' in the hostname field, does it work?

---

### Post by the.dark.lord on 2007-08-25
> **oldos2er said:**
> If you go to 'Advanced,' 'Select computer...,' and type 'localhost' in the hostname field, does it work?

Nope :(

Same problem...

---

### Post by mikex on 2007-08-25
I had the same problem when i first installed it. I had downloaded it myself in one location, and also got it from the Synaptics utility. It wouldn't run until I got rid of one of the installations. I doubt that is your problem though. I finally got it running despite my bungling.

---

### Post by xzero1 on 2007-08-27
I use BOINC to run rosetta using the 64 bit beta client and have no major issues with it. I don't know what client you are trying to run but the rosetta site has a user forum that may be helpful.

---

### Post by OisinT on 2007-09-12
sounds to me like you have the BOINC manager installed, but not the client.

close down BOINC and try
```
sudo apt-get install boinc-client
```

and see if that works

---

### Post by bunny rabbit on 2007-09-28
> **OisinT said:**
> sounds to me like you have the BOINC manager installed, but not the client.

close down BOINC and try
```
sudo apt-get install boinc-client
```

and see if that works


That worked for me...

---

### Post by chilker on 2008-05-21
Haha, I feel dumb. Thanks for pointing that out... now, there should be a way to install both portions of BOINC through one icon on Add/Remove programs.

---

