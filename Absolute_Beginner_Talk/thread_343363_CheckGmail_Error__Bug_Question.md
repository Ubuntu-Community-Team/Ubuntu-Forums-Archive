---
title: "CheckGmail Error / Bug Question"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-01-21
Hello everyone,

I have this error with CheckGmail.

[https://bugs.launchpad.net/edgy-backports/+bug/74141](https://bugs.launchpad.net/edgy-backports/+bug/74141)

I read the bug report and supposedly this issue was resolved in 10.1.1 of the checkgmail.  I looked at my version and in preferences it says 10.1, but in the repository the version that is checked is 10.1-1.  What is going on?

---

### Post by Pobega on 2007-01-21
Keep checkgmail from the repos installed

Download the source from: [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Extract the source to your home folder, but rename the folder to be hidden (Put a period as the first character).

Then:> ln -s .checkgmail-1.10.1/checkgmail checkgmail
sudo mv /usr/bin/checkgmail /usr/bin/checkgmail2
sudo mv checkgmail /usr/bin/checkgmail

Now when you run checkgmail it will run 1.10.1

This also means you won't have to edit your autostarting programs or anything, and if you want to run the *old* checkgmail (Why would you?) just run checkgmail2.

---

### Post by brandoncolorado on 2007-01-21
> **Pobega said:**
> Keep checkgmail from the repos installed

Download the source from: [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Extract the source to your home folder, but rename the folder to be hidden (Put a period as the first character).

Then:

Now when you run checkgmail it will run 1.10.1

This also means you won't have to edit your autostarting programs or anything, and if you want to run the *old* checkgmail (Why would you?) just run checkgmail2.

Thanks!  :guitar:  Rock on

---

