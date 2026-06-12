---
title: "fakeroot??"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by hwe001 on 2006-07-03
Hi I am working on a workstation and can not use 'sudo', but how to install a software (eg Skype) locally?  anyone knows how to use "fakeroot"? does that mean I still can use "fakeroot" to install a software locally?

Thanks, Harvey

---

### Post by golfbuf on 2006-07-03
[QUOTE=hwe001]Hi I am working on a workstation and can not use 'sudo', but how to install a software (eg Skype) locally?  anyone knows how to use "fakeroot"? does that mean I still can use "fakeroot" to install a software locally?

Thanks, Harvey[/QUOTE]

No, fakeroot is used when building packages in your user account, and all it does it change the owner of the files in the package to root:root, instead of user:user.

If you want to install packages on your system directories, then you have to use sudo or be root.  However, you can locally install software in your user directory and use it successfully.  This is not secure, because you could mistakenly remove a file from your user account and break the software.  A good example is the firefox binary from mozilla.org .. you can download it into your user directory, untar it, and just click on the 'firefox' script to start it.  I have not used Skype, but maybe you can do this with Skype too.

You should get access to sudo to install software properly, or have someone who has sudo install it for you.

HTH,

---

### Post by MaximB on 2006-07-04
actually battleroyalex found a solution :
"seach for "alien" in the package manager and install it
then type fakeroot
it will log you into something like root@username: and no it didn't ask for a password"

---

### Post by Jagot on 2006-07-04
Or you could just use sudo -i

---

