---
title: "Suspend on Drapper Drake (6.06)"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by artur123 on 2006-11-04
Hi,
I have problem with suspend on my computer. I have GNOME. If i will suspend its good. When i will restore computer from suspend all starts but my monitor will not start. Sorry for my bad english. 
Under Windows XP suspend 100% works ](*,) . If this topic was on forum please link me to it. 
My computer is Dell Optiplex GX150
Mainboard in dells delfaut 
CPU: Intel Celeron 900 MHz
RAM: 192 MB

Please help.

---

### Post by justplayin on 2006-11-04
Uh, well I'm no specialist on this but I got suspend to ram working with [this HowTo]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") from the wiki. But the Howto is only for Nvidia video cards. There's a more generalized guide for every pc which includes suspend instructions [here.]("https://help.ubuntu.com/community/SuspendHowto")

You probably have a problem with the initialization of your video card on resuming your pc. But problems with suspend can also result from a bios which doesn't respect acpi-standards, so maybe updating your bios may help. But don't update your bios if you haven't gone through every other guide on resuming after a suspend in linux on the web, because updating your bios can go terribly wrong as well!

I have a laptop too, but can't get suspend to work because of an outdated bios. By the way, maybe have a look at the boot-options in grub. When I change the boot options in the /boot/grub/menu.lst to "acpi=on apm=off" or "acpi=off apm=on" the laptop behaves different when suspending (although it  still doesn't resume at all). See the [GrubHowto]("https://help.ubuntu.com/community/GrubHowto") for details.

Hope this might help,

justplayin

---

### Post by artur123 on 2006-11-04
I haven't got a laptop. Dell GX150 is a desktop computer. My video card is Intel's OnBoard. 
maybe i have outdated Bios.

---

### Post by justplayin on 2006-11-04
Maybe you could try to figure out the names of the components on the motherboard and see if you can find any posts related to the "resume after suspend" issue. For example your Motherboard seems to have a Intel 82815 (or 815e) Intel Chipset, though I'm not sure about this. Doing a search on this would be [82815 suspend linux]("http://www.google.de/search?hl=de&client=firefox-a&rls=com.ubuntu%3Ade%3Aofficial&q=82815+suspend+linux&btnG=Suche&meta="). Or try "hibernate linux" and the name of the video chipset.
When searching the [Dell Website]("http://support.dell.com") I find a file for [updating your bios]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R89211&SystemID=PLX_PNT_P3C_GX150&os=LNUX&osl=en&deviceid=162&devlib=0&typecnt=1&vercnt=6&formatcnt=3&libid=1&fileid=120829") or a link to the [manuals]("http://support.dell.com/support/edocs/systems/opgx150/") where you can find the names of the components of your computer. With these names I'd try to do a search on your issue.
Or you can search the [Dell forums.]("http://forums.us.dell.com/supportforums?category.id=optiplex") They have quite a lot of threads about your computer.

But I must say I'm not very optimistic because the GX150 seems to be an old system and the old computers are known for mostly having a faulty acpi or apm implementation. And as I have said, I didn't get suspend to ram to work with my laptop but it works flawlessly with my newer desktop pc with an asus motherboard.

---

