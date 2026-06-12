---
title: "Download 250 Megs of Updates with Dial-up -- Must do all at once?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-04-20
I would like to upgrade to Feisty, but the instuctions say to first use the package manager to get all the updates and install them first.  I have dial-up and my updates come to about 250 Megs, so updating the files all at once would be impractical, if it could even be done at all.

Is it possible to download the updates a little at a time, or must they be downloaded all at once?  I plan to get broadband withiin the next six months, but it's not currenly an option.

Thanks in advance.

---

### Post by Nythain on 2007-04-20
if you dont mind waiting... you can start them all... stop when you want, aptitude will store the ones you've already downloaded... then start again when you want... get more... lather rinse repeat untill all are grabbed... using this method they wont install untill all are downloaded though

---

### Post by heimo on 2007-04-20
May I suggest buying an Ubuntu CD or requesting a free one, over here?
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Yes, there must be a way to download the files bit by bit, somehow. But if you can get it on a CD (perhaps ask some friend with broadband to download & burn), it'll probably be best option.

---

### Post by F_r_e_d on 2007-04-20
I guess I failed to make it clear that I already have Edgy Eft, so I'm not looking to download the distro -- just need to download the updates so I can upgrade to Feisty.

BTW, I have access to broadband at work, but, as far as I know, it's not possible to download the updates to CD then install on my computer.  If it is possible, please let me know how.

---

### Post by Surkow on 2007-04-20
You could download the new Feisty CD and use the CD as repository to upgrade Edgy to Feisty. This way you can upgrade without using internet.

---

### Post by Nythain on 2007-04-20
theres a way... i forgot exactly how but you basically add an entry to your sources.list that treats the cd rom drive as a repo so apt-get checks whats in it for available packages also... but like i said, id stick with the little at a time method

---

### Post by Surkow on 2007-04-20
Just add something like this to your sources.list

```
deb file::///media/ubuntu-7.04-desktop-i386/ feisty main restricted
```

Media is the place where the CD's are normally mounted. Don't forgot to change the name "ubuntu-7.04-desktop-i386" to the name from the CD.

---

