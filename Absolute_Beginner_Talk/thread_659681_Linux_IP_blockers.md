---
title: "Linux IP blockers"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by kellogs908 on 2008-01-06
I hate to be create so many new topics and I havnt seen too much about this so I hope Im not bringing up soemthing that has been brought a a million times but is anyone runnign an ip blocker. I used to run peerguardian on xp, and I ran the beta on vista but it essentially made me reformat my computer. I have heard MoBlock is the peerguardian alternative so i tried installing it with no avail. I was wondering if anyone has had experiance with this ip blocker or others?  I appreciate everyones patience and people not jumping on my back for questiosn that have already been asked, after this is done the system shoudl be set for my requirments for some time.

---

### Post by Bachstelze on 2008-01-06
What do you want, exactly ? Just something that woul forbid a given IP address to access your system ? This can be done very easily by adding this address to /etc/hosts.allow, like :

```
ALL : 123.123.123.133 : deny
```

---

### Post by kellogs908 on 2008-01-06
that would mean i have to block every single address manually, peerguardian has it all configured for me automatically, it blocks everything from online trackers to my university if need be

i dont always have the time or knowledge to setup everything manually like that

---

### Post by kellogs908 on 2008-01-06
i actually figured it out i installed ipblock, dont like it quite as much as peerguardian but its close enough

---

