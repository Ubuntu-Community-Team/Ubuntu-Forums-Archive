---
title: "Need to Install a Network printer"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2006-08-07
i am a n00b at xubuntu and need to install an hp 2300 network printer. I cannot figure it out:(    i cant find out how to work CUPS and i dont know anyone who can help me.....the network is all windows computers and i just have one xubuntu to add to it...if you can help me.... thank you

---

### Post by houseisland on 2006-08-07
I a quite new here so don't take anything I say as authoratative.

1.  You need to know what the IP address of your HP print server/JetDirect is.  You can find this out by getting the print server to spit out a test page.  Is the Jet Direct an external or internal model?

2.   You need to find out whether the JetDirect will work with the Internet Printing Protocol.  Older JetDirects will not.  Newer ones will, but sometimes the feature needs to be turned on.

3.   If the JetDirect does not support IPP, you probably can't use CUPS.  Setting the printer up as HP JetDirect printer will work, though.

I beat my head against this problem for a bit with some Lemark print servers.  I could not get them to work with CUPS.  One of the print servers supported IPP, but the Brother printer attached to it refused to process any print jobs sent in this manner.  The non-IPP print servers could not be found using CUPS -- printing wouldn't work -- nowhere to send the job to.  All worked just fine configured without CUPS.  All set up as JetDirects.

---

### Post by Sniper99 on 2006-08-07
that seems to work but we would like to have a socket print function as opposed to an IPP....if you know how to do that it would be really appreciated      :)

---

