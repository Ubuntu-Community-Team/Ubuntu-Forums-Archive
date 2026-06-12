---
title: "[SOLVED] Warning - package cannot be authenticated"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-25
OK - first time I use apt-get to install in terminal without any prompting or help I get 

WARNING: The following packages cannot be authenticated!

Is that simply because I'm installing something which I guess isn't supported by Ubuntu - the k3b mp3 package?

Can i say yes!

I was trying to do it through synaptic but that seems to be on a go slow with this file so thought I'd try this out - 

TIA :D

---

### Post by Sparkster185 on 2007-05-25
I think you're right.  Ubuntu does not include any restricted (non-open) packages in the default install.  However, there is a repository of restricted packages that contain various drivers, codecs, etc.  That's why you get that warning (I'm guessing).

---

### Post by meng on 2007-05-25
Just say yes. In my experience, the lack of authentication (unable to verify GPG keys, or something like that) is often temporary, unless you've added a non-official repository to your sources.list.

---

### Post by benanzo on 2007-05-25
This usually means that the repository you're downloading the packages from offer GPG keys that you can get which will be used to authenticate the origin/maintainer of that repo as legit. However, in this case which ever repo you're downloading from does not require you to have the GPG key, so apt is just telling you that no authentication is going to be performed. It is generally harmless, but you might look into where to obtain the keys for that repo, otherwise it's possible for someone with access to their server to plant dummy packages without you being the wiser. That's why the GPG authentication is important. The true maintainer/packager will sign the packages with their private key and then offer their public key to users, which they use to verify that the packages are legitimate.

---

### Post by forestpixie on 2007-05-25
Thanks all - 

I haven't added any repos for a while - I was under the impression if it showed in synaptic I'd added it and had the key? 

It definitely came from medibuntu which I'd already used - just trying a different way of installing on my own and get asked a question I wasn't expecting!


And thanks for the wise up on GPG keys - another piece of the puzzle.

---

### Post by meng on 2007-05-25
If it came from medibuntu, maybe you never added the GPG keys.
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)
should fix it.

---

