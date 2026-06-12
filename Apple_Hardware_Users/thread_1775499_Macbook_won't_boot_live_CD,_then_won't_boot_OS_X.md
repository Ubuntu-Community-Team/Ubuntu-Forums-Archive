---
title: "Macbook won't boot live CD, then won't boot OS X"
date: 2011-06-04
forum: Apple Hardware Users
---

### Post by K1251 on 2011-06-04
OK so my problem is this:

The live CD (no specific distro - I get the same problem with Ubuntu, Kubuntu, and Lubuntu CDs) runs to the point of the text-based menu with "Try before installing", "Install" etc.

So I select Try Before Installing, the CD spins for a bit, then I get a black screen. Nothing happens from this point on so I power off and on again. At this point I eject the CD, and I get the Apple logo as usual blah. But then this turns into a sort of No Entry sign, which I googled and apparently it means the Mac can't find a boot device. So after extensive googling and trying different things (holding Alt and selecting Macintosh HD still does NOT boot, still get a no entry sign) I discovered that 'single user' mode gets it to boot. At which point I can go into preferences and reset the boot device.

I can't think of any reason why running the live CD would remove OS X from the boot devices, but it does.

Any suggestions?

- K

---

### Post by srs5694 on 2011-06-05
Are you able to boot OS X normally now? My impression is that you are, and you want to try again with Ubuntu, but obviously with better results. If I'm wrong, please clarify.

If I'm right, then it sounds as if the installer is messing with your firmware settings. It could be this is happening because it's trying to boot in EFI mode and then getting hung up. (I've seen reports that a direct EFI installation of Ubuntu 11.04 damages the firmware of some Macs, so this could be related.) If so, finding a way to force it to work in BIOS mode might work. I have several ideas along those lines, but these are just untested ideas:


[list]
[*]I've heard of a Mac-specific boot disk that, ironically, lacks EFI support. You could hunt that down and try it.
[*]Create a variant of the installer you've already got, but rip out the efi directory on the disc. You'd need to make it a bootable disc, though. If you've got the tools and know-how, you could try this. If not, it'd take too long to explain, at least unless and until you try other approaches.
[*]Try the 32-bit installer rather than the 64-bit installer, since the former lacks any EFI booting capability (AFAIK).
[*]Try the 10.10 installer and, if you want to upgrade to 11.04, do an in-place upgrade rather than use the 11.04 installation disc.
[*]Try another (unrelated) distribution, like Fedora or OpenSUSE.
[/list]

---

### Post by K1251 on 2011-06-05
Yes I can boot into OS X fine now, once the startup disk is reset it works fine. I'll try Ubuntu 10.10, and I'll try an unrelated distribution. I was looking at Linux Mint too, but since that's essentially Ubuntu-based I'm thinking I might have the same problem. I'll try your suggestions and post if I have more problems.

Thanks!

---

### Post by JohnAtilano on 2011-06-05
Don't change anything.  Try it again.  Except when you get to the "Try Ubuntu..." screen, press F6, scroll down and put an "X" next to "nomodeset" (you do this by pressing Enter or the SpaceBar).  Then select "Try Ubuntu", "Install" or whatever you want.  It will then boot fine.

I had to do this when installing Natty on my MacBook Pro 5,1.

---

### Post by Kobalt on 2011-06-06
Hello,

To by-pass the EFI problem and make it clean, I partitioned my MacBook hard drive using the BootCamp utility. Then I installed rEFIt, an EFI utility that will let you chose which OS to boot when your computer starts. Once rEFIt was installed, I booted up using the LiveCD of Ubuntu 11.04, pointed it to install on the BootCamp created partition... 
Now working like a charm.

---

### Post by K1251 on 2011-06-06
JohnAtilano, it didn't work! I'll give rEFIt a go and see what happens.

---

