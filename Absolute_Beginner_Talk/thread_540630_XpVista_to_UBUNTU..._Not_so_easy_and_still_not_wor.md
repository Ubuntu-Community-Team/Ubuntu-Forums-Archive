---
title: "Xp/Vista to UBUNTU... Not so easy and still not working"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by hamhoks on 2007-09-01
Hey there,

Everyone said it would be easy and well, as I expected, it is not.

Prior to my absolute beginner Linux/Ubuntu experience, I drove an exclusively MS rig with XP and Vista installed on separate drives and now Ubuntu is installed on a 3rd dive (I have 6 drives in all with a pair of WD Raptors in RAID 0).  XP was installed first and then Vista (the recommended MS way) and of course then Ubuntu.

As it stands now, XP is working, and both Vista and Ubuntu won’t load – heck, it could be worse:)

------------------------------------------------------------

What it took to get here, issue 1:
I have an ATI X card and was unable to install the GUI version of 7.04.
I read up on the Alternate Install method and FTP’d a TEXT ONLY image which I then installed

What it took to get here, issue 2:
Ubuntu wouldn’t load because I probably misconfigured GRUB… My XP install was NOT on (hd0,0) [wow, I'm speaking Linux!] and so the GRUB BOOT LOADER went to the wrong place.  Worse, was unable to fire up XP.  I ripped out the drives, installed them with XP as (hd0,0) and Ubuntu as (hd1,0) or in other words, as the master and slave on the primary EIDE port (Vista is installed my RAID drive so no stress here about getting it up and running – yet!).  Next, I fired up the XP Recovery console and reconfigured my MBR to recognize XP again.  But still, Ubuntu wouldn’t load.

What it took to get here, issue 3:
Seemed no real intuitive way to get GRUB working so I instead reinstalled it and this time around, installed GRUB correctly (I think!) where at least, it tries to fire up Ubuntu and, I still have access to XP – am assuming to get Vista up again, will need to undo my GRUB install via the XP recovery console, then boot into the Vista Recovery console so that, as far as my overall system is concerned, XP and Vista are the only installed systems.  Once done, I’ll hammer GRUB back into the mix.

------------------------------------------------------------

What’s actually installed byway of Ubuntu:
After I successfully loaded the text (err DOS version – is DOS the proper word?) version, I eventually figured that to apply the patch ([Installing Ubuntu 7.04: ATI X**** Cards ]("http://ubuntuforums.org/showthread.php?t=414194")), I had to start Ubuntu in Recovery mode (which the link doesn’t mention).  I then followed the commands and rebooted to find that I now seemingly had two versions of Ubuntu installed:
```
UBUNTU, KERNEL 2.6.20-16 generic
UBUNTU, KERNEL 2.6.20-16 generic (recovery)
UBUNTU, KERNEL 2.6.20-15 generic
UBUNTU, KERNEL 2.6.20-15 generic (recovery)

```

(Someone mentioned that even before Installed the ATI-X update that I'd at least be able to boot into the Ubuntu GUI but that I'd not have any 3D extension but that didn't appear to be the case.)

Assuming that ‘16’ was the most current version, I tried to boot into it and same ATI-X issue…. Monitor would shut down… So, tried the ‘15’ version and same ATI-X issue, Monitor would shut down.

------------------------------------------------------------

Am compelled to admit, what I’ve had to go though thus far as been fun especially since, I’m drawn back to the basics where I’m once again immersed into my hardware and the underbelly of how all the pieces fit together at a lower level.  But at the same time, although frustrated doesn’t fit, I’m of the mind that just the crud I’ve had to go though over the years from Atari 800, to Dos x86, to Win3.x, to Win95, to Win 98, to Win XP to Vista – that essentially, nothing has changed (albeit, Linux is free and Linux will eventually force MS to become lean and competitive once again).  Further, as in just about all the OS’s I’ve mentioned, things are usually golden when starting with a virgin system tailored to the OS in question.

------------------------------------------------------------

So, what next?  Not withstanding my purchasing an NVIDA card on the Ubuntu ‘approved’ list, what more can I do to log into Ubuntu and experience Linux goodness?

Also, regards getting Vista up again, is there an easier way get it working without playing the game I mentioned above?  To that extent, I imagine GRUB isn’t able (yet) to natively have both XP and Vista on it’s menu but instead passes control to whatever Windows loader has been installed and from there, I’d again have to select which of the two WIN OS’s to start from… Yes?

Thanks for your support thus far :)

---

### Post by HermanAB on 2007-09-01
Note that if you have two or more problems with a Linux install, then you should try a different distribution.  Each distro has a different set of wizards and while all distro makers have large labs, they don't have one of everything ever produced in the whole wide world, so if a distro won't install properly for you, then you should shop around a bit and try Mandriva, Fedora, Mepis, Suse and so on.  Chances are that one of them will install flawlessly.  

Underneath the superficial glitz they are all the same anyway.  It really is only the configuration wizards and wallpapers that differ!

BTW,  virtualization has improved enormously in the last two years.  Therefore my preferred method to have trouble free systems, is NOT to dual boot, but rather install a base system, be that Windoze or Linux, then install VMware/Virtualbox/Qemu and install my guest systems in that.  This is the best way to avoid hosing the host system and you then get the advantage that you can run everything concurrently and never need to reboot.

Cheers,

H.

---

### Post by mgmiller on 2007-09-01
It's kind of a cheaty way to do, but have you considered installing wubi on your XP disk?

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by hamhoks on 2007-09-02
Thanks guys for the alternative... I'm kinda stubbord though and am going to press ahead with this distro.  I did expect problems and to jump to a new distro 'half baked' as it were only to potentially run into a new set of issues, a new forum and account, isn't all that appealing to me.  At least for now I have a relatively stable config where I can at least log into both my primary OS and this one, albeit in a restricted fashion :)

