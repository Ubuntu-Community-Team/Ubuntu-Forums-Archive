---
title: "Apple Mac Mini LAMP Boot issue"
date: 2020-03-18
forum: Apple Hardware Users
---

### Post by kokoroexchange on 2020-03-18
Hello,

I'm returning here to the forums after a LONG time away. I have a question about an Ubuntu LAMP (14.04) that used to work flawlessly but now will not boot. Short story: I have two Mac Minis both running Ubuntu 14.04 LAMP servers. I was away for a year on sabbatical and shut them both down, boxed them and stored them. Several months after returning from sabbatical, I got them out, plugged them in and turned them on. One of the started up with no issues. The other, however, initially booted part way and then stuck at an Apple USB driver...appeared to be a keyboard. I tried several times, booted into the recovery tool, tried various safe modes but each time the boot stops at a USB driver. I burned a live CD of 14.04 and can start from it but when running the fix defective disc tool I get a blank screen. If I run the fix defective system (wording is probably off) it starts to boot but then stops at an Apple IR driver.

If possible, I would like to save the contents of the web server directory. The rest is not important...although ideally I'd like to get it up and running again.

Just curious if, given the information I've provided here, there are any ideas about what could be causing the problem.

Thanks in advance for any help that can be provided.

Jason

---

### Post by SeijiSensei on 2020-03-18
14.04 is getting a bit long in the tooth.  Maybe you should try installing 18.04 which may play better with your hardware.

---

### Post by kokoroexchange on 2020-03-18
SeijiSensei,

Yes, actually it was my plan to update and upgrade but as I cannot even boot, I'm stuck. Is is possible to install 18.04 without overwriting content on my current system? I would need to install from a CD as the drive is not bootable so I'm wondering if a new install is 'aware' of previous content or if it simply writes to the drive oblivious to what is already there? I'm suspecting the later is the case but would be very happy to be wrong. ;-)

Jason

P.S. I should have included the fact that my Mac Mini is an OLD one. One of the first Intel chipped Mac Mini's. ;-)

---

### Post by gsahli on 2020-03-19
Your old mini has a CD/DVD drive, right? Burn a CD/DVD (on another machine) with a newer version linux, start up from that, and plug in a USB stick and copy files/folders to it.

---

### Post by kokoroexchange on 2020-03-19
gsahli,

I see...so I just need to find a live CD iso that I can boot from. Good idea...I'll see if I can find a bootable CD image that can be used for this purpose. If you, or anyone, is aware of such a CD image that will work for an old Intel mac and can point me in the right direction I would be most appreciative.

Jason

---

### Post by kokoroexchange on 2020-03-20
Adding a quick note here...for some reason I cannot get any iso discs to be recognized by my system outside of 10.04.6...I have no idea why. All other discs get spit out of the drive...

From the 14.04 disc I run "fix a broken system" and the process sticks every time at:

[3.554679] usb 5-2: Product: IR Receiver
[3.555368] usb 5-2: Manufacturer: Apple Computer, Inc.

Like I mentioned initially, this system was functioning without issue in early 2018 but then was shut off for about two years (a bit longer than I originally posted). It was disconnected from power and stored in a cool/dry location. I understand that anything is possible but...the fact that it sticks at the same place every time makes me think there is a consistent issue that I am missing...

The live CD boot idea sounded great but....only if I can find an iso that will actually boot. :-(

Any advice will, of course, be much appreciated. 

Jason

---

### Post by SeijiSensei on 2020-03-20
Use the working system to create a bootable USB stick: [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu).  There's also a tutorial about using Windows for that purpose: [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows).

I'd go with 18.04 or 20.04 which will be released in just a few weeks.

[http://cdimage.ubuntu.com/releases/18.04.4/release/](http://cdimage.ubuntu.com/releases/18.04.4/release/)

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by kokoroexchange on 2020-03-20
SeijiSensei,

Thanks but I am working with a command line only LAMP...so I'm guessing the process for creating a bootable USB stick is going to be quite different than the one outlined in the link you provided. Also, to restate my issue, I am working with an old Mac Mini 2007. I don't think standard images will boot onto my machine...it uses the old 32 bit EFI firmware...but...I do have GRUB installed so...hmm. I've already toasted several DVDs but I have more to work with...guess I need to keep experimenting.

---

### Post by kokoroexchange on 2020-03-21
SeijiSensei, all,

I finally managed to revitalize my system. Somehow I managed to get the "Repair a damaged system" option to run from the 14.04 LAMP disc that would actually boot on the computer. It ran through a basic setup and then gave me an option to attempt to boot the system. I had to restart once as GRUB seemed confused with the CD still in the bay but after ejecting the CD and rebooting, everything worked.

The kicker is that I think possibly the root of all of the problems was how I had USB devices plugged into the computer. I have two Mac Minis running Ubuntu 14.04 and they are connected to a monitor via an old KVN switch. It seems the USB cables from the switch have to be plugged into exactly the same port they were in the past and the keyboard must be plugged into the switch, not the computer....? Or, maybe because the "repair" program from the CD remapped my keyboard...?

I'm not sure because both of those changes (KVM switch connections and keyboard mapping) were done prior to getting everything to work...so I'm not sure which was the fix....and have no interest in going back and trying replicate the issue. :-)

At any rate, thanks to everyone who provided suggestions. They were much appreciated.

Regards

Jason

---

