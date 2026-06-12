---
title: "Mac terminal freezes when I try this command"
date: 2015-08-02
forum: Apple Hardware Users
---

### Post by Hugo_Kapteijn on 2015-08-02
[FONT=arial]the command is this: [/FONT]sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m. it is part of the process of making a bootable usb on mac. When i type it in, The terminal still accepts commands, but doesn't fullfill them and doesn't respond to the command that I just entered. I replaced all of the placeholders with the correct info, such as the location of the .i[FONT=trebuchet ms]c[/FONT]mg and the name of the usb. Terminal only responds when i remove the usb again, and after this, my mac won't recognise the usb format, which leads to me having to erase it again. Here is the log: [FONT=courier new]Hugos-MacBook-Pro:~ Hugo$ diskutil umountDisk /dev/disk2[/FONT][FONT=courier new]Unmount of all volumes on disk2 was successful[/FONT]
[FONT=courier new][/FONT][FONT=courier new]Hugos-MacBook-Pro:~ Hugo$ sudo dd if=/Users/Hugo/Desktop/ubuntu.img  of=/dev/rdisk2 bs=1m[/FONT]
[FONT=courier new][/FONT][FONT=courier new]Password:[/FONT] It freezes like that after I enter my password. After I remove the usb drive, This shows up: [FONT=courier new]dd: /dev/rdisk2: Device not configured[/FONT]
[FONT=courier new][/FONT][FONT=courier new]436+0 records in[/FONT]
[FONT=courier new][/FONT][FONT=courier new]435+0 records out[/FONT]
[FONT=courier new][/FONT][FONT=courier new]456130560 bytes transferred in 90.667149 secs (5030825 bytes/sec)[/FONT]
[FONT=courier new][/FONT][FONT=courier new]Hugos-MacBook-Pro:~ Hugo$ [FONT=trebuchet ms]It then displays the following error after I try to plug in the usb drive again:[/FONT][/FONT][ATTACH=CONFIG]263583[/ATTACH]

---

### Post by mystics on 2015-08-02
It takes a while for dd to copy the file over the USB. The .img file is  large. Think about what happens if you try to copy a large file over  to a USB. It isn't instantaneous, and dd isn't going to behave any  differently. Just be patient.

As for the error message, this also  is very standard on Mac. OS X doesn't recognize the file format and is  wanting to erase and re-partition the disk so that it can recognize it  and do something with it. However, the drive, if dd was successful, will  be able to be bootable, but you don't boot from inside OS X.

Unfortunately, since it looks  like you pulled out the drive in the middle of copying the file over,  your USB drive won't work to boot Linux, as not all the files were  copied over. When the error comes up, if you click "Initialize..." then  it should open up Mac's disk utility. From there, you can select the  drive, erase it, and set it to MS-DOS (FAT) format. You'll also need to set up the partition scheme to one partition with Master Boot Record  (MBR). Once that's done, go back through the process to set up the USB  drive to be bootable. Just be sure to be patient and wait for dd to  finish.

Once done, you'll get the same error message again. Again, don't worry. This is normal. Just eject and remove the disk, turn off the computer, re-insert the disk, turn the computer on, and once you hear it turn on hold down the Alt/Option until you're given a choice to boot into Mac, Mac Recovery, or the USB. Just select the USB drive and you should be good to go.

---

### Post by Hugo_Kapteijn on 2015-08-03
Thanks! I'm now running ubuntu and ready to go!

---

