---
title: "Dapper live CD fails to boot - iMac PPC g3"
date: 2006-06-29
forum: Apple PPC Users
---

### Post by JoshHendo on 2006-06-29
Ok. So I am promoting Ubuntu to some of my friends, and one of them said he would like to put it on his imac g3. So I went around to install it for him.

I put in the Dapper Live CD for Mac (that I got from shipit), hold down 'c', turn the computer on, and it comes up asking what I want to boot. I simply hit return/enter to continue, but then I get the following message:

```

Can't allocate initial device-tree chunk

```

And it has some text after it about the Apple firmware, and then a field where I can type things in.

Does anyone know how I could fix this problem? Does Breezy do this (I will install the breezy version and then upgrade to dapper if that is a way around it).

Thanks!

---

### Post by nkbj on 2006-06-30
That is a known bug in the Dapper kernel which has been fixed in the latest kernel update. Unfortunately it arrived after the shipit cdroms went into production. The way around it is to install Breezy and then upgrade to Dapper - just remember to enable the dapper-security repositories.

---

### Post by JoshHendo on 2006-06-30
Ok thanks!

I will download Breezy and install it that way.

Will report back here when I have tried that.

---

