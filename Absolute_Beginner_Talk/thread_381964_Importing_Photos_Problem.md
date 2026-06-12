---
title: "Importing Photos Problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by TwistesdTexan on 2007-03-11
I have been able to import photo's before but something has changed. I receive the following error.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Can anyone help?

Edgy 6.10
P4 3gig Hz 1gig ram
Camera Canon PowerShot A510

---

### Post by TwistesdTexan on 2007-03-11
I'm still having problems. Can someone please try to help?

---

### Post by Lord Darth Vader on 2007-03-11
It is really strange. I have had no problem with my camera until yesterday. 
I also get this error message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I have not changed anything (as far as I know). 
Does anybody know what can be the possible problem?

(my camera is  Canon A70 and as I said, it has been working with edgy just fine until yesterday)

---

### Post by TwistesdTexan on 2007-03-11
Resolved. Found another thread that suggested to force and older version of libgphoto.
I went into synaptic and searched for libgphoto. Then highlight ' libgphoto2-port0 '. Then from the menu bar click 'Package' and Force Version'. Select an older version of libgphoto. This should take care of the problem.
I hope this helps.
Forward Message

---

### Post by Lord Darth Vader on 2007-03-11
Thank you! I forced the older version and it fixed the problem.

---

### Post by cnbiz850 on 2007-03-13
> **TwistesdTexan said:**
> Resolved. Found another thread that suggested to force and older version of libgphoto.
I went into synaptic and searched for libgphoto. Then highlight ' libgphoto2-port0 '. Then from the menu bar click 'Package' and Force Version'. Select an older version of libgphoto. This should take care of the problem.
I hope this helps.
Forward Message

It seems that I can't.  When I do "force version", I have two choices, and if I select the earlier one, then a whole bunch of critical packages (including Ubuntu-desktop) will be deleted. What can I do?

---

### Post by tgone on 2007-03-15
> **cnbiz850 said:**
> It seems that I can't.  When I do "force version", I have two choices, and if I select the earlier one, then a whole bunch of critical packages (including Ubuntu-desktop) will be deleted. What can I do?

I have a similar problem...

I get two options when I choose "Force Version":

2.3.0-0ubuntu3~edgy2 (edgy-backports)
2.2.1-2ubuntu4 (edgy)

When I select the older version (2.2.1), it warns that the following packages will be removed:

gphotofs
gthumb
libgphoto2-2

But this sounds bad. How can I revert back to an older version of libgphoto? I just want my camera to work like it always has!

I still get this error when I try to import photos:

"An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x3070). Make sure this device is connected to the computer."

---

### Post by tgone on 2007-03-15
No need to remove any packages!

I found the fix: [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

I'm very happy now.

---

### Post by alyson on 2007-03-17
Thanks for the link, tgone.  That did the trick for me.

---

### Post by tgone on 2007-03-17
> **alyson said:**
> Thanks for the link, tgone.  That did the trick for me.

no problem ;) spread the word! it looks like a lot of people are affected by this bug...

---

### Post by Mud.Knee.Havoc on 2007-10-13
If you're still having problems after going through what that bug fix tells you to do, [check this out]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/64146"). I had to go through both before getting my brand new Fujifilm Z10 importing properly.

---

