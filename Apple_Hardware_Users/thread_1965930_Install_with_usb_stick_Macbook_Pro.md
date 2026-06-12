---
title: "Install with usb stick Macbook Pro"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by hackarre on 2012-04-26
I've just downloaded ubuntu 12.04 and wanted to make a fresh install on my macbook pro, I followed the instructions given here [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) and when the operations are completed I get this result:

The disk you inserted was not readable by this computer

Obviously, when I restart the pc, it cannot find any bootable device.

Note I've tried using Lion OSX

Thank you very much for your help!

---

### Post by otoris on 2012-04-30
I have this issue too and would like to know how to remedy this. (Running OS X 10.7.3 Lion on MacBook Pro Mid 2010)

---

### Post by falconbeak on 2012-04-30
upvote:I have the same problem. I have a macbook pro version 5,4. Already dual-booting Lion and Windows 7, and there is a empty fat32partition waiting for Ubuntu. Using refit. Followed the instructions from ubuntu.com to set up a bootable usb from inside os x, but something went awry, because can't boot from the usb, it automatically boots into windows, and lion can't read the usb now. It asks to initialize or eject it. Unfortunately, the dvd drive is broken. Next, I will wipe the usb and use some grub2-efi manipulations with the precise image on the usb to see if that will help.

---

### Post by otoris on 2012-05-01
This guy -> [http://askubuntu.com/questions/125503/install-through-usb-stick-macbook-pro](http://askubuntu.com/questions/125503/install-through-usb-stick-macbook-pro) apparently got his to work, but when I tried to replicate his success I ended up with the exact same issues I'm having now.

---

### Post by subehsharma on 2012-05-01
I have been there where you're right now and spent many sleepless nights trying to work it out. FInally i was able to do it by following this link. 

[http://www.b3ns.com/threads/ubuntu-11-04-11-10-macbook-pro-2011-unable-to-find-a-medium-containing-a-live-file-system.29/](http://www.b3ns.com/threads/ubuntu-11-04-11-10-macbook-pro-2011-unable-to-find-a-medium-containing-a-live-file-system.29/)

The trick is that unlike installation in a windows machine, in mac you'd need Ubuntu on USB stick as well on a CD. So, you'l boot into cd and from there all the files will automatically be taken from your USB.

---

### Post by falconbeak on 2012-05-02
Solved! You don't need a cd as well, as long as you set the usb up the right way, to boot via efi. On your partition, you need an efi directory. Nested inside, have a boot directory. Inside there, have a .efi configuration file and your iso. In fact, there exists a graphical program written in java that will do everything for you. Go here for more info:
[http://penguintosh.com/]("http://penguintosh.com/")
If you are triple booting with lion like me, then you just need to fix your hybrid mbr with gpt fdisk, and you are all set! I am typing this from ubuntu :) And thank you google and Henry Mound.

---

### Post by m3topaz on 2012-05-04
I've got a mid-2010 Macbook Pro 6,2 and I've had some 'fun' trying this stuff. Firstly, the machine was a little non-standard as the DVD had been swapped for an SSD and running Lion from it. I started with rEFIt 0.14, but install attempts via USB (*.img) or external bootable CD didn't work. I'd usually get the installer menu, which consistently failed - but doubling up drives definitely wasn't a fix. The Macbook consistently deluded me into thinking there was something happening - there wasn't.

What I then did was format the HDD (320G : 280GB FAT, 40GB OSX), then install rEFIt again in the new 40GB partition, then revert the machine to single HDD and internal DVD.

I then got the original recovery disk, and installed Snow Leopard onto the 40GB partition - maybe not vital, but I wanted the thing to boot into *something*... Then installed rEFIt again on this partition (to be sure, I'm SO untrusting of these machines!) and ran rEFIt from boot to sync the partition tables. Having made sure the machine worked, I re-started it into rEFIt with bootable Ubuntu 12.04 CD (note that the bootable USB didn't work). I ran the installer for Ubuntu - first "Try Ubuntu", then install - and it fell at the last hurdle, which was the grub install piece (I guess you have no 'Advanced' in the 12.04 installer. Or I was too lazy to look for it...!).

With Ubuntu running from the CD still, and in "Try Ubuntu" mode, I then grabbed a terminal and forcibly installed grub to the partition (NOT the MBR. I assume that the installer defaults to try to put grub on MBR - that isn't going to happen in Macland). It doesn't like this installation of grub to the partition at all, and I had to

  #grub-install --force /dev/sda3

It seemed to do its thing, although this bit is pretty clear that it's not the 'done thing' :-)

I rebooted, via rEFIt. The Penguin was present in the right place - but the machine booted to grub command line.

Three sequential commands from this grub prompt let me boot Ubuntu:
  set root=(hd0,3)
  linux /vmlinuz root=/dev/sda3 ro
  initrd /initrd.img
[Note these are *very* specific to my Macbook and how I set it up!]

On reboot into rEFIt, the Penguin this time lets me start Ubuntu, via the usual boot screen, which sees the Mac stuff too. So I then ran #grub-update, which was seemingly OK. Now Ubuntu is also updated and runs very well.

I also put the Lion SSD back in, and rEFIt sees that. So I can triple boot Ubuntu/Lion/Snow Leopard. (The SSD is too flaky to be reliable though, for reasons that can wait until another day. Not that I care as I prefer Ubuntu).

The cynic in me thinks two things:
1) You need an internal CD/DVD drive to be successful. External via USB didn't work, nor did boot from USB using an *.img.
2) I think there's something in Lion that messes up attempts to install Ubuntu. I tried - not thoroughly, mind - an old 2006 Macbook which runs Lion and it stopped me at every hurdle. For this newer Macbook, it was only when Snow Leopard installed that I had any success.

[The usual disclaimers about doing anything resulting from this post apply - I'm only saying what I did. Proceed at your personal peril!]

---

