---
title: "uninstall a virtual machine"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Doug11 on 2006-12-09
I just installed winxp with vm virtual server.I must have messed something up during the install of xp cause i just cant get it to connect. I had it the first time i tried it,,but seeing that it worked, i reformatted my whole hd and am running ubuntu mainly and will jsut boot up xp on vmware only as needed. Is there a way to get past this error or shold i do another install of xp and if so, how?

Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0.

thats the error i get on a boot of xp.

---

### Post by useResa on 2006-12-09
> **Doug11 said:**
> I just installed winxp with vm virtual server.I must have messed something up during the install of xp cause i just cant get it to connect. I had it the first time i tried it,,but seeing that it worked, i reformatted my whole hd and am running ubuntu mainly and will jsut boot up xp on vmware only as needed. Is there a way to get past this error or shold i do another install of xp and if so, how?

I don't think you have to re-install XP.
But if you want to delete a VM, select a VM and when you get the screen which allows you to start the VM, go to the menu and select VM-->Delete from Disk. This will remove the entire directory in which the VM was located.

> **Doug11 said:**
>  Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0.
This has to do with your Ethernet setting.
Are you using bridged networking?

**[COLOR=red]EDIT:[/COLOR]** I do not know to much about these things, but I know I have received some good answers on the [VMWare Forum]("http://www.vmware.com/community/index.jspa?categoryID=1")
Maybe if nobody can help you here someone there may be able to help you

---

### Post by Doug11 on 2006-12-09
[/I]
I've tried it bridged and I also tried it in NAT mode. Each way I keep getting the same error. Will keep messing with it.

---

### Post by useResa on 2006-12-09
> **Doug11 said:**
> [/i]
I've tried it bridged and I also tried it in NAT mode. Each way I keep getting the same error. Will keep messing with it.

Personally I am using (I'm on wireless) a "Custom: Specific virtual network" and that always works for me.
However, unfortunately :(, I cannot remember what made me choose for one of the specific virtual networks (got the hint from someone at work). Since I set this, it always worked.

---

### Post by Doug11 on 2006-12-09
I'm wireless also. Will give it a whirl. Thanks

---

### Post by useResa on 2006-12-09
> **Doug11 said:**
> I'm wireless also. Will give it a whirl. Thanks
Then let me add: I am using /dev/vmnet2

---

### Post by Doug11 on 2006-12-10
Well, i re-installed vmware, and when the option come up again as to it being part of a network, i chose "yes" paid attention to what is was configing and setup "Custom: Specific virtual network" slected /dev/vmnet8 and works fine now. Thanks for the help.

---

### Post by useResa on 2006-12-10
> **Doug11 said:**
> Well, i re-installed vmware, and when the option come up again as to it being part of a network, i chose "yes" paid attention to what is was configing and setup "Custom: Specific virtual network" slected /dev/vmnet8 and works fine now. Thanks for the help.
Glad that I could help and glad that you have VM working now.
Hope you will enjoy VM Server as much as I do. Good luck  :-D

---

