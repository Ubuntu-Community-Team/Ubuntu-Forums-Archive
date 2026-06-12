---
title: "Ubuntu keeeps freezing"
date: 2015-02-13
forum: Apple Hardware Users
---

### Post by Jakesploder on 2015-02-13
I recently purchased a mid 2010 macbook, and everything is working great. after installing the windows 10 beta alongside OS X, i installed ubuntu 14.04. the problem is, it will freeze after about a minute after logging in. Also, all graphics and fonts are screwed up. I was happy to see that the trackpad seems to work tho, after my experience with my mid 2007 macbook. Oh, and when i select Windows in either the standard boot selection (holding option/alt when starting up) or rEFInd menu, grub comes, but it only shows the windows recovery and ubuntu. Please Help!

---

### Post by Jakesploder on 2015-02-14
Oh, and FUSE stopped working, so i can't edit the ubuntu drive from mac OS X. I would now have to boot windows to change the linux partition, but it won't show up in grub. Help!!

---

### Post by luigiburdo on 2015-02-14
Windows dont have been installed bootcamp? in case from there probably you will be able to load macosx.
about ubuntu freezing you machine is nvidia board or ati + intel hd ?
try to add kernel options to Linux on grub.

---

### Post by Jakesploder on 2015-02-14
It has nvidia and it turns out the windows recovery option actually just boots into windows normally. mac OS X loads fine, because it uses EFI.

---

### Post by luigiburdo on 2015-02-14
im not expert on grub but i think it work like yaboot.
on grub command load option try :

```

Linux video=nouveaufb:off nouveau.modeset=1
 and check if the system continue freeze or not.



```

---

### Post by Jakesploder on 2015-02-15
Ok thanks i will try that.

---

### Post by Jakesploder on 2015-02-15
i put that line at the end of the boot options and it told me that [FONT=Ubuntu Mono][COLOR=#000000]video=nouveaufb=off[/COLOR][/FONT][FONT=arial][COLOR=#000000]&#8203; was a bad file or something like that. Sadly, it still froze.[/COLOR][/FONT]

---

### Post by ronsking on 2015-02-19
I had poor luck using plain Ubuntu 14.04 on my 2008 MacBook Pro; it also kept freezing.  I have since tried the MATE-Ubuntu remix and Kubuntu which both work fine without any lock-ups or freezing.  I stuck with Kubuntu 14.04 and everything works fine.

---

