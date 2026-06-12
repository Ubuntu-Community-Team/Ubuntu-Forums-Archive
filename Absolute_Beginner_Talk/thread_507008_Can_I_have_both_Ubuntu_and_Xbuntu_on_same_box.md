---
title: "Can I have both Ubuntu and Xbuntu on same box"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by tommy2c on 2007-07-22
HI, 

I recently installed Ubuntu and really enjoy it. :)  I would like to try some other flavors.  

I'd want to try Xubuntu to see if my old PC might run better with the smaller release.  

If I install Xubuntu will it overwrite Ubuntu, or will GRUB allow me to dual boot?  Or, is there an easer way?

Thanks

---

### Post by misfitpierce on 2007-07-22
GRUB should let you dual boot so long as you resize your drive to allow space for new one. Im unsure if it uses same swap or not...

---

### Post by testube_babies on 2007-07-22
You can install them side-by-side as dual boot, and they will use the same swap.

Or, you could install one on top of the other:
[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

---

### Post by Majorix on 2007-07-22
Why do you have to dual boot when you can do this:

```
sudo aptitude install xubuntu-desktop
```

---

### Post by JesterDev on 2007-07-22
You don't need to dual boot. Just install it via the synaptic package manager, or via apt-get in the terminal. When you login look at the bottom left corner and choose Xfree as the session. You will boot right into Xfree just like you had installed Xbuntu.

---

### Post by por100pre1 on 2007-07-22
An even easier way:

```
sudo aptitude install xubuntu-desktop
```

Then select Xfce session at the login screen.

EDIT: Sorry, didn't see Majorix' post

---

### Post by misfitpierce on 2007-07-22
Man I just woke up and forgot all about that... Yes and kubuntu can also be installed through repo's to try another flavor

---

### Post by tommy2c on 2007-07-22
HI,

I did the install with terminal.  Seems to have worked fine as I'm in Xubuntu now.  

Thank you all for you helpful posts.

---

