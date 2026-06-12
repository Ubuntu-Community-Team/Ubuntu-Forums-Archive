---
title: "Can't install applications"
date: 2009-10-12
forum: Apple Hardware Users
---

### Post by victoral.com on 2009-10-12
Hi first of all,

  Ok! So here's the deal every time I open Applications>Add/Remove..
I get:
 So I click Reload but then I get Whats going on?!
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131713&stc=1&d=1255366076[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=131713&stc=1&d=1255366076")[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131714&stc=1&d=1255366076[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=131714&stc=1&d=1255366076")

---

### Post by howefield on 2009-10-12
Which version of Ubuntu are you using ?

---

### Post by victoral.com on 2009-10-12
I;m Using 6.10  **(Drapper)**

---

### Post by howefield on 2009-10-12
I'd guess it has reached end of life, so the repositorys are dead.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Btw, Dapper Drake was 6.06, 6.10 was Edgy Eft.

---

### Post by victoral.com on 2009-10-12
Hmm could be, but is there a way i can change that? Say use other ones?

---

### Post by howefield on 2009-10-12
> **victoral.com said:**
> Hmm could be, but is there a way i can change that? Say use other ones?

Probably but is an upgrade to a later (supported) version out of the question ?

---

### Post by victoral.com on 2009-10-12
Yea because every time I go to System > Administration > Update Manager I get the same error messege

---

### Post by howefield on 2009-10-12
> **victoral.com said:**
> Yea because every time I go to System > Administration > Update Manager I get the same error messege

I was thinking on something a little more involved, like a reinstall with a current version. The current LTS is 8.04 Hardy Heron, and the current 9.04 Jaunty Jackelope being the latest but non LTS version.

---

### Post by victoral.com on 2009-10-12
You I fixed it all I had to do is change the repositories to the old ones thanks anyway

---

### Post by blackened on 2009-10-12
If you *are* using Dapper, then you can do a dist-upgrade to Hardy because they are both LTS releases.

That said, judging by your repo list, I think you're using Edgy (which reached its end of life 2008 April) and basically have two choices:

1. Do repeated dist-upgrades until you get to a version that still receives support (3 times to get to Hardy) or

2. Do a clean install of a supported version (preferably as current as possible for convenience).

**Edit:** Since your repo list was incorrect, I take back my entire comment. Good luck.

---

### Post by rjcalifornia on 2009-10-13
nevermind... you solved :)

---