Someone closer to home made comment regards my resolution setting and that I didn't have a monitor config in my XORG.CONF file... Not sure how even to edit files from the Linux recovery console but can always reinstall from scratch and at least control my resolutions to something more stable across the board.

---

### Post by nonewmsgs on 2007-09-02
first i want to commend you on the positive attitude you have.  although the problems are rough, you're handling it like a pro.

grub gets funny sometimes about which drive it considers first.  i would venture to guess that you might have one pata and the rest sata and it's calling one of them the first drive (sometimes it does this against the will of the BIOS boot order especially if there is a pci card involved.  anyway yo can try unplugging the non ubuntu drives and see if that helps at all.  if it is that means grub misnumbered the drives (as i have seen it do before and is trying to boot the wrong drive.

---

### Post by hamhoks on 2007-09-04
Thanks for the kudos:)

It's even more diverse... I have 3 EIDE (PATA), 1 SATA, and a pair of SATA in Raid 0 :rolleyes:.

But, I'm relatively past the GRUB issue (for now... will eventually tackle my unrecognozed Vista install but I hardly ever used it before even though it's the Ultimate edition!).

I'm stuck on the (or what I think to be) video driver issue.

I've reinstalled UBUNTU from scratch (didn't run into any GRUB issue this time around with my drives ordered in a GRUB friendly manor) then applied the ATI fix ([Installing Ubuntu 7.04: ATI X**** Cards ]("http://ubuntuforums.org/showthread.php?t=414194")), found again that I have two version of UBUNTU installed again (15 and 16) but still, when I fire up the OS, my monitor shuts down.

So, am  wondering from the console how I might install ATI latest drivers from the recovery console?  Call me a sadist but am looking for the most complicated way... in other words, am interested in doing a complete install from the recovery console including any downloads that need to occur.  Am hoping to gain more expereince this way:)

If it helps, I'm driving a ATI RADEON X850 (pro I think)...


Thanks!

---

