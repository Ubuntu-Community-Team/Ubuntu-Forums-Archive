---
title: "GPG and Unbuntu Code of Conduct"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Ub-linx on 2006-05-25
hi everyone

First of all please excuse me if I sound silly but am new to Ubuntu and linux.
Well since I really like what I've seen so far about Ubuntu and linux, I wanted to join the community and maybe see how I could help. But it seems I need some help with that :oops:  Well to sign the Code of conduct you have to generate keys using gpg and then clearsign the document which was previously downloaded (doc.txt). Did

gpg --gen-key

Keys were generated, then did 

gpg --clearsign doc.txt

It generated a file called doc.txt.asc, the content of which I pasted on the website and submitted. But it keeps telling me that the message doesn't have a public key. :confused: 

if I do gpg --verify doc.txt.asc I get the correct signature. Can anyone help me please? :-k

---

### Post by tminton on 2006-06-03
Wish I could, I'm running into the same issue..](*,)

---

### Post by az on 2006-06-03
[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)


You need to upload your key to the keyserver.

---

### Post by brentoboy on 2006-06-05
azz,
do you know how we can update the "sign the code of conduct" page (here...)
[https://launchpad.net/codeofconduct/1.0/+sign](https://launchpad.net/codeofconduct/1.0/+sign)

so that it explains that, I had the same issue.  anyone with a fresh install of dapper will need to know the stuff in that wiki page in order to get the job done.

---

### Post by kb3hkg on 2006-06-05
There used to be an explanation of this somewhere, I ran into the same problem but it was explained either through launchpad, or possibly through something with the ubuntu DCTeamLoco

---

### Post by slimb on 2006-06-05
i was able to follow the instructions both at the launchpad and at [https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)  to successfully sign the doc.

the wiki entry also includes information about the launchpad signing and it works rather well.

---

### Post by scantellay on 2006-09-06
Wow it was defnatily a learnning experance, but got it done. Can't stress enough to download the newest version of the code. Thanks to the people in the Ubuntu forums for helping me out.:)

---

