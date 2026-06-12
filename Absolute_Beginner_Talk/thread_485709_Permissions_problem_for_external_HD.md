---
title: "Permissions problem for external HD"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by lalji on 2007-06-27
I'm having trouble accessing an external HD from my ubuntu desktop. My old mac mini died, so to extract the data I physically removed the hard drive and used an external USB enclosure to try and access it from my desktop. I can mount the hard drive and access parts of it, but the particular folder that I want is locked and ubuntu gives me the error message that: 

"You do not have the permissions necessary to view the contents of "Documents"

I've tried to access it through terminal but i also get 'permission denied.'

Any suggestions? (Yes, I am the root used on the desktop).

Thanks!

---

### Post by phizikal on 2007-06-27
sudo chown YOURUSERNAME /HDFOLDER

---

