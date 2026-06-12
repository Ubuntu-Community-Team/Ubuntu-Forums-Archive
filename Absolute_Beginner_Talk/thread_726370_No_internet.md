---
title: "No internet"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by .ultimate on 2008-03-16
Hey, i have a problem with putting my IP address into ubuntu, i have an error message coming up saying that the interface does not exist, so i can not acsess the internet at all using ubuntu. can anyone help me with this?

---

### Post by durand on 2008-03-16
A little information would be nice. Do you have a static or dynamic ip address, do you have a router? You can try ```
sudo dhclient
``` in a terminal (Applications > Accessories > Terminal) and see what error comes up. dhclient just configures dynamic ips.

---

### Post by .ultimate on 2008-03-16
i have a static ip addres and the computer plugs directly into the modem via ethernet

---

### Post by bsharp on 2008-03-16
Could you tell us what type of internet you have?

---

### Post by durand on 2008-03-17
Like whether it's cable internet, dsl, dialup or adsl or something else :S

---

