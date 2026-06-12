---
title: "Is there any hope for a Macbook8,2?"
date: 2016-10-12
forum: Apple Hardware Users
---

### Post by Qbeta on 2016-10-12
I have a 15" Macbook Pro from about 2011-2012. I'm wanting to install Linux on it since I really no longer have any use for Apple stuff but the hardware is still quite good (quad core I7 with hyperthreading at like 2.6GHz). I've tried several distros including Ubuntu 16.04, Linux Mint 18, and the latest Debian. None of them seem to be able to cope with this Macbook's wacky "hybrid" video scheme and get into X windows. The system seems to be still running as you can still do "Option-arrow" and get a text console but the graphics simply do not work. Without a desktop environment I can't make much use of it. I've researched this but I haven't found a clear exposition of the problem or, more importantly, a clear set of steps to use to get a graphics environment working for the installation. The "fix" that's usually offered is adding "nomodeset" to the boot params at the end of the command string. I've tried various versions of this with different combinations of the other params in there and none work.

---

### Post by alejandro-f on 2016-10-12
with this you should get it to work:

[https://ubuntuforums.org/archive/index.php/t-2157775.html](https://ubuntuforums.org/archive/index.php/t-2157775.html)

but i only can make it happen with the intel graphic card, i dont seem to get working the radeon card.
best

---

### Post by Qbeta on 2016-10-12
Yes, I think I found that post in my searches but had only skimmed it. It looks like it might be worth another try though the post is from 2013. I have some other doubts about this post though. For instance, is all that stuff about rEFInd really necessary? He also says things like this that I think are highly dubious > You should only attempt this after a fresh install of MacOs. Not doing so may result in undesired effects. The standard 64bit install images I made booted just fine, they just wouldn't run the video card properly. My installation of MacOS is far from fresh and I don't really want to go through all the nonsense of re-installing it only to destroy it immediately afterwards. I mean I'm not sure I even plan to keep MacOS around for anything and will probably get rid of the laptop itself when I can afford a new one from someone other than Apple. I'd like the fix to be as simple as possible. I really just need the thing to run development tools like javac, Eclipse, Arduino IDE, and LibreOffice.

---

### Post by &amp;KyT$0P# on 2016-10-13
> **Qbeta said:**
> Yes, I think I found that post in my searches but had only skimmed it. It looks like it might be worth another try though the post is from 2013. I have some other doubts about this post though
Don't waste your time over those other doubts.  The only thing you need to doubt is its relevance to your issue in 2016 with an Ubuntu version released in 2016 -
> The standard 64bit install images I made booted just fine, **they just wouldn't run the video card properly**.
Please see [this thread]("https://ubuntuforums.org/showthread.php?t=2335586") and report back.

---

### Post by Qbeta on 2016-10-14
> **halogen2 said:**
> Don't waste your time over those other doubts.  The only thing you need to doubt is its relevance to your issue in 2016 with an Ubuntu version released in 2016 -

Please see [this thread]("https://ubuntuforums.org/showthread.php?t=2335586") and report back.

Well, since I posted I've solved the problem and am running Linux Mint 18 (Cinnamon) on the thing :cool: Yes, I know this is Ubuntu Forums but the issue affects *any* distro of Linux.

The thread you reference, and especially your post at the end: [https://ubuntuforums.org/showthread.php?t=2335586&page=2&p=13539492#post13539492]("https://ubuntuforums.org/showthread.php?t=2335586&page=2&p=13539492#post13539492"), does provide useful hints. The problem the 8,2's have is more severe in that you can't run the installer to even get to the point where you can complain about your black looking green. In the thread you reference the complainants have clearly already got Linux running on the Macbooks > I've got a macbook pro running kubuntu (Ubuntu 16.04.01 LTS) some time in the last week or so the blacks started showing up as green bars ... From the research I did it seems that I was "lucky" and got the version of the Macbook (8,2) that was particularly hostile to Linux with the versions before and after being more cooperative.

You've found the core tweak though and I think this is actually the only thing that is technically **absolutely** required to just get the installers to work at all on these things.

> 
# we're using intel graphics; disable discrete gpu
  echo "	outb 0x728 1" | sed "s/^/$submenu_indentation/"
  echo "	outb 0x710 2" | sed "s/^/$submenu_indentation/"
  echo "	outb 0x740 2" | sed "s/^/$submenu_indentation/"
  echo "	outb 0x750 0" | sed "s/^/$submenu_indentation/"


You also have an i915 parameter > GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=3". I believe that these things, especially the outb commands, are the essential core hacks needed to boot the 8,2 MBPs in graphical mode to do the install. You also mentioned installing gfxCardStatus and turning off the discrete GPU in OSX. I never did those things. The Macbook does run hot but it always did. Maybe I'll revisit that since it might save battery life and extend component life to have it run cooler. The only thing I actually needed to get the Mint 18 installer to work though was to have this entry in grub.cfg.

> 
menuentry "Start Linux Mint 18 Cinnamon 64-bit" {
        set gfxpayload=keep
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        outb 0x750 0 
        linux   /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper 
iso-scan/filename=${iso_path} quiet splash i915.lvds_channel_mode=2 i915.modeset
=1 i915.lvds_use_ssc=0 --
        initrd  /casper/initrd.lz
}


I suspect that these two things, the i915 params and the outb commands, are the only things really needed to get the GUI installer working for just about any version of Linux. Actually I'm not even sure about the i915 stuff since you and I have different ones and to be honest I'm not exactly sure what each does. I'm planning to do a bit more research and provide a detailed HOWTO on my blog once I find out more about the i915 stuff. It seems like the outb commands (which turn off the discrete card) might in fact be the only thing truly needed.

I would like to add more crucial thing. When I first tried the outb tweak I almost gave up. It didn't seem to work at first in fact. I had entered the stuff above all as part of the "linux" line and thought they were kernel parameters. On a lark I tried the commands exactly as I have it now with the outbs each on a separate line. I now understand that grub is actually a little language of its own and these are all different commands. So you need to have the outb commands happen before the "linux" command.

---

