---
title: "chinese input method issue"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by craneo on 2006-09-30
I have been told there is a little bit of conflict between Openoffice and SCIM, and got the suggestion to install scim-bridge. but I can not find scim-bridge.

execution
> sudo apt-get install scim-bridge

result
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim-bridge


How can I get it?or it doesn't exist?

---

### Post by xtra2000 on 2006-09-30
you could try to use fcitx input method.

---

### Post by HeresJohnny on 2006-10-04
Hey, I think you are on to something.  I didn't know which command to use to download the right package.  You did.  I know what to do to get that package.  This package is in the Dapper Universe repository, and I'm guessing you haven't enabled it.  System>Administration>Synaptic Package Manager>Settings>Repositories.  Make sure the channels with 'Universe' in them are checked.  Apply your changes, repeat your 'sudo' command, and you should be good to go.

Hope this helps!

---

### Post by whizbaby on 2006-10-04
> **HeresJohnny said:**
>  repeat your 'sudo' command, and you should be good to go.
Yes, if you do **sudo apt-get update** first.

---

