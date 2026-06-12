---
title: "[SOLVED] email works but most web pages will not load"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Muad Dib on 2007-11-11
Hey Noob Team,
I've seen a few threads on this, but none that completely apply to my problem.  I am using a Dell Inspiron 1200 with a D-link wireless card (1330 I think?).  I had a little trouble getting my settings right to connect to my home network using a DHCP protocol, but I think I have them now.  I am able to receive email.  However, some websites get completely hung up, some load partially, and some (very few) load just fine.  I would figure I botched the settings or that there was some other problem if I had absolutely no connectivity.  But, as I said, I get email and a few sites load right up.  Please send me your wisdom and get me straightened out.  I'm anxious to get used to Linux so I can trash my dual boot and dump XP.

Many thanks

---

### Post by scmason on 2007-11-11
Sounds like a problem with your MTU settings. If your network is using a non-standard mtu size, it can cause these types of problems.

[Read this thread]("http://ubuntuforums.org/showthread.php?t=3985") for more information.

---

### Post by Muad Dib on 2007-11-11
Sorry for my ignorance here.  What's an MTU and how do I adjust the settings to work properly?  Thanks for your reply.

---

### Post by Muad Dib on 2007-11-12
Read the link and it's very confusing for me.  One of the suggestions recommends creating a file in an executable file within the /etc file.  I finally found the initd file, but the option to create new file was blanked out.  Can anyone help with this?  Thanks.

---

### Post by Muad Dib on 2007-11-12
It was the ipv6 setting in Firefox.  I turned it off and it worked.  Yippee!!

---

