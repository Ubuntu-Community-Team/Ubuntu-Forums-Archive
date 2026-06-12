---
title: "Synaptic or apt-get: upgrading packages."
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-28
People,

How do I upgrade installed packages using Synaptic or apt-get?

For instance: apt-get install told me that I need libc6 version 2.3.4-1 or greater, but Synaptic reports 2.3.2.ds1-20ubuntu as the latest version, which seems to not be the case.:???:

---

### Post by MichaelM on 2005-11-28
That's very odd; apt-get and Synaptic should be using the same repositories. If in doubt, I would do```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by paulozzzz on 2005-11-28
They did not work.

I tried the -f option.  It removed the broken package, but the old versions remained.  Both apt-get and Synaptic seem to not find the latest versions of the required packages.

What else should I try?:confused:

---

### Post by MichaelM on 2005-11-28
OK, which version of Ubuntu are you running? Hoary? Breezy? (I ask because my version of libc6 is 2.3.5-1ubuntu12.) Are you getting any error messages? What does your sources.list file look like?

That's about all I can think of right now.

---

### Post by akiro.yamamoto on 2005-11-29
[QUOTE=paulozzzz]They did not work.

I tried the -f option.  It removed the broken package, but the old versions remained.  Both apt-get and Synaptic seem to not find the latest versions of the required packages.

What else should I try?:confused:[/QUOTE]

Use the Synaptic package manager under System to enable your repositories and get the package you need.

If you need help the Official Wiki should be one of your stops it's got some great info.
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

Regards

---

### Post by paulozzzz on 2005-11-29
[QUOTE=akiro.yamamoto]Use the Synaptic package manager under System to enable your repositories and get the package you need.

If you need help the Official Wiki should be one of your stops it's got some great info.
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

Regards[/QUOTE]

Thanks, Akiro!  But I think it was not Synaptic's fault.  Today people of Linmodems newsletter told me to forgot about sl-modem-daemon module.  They sent me instructions to compile the softmodem driver because the fix (the required versions not found in Synaptic) is not available yet.:)

---

### Post by paulozzzz on 2005-11-29
[QUOTE=MichaelM]OK, which version of Ubuntu are you running? Hoary? Breezy? (I ask because my version of libc6 is 2.3.5-1ubuntu12.) Are you getting any error messages? What does your sources.list file look like?

That's about all I can think of right now.[/QUOTE]

Hoary.  Perhaps that is the cause.  There is no error.  Anyway I will try the compilation procedure suggested by the Linmodems crew.

---

### Post by Kyral on 2005-11-29
In case you are interested, to upgrade to Breezy change all instances of "hoary" to "breezy" in the /etc/apt/sources.list (you'll need sudo to edit it) then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

