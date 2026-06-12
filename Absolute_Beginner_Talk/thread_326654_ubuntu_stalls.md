---
title: "ubuntu stalls"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by 1KuleKatDaddy on 2006-12-27
Hello.  I've downloaded both 6.1 and 6.06 and burned both to iso cd images.  when i load from initial startup, both versions hangup.  6.06 says "loading' and that is all, while 6.1 gives me other errors.  

none of the other menu options work either.  adivce?

---

### Post by taurus on 2006-12-27
Did you check the integrity of the ISO image before you burned it to a CD and did you remember to burn it at 4x instead of default speed?

---

### Post by 1KuleKatDaddy on 2006-12-28
Thanks for the ideas.  The MD5 verifies correctly and I burned at 4x, but still the same problem.  It begins to load and hangs up with "loading" and no dots after the word.  I am trying to install over FC6.  Could this be a problem?

---

### Post by KenSentMe on 2006-12-28
I presume you are trying to install from the liveCD. Maybe you could try downloading the alternate cd. It comes with an text-based installer that has a bigger chance to run compared to the liveCD.

---

### Post by 1KuleKatDaddy on 2006-12-30
Hello again.  I tried the alternate version.  I still get a stall with an error stating Buffer IO error on device hdc, logical block 241600, 241602, etc.  

I have a new HD with FC6 installed.  I can't get the FC6 to work with my wireless NIC and postings I've read said this is a common problem with this version. So then I found ubuntu.  

How can you reformat a laptop hard-drive from Linux?

---

### Post by robinl on 2006-12-30
How about maybe doing a memory scan from the LiveCD?

---

### Post by riven0 on 2006-12-30
Well... if you want to wipe the hd completely, you could always try [killdisk]("http://killdisk.com/"). Not sure if this will help at all with those logical block errors, but it is a possibility. Maybe something went wrong with the way FC6 partitioned the hd? :confused:

---

### Post by 1KuleKatDaddy on 2006-12-31
riven0,

thanks for the help.  I used killdisk and then re-installed 6.1 and it works great.  


regards.

---

### Post by riven0 on 2006-12-31
> **1KuleKatDaddy said:**
> riven0,

thanks for the help.  I used killdisk and then re-installed 6.1 and it works great.  


regards.

Awesome! Glad to hear. :KS

---

