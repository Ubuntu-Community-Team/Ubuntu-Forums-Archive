---
title: "How to access Add/Remove"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-02-06
Hello. From the very gitgo, when I installed Ubuntu, Add/Remove Programs was in my Applications List at the very bottom. I went into it, and it has disappeared and never more to be seen.

I would like to know, either how to get it back, or how to access it by a command.
I know synaptic does bascially the same thing, if not better, but I would like to be able to access Add/Remove Programs.

Anyone have any ideas?

Dr Small

---

### Post by xpod on 2007-02-06
Have you tried checking the menu editor to see if it`s enabled ok?

Either by right clicking your menus then "edit menus" or by navigating to System>preferences>menu layout.If it`s not enabled in the applications tab then you just need to check the box.

Other than that i`m not sure what you could have done with it:)

---

### Post by Maestro23 on 2007-02-06
Might help: [http://www.ubuntuforums.org/showthread.php?t=352380&highlight=Add%2FRemove+programs](http://www.ubuntuforums.org/showthread.php?t=352380&highlight=Add%2FRemove+programs)

If not, run some keyword searches for add/remove.

---

### Post by Dr Small on 2007-02-06
> **xpod said:**
> Have you tried checking the menu editor to see if it`s enabled ok?

Either by right clicking your menus then "edit menus" or by navigating to System>preferences>menu layout.If it`s not enabled in the applications tab then you just need to check the box.

Other than that i`m not sure what you could have done with it:)
I checked dozens of times for it in there, but it wasn't there for me to enable.
@Maestro23: I'll try "sudo apt-get install gnome-app-install" once I reboot in Ubuntu.
I'm on Windows doing school.

Thanks for your help!
I'll keep you posted if things go sweet or sour. :)

Dr Small

---

### Post by Dr Small on 2007-02-06
uh oh. things went really sour.
Here's what I did:
> drsmall@drsmall:~$ sudo apt-get upgrade gnome-app-install
Reading package lists... Done
Segmentation faulty tree... 50%


I got that error, so now when i go to System -> Administrator -> Synapic Package Manager, it brings it up briefly, blinks and disappears! I can't access Synaptic!
What do I do now?

**EDIT**: I rebooted, I was able to access synaptic and I installed gnome-app-install and now I have Add Remove Programs!
Thanks!

Dr Small

---

### Post by Maestro23 on 2007-02-06
> **Dr Small said:**
> uh oh. things went really sour.
Here's what I did:


I got that error, so now when i go to System -> Administrator -> Synapic Package Manager, it brings it up briefly, blinks and disappears! I can't access Synaptic!
What do I do now?

**EDIT**: I rebooted, I was able to access synaptic and I installed gnome-app-install and now I have Add Remove Programs!
Thanks!

Dr Small


Good deal man. Glad it helped.:)

---

