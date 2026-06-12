---
title: "Restriced driver"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-01-23
Hi,

Ive just clean installed gusty gibbon and tried to enable desktop effects. It keeps asking me to install the nvidia restricted drivers but every time i click to do this it stays red and wont do anything. I have a gt 7800. Can anyone help. Thanks

---

### Post by thelatinist on 2008-01-23
> **Tek-Noir said:**
> Hi,

Ive just clean installed gusty gibbon and tried to enable desktop effects. It keeps asking me to install the nvidia restricted drivers but every time i click to do this it stays red and wont do anything. I have a gt 7800. Can anyone help. Thanks

Go to System > Administration > Restricted Drivers Manager and enable them there.

---

### Post by Tek-Noir on 2008-01-23
Thats what i was doing but it wont let me change them. Just stays at not in use and wont change.

---

### Post by Paul41 on 2008-01-23
Did you use envy to install the driver before?  The documentation says that the Restricted Devices Manager may not work properly if you did.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

---

### Post by Delkster on 2008-01-23
> **thelatinist said:**
> Go to System > Administration > Restricted Drivers Manager and enable them there.

And if that doesn't work, go to Applications > Add/Remove, search for "nvidia driver", and select to install the "new" variant. The 7000 series may require that (I'm not sure). Restricted Drivers Manager should probably figure that out for you and choose the correct version of the driver but in case it doesn't, try installing the "new" one yourself.

---

### Post by cooltd825 on 2008-01-23
try installing the nvidia-glx-new through Synaptic.

this worked for me......for a day, at least.  long story.

---

### Post by Delkster on 2008-01-23
> **cooltd825 said:**
> try installing the nvidia-glx-new through Synaptic.

That's pretty much the same thing as finding the "new" driver variant in Add/Remove Applications. So, yes, that might be one way.

---

### Post by Tek-Noir on 2008-01-23
Thanks, im gonna give them all a tr soon. Doing a full update first to see if that'll solve anything.

---

### Post by Tek-Noir on 2008-01-23
Thanks, did the full update and i think thats sorted it :)

---

