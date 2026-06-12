---
title: "Sharing an External Drive between Windows XP and Gutsy."
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Pthance on 2008-01-09
First off, I'm relatively new to linux and very pleased with the OS that Ubuntu Gutsy provides.  With that said, I have been mostly successful in my ventures with the operating systems thus far.  However, the wifey is a little reluctant to the change as her comfort level with the M$ "operating system" as she likes to call it (an oxymoron imho) is keeping her back.  Because of this, I now have the burden of divining a solution to sharing a FAT32 external drive between us.  Previously I had the drive networked between the two computers in the house, but now I have it plugged into her computer and have no access to it (barring loading back my XP OS...I dual boot).  She likes her music on my...erm...her drive. But enough with the narration of life in my household.  I was wondering if someone could explain to me (in dummy terms) what I need to do to get my...I mean OUR drive back on my computer and allow her access to it.

Please bare in mind that I am new to linux still, so even though your instructions may be step by step valid, I would be much appreciative if your responses also gave brief explanations as to what certain commands were doing.  Anyways, I normally wouldn't ask for help but I'm really in a bind here.  I have read a walkthrough or four about setting up Samba but have either completely failed in my ability to follow simple instructions or have been woefully mislead with incomplete instructions.  If there is another easier program out there (gui based) instead of having to edit config files manually I would appreciate someone pointing me in that direction.  If there isn't, dummy proof instructions would be acceptable as well.  You guys Rock!! Thanks.

Pthance

---

### Post by tonycm1 on 2008-01-09
Here's a really good (yet enormous) guide on Samba :)

[http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/](http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/)

There's a section on there for "quick setups" i believe.... i remember what I did it a few months ago, it didn't take more than a few minutes using samba from the synaptic packet manager in Gutsy :)

---

### Post by kyphi on 2008-01-09
FAT32 can be read by both Ubuntu and Windows.  Just plug it into either operating system.

---

### Post by NullHead on 2008-01-09
K you need a user name to access files form Windows correct? well than to do that you need to run the following commands. ```
smbpasswd -a <username>
```and ```
sudo /etc/init.d/samba restart
```

---

