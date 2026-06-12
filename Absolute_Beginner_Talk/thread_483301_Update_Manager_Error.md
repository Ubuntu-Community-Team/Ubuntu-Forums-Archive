---
title: "Update Manager Error"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-24
Hi people
When I try to get updates using the update manager, I get an error message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

how do I fix this??

thanks

---

### Post by uberushaximus on 2007-06-24
Run

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

in a terminal :)

---

### Post by overdrank on 2007-06-24
> **ROUBOS said:**
> Hi people
When I try to get updates using the update manager, I get an error message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

how do I fix this??

thanks

you need to add the public key   did you add that source to your repos?


 	
uberushaximus      that sounds right

---

### Post by ROUBOS on 2007-06-24
thanks that fixed it :)

How do you people remember all those commands?

If only I could fix my ATI issue :(

---

