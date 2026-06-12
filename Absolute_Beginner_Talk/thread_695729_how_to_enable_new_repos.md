---
title: "how to enable new repos"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Cew27 on 2008-02-13
hi are there any repos out their that contain even more usefull software, if so how do i enable them

---

### Post by jan quark on 2008-02-13
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Cew27 on 2008-02-13
that didnt work for me
cew27@cew27-laptop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
[sudo] password for cew27:
gpg: no valid OpenPGP data found.

---

### Post by spiderbatdad on 2008-02-13
#

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

#

Then, add the GPG Key:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by Cew27 on 2008-02-13
done but i cant see any new programs in add/remove can you name any?

---

### Post by spiderbatdad on 2008-02-13
look in synaptic package manager...you may have to hit the reload button... also see this site regarding medibutnu: [http://www.medibuntu.org/](http://www.medibuntu.org/)

you may also find getdeb interesting for software:[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Cew27 on 2008-02-13
what can i look for in package manager

---

### Post by taurus on 2008-02-13
What are you looking for anyway?

---

### Post by Cew27 on 2008-02-13
i just want to have a larger range of applications

---

### Post by taurus on 2008-02-13
If you could be a little more specific of what you have in mind, perhaps people can give you the right repos to add to your /etc/apt/sources.list.  Larger range of applications can mean anything and you don't want to add unnecessary repos to your /etc/apt/sources.list because doing so could crash your machine!

If you uncomment out all the repos in your original /etc/apt/sources.list and add Medibuntu's, you probably get everything that you need.

---

### Post by Cew27 on 2008-02-13
i want some dvd software aswell as music and media software

---

### Post by FuturePilot on 2008-02-13
What kind of DVD and music software? There's tons of stuff in the repos, but it depends on what you're planning to do. Could you please be more specific?

---

### Post by Cew27 on 2008-02-13
i was just wanting a larger choice of application

---

