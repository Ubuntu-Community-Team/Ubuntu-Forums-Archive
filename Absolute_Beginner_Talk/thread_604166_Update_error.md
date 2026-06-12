---
title: "Update error"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by frank002 on 2007-11-05
For the last week or so, I have been getting these error messages after doing the automatic updates

   W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 

W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release: The following signatuW: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
  
 This is the first time I run into this. Do I have to update the public keys? If so, how? I have had Gutsy for about 3 weeks and I had not seen these up until about a week ago.

---

### Post by frank002 on 2007-11-05
Sorry about cut & paste error. The [http://packages.medibuntu.org](http://packages.medibuntu.org) appears twice and the debian-multimedia.org error is missing the part about public key not available.

---

### Post by Maestro23 on 2007-11-05
You can just comment those 2 entries out in your sources.list.

Then run:

> sudo apt-get update && sudo apt-get upgrade

---

### Post by diablillo77 on 2007-11-08
Hello, I'm getting the same error when I "apt-get update". I have a few questions. I noticed most of my sources have a # at the beginning of them. They weren't that way in Feisty.

I only have 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
and all the lines for automatix... which I removed

The rest have #

Second, what do you mean by commenting out? Is that adding or removing the #?

---

### Post by Maestro23 on 2007-11-08
> **diablillo77 said:**
> Hello, I'm getting the same error when I "apt-get update". I have a few questions. I noticed most of my sources have a # at the beginning of them. They weren't that way in Feisty.

I only have 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
and all the lines for automatix... which I removed

The rest have #

Second, what do you mean by commenting out? Is that adding or removing the #?

You need to uncomment (delete the #'s) from all your deb and deb-src lines.  Save the file, then run:

> sudo apt-get update

sudo apt-get upgrade

---

### Post by frank002 on 2007-11-08
Thank you for your quick reply.

---

### Post by shahin on 2008-04-08
I tried to comment out the statements, but I do not see any statement in my sources.list file that looks like the name of the packages I get the error about.  Could it be anywhere else?

---

### Post by Boyohazard on 2008-04-08
There's an application under the administor menu called source manager or similar, immediately before synaptic package manager. Check that to see what you can enable/disable

---

### Post by philinux on 2008-04-08
Solution
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get upgrade

---

### Post by shahin on 2008-04-08
Thanks, this worked.

---

