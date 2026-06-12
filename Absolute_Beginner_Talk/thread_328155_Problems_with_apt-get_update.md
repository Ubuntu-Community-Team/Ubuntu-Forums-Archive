---
title: "Problems with apt-get update"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by FarthestStar on 2006-12-30
I've just started trying out Dapper by following the [starter guide]("http://ubuntuguide.org/wiki/Ubuntu_dapper"), and I'm having problems updating. When I apt-get update, I get 

W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

at the very end. I'm pretty sure I set the key up correctly. Can anyone help?

Thanks in advance.

---

### Post by macogw on 2006-12-30
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

Put that in the terminal before you apt-get update.

---

### Post by FarthestStar on 2006-12-31
Does "|" mean like either or, or do I copy the whole line in verbatim?

---

### Post by taurus on 2006-12-31
> **FarthestStar said:**
> Does "|" mean like either or, or do I copy the whole line in verbatim?

That's called the pipe!  Otherwise, just cut the text with the left button of your mouse and paste it with the middle (little track button) button.  Then, you don't need to type anything which would minimize the typing mistake...

---

