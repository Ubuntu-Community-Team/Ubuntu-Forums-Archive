---
title: "Linux headers"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-25
My machine is an i686 on running uname -m. However Linux or rather synaptic has been installing linux headers for i386 on it. Is it ok if I load i686 even though it insists on updating i386? Is there harm if I proceed with i686?

---

### Post by johnc4510 on 2006-05-25
I'm assuming that you did a regular install, which would include the i386, and then installed the i686. If this is the case, and you didn't remove the i386, it is also still installed on your computer, and when updates come down the pipe, your system automatically installs them because it stills reads i386 in the tree.

---

### Post by Koech on 2006-05-25
Ah, ok I haven't done nothing I only saw the headers in synaptic and was wondering whether to use the i686 regardless of the i386 already there.

---

### Post by johnc4510 on 2006-05-25
It won't hurt anything because the system will use the i686 package.
I will say this, everytime there's a kernel change you will get both the i386 and  the i686 image.
Which is just unnecessary.

---

### Post by Koech on 2006-05-25
Thanks for that, how do I then get rid of the i386?

---

### Post by user1397 on 2006-05-25
oops! bad post!
(nevermind me :))

---

### Post by az on 2006-05-25
[QUOTE=Koech]My machine is an i686 on running uname -m. However Linux or rather synaptic has been installing linux headers for i386 on it. Is it ok if I load i686 even though it insists on updating i386? Is there harm if I proceed with i686?[/QUOTE]
You can happily remove anything that is linux-386, linux-image-386 or linux headers-386 since you aer running a 686 kernel.

You can install the linux-headers-686 package.

---

