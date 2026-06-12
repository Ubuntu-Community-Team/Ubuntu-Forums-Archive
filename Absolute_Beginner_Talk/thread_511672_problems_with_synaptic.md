---
title: "problems with synaptic"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by omkarwagh on 2007-07-28
i dont know if you guys have been having the same problems as me but i have a dual boot with ubuntu and windows.

ive noticed that most of the "upgrades" that i do via synaptic for system files like the new kernel image released recently or some other things that i barely remember fail to update the grub configuration properly.

i mean common cant we have these upgrades or new installations with at least the basic sense as to realise that a swap partition CANNOT be a root partition even if god himself wishes it to be so, somehow they seem to have a fetish for setting my swap partition as my root in a variety of places thereby giving me a variety of confounding errors every time.

its not a one off problem. ive had it so many times that im quite sure nobody at the developers end thinks of this. we have a lot of talk of linux being ready for the desktop. but it cant be done if users like me who have absolutely no idea of computer programming and who use it for "regular" purposes keep facing these irritating problems. i mean i should be able to trust at least something like synaptic right? you cant expect most of your users to know the insides and out of a computer to be able to use it. doesnt make sense. that's not the major section of computer users. 

take a look at windows. it may crash. it may be slow. it may be idiotic(i still prefer ubuntu. except for the installing and upgrades part i have no problems with it and it WAY better than windows and suse(which i used previously)). but cmon an "official microsoft installation/upgrade" will NEVER screw up your comp.

sorry if im being a bit harsh but this is really not the first time. u may say since i have no idea of programming its easy for me to sit back and simply talk but hey its not a one time thing. and if microsoft can do it, why not ubuntu?

---

### Post by be4truth on 2007-07-28
If you find Windows better why don't you stay with it?
If you search the forum a bit you will find that you are not the rule but rather the exception. I don't exactly know what you do with your installation but I had never ever a problem like this upgrading a kernel. Sometimes I have 5 operations system with 2 or 3 swap files over 2 hard drives and no problems. Only the boot loader will be wiped out sometimes. But I feel you can't expect a developer to know how you set up your system, can't you? Stay with defaults and it works. Change them and learn how to fix stuff.
I have done years of Windows maintenance and once people start to play around with boot loaders and partitions .... How often do you reinstall Windows because you can't fix it any more? Be honest with yourself, not angry. 
Calm down and try to see where you make the mistake instead of blaming developers. They work for you - for free. What is your contribution?

---

### Post by por100pre1 on 2007-07-28
> **omkarwagh said:**
> 
ive noticed that most of the "upgrades" that i do via synaptic for system files like the new kernel image released recently or some other things that i barely remember fail to update the grub configuration properly.

i mean common cant we have these upgrades or new installations with at least the basic sense as to realise that a swap partition CANNOT be a root partition even if god himself wishes it to be so, somehow they seem to have a fetish for setting my swap partition as my root in a variety of places thereby giving me a variety of confounding errors every time.



First, GRUB keeps the old kernel on display which is a good idea, in case sothing doesn't work with the new kernel. In windows you don't get to choose the previous service pack at startup so if the new service pack breaks something you just got to see hell.

Second, I don't understand what issue are you having with the swap partition, in Windows you can hardly see pagefile.sys and you can't do much with it...

Third,** I'm a n00b** with just three months using Ubuntu and let me tell you Ubuntu is ready for my desktop. Is up to the user to unleash to power of the desktop.

---

### Post by rillip on 2007-07-28
> **omkarwagh said:**
> 

take a look at windows. it may crash. it may be slow. it may be idiotic(i still prefer ubuntu. except for the installing and upgrades part i have no problems with it and it WAY better than windows and suse(which i used previously)). but cmon an "official microsoft installation/upgrade" will NEVER screw up your comp.

sorry if im being a bit harsh but this is really not the first time. u may say since i have no idea of programming its easy for me to sit back and simply talk but hey its not a one time thing. and if microsoft can do it, why not ubuntu?

a) You are in the minority.  If you search around, however, I am sure there are people who have had your issue before and probably had it resolved.  I'm not familiar enough with Gnome to tell you had to troubleshoot synaptic.

b) Microsoft routinely releases hotfixes for updates because an update caused people's computers to stop working correctly. For example, my brother in law had to apply a hot fix because litterally every minute it would pop an error report.

c)You don't have to be a program to learn how to fix things in Linux typically speaking.  But again, this issue does exist for Windows, you just haven't experienced it, as most people don't experience your issue.

The only thing I can suggest, not knowing Gnome that well, would be to recommend you try manually editing your /boot/grub/menu.lst.  You'll have to launch the program with sudo to do it.  If you can't modify the file as root, then the file might be set to immutable, which would cause it not to update with package upgrade.

---

