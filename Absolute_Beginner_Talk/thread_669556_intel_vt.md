---
title: "intel vt"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-16
Hello,

I have to run a vm on my machine, I have an IBM T61, I am running VM-Ware.  My processor has VT technology.  I have enabled my the VT on the processor and am preparing to install windows xp.  The question is do I have to install winxp64 to take advantage of the "vt" or can I install the regular version of XP?

I can't find very many clear cut easy to understand answers on the whole "VT" technology.   

Also, I have been told virtual box is another good vm, but it doesn't do USB is this true?

Thanks
Kezz

---

### Post by veloce on 2008-01-16
As  I understand it, VT helps the host do virtualisation better for all virtual machines.  If I am right then standard xp will recieve the benefits of vt.

The key to a good vm is to keep it "focussed", I found that, without virus checkers and all the other guff I tend to load systems with, than my xp vm ran quicker than native without vt technology!

USB is still a bit iffy under virtualisation.  It *should* work nicely under vmware but I have had various issues.  For example, a bluetooth dongle kept getting taken over by the host (ubuntu) and being lost to the vm.

---

### Post by KezzerDrix on 2008-01-16
Thanks, but I am reading mixed responses on the net.  Should I use the vt option or not? In Vbox it is a check mark, could turn it on and off and benchmark somehow.  What would I use to benchmark?  It would need to be a windows benchmark as it is windows I am virtualizing.

Sigh... To use VT or not to use that is the question? and if I should use VT should I use xp64 or xp32?

---

### Post by veloce on 2008-01-16
That's the trouble with the Web.  If you get a definitive answer it's most likely wrong!

IMHO, I would turn it on with vmware and not with virtualbox as vmware claims to use it and it can only improve performance.  I would use xp32 because the 64b stuff in vmware is still in beta.

---

