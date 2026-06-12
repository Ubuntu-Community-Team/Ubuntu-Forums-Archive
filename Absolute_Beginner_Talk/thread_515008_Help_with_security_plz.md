---
title: "Help with security??? plz"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by gpap1266 on 2007-08-01
Recently i installed Ubuntu feisty and I'm behind a proxy.
I have this problem , i installed Google earth and when i run it from the console with sudo googleearth it connects perfect and everything it's ok, when i run it from the desktop icon , it says "could not contact the authentication server..."
I have the same exactly installation at home but with no Proxy and everything it's perfect.
I'm sure that is something about the security and how a usre can "react" with a proxy, but i'm too new to ubuntu so i can't fix it...:(
 Please any ideas???

---

### Post by Delkster on 2007-08-01
First of all, you shouldn't run the application itself with root privileges (i.e. with sudo) -- you only need that for the installation. Have you tried running it from the console with just "googleearth" without sudo? It might print something on the console and give a hint regarding what's wrong.

---

### Post by gpap1266 on 2007-08-01
I works fine if i run it from console even without sudo....

---

### Post by Nekiruhs on 2007-08-01
> **gpap1266 said:**
> I works fine if i run it from console even without sudo....
He is saying that it is not good to run apps as root when unessecary. So if the app does not require root permissions, just run it without sudo.

---

### Post by gpap1266 on 2007-08-01
thanks for the reply
but still i can't understand why the aplication still don't connect if i double click the desktop icon

---

### Post by gpap1266 on 2007-08-02
Another thing it's going on is gmail-notifier , at home ubuntu installation its working normal, but at the job (proxy) it says connection failed......

---

