---
title: "Firefox cookies problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Paqman on 2007-03-31
I'm having cookie trouble with Firefox that's stopping me from accessing some sites. I'm running 64-bit Dapper, so have both a 64-bit and a 32-bit version installed. Both of them handle cookies fine when I run Firefox as root, but when I check the permissions on the cookies they seem fine (ie: read and write for me and others)

Any thoughts?

---

### Post by Trab on 2007-03-31
have you tried reinstalling firefox or reconfiguring it?
if you just use the reinstall option in synaptic it should save all your old settings.

if doing that doesnt fix it, that narrows it down to a user specific problem. from there i would reccomend saving the settings you need to from it, then using the completely unistall option in sypnatic (And then even checking ~/.mozilla or ~/.firefox and deleteing them if you dont have anything else in them). then reinstalling.

have you tried running firefox from console as regular user? does it give any errors?
cheers,
Trab

---

### Post by Paqman on 2007-04-01
No change when running it from a command line. I reinstalled the 64-bit version, there's no option to reinstall the 32-bit in Synaptic. No dice.

From the way it runs perfectly as root, am I right in thinking it's a permissions thing? Surely it's just a matter of tweaking the right file?

---

### Post by Paqman on 2007-04-04
(Bump)

Anybody got any thoughts?

---

### Post by cbonar on 2008-03-01
Hi Paqman, I hope your problem is solved today.

For others that would find this page from an internet search, I post here the solution I found working for me :

There was a difference in the configuration of the root user and my user : with my user I had the "web developer" module installed, and the option "Disable external site cookies" enabled.

Disabling it solved the problem.

---

