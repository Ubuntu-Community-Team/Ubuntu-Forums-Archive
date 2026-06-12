---
title: "Successfully installed F-prot; yet installer keeps showing up in Synaptic"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by wildcardny on 2007-05-31
After failed attempts at installing F-prot via package manager, I was able to get it and the gui installed using posts found here.  Now, however, each time I try to install or remove a package, F-Prot installer shows up again.  How the hell can I rid myself of this nag?  Been so far unable to find a solution searching here.  TIA

---

### Post by wildcardny on 2007-06-02
bump :(

---

### Post by RomeReactor on 2007-06-02
Hi. Did you install F-prot with a downloaded file from [their site]("http://www.f-prot.com/products/home_use/linux/")? If so, that may be the reason it keeps popping up; sometimes Apt (the package manager behind Add/Remove, Update Manager and Synaptic) will treat a program installed this way with lower priority than one installed through it, so it will keep asking you to upgrade it. Or it may be that a new version has come up in the repositories. If you *did* download the program, it would probably be best to install the version from the repositories (using Synaptic).

---

### Post by wildcardny on 2007-06-02
Appreciate the response.  First attempts at install were thru Synaptic.  Tried "download and install", then "..download only/install later", whatever.  Always failed, and when I returned to Synaptic or used apt for other installs, the F-prot install prompt always returned and failed at install attempts.  Then, per [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357), I was able to successfully install.  But, it's the previous Synaptic install that keeps reappearing.

---

### Post by H.E. Pennypacker on 2007-06-02
The whole time I kept thinking "This newb isn't getting F-*Sp*ot right."  I guess I am the newb.  :)

---

### Post by RomeReactor on 2007-06-03
wildcradny, are you having problems installing other programs through Synaptic? I ask this since you say you tried installing F-prot this way and you had to resort to download the file from the site (the method you linked to). Do other programs install ok using Synaptic, Add/Remove, or from the terminal?

---

### Post by wildcardny on 2007-06-03
No probs installing any other app via any method; just that during install of other apps, the F-Prot installer pops up again.  Clearing cache and history from Synaptic doesn't help.

---

