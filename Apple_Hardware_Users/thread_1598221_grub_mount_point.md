---
title: "grub mount point ??"
date: 2010-10-16
forum: Apple Hardware Users
---

### Post by andreacfm on 2010-10-16
I am trying to install 10.10 on my book pro 6.2 with refit.
I made my partition deleted and click on install . The issue is that when I arrive to choose the partition where I want to install the 10.10 installer is not anymore like this : [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) and I am not sure what to do.
I select the 100 gb free space and create a new ext 4 partition ?? What do I have to set as mount point ? Where do I say I want to install on /dev/sda3 as I did with previous ubuntu installers ??

Any suggestion is appreciated.

Thanks

Andrea

---

### Post by pc_michael on 2010-10-16
Hi Andrea,

I ran into a similarly confusing problem when I initially installed on my Macbook Pro a few releases ago.  What I did to solve it was manually partition my drive before running the installer.  Here's what I did:

[LIST=1]
[*]Boot into the LiveCD
[*]Open GParted (System > Administration > GParted)
[*]In the free space, create three partions:
[LIST=1][*]First, an NTFS partition around 100MB.  This will be mounted as /boot (where grub in installed)
[*]An EXT4 partition for as large as you like.  This will be your main system, mounted as /
[*]A Linux Swap partition twice the size as your RAM.[/LIST]
[*]Commit the changes in GParted
[*]Run the installer, and choose whatever mode will let you specify which partitions to use
[*]Mark each partition as noted above (NTFS gets /boot, EXT4 gets /, Swap gets Linux Swap)
[*]Install
[/LIST]

Again this was an earlier release so things may have changed, but that's the gist of it.  Let me know if you have any questions, and if anyone else would like to add to this, please do!

**Edit**: Attached screenshot of my partitions.  Ignore the unallocated space. ;)  /dev/sda2 is Mac OS X, /dev/sda3 is /boot, /sda4 is Ubuntu, /dev/sda5 is my swap, which is much smaller than it should be, but with 4GB of RAM, I don't have the space for eight gigs of swap.

---

