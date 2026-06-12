---
title: "[SOLVED] 2 persisent Issues with HAL and web browsing"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-19
Is there any way to not have to do a sudo /etc/init.d/ hal start everytime i do a reboot?  It is highly annoying...

Im not sure if this is related but im experiencing exteremely slow responsiveness from any browser I have (Swiftfox or Opoera 9.5)  Im not sure if the two things are related..

Can anyone help my poor situation or is this a lost cause?

---

### Post by sports fan Matt on 2008-03-19
Is there something i could use to "force" hal to like start at every reboot and I wonder why mu browsers are wierd...Edit: Opera only shift words and text with Spaces to the right...

---

### Post by Shazaam on 2008-03-19
Do you have bum (boot up manager) installed? Gui for editing startup stuff. If you do, open it and click the "Advanced" button at the bottom. The first tab that opens should be "Summary". Look for  "Hardware Abstraction Layer" and see if it's checked.
Be carefull using it, some settings may render your pc inoperable.

---

### Post by sports fan Matt on 2008-03-19
Can i get BUM from Synmpatic?  I dont have it installed

---

### Post by sports fan Matt on 2008-03-19
Im installing it now...Would i need to relog in after i check and see?

---

### Post by sports fan Matt on 2008-03-19
Its checked but where it says "running" there is a question mark..

---

### Post by Shazaam on 2008-03-19
Might be related to your other post.....

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881)

---

