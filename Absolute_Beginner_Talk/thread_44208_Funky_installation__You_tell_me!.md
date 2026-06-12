---
title: "Funky installation?  You tell me!"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by Scoodaddy on 2005-06-24
When I first installed Ubuntu 5.04 I got what seemed like weird behavior.  Can someone tell me if it was normal, or if there was something wrong with my install (and if the way I resolved it is OK)?

After first logging in I tried to run Synaptic but it wouldn't accept my password.  After looking into solutions, I ran visudo and edited sudoers by adding the line "%admin  ALL=(ALL) ALL".  Then I ran Users and Groups (which I had to do from the command line with users-admin, since System -> Admin -> wouldn't accept my password either), created a new "admin" group, and added my username to it.  Then I logged out and back in, which allowed me to see the "Executing system administration tasks" checkbox in Users and Groups, which I now checked.  Only now could I run Synaptic &  Users and Groups.

Was this normal?  I have a hard time believing that.  I'm a relative newbie and it took a fair bit of learning to figure out how to do the above.  So did something go wrong with the install?  Did the steps I took restore things to how they should have been?  What gives?

Thanks in advance!

---

### Post by vtechstu on 2005-06-24
I had a similar problem.  Though I can't tell you exactly what i did to solve it.  Either it was the Kubuntu reinstall, or eventually it started working, either through updating through  sudo apt-get update or just over time, but everything works now.  Don't feel alone!

---

### Post by TheDude on 2005-06-25
[QUOTE=Scoodaddy]When I first installed Ubuntu 5.04 I got what seemed like weird behavior.  Can someone tell me if it was normal, or if there was something wrong with my install (and if the way I resolved it is OK)?[/QUOTE]

Thats a funky install. Same thing happened to me the otehr day on a Ubuntu box I was building. I just reinstalled to fix it.

---

### Post by Scoodaddy on 2005-06-29
I'd rather not re-install it, especially as I *might* have already fixed it adequately.  Would someone please tell me if the fixes I made are basically the same as what a proper install would have done?

- Added the line "%admin ALL=(ALL) ALL" to sudoers.
- Ran users-admin, created group "admin", and added my username to the new admin group.
- Gave my username "Executing system administration tasks" rights.

In particular I wonder if a proper install creates the admin group and puts the first username in it.  Thanks!

---

### Post by davahmet on 2005-06-29
[QUOTE=Scoodaddy]
In particular I wonder if a proper install creates the admin group and puts the first username in it.  Thanks![/QUOTE]

Yes.

---

