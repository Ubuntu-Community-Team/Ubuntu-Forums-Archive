---
title: "Dead key in VirtualBox 1.5.0 in Feisty"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Biochem on 2007-09-10
Now that my warranty on my computer I want to get rid of dual booting and go for visualization for my Windows needs. I installed VirtualBox 1.5.0 (in feisty) and installed windows XP.

The problem is that many keyboard keys are dead in the guest OS. I found on the VirtualBox bug site something that looks like the solution. ([http://www.virtualbox.org/ticket/599](http://www.virtualbox.org/ticket/599)). 

However, they provide a file called VBoxKeyboard.so but I really don't know what to do with it. I guess all I need is to replace some file but where are they (Or even better how can I find it)

Thank you

---

### Post by steve.horsley on 2007-09-10
The link you give says it's a new version of VBoxKeyboard.so. It seems the existing copy is in /usr/lib. I guess that needs replacing.

---

### Post by Biochem on 2007-09-10
Thank you steve.horsley, that is exactly what I was looking for.

Too bad the new driver didn't solved my problem :(

---

