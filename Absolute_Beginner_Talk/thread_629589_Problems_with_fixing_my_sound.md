---
title: "Problems with fixing my sound"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-02
Originally Posted by mcmc  View Post
Try putting the following into a new file inside /etc/modprob.d/ folder (call is sound or something):
"options snd-hda-intel position_fix=1 model=3stack"

(without the quotes)

Then run

Code:

sudo update-modules

and reboot

HTH

I found this on the forums for helping me fix my sound problems I have been having

I've been having a problem though, with putting a new folder into the modprobe.d file.
When I try to put one in it says, 

"Creating of folder /etc/modprobe.d failed"
can anyone tell me why. I need to get this sound issue fix
(ear Shattering high-pitched sound)

---

### Post by Dapman01 on 2007-12-02
Nevermind, got it working, thanks

Had to run it as root

---

