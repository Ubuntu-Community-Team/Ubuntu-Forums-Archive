---
title: "install Ubuntu on old Intel Mac"
date: 2014-07-22
forum: Apple Hardware Users
---

### Post by scrufulufugu517 on 2014-07-22
I have a old intel mac that I want to install ubuntu on. So I download the newest version of ubuntu and burn it to a disk using OS X built in Disk Utility but when I put the disk in to the computer it gives me this: [https://www.dropbox.com/s/39ti3awooegbfa5/ware.tiff](https://www.dropbox.com/s/39ti3awooegbfa5/ware.tiff) I tried it on my new mac and same thing. please help!!

Short Tech Specs:

OS X 10.6.8

iMac Early 2006

---

### Post by este.el.paz on 2014-07-22
> **scrufulufugu517 said:**
> I have a old intel mac that I want to install ubuntu on. So I download the newest version of ubuntu and mount it to a disk using OS X built in Disk Utility but when I put the disk in to the computer it gives me this: [https://www.dropbox.com/s/39ti3awooegbfa5/ware.tiff](https://www.dropbox.com/s/39ti3awooegbfa5/ware.tiff) I tried it on my new mac and same thing. please help!!

@scruful, etc:

When you say "mount it" . . . do you mean you "burned it to a DVD"???  And, if you ***burned it*** did you check the md5sum number of the .iso?  Or any of the other checksum numbers to make sure the file was not corrupted?  Seems like that is more important these days . . . .

And, let's say you burned the "live" version to a DVD, did you ***reboot*** the computer and then hold down the "C" key??  Because, indeed if you just put the linux/ubuntu disk into the drive booted in OSX . . . OSX does not "recognize" the existence of linux . . . ever . . . .  You have to boot the DVD with the iso **live dvd*** and let the DVD run the computer . . . .

e.e.p.

---

### Post by scrufulufugu517 on 2014-07-23
Yes I meant burn, I did check the MD5, and the C key doesn't do anything when rebooting OS X. 
P.S. I burned a second DVD to double check.

---

### Post by este.el.paz on 2014-07-23
> **scrufulufugu517 said:**
> Yes I meant burn, I did check the MD5, and the C key doesn't do anything when rebooting OS X. 
P.S. I burned a second DVD to double check.

@scruful:

OK, . . . good that you checked the md5 . . . but, "c key doesn't do anything"??  Hopefully my putting "C" didn't throw you off, it's "c" . . . I put the capital for visual clarity.  So, the new DVD is in the optical drive, spinning OK, reboot the computer and when screen goes black you hold the "c" key down?   And, if the md5 number checks out there is no point to reburn a second DVD until you figure out why the first one isn't booting . . . OSX does an integrity check on what it burns, if it says it has "completed the task" . . . it has . . . .

Even if you just have an installer version the c key should boot you into the installer screen . . . or, the other day messing with a YDL disk it took a loooooonnnngggg time before it booted into the installer . . . .  If you hear sounds of the drive,then you should be patient until the machine figures out what to do under the command of the disk.  Or if you see the black screen with the flashing boot prompt in the upper left corner you can let off the c key . . . I don't think it's just a matter of simply touching the c key while the machine reboots . . . if that is what is happening . . . it has to be held down in a manly or, uh womanly fashion . . . with the disk in the computer and of course the drive should be spinning it up . . . before rebooting, etc.

Otherwise, if holding the c key "does nothing" . . . possibly a keyboard problem??  Can you type the letter "c"?

e.e.p.

---

### Post by scrufulufugu517 on 2014-07-24
> **este.el.paz said:**
> @scruful:

OK, . . . good that you checked the md5 . . . but, "c key doesn't do anything"??  Hopefully my putting "C" didn't throw you off, it's "c" . . . I put the capital for visual clarity.  So, the new DVD is in the optical drive, spinning OK, reboot the computer and when screen goes black you hold the "c" key down?   And, if the md5 number checks out there is no point to reburn a second DVD until you figure out why the first one isn't booting . . . OSX does an integrity check on what it burns, if it says it has "completed the task" . . . it has . . . .

Even if you just have an installer version the c key should boot you into the installer screen . . . or, the other day messing with a YDL disk it took a loooooonnnngggg time before it booted into the installer . . . .  If you hear sounds of the drive,then you should be patient until the machine figures out what to do under the command of the disk.  Or if you see the black screen with the flashing boot prompt in the upper left corner you can let off the c key . . . I don't think it's just a matter of simply touching the c key while the machine reboots . . . if that is what is happening . . . it has to be held down in a manly or, uh womanly fashion . . . with the disk in the computer and of course the drive should be spinning it up . . . before rebooting, etc.

Otherwise, if holding the c key "does nothing" . . . possibly a keyboard problem??  Can you type the letter "c"? 

The "C" didn't throw me off and the keyboard is fine. I'm gonna try to do the mac 32 bit setup, I found a guide at [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) I will try it as soon as I get my 32 bit DVD back from a friend.

---

### Post by este.el.paz on 2014-07-24
> **scrufulufugu517 said:**
> The "C" didn't throw me off and the keyboard is fine. I'm gonna try to do the mac 32 bit setup, I found a guide at [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) I will try it as soon as I get my 32 bit DVD back from a friend.

@scruful:

Great, yes, to boot or dual boot linux on a mac the rEFInd app is helpful . . . apparently not everyone uses it, perhaps the iso that says something about "mac" might not need it???  Don't know; but I have used both rEFIt and now rEFInd for my triple boot set up . . . '10 MBPro . . . use the "easy install on osx" . . . method that he shows how to do . . . .

e.e.p.

---

### Post by scrufulufugu517 on 2014-07-25
Good news! I got it to work
1. I found out my computer is 32 bit
2. Ubuntu has 14 32-bit has built in EFI support so I didn't have to go through all of [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) steps
3. For the newer Apple aluminum wired keyboards the keyboard drivers boot after the OS for some reason

Now my only problem is my built in WIFI card is not working and I don't want to buy anything if I can help it

---

### Post by este.el.paz on 2014-07-26
> **scrufulufugu517 said:**
> Good news! I got it to work
1. I found out my computer is 32 bit
2. Ubuntu has 14 32-bit has built in EFI support so I didn't have to go through all of [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) steps
3. For the newer Apple aluminum wired keyboards the keyboard drivers boot after the OS for some reason

Now my only problem is my built in WIFI card is not working and I don't want to buy anything if I can help it

Good job . . . interesting on the "EFI support" in 32 . . . I've got the 64 bit going . . . did the rEFInd . . . but I do XFCE/Xubun . . . possibly no option at the time??

Anyway, wifi is a "normal" issue . . . probably in the wiki or sticky at the top of Apple user . . . or, just use the "Additional Drivers" app . . . give it yr password . . . and let it run . . . in Mac it may show available video drivers for Nvidia (if you have that) . . . generally I pick "recommended" . . . and should be down at the bottom there will be a "Broadcom" option . . . for the wifi, select that.  Sometimes there is a "Unknown" driver . . . I don't know what that is for . . . it doesn't say, so sometimes I let it go . . . up to you . . . .  If it's through the app it's more or less "controlled" . . . .  After that you should be in "business" . . . enjoy.

e.e.p.

---

### Post by scrufulufugu517 on 2014-07-27
Here we go again.
 additional drivers says "no additional drivers available"

---

### Post by este.el.paz on 2014-07-28
> **scrufulufugu517 said:**
> Here we go again.
 additional drivers says "no additional drivers available"

Interesting . . . so does that mean that there are no "nvidia" drivers showing up in the list?  Only "no additional drivers"?  There has been a "bug" with network manager . . . I don't know the details of it, but there might be something in a wiki about it; in other words possibly the bug is not reading that there is a probably "Broadcom wifi card" . . . so it isn't showing up.  Or, it has already installed it, but, can't "see" it . . . .

There are lots of threads about getting wifi working, possibly you can find them or look for how to "manually" install the wifi driver . . . or using synaptic to search for wifi or "broadcom driver" and see what shows up . . . .  I have gone thru this a few times, but it's been awhile . . . might look thru the "Testers wanted for 12.04" thread for these details . . . .  It's a continuing issue . . . with wifi . . . .

e.e.p.

---

### Post by scrufulufugu517 on 2014-10-03
K new problem whenever I press a button that says reboot (installing software or just pressing the reboot button) ubuntu brings me to the boot screen and sits there in an endless loop of loading. Can anyone help.

---

### Post by este.el.paz on 2014-10-04
> **scrufulufugu517 said:**
> K new problem whenever I press a button that says reboot (installing software or just pressing the reboot button) ubuntu brings me to the boot screen and sits there in an endless loop of loading. Can anyone help.

@scruful:

"Endless loop of loading" . . . loading what?  I'm assuming that you have gotten passed your initial issues, and you've gotten ubuntu to boot many times . . . and now it isn't?  Did you ever get to rEFInd?  Or do you have GRUB installed?  On restart are you getting to either of those windows?  Have you done an OSX upgrade recently?  These type of questions . . . .

e.e.p.

---

### Post by scrufulufugu517 on 2014-10-07
When I push this
[IMG]https://dogsdogsalldogs.files.wordpress.com/2014/10/ubuntu013-04-turn-off-options.jpeg[/IMG]
This happens until I force quit it
[IMG]https://dogsdogsalldogs.files.wordpress.com/2014/10/ubuntu-bootscreen.png[/IMG]

---

### Post by scrufulufugu517 on 2014-10-07
It will shut down just fine and boot up just fine but when I push that button...

P.S. I am single booting (no OSX)

---

### Post by este.el.paz on 2014-10-07
> **scrufulufugu517 said:**
> K new problem whenever I press a button that says reboot (installing software or just pressing the reboot button) ubuntu brings me to the boot screen and sits there in an endless loop of loading. Can anyone help.


The window that has "Ubuntu" with the buttons under it that light up is the "Splash" screen . . . .  Hope that helps. : - ))

e.e.p.

PS: This one is beyond my pay grade; it's sort of like the various issues with failing to wake from suspend or failing to suspend . . . probably a bug . . . .

---

### Post by scrufulufugu517 on 2014-10-08
yea the computer won't suspend ether

---

### Post by scrufulufugu517 on 2015-02-05
Can anyone answer this I still can't reboot the computer or suspend it. rebooting gets stuck on the splash screen and suspending gives me a frozen cmd cursor.

---

