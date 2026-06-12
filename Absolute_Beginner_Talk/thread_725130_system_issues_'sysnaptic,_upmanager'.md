---
title: "system issues 'sysnaptic, upmanager'"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2008-03-15
synaptin manager says : E:the package second-half life needs to be installed but cant find archive          for it
  
E:internal erroropening cache(1). please report

and when i try installing it, it give and error message

when i try updating my ubuntu with my update manager it says:Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package secondlife-install needs to be reinstalled, but I can't find an archive for it.'

please how do i resolve these issue 

thanks expecting a sharp response

---

### Post by nnamdi on 2008-03-15
sorry it all started when i tried downloading a game called secondlife-install_1.19.0.5-0~getdeb1_i386 and tried installin itthen my internet connection got messie

---

### Post by FuturePilot on 2008-03-15
Try this
```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```
That will force remove it. You can try to install it again afterwards if you want.

---

### Post by nnamdi on 2008-03-15
thanks a lot,i got your reply,it worked.

---

