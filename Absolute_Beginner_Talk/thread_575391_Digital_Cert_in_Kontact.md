---
title: "Digital Cert in Kontact"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-10-14
I just switched from Ubuntu to Kubuntu and thus I'm attempting to configure Kontact.  I can't figure out how to load my cert into Kontact.  When I was running Evolution, I just pointed to the cert file.  Kontact doesn't seem to work that way.  Is there some place I'm supposed to load the cert into the OS?

Thanks

---

### Post by jaygo on 2007-10-14
bodam,
I think this will do it for you (don't have SSL certs myself so can't test it):

[LIST=1][*]Pull up kmail (within kontact is fine)
[*]go to settings > kmail settings
[*]go to security & enable whatever cryptography backends you need
[*]go to Identities (top left), choose one, then modify
[*]from cryptography, you should be able to import whatever certs you need
[/LIST]

GL

---

