---
title: "rEFIt boot menu does not appear - ubuntu boots automatically; boot menu weirdness"
date: 2015-03-30
forum: Apple Hardware Users
---

### Post by Nina_Milliken on 2015-03-30
A week ago I successfully installed Ubuntu (ver. 14.04) on my Macbook alongside OSX.  I used rEFIt as my boot chooser and when I turned on the computer it would prompt me with two primary options: [FONT=courier new]Boot OSX from disc[/FONT] (default) or [FONT=courier new]Boot Linux from disc[/FONT].  I had five partitions: the rEFIt partition, the OSX partition, a Recovery partition, a Linux Swap partition, and the Linux partition.

Yesterday, I decided to re-install OSX on my Mac partition because it was so inundated with junk.  I booted into OSX and disabled rEFIt so that it would automatically boot OSX and I could restore it as per the instructions here: [https://support.apple.com/kb/PH18869?locale=en_US](https://support.apple.com/kb/PH18869?locale=en_US).  This was successful in restoring OSX to its factory settings.  I reactivated rEFIt and restarted.  When I tried to boot back into Ubuntu, it got hung up on the Tux logo and it kept doing this after multiple restarts.

Since I hadn't done too much in Linux I just decided to re-install Linux using the process I used before: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation).

I deleted the Linux partition but was unable to delete the Linux swap partition in OSX Disk Utility.  I successfully re-installed Unbuntu, but here is the problem.  When I turn on the computer, it does not bring up the rEFIt boot menu, it boots automatically into Ubuntu.  I know that the rEFIt partition exists as it appears in gParted and it is flagged as the boot partition.  I still have five partitions, but there is also 1GB of "unallocated" space which was, perhaps, the Linux Swap partition I could not erase.  

When I turn on the computer and hold [FONT=courier new]option[/FONT], I am given three choices: rEFIt, Windows (I don't know where this came from), and Recovery.  When I choose rEFIt, I am given FIVE options: [FONT=courier new]Boot EFI\ubuntu\shim64.efi[/FONT] (default),[FONT=courier new] Boot EFI\ubuntu\grub2.efi[/FONT], an EFI non-boot option, [FONT=courier new]Boot OSX from disc[/FONT], and [FONT=courier new]Boot Linux from disc[/FONT] (Tux icon).  I can then boot to OSX by choosing the OSX option but I can only boot to Ubuntu through the two Boot EFI options, not the Tux option - it just gets hung up on the Tux logo.  I have gone into OSX and reactivated rEFIt, ensured that the rEFItBlesser was present but this has not worked and apparently rEFIt only works from the OSX side.

This is what I want to accomplish: When I turn on the computer, the rEFIt boot menu appears and gives me two choices: OSX or Linux, as it was before.  Is this going to be possible?  Sorry for such a long post!  Any help is greatly appreciated :)

---

### Post by bardo2 on 2015-03-31
i am sorry: neither do i use OSX nor EFI-Boot - nor refind - for that matter. It's been a year since i looked into it. But you might find this documentation (and linked pages) useful:
[http://www.rodsbooks.com/refind/]("http://www.rodsbooks.com/refind/")

one thing though: from your post, you seem to be hasty at taking action without being aware of all the consequences. Slow down and investigate! To mess with the boot procedure usually tends to render (one or more) OS'es unuseable. And hasty actions tend to mess it up even further.

UEFI boot involves quite a number of parts and above links are doing a good job at explaining some of those. IMO

---

### Post by este.el.paz on 2015-03-31
Right, slow down, there are some details that you aren't mentioning, like, which version of OSX are you running?  Because, rEFIt doesn't support OSX after 10.7??? so as Bardo mentions if you are in something later than that you will need--rEFInd.  

And, which MacBook?  might make a difference as well.  In terms of my experience with a '10 MBPro, each time OSX is upgraded or even security update is added, rEFInd is "unblessed" . . . so it has to be "blessed" again via the rodbooks link.  So that is something to try.  But, in terms of doing your re-install of linux, if you choose "manual" then when the GParted window opens you can either delete the / partition and then re-label it, but really no reason to try to delete swap--if you aren't re-sizing it--it's I believe, just formatted "space" . . . .

But, what you aren't mentioning is "GRUB" . . . in my case if I don't format a 10MB partition in front of the "/" folder, labeled as "bios_grub" then even if rEFInd shows the system, it won't boot linux.  The install might even say "GRUB installed successfully" but . . . no boot.

And, just for your info, rEFIt or whatever, or the OSX boot selector will show linux as "windows" . . . .

e....

---

### Post by Nina_Milliken on 2015-04-01
Thanks very much for the documentation!  You're right, I am being a bit hasty...since my configuration is currently functional (and I definitely don't want to break it!) I'll comb through some more forums and resources before I try anything further.  Thanks for the help!

---

### Post by Nina_Milliken on 2015-04-01
Thanks for the information, like you and bardo2 said, I'm definitely being a little hasty.  I'll pump the breaks a little and do some more research before I jump into trying to straighten this partition/boot business out.  Thanks!

---

