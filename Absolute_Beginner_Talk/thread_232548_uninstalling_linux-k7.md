---
title: "uninstalling linux-k7"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Ludwig7666 on 2006-08-08
howdy. it's me again. :p 

Ok I the other day tried to install some nvidia driver for linux so I can play some 3D games. It works and all but the site I was on said something about installing blah blah blah some numbers with a k7 at the end. I did just that but when I go to boot up my machine it always tries to load up that version of linux. It always freezes on loadup to, so hardboot time. I would have to esc all the time to just use 386 whatever version of linux. It also claims that I have a 324 something version also. So I would see

k7
k7 recovery
386
386 recovery
324
324 recovery.

I would use the 386 recovery one all the time.

How would I go about uninstalling them other ones?

---

### Post by louistan3 on 2006-08-08
i thnk the k7 version of the kernel is for AMD processors only.. tho im not sure.. but thats what i run in my box.. what kind of processor do you have?

---

### Post by Ludwig7666 on 2006-08-08
I have a pentium 4 2.8Ghz multi processor. 32bit not sure if it's 64bit compatable. don't think it is at all.

---

### Post by msak007 on 2006-08-08
Yes the k7 kernel is the non dual-core Athlon-specific kernel. If you are not running an Athlon or higher processor, that's most likely the cause of the lockups. If you want to remove it, simply go to Add / Remove Programs or use Synaptic to find the name of the kernel in the list, uninstall, and reboot. - basically, uninstall it the same way you installed it. Installing / uninstalling a kernel automatically updates GRUB for you, so by doing an uninstall it will update the list you see when you first boot. When you reboot after the uninstall, you should only see the 386 options. You can repeat the same procedure for other kernels installed that you don't want, but general rule of thumb is you should always keep an older kernel as a backup after an update just in case it doesn't work and you need to revert. So I would uninstall the k7 kernel and keep the other 2 (including the recovery kernels). They don't take up that much space anyway so it doesn't hurt to keep them around.

Also, as an alternative to uninstalling a kernel simply because you have to hit ESC every time, you could manually edit your GRUB list to not have a default kernel so you're prompted with a menu every time and can choose which one you want.

EDIT: You were posting at the same time I did so I didn't see that you're using a P4. That's definitely the cause of the lockup then, because as was stated already the k7 is an Athlon kernel. The kernel that's optimized for Intels is the 686 kernel. Try [this]("http://ubuntuforums.org/showthread.php?t=85917") thread for more info, it explains a little more what the kernels are and what you need to install. What you most likely need is the 686-smp kernel because of your dual-core processor. If you opt for a 686 kernel and everything works after the install, you can safely uninstall the 386 kernels you had installed before.

---

### Post by Ludwig7666 on 2006-08-08
see the problem was that I didn't use the add/remove to install any of that. i used the Terminal.

---

### Post by msak007 on 2006-08-08
Using the terminal is just another interface to apt. You can easily use Add / Remove Programs or (preferentially) Syanptic (as they're both GUI front-ends for apt), search for "k7", and uninstal anything you find that has that in the name that's currently installed. Then, search for the 686 kernel in the post I linked you to and install it. The point is that you can mix and match install / uninstall methods - it's all the same net result.

---

### Post by Ludwig7666 on 2006-08-09
thanks. I got both things done no with no problems.

---

