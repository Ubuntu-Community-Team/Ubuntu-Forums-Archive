---
title: "help installing alien"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by hawksigns on 2006-03-15
ok.. I'm following the instructions to install alien so I can translate .rpm files to .deb files and it's not working.

 sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  alien: Depends: debhelper (>= 3) but it is not going to be installed
         Depends: rpm (>= 2.4.4-2) but it is not going to be installed
         Depends: dpkg-dev but it is not going to be installed
         Depends: make but it is not going to be installed

Not sure how to fix this.  I need to figure it out because while I found a printer driver that will print black and white just fine, my colour printing is crappy!  I need to be able to translate the one from japan :(   I think I can figure it out, but I can't get this part to work!

---

### Post by zubrug on 2006-03-15
Try this after sudo apt-get install
sudo apt-get -f install

---

### Post by hawksigns on 2006-03-15
Ok, problem with that is it wants to remove my nvu because it has dependencies (but works fine anyway) and it doesn't look like it would fix this either...

 sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  nvu
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 26.3MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

am I wrong?

---

### Post by zubrug on 2006-03-15
try this
sudo apt-get update
sudo apt-get install alien

---

### Post by hawksigns on 2006-03-15
I did that the first time.  Can I just apt-get install the stuff that it's dependant on or will that not work?

---

### Post by hawksigns on 2006-03-15
honestly, if no one has any ideas then i have to go back to windows... I NEED my printer to work properly!!  Anyone???!!??? :confused:

---

### Post by KansasJoe on 2006-03-15
Try getting those packages it requires...i installed alien without a hitch and then put in the ones you are missing to see if they were installed on my comp and they were so you may just have to do them

sudo apt-get install debhelper rpm dpkg-dev make

---

### Post by aysiu on 2006-03-15
When you have weird dependency problems with apt-get, it usually means you have conflicting repositories.

Get a good list here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then do ```
sudo apt-get update
sudo apt-get install alien
```

---

### Post by hawksigns on 2006-03-16
I did that a few days ago.... looks like linux wasn't that good an idea for me.:( :( :(

---

### Post by hawksigns on 2006-03-16
Ok, I managed to get it installed by using synaptic, but apparently the rest of my instructions sucked because now I can't even get a test page.

---

