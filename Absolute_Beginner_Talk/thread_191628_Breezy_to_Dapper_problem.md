---
title: "Breezy to Dapper problem"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-06-07
I had no problem on my box, but I get this message on my parent's computer:
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

I checked to see if Breezy was up to date and it was.  Any help?  Thanks.

---

### Post by ola on 2006-06-07
What this means is that the file Packges.gs is not found on the site [http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/)

You can use your web browser to verify that by surfing to: [http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/)

In the second case its seems like the user on the server have moved the packages grom /breezy to _breezy_obsoltete/

The users have probably stoped support breezy and if you dont use any packages from that repository it can safely be removed using synaptic (look for repositories in the menues, I cant remeber which it was right now). It's not critical that you remove the repositories.

Hope it solves you issue!

---

### Post by BarFly on 2006-06-07
Should I just burn an ISO?  I tried upgrading from both the update manager and from the terminal.  Same results.  Again, I had no problem with my computer, but that was when Dapper was in beta.

---

### Post by BarFly on 2006-06-07
Negative, my Swedish friend.  I wound up erasing the HDD and installing Dapper (they did not have any files).  Sure, there is a better way, but this was easier as my parents kept hovering over me asking why their computer is not yet updated (that and the simple methods failed).  Yes, I looked at the repositories and deleted the suspect ones, and some that I did not know what they were for.

Everything is fine now.  My parents have Dapper Drake.  Please remind me to never touch my parent's computer again!  I have no idea what they did to it to cause such a headache.

---

