---
title: "bootloader problems after major upgrade"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by jbag on 2006-11-15
Hi Guys

I have just upgrade my motherboard & CPU. As usual with Windows it required me to do a repair so it would boot properly into XP. The problem now is that GRUB has disappeared from the screen & the machine boots directly into Windows.

Can I get GRUB back? If so, how?

If it weren't for my grandson needing Windows for school projects & my son needing it for his work, I would remove Windows altogether.

Thanks

jbag

---

### Post by indytim on 2006-11-15
jbag,

There are a number of ways you can recover your GRUB.  I recommend downloading and burning the iso to CD for SuperGrub [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
.  After you have done that, boot to the CD and walk through the dialog.  The end result will be a rebuild of your GRUB.  

btw- this is a nice "tool" to have in your recovery arsenal anyways.

Good Luck,

IndyTim

---

### Post by jbag on 2006-11-15
Thanks indytim

I will give that a shot.

Will let you know the outcome

Thanks a lot

jbag

---

### Post by jbag on 2006-11-16
Thanks for the tip indytim

I downloaded the Super Grub Disk as you suggested & that brought my GRUB menu back on line. Now however I can't get into Ubuntu. I keep getting an error 17 -- "Cannot mount selected partition".

I have gone through everything that I can find on this & how to correct it & have had no luck.

When I do: sudo fdisk -l I get:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 822520 bytes

 Device   Boot  Start    End     Blocks    ID      System
dev/hda1   *     1      18122  145564933+   7     HPFS/NTFS
dev/hda2        18123   18186     514080   82  Linux Swap/Solaris
dev/hda3        18187   19457   10209307+  83      Linux


If I am right in my assumption. This translates into

Windows XP   (hd0,0)
Linux Swap   (hd0,1)
Linux        (hd0,2)

My GRUB menu under Ubuntu, kernel 2.2.15-27-386 shows:

root (hd0,1)  
Kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
Initrd /boot/initrd.img-2.2.15-27-386
Save default
boot

On the 1st line it should read "root (hd0,3) I think
the 2nd line "..... root=dev/hda3 ....."

I have tried to edit these lines by selecting "e" in the menu, but, I can't seem to save the changes. Maybe I am doing something wrong, (quite possible). 

After even temporarily making the changes I get as far as:

Failed to start x server your graphical interface. It is likely
that it is not set up correctly. Would you like to view the x server output to diagnose the problem?

              <Yes>                  <No>

Selecting <yes> gets me:

X Window System version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, revision 0, Release 7.0
Build Operating System: Linux 2.2.15.7 i686
Current operating system: Linux jim-desktop 2.2.25-27-386 #1 PREEMPT
build date: 16 March 2006
  Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
  to make sure that you have the latest version
Modular loader present
Markers: (--)probed, (**)from config file, (==)default setting
         (++)from command line, (!!)notice, (II)informational,
         (ww)warning, (EE)error, (NI) not implemented,   
         (??)unknown
(==) Log file: "/ver/log/xorg.0.log", Time: Thur Nov 16 18:09:10
(==) Using config file: "etc/x11/xorg.conf"

                              <OK>

If I select <OK> it takes me to another screen:

Would you like to view the detailed x server output as well?

                  <YES>                 <NO>

Selecting yes takes me back to the previous screen
When I choose <OK> I get:

The x server is now disabled. Restart GDM when it is configured correctly. 

Selecting <OK> takes me back to the GRUB menu.

From here I can boot into Windows fine but not Ubuntu. I keep getting the error 17 message.

Should I maybe just delete Ubuntu & re-install or can I restore it?

Any ideas

jbag

---

### Post by jbag on 2006-11-17
Ok Guys

I got rid of the "error 17" in GRUB. 

I was able to go into the menu.lst & modify the settings involved.
Now I have to figure out how to get the xserver to run.

Thanks for your help

jbag

---

### Post by marx2k on 2006-11-17
try sudo "dpkg-reconfigure xserver-xorg"

and then try to start your x server again

If not, post what it says in /var/log/Xorg.0.log

---

### Post by marx2k on 2006-11-17
misplaced quotes...
Just type at a terminal: sudo dpkg-reconfigure xserver-xorg

---

### Post by bulldog on 2006-11-17
To get X running again try in your console```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` to reconfigure your hardware.

With some luck all will be fine if not,well a reinstall is done in about 30 minutes.........
You made some major changes to your hardware and it needs to be reconfigured just try or do a reinstall which will be much quicker than waiting for a reply.

---

