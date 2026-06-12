---
title: "VMware - root password"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by redearl on 2005-12-29
Ihave down loaded the Image file to run ubuntu, in the new VMWare reader.
I cannot find any documentation on the password to do any thing with this image.
It comes up automagically in the gnome window. if i try to do any thing that requires root type of  privledges, it prompts for a password.
Does any one know what it is?

---

### Post by kevcart3 on 2005-12-29
the root account doesn't have a password to start out with, so in most cases, all you have to do it just type your password if it asks you for one.

If you need to specify a password for the root account, do this:

```

sudo passwd root

```

then type in a new password to use for the "root" account.

Edit: VV that's probably what you were looking for, guess i misunderstood the question :(

---

### Post by Miro on 2005-12-29
Do you mean the VMWare Player Browser Appliance -password? It is "vmware". Some info here: [http://www.vmware.com/pdf/bavm_getting_started_100.pdf](http://www.vmware.com/pdf/bavm_getting_started_100.pdf)

---

### Post by redearl on 2005-12-29
That password did not work. the image i'm working with is just the plain ubuntu image that can be down loaded.

---

### Post by linear on 2005-12-29
It's "ubuntu".

---

### Post by redearl on 2005-12-29
thank you linear that worked.
i tried it before but must have fat fingered it a number of times.

---

### Post by Miro on 2005-12-30
Hey, this is very nice, I didn't know there was a VMWare-Ubuntu image too. I am just now trying it and got audio working from the start. I never managed to get any sounds to work with the Browser Appliance -image. :-)

---

