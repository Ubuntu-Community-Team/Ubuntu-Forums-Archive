---
title: "[SOLVED] Network Places question"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-09-23
How come when I am using Gimp (we will use this application for this example) and I select open file my network drives do not show up under places? (see Screenshot).  I am sure that there is a simple explanation for this. Somehow i have managed to navigate to me server but am not sure is it is all set up the way it is supposed to be.

---

### Post by jimrz on 2007-09-23
> **mramsey said:**
> How come when I am using Gimp (we will use this application for this example) and I select open file my network drives do not show up under places? (see Screenshot).  I am sure that there is a simple explanation for this. Somehow i have managed to navigate to me server but am not sure is it is all set up the way it is supposed to be.

You can mount the network drive by creating a mount point and using smbmount, this will make it appear in your "places". Here is the [[COLOR="Sienna"]**_HowTo_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") that I followed. It works well and also allows playing video across your network using samba.

---

### Post by mramsey on 2007-09-23
> **jimrz said:**
> You can mount the network drive by creating a mount point and using smbmount, this will make it appear in your "places". Here is the [[COLOR="Sienna"]**_HowTo_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") that I followed. It works well and also allows playing video across your network using samba.

Thanks...That did the trick!:guitar:

---

### Post by jimrz on 2007-09-23
:)

---

