---
title: "checkinstall being held back"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-09-25
when i aptitude update/upgrade

it says checkinstall will be held back. does anyone know why? this doesn't seem to be affecting my computer but i am just curious.

---

### Post by dmizer on 2006-09-25
i'm not positive about checkinstall, but usually packages are held back because they require some intervention on your part (ie: rebooting).  this will usually only occur with kernel updates, but there are other updates that require it as well.

you can go into synaptic and click on the "mark all updates" option to install this update.  then you will most likely have to reboot.

---

### Post by wildseven on 2006-09-25
hmmm thanks, i tried that and nothing happend. ill keep checking. would it be safe to just
aptitude install checkinstall ?

i'm not sure what this program does.

---

### Post by dmizer on 2006-09-25
it's used for building packages from source.  if you've installed a non ubuntu version firefox, this is probably where it came from.

it's certainly not essential for day to day operation.  but as you suspected, aptitude install checkinstall should get rid of the message.  i thought sure that synaptic would do it too, but apparently i'm mistaken.

edit to add:
i'm not sure, but automatix might also install this.

---

### Post by wildseven on 2006-09-25
heh thanks for the reply,
aptitude install checkinstall definitely removed the error. thanks ^^

---

