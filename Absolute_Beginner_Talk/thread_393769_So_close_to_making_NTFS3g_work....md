---
title: "So close to making NTFS3g work..."
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-26
Well, Ive gone through most of the typical crap trying to get this to work.. but when I try to mount using

sudo mount -a

I get the following response:
Error opening partition device: Is a directory
Failed to startup volume: Is a directory
Failed to mount '/dev/': Is a directory

Ive already gedit sources.list, and imported the GPG key. I dont know what locale or changing your locale means. 

What am I missing?

---

### Post by cowlip on 2007-03-26
try ntfs-config [http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

---

### Post by GSF1200S on 2007-03-26
> **cowlip said:**
> try ntfs-config [http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)
Holy crap... it was in a directory buried in my filesystem. WOW! But, while it appears all my system files are there, what about documents and crap like that? Not that I really need this function (access to fix messed up files is primary for NTFS3g), but isnt documents, music, videos, etc supported by NTFS3g? Yeah, I know that Ubuntu may not operate those files (ex: wont play mp3, plays .ogg).

---

### Post by cowlip on 2007-03-26
yes, everything you can see in Windows should be seen in Ubuntu's ntfs-3g.  Ubuntu can open mp3 files BTW, it just doesn't include them by default because of software patent insanity, but you can easily enable it and it will be even easier in Feisty Fawn :)

---

### Post by GSF1200S on 2007-03-26
> **cowlip said:**
> yes, everything you can see in Windows should be seen in Ubuntu's ntfs-3g.  Ubuntu can open mp3 files BTW, it just doesn't include them by default because of software patent insanity, but you can easily enable it and it will be even easier in Feisty Fawn :)

Sorry... im new but im really determined! Yeah, the folders seem to be different than I remember them in windows. That being said, Ive found all my music etc, and amazingly mp3 files are playing on Ubuntu right now. I dont know if I did something to  enable that function as you said, or if it was enabled right off the install. It all works.

Does Linux have the capability of playing wma? I could swear some of the songs in rythmbox were wma in windows, but theyre playing fine!

---

