---
title: "Wireless init during boot sequence"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by spencewah on 2006-04-10
After much tinkering, I finally got my broadcom wireless card working.  It won't set itself up during startup though, I have to do that manually after Ubuntu is up and running. 

Not sure what info you need.  It's a belkin 54g (7010).  It's on wlan0.

---

### Post by taurus on 2006-04-10
What do you have to do manually to set it up?  Do you have to run something like
```

sudo modprobe ndiswrapper

```
from a terminal?  If yes, you can add that to your /etc/modules (but without the sudo) then...

---

### Post by spencewah on 2006-04-10
Hmmm, not sure.  I don't do it through the console, I go through System>Administration>Networking

---

### Post by taurus on 2006-04-10
Can you be a little more specific exactly what you have to do in Networking to activate your wireless card?

---

### Post by spencewah on 2006-04-10
System>Administration>Networking

type my password into the prompt

Under connections tab, I click on Wireless Connection

I click on the properties button

(in properties) Under the ESSID dropdown, I select my network (called Phi Psi)

(in properties) I make sure "Enable this connection" is checked

I back out of properties to the main screen, still under the connections tab by pressing the OK button.

I then click the "Activate" button to activate my wireless connection, and click OK to leave the Network settings window.

---

### Post by echo $USER on 2006-04-11
Can you post what your /etc/network/interfaces file contains?  You will need to add your wlan0 to that file to start it at boot.

---

