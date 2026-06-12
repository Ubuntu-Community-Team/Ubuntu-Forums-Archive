---
title: "Installed on my MacBook, some issues"
date: 2007-07-27
forum: Apple Intel Users
---

### Post by Tu13erhead on 2007-07-27
I just picked up a MacBook earlier this week.  I pretty much immediately installed Ubuntu via boot camp and rEFIt.  I then compiled a custom kernel via the tutorial that's in another thread here.  After that my trackpad wasn't working, so I tried again changing some stuff in menuconfig.  Now my trackpad works beautifully, but I'm having some issues.  Listed are in order of priority.

1 - Wifi - I've got the MadWifi driver installed and wifi works great when I boot up. However, after a while (could be a few minutes, could be longer), the connection seems to drop and I'm not sure why nor how to fix it.  The NetworkManager applet thing doesn't locate any wireless networks, and ifconfig ath0 down/up, dhclient ath0, wlanconfig ath0 list scan doesn't do anything either.  Any ideas to try here?

2 - Sound - Was working up until the latest recompile, now I get no sound, and VolumeControl says "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."  I have no idea where to start here.

3 - Backlight - F1 and F2 do not control the backlight as I assumed they should.  I tried installing macbook-backlight as per the MacBook tutorial.  No dice.

4 - HFS+ - Eh, I'll get to this later.

Any input would be greatly appreciated!

:)

---

### Post by cyberdork33 on 2007-07-27
I can't help much, but number 4 requires a kernel module so make sure it is enabled in your kernel config.

---

### Post by Tu13erhead on 2007-07-28
Anyone have anything they could offer?  I don't even know where to start!

---

### Post by Ptero-4 on 2007-07-28
you can use the .config in the macbook kernel compilation tutorial. Or you can compile a new kernel using the default .config file and then begin redoing your mods one at a time until you hit the ones that cause the breakage.

---

### Post by russo.mic on 2007-07-29
Not sure if this will help, but for me, installing the package pommed made my sound controls, eject, and backlight controls work.

Russo

---

### Post by Tu13erhead on 2007-07-29
> **russo.mic said:**
> Not sure if this will help, but for me, installing the package pommed made my sound controls, eject, and backlight controls work.

Russo

Mmm, it's already installed. :(

---

### Post by Tu13erhead on 2007-07-29
> **Ptero-4 said:**
> you can use the .config in the macbook kernel compilation tutorial. Or you can compile a new kernel using the default .config file and then begin redoing your mods one at a time until you hit the ones that cause the breakage.

Yeah, I used the patch from mactel-linux and the config file linked to on the Gentoo page.  I then went in and changed just a few items in menuconfig.

*shrug*

---

### Post by luisbg on 2007-07-29
To me the generic 386 kernel works fine.

Don't forget to read this.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by ronocdh on 2007-07-30
> **cyberdork33 said:**
> I can't help much, but number 4 requires a kernel module so make sure it is enabled in your kernel config.
I'm not sure what is meant by this; I know that I have full read/write to HFS+ in Ubuntu. All I had to do was disable journaling on my OS X partition from within OS X. This can be done via the terminal or with Disk Utility. Don't forget to edit your fstab if you want your OS X volume available upon boot in Ubuntu.

---

### Post by pveith on 2007-07-30
On Backlight:

If you got a new macbook, you probably have to change hal-macbook-backlight definition in "/usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi"

Use hardware-information to look up your macbooks vendow string. I suppose it is "Apple Inc." not "Apple Comupters, Inc.".  If this is the case, Replace "Apple Computers, Inc." with "Apple Inc." in the mentioned file. On restart of hal or on next reboot backlight should be working.

Hope that helps.

---

### Post by Tu13erhead on 2007-07-30
Hm..

I went through the tutorial again with linux kernel 2.6.22 and the latest mactel SVN version.  Sound and trackpad appear to work fine, and wireless is working after installing the driver again.  We'll see if that drops out.

Working on the backlight now.

---

### Post by Tu13erhead on 2007-07-30
> **pveith said:**
> On Backlight:

If you got a new macbook, you probably have to change hal-macbook-backlight definition in "/usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi"

Use hardware-information to look up your macbooks vendow string. I suppose it is "Apple Inc." not "Apple Comupters, Inc.".  If this is the case, Replace "Apple Computers, Inc." with "Apple Inc." in the mentioned file. On restart of hal or on next reboot backlight should be working.

Hope that helps.

I did this a few days ago, no dice.

Someone else mentioned trying pommed, when I sudo apt-get install pommed I get "Starting pommed: invoke-rc.d: initscript pommed, action "start" failed."

I'm thinking I might have fubared things by trying multiple different methods.  I believe I followed something to bind F1 and F2 to backlight controls manually, which didn't work either.  I can't remember where I did that.  

Any other ideas?

Thanks, all!

---

### Post by cyberdork33 on 2007-07-31
> **ronocdh said:**
> I'm not sure what is meant by this; I know that I have full read/write to HFS+ in Ubuntu. All I had to do was disable journaling on my OS X partition from within OS X. This can be done via the terminal or with Disk Utility. Don't forget to edit your fstab if you want your OS X volume available upon boot in Ubuntu.
In the first line of his post, he stated he made a custom kernel. if HFS support is not in the kernel, then you will not be able to use it. The generic Ubuntu kernel includes this, so it is not an issue.

---

