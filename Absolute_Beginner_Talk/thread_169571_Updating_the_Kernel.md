---
title: "Updating the Kernel"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-05-02
How do I update my kernel to 2.6.16? Will my stabiltiy increase with the new kernel? I download the patch already, I need to know how to install it.

---

### Post by xyz on 2006-05-02
HI-Here's a link to a HowTo compile the new 2.6.14 kernel from kernel.org
[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)
I hope this is what you're looking for.
Also the Vanilla kernel ((Enhanced Performance kernel)
[http://ubuntuforums.org/showthread.php?t=84174&highlight=vanilla](http://ubuntuforums.org/showthread.php?t=84174&highlight=vanilla)

PS:BoneKracker,I think you're right about 2.6.16!!Oops!

---

### Post by BoneKracker on 2006-05-02
I think the current kernel for Breezy is 2.6.12 or so, isn't it?  I don't think 2.6.16 is in the mirrors yet for Breezy.

However, here are some alternatives:

1.  You mentioned stability.  Stick with what's supported for Breezy right now.  When Dapper is released in a month, if you upgrade, you'll get the new kernel anyway.

2.  You could upgrade now to the Dapper beta.

3.  You could compile and install your own kernel.  Someone's already pointed out a resource for that.

---

### Post by ComplexNumber on 2006-05-02
[quote=xyz]HI-Here's a link to a HowTo compile the new 2.6.16 kernel from kernel.org
[http://ubuntuforums.org/showthread.php?t=157560]("http://ubuntuforums.org/showthread.php?t=157560")
I hope this is what you're looking for.[/quote] that way is soooooooo unecessarily complicated. thats making it 100 times more long winded than it needs to be.   i've just updated my kernel to to 2.6.16. here is what i did:
-downloaded the new kernel and put it in my home directory
-logged out and booted into failsafe terminal 
-updated the kernel using rpm -Uvh kernel-2.6.16* (i have fedora core 5, so for ubuntu, it will be the equivelent dpkg command)
-rebooted

and voila. thats all thats necessary. i now have version 2.6.16 whereas before i had 2.6.15

---

### Post by xyz on 2006-05-02
[QUOTE=ComplexNumber]that way is soooooooo unecessarily complicated. thats making it 100 times more long winded than it needs to be.   i've just updated my kernel to to 2.6.16. here is what i did:
-downloaded the new kernel and put it in my home directory
-logged out and booted into failsafe terminal 
-updated the kernel using rpm -Uvh kernel-2.6.16* (i have fedora core 5, so for ubuntu, it will be the equivelent dpkg command)
-rebooted

and voila. thats all thats necessary. i now have version 2.6.16 whereas before i had 2.6.15[/QUOTE]

Thanks!This is 'right on'.Will give it a try!:)

---

### Post by ComplexNumber on 2006-05-02
[quote=xyz]Thanks!This is 'right on'.Will give it a try!:)[/quote] oh, and by the way, make sure you uninstall all kernel components (eg kernel-devel etc) before you do the install of the new kernel (ie so that you only have the basic kernel package remaining).

---

### Post by BoneKracker on 2006-05-02
Ah, I see.  You downloaded _binary_.

(In my opinion, if you're going to bother with deviating from what's automatically updated by apt, then it's worth configuring it yourself and compiling it for your rig.  But that's just my opinion.) 
:-D 

Good advice from complex.

---

