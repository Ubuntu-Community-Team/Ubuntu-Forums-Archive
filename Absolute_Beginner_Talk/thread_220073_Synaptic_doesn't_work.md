---
title: "Synaptic doesn't work"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-20
Hi everyone, when I tried to open synaptic Package Manager, a window popped up with the following:
> E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)

I really have no idea what happened.:confused: :confused:  Can anyone help? Thanks!:p

---

### Post by TravisNewman on 2006-07-20
yikes. Have you enabled the root account?

You might try opening a command prompt and typing
sudo mkdir /root

and trying again to see if that fixes things.

---

### Post by az on 2006-07-20
> **GStubbs43 said:**
> Hi everyone, when I tried to open synaptic Package Manager, a window popped up with the following:


I really have no idea what happened.:confused: :confused:  Can anyone help? Thanks!:p

How did you start synaptic?

Did you click on it from the menu?  Did you run

sudo synaptic 
from the command line or did you open a terminal, became root and then tried to start synaptic?

---

### Post by GStubbs43 on 2006-07-20
Thank you panickedthumb! That code worked! It also fixed my sudo problem which was linked to in my sig! What exactly did it do?

To azz: I did try running it both from the menu and terminal but neither worked, thanks anyway, it's fixed now so I'm all good! yay!

---

