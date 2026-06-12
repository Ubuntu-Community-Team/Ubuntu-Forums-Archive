---
title: "[SOLVED] No desktop effects..."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by JimBuntu on 2007-12-13
I've tried to turn on the Compiz desktop effects but they just wont work. I to to System>Preferences>Appearance>Visual Effects>Normal and it says, "The Composite extension is not available". Any ideas as to why this is? I have tried to download all packages i could with Package Manager, but I think there are some that I still do not have. Which ones do I need to get this thing running. My version of Ubuntu is the AMD64 on a laptop. Its dual-booted with XP.

---

### Post by JimBuntu on 2007-12-13
:~$ /usr/bin/compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

This is what i got in terminal. Please help.

---

### Post by Bert_2 on 2007-12-13
Please check whether you have the appropriate driver installed for your graphics card (check it in the restricted drivers menu), if you use an nvidia card + driver it should work, intel cards work automatically, AMD and ATI cards work sometimes.
Keep in mind that if compiz (desktop effects) doesn't work 100% with your card that ubuntu then will not let it start (to prevent users from having very strange and bad looking graphics like off set stuff etc.)

---

