---
title: "Unable to boot from Ubuntu Server CD"
date: 2007-06-12
forum: Apple PPC Users
---

### Post by aek82 on 2007-06-12
A friend gave me an old Mac G4 with a PPC Processor to use as a server at home. So I tried to load Ubuntu Server 7.04 Fiesty for PowerPC onto it. After browsing the forums, I ran into plenty of posts that detail similar problems I have run into tonight, however, none of the solutions have helped.

This is what I try to do:

1. Burn install CD using .ISO image with Nero in Windows.
2. Turn on the Mac.
3. After booting into the login screen, I open the CD-ROM drive and place the install CD.
4. Select Reboot and hold down the [Alt] or Option key
5. I am then greeted with a gray screen with 4 buttons:

[LIST]
[*]HD disk with an X - I assume to boot into Mac OS X
[*]A CD with a Penguin - This is the Linux install CD
[*]An arrow pointing right - I assume this is the OK button
[*]Reboot Arrow - I think this reboots.
[/LIST]

6. After clicking on the CD button and pressing the Arrow pointing right, the screen turns blank for a second and then the same screen is shown a few seconds later, except in 8-bit color. 

I've looked through the forums and suspected that I have a badly burned CD, but after logging into OS X and browsing through the files of the CD, I do not think this is the case. I even tried re burning the image on my laptop using Ubuntu's CD writer, but I get the same end result. 

I've also tried booting from the 'Open Firmware' console.

I attempted this by:

1. Rebooting and then holding down the keys {Command} - {Option} - {O} - {F}
2. Then typing 'boot cd:,\\:tbxi'
3. I am then given the error message: 'Can't open cd:,\\:tbxi' 

I've also tried holding down the 'c' key at boot, but the login screen just appears. 

Any help is appreciated. Thanks.

---

### Post by pxwpxw on 2007-06-12
> **aek82 said:**
> A friend gave me an old Mac G4 with a PPC Processor 
I've also tried booting from the 'Open Firmware' console.

I attempted this by:

1. Rebooting and then holding down the keys {Command} - {Option} - {O} - {F}
2. Then typing 'boot cd:,\\:tbxi'
3. I am then given the error message: 'Can't open cd:,\\:tbxi' 

I've also tried holding down the 'c' key at boot, but the login screen just appears. 

Any help is appreciated. Thanks.

boot cd:,\\:tbxi should work (just checked here on ibookg4)
also 
```

0> dir cd:,\
0> dir cd:,\\

```
should show files on the cd, but will probably give the same error.

Sounds like the cd drive or the disk  may be bad, have you checked booting from  a macos disk and looked at the ubuntu install cd from macos or otherwise proved it is ok? (check downloaded iso md5 sum ).

Must be something working or you would not get the penguin icon.

---

