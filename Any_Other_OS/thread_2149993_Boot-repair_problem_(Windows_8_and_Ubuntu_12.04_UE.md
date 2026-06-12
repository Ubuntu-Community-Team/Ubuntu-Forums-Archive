---
title: "Boot-repair problem (Windows 8 and Ubuntu 12.04 UEFI)"
date: 2013-05-30
forum: Any Other OS
---

### Post by bart.vanaudenhove on 2013-05-30
Hello,

I installed Ubuntu 12.04 64 bit (actually Linux Mint 13 but it's basically he same, right?) next to Windows 8 on a HP Envy dv7 laptop, following first [this tutorial]("http://www.linuxbsdos.com/2012/11/14/dual-boot-mint-13-matecinnamon-and-windows-8-on-uefi-hardware/2/") (which didn't really work, install went fine but couldn't boot into Linux), and then [this one]("https://help.ubuntu.com/community/UEFI") (the "Trial and error" approach) using boot-repair from my linux live-USB.
This created a new dual-boot startup screen with an old-fashioned "Debian" background and lots of strange entries but it worked, so I was very happy. So everything seemed to work fine but I have one recurring problem.

Every time I want to boot into Windows and choose "Windows Boot UEFI", it says:
```
error: no such device AAC7-6C28
error: file not found
```
Then I have to select the entry "Windows 8 Recovery", which gives me the error:
```
error: unknown command 'drivemap'
error: invalid EFI file path
```
Then, if you can still follow, I **re**choose the entry "Windows Boot UEFI" (*the same that gave an error message before*), and I can boot into WIndows! I find this very weird but it works...

So finally I can boot into anything I want, which is great, but this weird error and the necessary procedure is a bit annoying.

I did boot-repair twice: the first gave me this link: [http://paste2.org/xJgG3f0M;](http://paste2.org/xJgG3f0M;) the second [http://paste2.org/gN3pB3GH](http://paste2.org/gN3pB3GH).

(I also used EasyBCD from within Windows but I don't think this has a lot of influence on the mentioned problem).

I'd be glad to provide any info if asked...

(Update: in the mean while I also posted this thread h[ere in Linux Mint forums]("http://forums.linuxmint.com/viewtopic.php?f=46&t=135412&p=725058#p725058"), might be more appropiate. Sorry for double posting...)

---

### Post by Perfect Storm on 2013-05-30
Moved to Other OS/Distro Support.

---

