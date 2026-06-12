---
title: "libstdc++5 cannot configure..."
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by listen on 2005-10-16
Hi 

Tried to installed Skype but got an error msg at the end of configuration saying that the libstdc++5 package needs to be configured and installed first....
synaptic was great as it auto detects it and notify me to install the relevant package, that is libstdc++5.... 
but after installation, it had this error at the end 
"E: libstdc++5: subprocess post installation script returned error exit status 135"

thot that i could solve it by purging removing skype and reinstall libstdc++5 again...but i still get the same error....

does anyone know what is the problem...

btw ..tried to start skype ...no prob ...yet to operate it though..so cannot be confirmed...

i also tried "sudo dpkg --configure -a" - didnt get rid of that error also...

Thanks in advance 

regards

---

### Post by DJ_Max on 2005-10-17
You need the development packages. 
*libstdc++5-3.3-dev*

---

