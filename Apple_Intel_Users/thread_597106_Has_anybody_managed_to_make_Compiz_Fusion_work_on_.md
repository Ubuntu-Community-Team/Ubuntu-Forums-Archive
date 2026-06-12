---
title: "Has anybody managed to make Compiz Fusion work on MacBook?"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by jingo811 on 2007-10-30
Has anybody managed to make Compiz Fusion work on MacBook?
I'm thinking about buying that laptop for a partition experiment and tutorial project.  But I'm guessing Macs doesn't come with ATI or Nvidia graphics so I'm worried that Compiz Fusion might not be able to work on the MacBook hardware.

Any MacBook eye witnesses out there with working Compiz Fusion Desktops on their Apple laptops?
[http://www.apple.com/macbook/macbook.html](http://www.apple.com/macbook/macbook.html)

---

### Post by cyberdork33 on 2007-10-30
> **jingo811 said:**
> Has anybody managed to make Compiz Fusion work on MacBook?
I'm thinking about buying that laptop for a partition experiment and tutorial project.  But I'm guessing Macs doesn't come with ATI or Nvidia graphics so I'm worried that Compiz Fusion might not be able to work on the MacBook hardware.

Any MacBook eye witnesses out there with working Compiz Fusion Desktops on their Apple laptops?
[http://www.apple.com/macbook/macbook.html](http://www.apple.com/macbook/macbook.html)
yes compiz fusion works with pretty much any video card that can do 3D rendering.

MacBooks have Intel graphics by the way, MacBook Pros have nVidia (and older ones have ATI)

---

### Post by schauerlich on 2007-10-30
I've got full Compiz-Fusion on mine, no problems.

---

### Post by dmber on 2007-10-30
up and running without any problems.  first gen macbook here.

---

### Post by jingo811 on 2007-10-30
What chipset are you using those of you who is successfully running Compiz Fusion on your MacBooks?

I got this response from the Compiz Fusion forums and it doesn't look positive too me what that Compiz Fusion blogger told me.  I don't want to make the mistake and buy a MacBook with some new non-working chipsets.
> 

I am assuming that because they use the **i950 chipset**, everything will work fine.

I'm not sure if the new santa rosa ones are using the **Q965 chipset**, which is currently blacklisted due to broken xv support via XAA. I've also heard that the new ones coming out soon are based on the **X3100 chipset**, which might have problems too.

So your luck varies. Obviously, you'd have to install linux first which can by quite a pain in itself with the EFI and such (Although it is getting easier)

//
//
The Compiz Fusion weekly blog, written by me, can be found here smspillaz.wordpress.com


---

### Post by cyberdork33 on 2007-10-30
The santa rosa machines are MacBook PROS, and I believe they are working now also.

---

### Post by jingo811 on 2007-10-31
That blogger mentions the bootloader EFI for Intel Itanium architecture.  Does that mean I can't replace and run the bootloader GRUB easily?  Without doing some high risk BIOS configurations to the Mac laptop?

---

### Post by cyberdork33 on 2007-10-31
> **jingo811 said:**
> That blogger mentions the bootloader EFI for Intel Itanium architecture.  Does that mean I can't replace and run the bootloader GRUB easily?  Without doing some high risk BIOS configurations to the Mac laptop?

You cannot overwrite the EFI with Grub or lilo. Apple has, as part of the compatibility package to run Windows, enabled a virtual BIOS that allows booting of legacy OSs. This includes an emulated MSDOS style partition table and MBR. 

The only change I would make about grub (which you actually don't HAVE to do), is to get it to install to your Ubuntu partition rather than the MBR. 

This blog information seems a little outdated / misinformed / uninformed. Installing Ubuntu is rather straighforward. The most difficult part of the process being resizing your OSX partition to make room for it.

---

### Post by dmber on 2007-10-31
granted i have a first-gen macbook, but it was a piece o' cake installing ubuntu on my macbook.  follow the ubuntu macbook wiki and you'll be good to go.

---

### Post by doublemeat on 2007-11-01
I have 7.10 with compiz-fusion working great on my gen 2 santa rosa macbook.  It wasn't without hiccups, but still fairly minor issues.  A fresh install should have no problems (mine was an upgrade).

You really don't want to use GRUB though.  For starters, the keyboard is only active on a low percentage of reboots, and it's completely random, and there is nothing you can do to increase your odds.  You want to use rEFIt instead, which is a much, much nicer solution anyway.  Beautiful, in fact, and is designed specifically for the mac.  To do this, you just have to make sure you DO install GRUB, but as a stage 2 loader only--NOT the default of stage 1.  If you do accidentally install as stage 1 you can still recover though, just not super easy.

---

### Post by cyberdork33 on 2007-11-01
> **doublemeat said:**
> I have 7.10 with compiz-fusion working great on my gen 2 santa rosa macbook.  It wasn't without hiccups, but still fairly minor issues.  A fresh install should have no problems (mine was an upgrade).

You really don't want to use GRUB though.  For starters, the keyboard is only active on a low percentage of reboots, and it's completely random, and there is nothing you can do to increase your odds.  You want to use rEFIt instead, which is a much, much nicer solution anyway.  Beautiful, in fact, and is designed specifically for the mac.  To do this, you just have to make sure you DO install GRUB, but as a stage 2 loader only--NOT the default of stage 1.  If you do accidentally install as stage 1 you can still recover though, just not super easy.
How exactly do you do that? We have been just installing grub to the partition rather than the MBR.

Also, the keyboard problems were fixed in that last round of firmware updates (although it seems to have gone away again for some people).

---

### Post by doublemeat on 2007-11-02
> **cyberdork33 said:**
> How exactly do you do that? We have been just installing grub to the partition rather than the MBR.

Also, the keyboard problems were fixed in that last round of firmware updates (although it seems to have gone away again for some people).

That's good news about the keyboard being straightened out.  However, I still highly recommend rEFIt.  It is ultra-clean, professional, very simple, and looks completely integrated into the Mac world.  Plus it is a damn smart program.  Also I believe it's the only way to get multiple boot options onto one menu (e.g. Mac, Linux, Windows), without having to have a two-step selection process (could be wrong on that).

If you install from the alternate Ubuntu boot CD image, I believe you have more GRUB options.  Or, you should be able to boot from a "Super GRUB" CD image after the fact (should be able to find via google), and straighten it out that way.  Super GRUB is fairly easy but very tedious to use.

The problem with GRUB as a stage 1 loader, is that you can have GRUB or NTLoader as boot menu between Linux/Windows, but not both.  With GRUB as a stage 2 loader, you can have both and it is a much more seamless way to have both OSes.  I think it can work this way because even though NTLoader has no such options as GRUB, the MBR is simulated anyway through GPT, rEFIt is installed on EFI (GPT), and thus always start first no matter what NTLOADRER or GRUB do.  Then from there, as long as GRUB is a stage 2 loader, you can boot directly into any of the three (or two) OSes.

I searched my notes and found the exact steps I took to get GRUB straightened out after the fact, and cleaned them up a bit.  This is after you already have Mac, Linux, and XP installed, with GRUB as a stage 1 loader.  (Directions should be the same if you have Vista instead of XP).

[LIST=1]
[*]install rEFIt
[LIST]
[*]	boot to Mac OS X
[LIST]
[*]	install [rEFIt]("http://refit.sourceforge.net/doc/c1s1_install.html")
[/LIST]
[*]	boot to Linux on hdd
[LIST]
[*]	open a Terminal window (menu: Applications | Accessories | Terminal)
[*]	command: sudo aptitude install refit
[*]	command: sudo gptsync [volume]
[/LIST]
[/LIST]
[*]fix GRUB taking over MBR
[LIST]
[*]	boot to Live CD
[*]	mount Linux partition
[LIST]
[*]		menu: Places | Computer
[*]		double-click on the volume that matches the size of your Linux partition
[/LIST]
[LIST]
[*]			it will be easy to tell if it's the right one, and if not, no big deal
[/LIST]
[*]	change GRUB from stage 1 to stage 2
[LIST]
[*]		open up a Terminal window
[*]		command: sudo bash
[*]		command: cd /media/disk
[*]		command: grub (to get grub prompt)
[*]		command: find /boot/grub/stage1 (note result)
[*]		command: root (hd0,2) [or whatever you noted above]
[*]		command: setup (hd0,2) [or whatever noted above]
[*]		reboot Ubuntu
[*]		when it spits out the Live CD, replace it with Windows XP SP2 CD
[/LIST]
[*]	fix broken Windows NTLOADER (XP or Vista)
[LIST]
[*]		reboot on Windows XP CD
[*]		At the "Welcome to Setup" screen, choose reair (R)
[*]		select the Windows installation ("1: C:\WINDOWS")
[*]		command: fixmbr (choose "y")
[*]		command: exit (to reboot)
[/LIST]
[/LIST]
[*]make Ubuntu the default boot option in rEFIt
[LIST]
[*]	boot to Mac
[*]	edit /efi/refit/refit.conf
[*]	change "#legacyfirst" to "legacyfirst" (no quotes)
[/LIST]
[/LIST]



Hope this helps.

---

### Post by cyberdork33 on 2007-11-02
Ok that is what we have been trying to get people to do. (with rEFIt, of course).

When you are installing Ubuntu (from the live cd) you can set where you want grub to install with the "Advanced" button at the end. Then it never replaces your Windows bootloader.

You can set it in the alternate installer too, but I can't remember how to do it. It has been too long since I used that method.

---

### Post by rickwood on 2007-11-02
With the alternate install disk you specify where you want to install grub as part of the install -- can't miss it.  That's why I've used it in the past.

---

