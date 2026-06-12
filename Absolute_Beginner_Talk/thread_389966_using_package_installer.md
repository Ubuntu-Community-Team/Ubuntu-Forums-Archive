---
title: "using package installer"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-21
HI 
I am using package installer to install Xbindkeys.deb which is needed to install keytouch etc etc  sob!!! :) 
now when i try the package installer gives me this message
"A later version is available from a software channel" -" you are advised to blah de blah"
Now 2 questions how does it know this? it must have a record of this new program somewhere?  if so why doesnt it tell me where to get it?

as a complete newbie i dont have a clue what to do next.:confused: 

can some one explain this for me please?

Thanks

Mike

---

### Post by Rumor on 2007-03-21
Hi Mike,
The package installer checks the apt-cache and sees that the repositories contain the package you are installing. The one in the Ubuntu repositories is older than the one you downloaded. 

If you open up Synaptic (System > Administration > Synaptic) and use the search utility, you'd find that older version of this package and could install it that way. There's (usually) nothing wrong with installing a newer version the way you are.

---

### Post by mpooley on 2007-03-21
Thanks Mate!

---

