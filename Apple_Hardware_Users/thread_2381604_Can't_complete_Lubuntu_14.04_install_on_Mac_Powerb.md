---
title: "Can't complete Lubuntu 14.04 install on Mac Powerbook G4 12&quot; laptop, powers off"
date: 2018-01-02
forum: Apple Hardware Users
---

### Post by outs1der on 2018-01-02
Hi all,

I am trying to install Lubuntu Desktop 14.04 desktop on an old Mac Powerbook G4 12" laptop, but have gone as far as I (seemingly) can and now stumped.

Booting successfully from a USB drive (via Open Firmware), and managed to solve the graphics and wireless issues to display the desktop with correct colours and connect to the internet. Wheee!

Ran the installation procedure, choosing one of the default partition options (don't want to keep a Mac partition at this stage because I no longer have the install disks). Got to the point of "copying files" but when the progress bar hit the end the machine just powered off. This happened twice in a row.

Thought it might be the default partition scheme, so I tried to set up partitions as discussed in the FAQ at [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) but I can't seem to get the right combination to allow the installation to proceed. Don't really know enough about the file system architecture to make this work

Can't find any similar issues reported in the FAQ, Known Issues, forums, or elsewhere. Anyone else run into the same problem? Any tips or alternative approaches I might consider?

Thanks
Duncan

---

### Post by mörgæs on 2018-01-03
Hi, welcome to the fora.

Lubuntu 14.04 is out of support. I recommend that you begin with a fresh install of 16.04:
[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

---

### Post by outs1der on 2018-01-08
Hi mörgæs,

I didn't find a newer version of Lubuntu in my searches of the ubuntu webpages, so thanks for pointing me to the more recent version

However, I can't boot from this version, on either of the machines that I'm working with (both 12" powerbooks). After selecting the USB boot volume, I just get a blank screen with steady cursor in the top left corner. (Mac #1 recognizes the boot volume after pressing the TAB key on power on, but the other seems to have some issues identifying other boot volumes. I can get it to boot from the USB drive via Open Firmware. However then it displays the same screen).

I created the bootable USB using the command 

sudo dd if=lubuntu-16.04-desktop-powerpc.iso of=/dev/disk2 bs=32768 conv=notrunc,noerror,sync 

Mac #1 has 867 MHz G4 processor with 640 MB RAM. The specs for the other are probably similar (or worse)

Any other suggestions appreciated!
D.

---

### Post by outs1der on 2018-01-08
Disregard the earlier message, on the second try (Mac #1) I got to the yaboot screen. Now "loading kernel"...

stay tuned...

---

### Post by outs1der on 2018-01-08
As a followup, I couldn't get any further than the "loading kernel" message on any attempt. After repeated tries, I can get to the yaboot prompt about one time in three, but then the boot just hangs

I tried both "live" and "check" as boot options, neither worked.

Can anyone suggest a way forward?

Thanks

---

### Post by mörgæs on 2018-01-10
I can't, sorry.
Maybe there is an even lighter (but still supported) ISO than Lubuntu for PowerPC to try.

---

### Post by djchandler on 2018-01-10
Try a new install after a thorough cleaning of that old laptop. Use compressed air if possible. Try to avoid static discharges. Don't let a vacuum tool come into contact with the computer.

The problems you are having are PROBABLY the result of the installation not finishing POSSIBLY because the computer overheated before clearing conflicts, correcting all the errors being encountered. Also why the problem looks so freakish and unique when describing your issues. Problems like yours are caused by the randomness of the moment of shutdown due to heat. Fan control is not great in the installation program. Even though that bar is at the end, especially on an older PC, it will take a while to sort out all the necessary issues.

I have run into similar sets of errors before, particularly on old laptops. And this solution has worked before.

---

### Post by outs1der on 2018-01-16
Hi dj,

thanks for the advice, that's not something I would have thought of, but the computer is certainly getting quite hot during installation

this step is not something i can easily do right now but will give it a try presently

Cheers
D.

---

### Post by mörgæs on 2018-01-18
Nothing wrong with using a vacuum cleaner but do it gently. Best is to block the fan with a toothpick or piece of wire to prevent it from spinning too fast. 

Only vacuum in the reverse direction of the normal air flow.

---

### Post by ernsteiswuerfel on 2018-01-25
Last supported Ubuntu-PPC Version is 16.04.3: [http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04.3/release/](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04.3/release/)

---

