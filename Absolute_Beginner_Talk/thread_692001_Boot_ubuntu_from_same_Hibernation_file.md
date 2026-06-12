---
title: "Boot ubuntu from same Hibernation file"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by syegen on 2008-02-09
--------------------------------------------------------------------------------

hello everybody, 

i want create a hibernation( swap file) for my ubuntu and I want to boot system from this file for every startup?

Is there any body have any idea, how to control hibernate(suspend2) settings od configurations..

Thank you

---

### Post by codeslicer on 2008-02-09
I don't think that would be possible, although I'm not sure. Hibernation involves using the swap partition, not file. If you want to restore the open applications at startup, go to: System->Preferences->Sessions. There, you can go to session options and select Remember currently running applications, which should start them up when you logon. Or, you can check the checkbox to remember currently working applications when you log off.

But think about it, restoring the same exact status of the OS could fail because when you update an application, the state saved in your old hibernation "partition" wouldn't match the application's current version, and this could cause the OS to fail, especially if the kernels are different.

---

