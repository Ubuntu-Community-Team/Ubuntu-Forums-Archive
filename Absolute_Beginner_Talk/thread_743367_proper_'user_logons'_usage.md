---
title: "proper 'user logons' usage"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by keyser_soze on 2008-04-02
I recently  installed Ubuntu 7.10 Desktop.  I'm confused with 'userlogons' usage. I setup an Administrator account and 2 user accounts (one with admin privilages & one 'auto logon' without admin privilages. ) I found that that any programs installed by the admin accounts ,stayed with that account that installed it. ie: only  logged user can use it... it is not global.  Also, I noticed  that there apparantly no way to install programs (when logged in as the 'auto logon'  non admin user account* ). I expected the options to be there, but ask for an admin logon dialog to complete. the only way arround this (that I know of ), is to logon as admin, add admin privilages to  that user account* .  I am the only user using this computer. Am I missing something here?

---

### Post by kostkon on 2008-04-02
> **keyser_soze said:**
> I recently  installed Ubuntu 7.10 Desktop.  I'm confused with 'userlogons' usage. I setup an Administrator account and 2 user accounts (one with admin privilages & one 'auto logon' without admin privilages. ) I found that that any programs installed by the admin accounts ,stayed with that account that installed it. ie: only  logged user can use it... it is not global.  Also, I noticed  that there apparantly no way to install programs (when logged in as the 'auto logon'  non admin user account* ). I expected the options to be there, but ask for an admin logon dialog to complete. the only way arround this (that I know of ), is to logon as admin, add admin privilages to  that user account* .  I am the only user using this computer. Am I missing something here?
Indeed, only a user with admin priviledges can install programs and that's the safe thing to have, I believe. Any applications you install using a package manager (Synaptic, Add/Remove, Apt) are supposed to become global. How did you install the applications you say that don't work for the other users of the system?

---

### Post by keyser_soze on 2008-04-04
> **kostkon said:**
> Indeed, only a user with admin priviledges can install programs and that's the safe thing to have, I believe. Any applications you install using a package manager (Synaptic, Add/Remove, Apt) are supposed to become global. How did you install the applications you say that don't work for the other users of the system?
thanks for your reply. I'm glad they are supposed to be global.  I am visually impaired and installed Orcha (a screen reader & magmifier) using the package manager and one of the admin accounts, but it wasn't there when I logged on using any of the other accounts.  somehow I must have missed a step or setting.   I will try it again. Thanks again

---

