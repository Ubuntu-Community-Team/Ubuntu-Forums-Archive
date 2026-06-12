---
title: "Your Help needed URGENTLY!"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by dsi-guy on 2007-03-23
I am currently running Ubuntu on my Dell Laptop and love it.
It is now time to ditch Windows on the main machine and install it there.
I decided to run the 6.06 lts live cd to test the waters. It froze with a black screen showing only a non-blinking cursor in the top left.

I downloaded 6.10 and tested that under the live cd, that one was working well and got my hopes up, tan/gold ubuntu screen came up and the pointer will move around a bit then freeze.

So..I d/loaded the 6.06 64bit version.. (having a 64bit processor).. same thing. froze with the black screen.

My System...
AMD Athlon 64 1.8 ghz
1 gig ram
200 gig hd
Nvidia fx5200 128mb video
DVD rom
DVD R +/- writer
ProView 19" widescreen Monitor
usb Keyboard and mouse.

I would love any help you all can give. I am looking forward to dumping MS for good.

Thank you
Dsi-Guy

---

### Post by Bachstelze on 2007-03-23
Try installing from an Alternate CD.

---

### Post by jcs_double on 2007-03-23
ok, so this may be my first post but i have been using ubuntu for about 3 months now

anywayi encounterd a smiliar problem is i went back into my windows installation and did a quick check disk and a defrag and that fixed everything up

hope that helps

---

### Post by tcrroadie on 2007-03-23
I agree HymnToLife.  Download and try installing Ubuntu using the alternate install cd. 

I'm also curious to know if the live cd is loading the opensource nvidia driver "nv".  Maybe that is what is causing your display problems.  You can also try passing a boot option when using the live cd.

Try adding this boot option when booting the live cd. 

```
xdriver=vesa
```

Vesa is a universal video standard that all modern video cards need to meet.

---

### Post by dsi-guy on 2007-03-23
> **HymnToLife said:**
> Try installing from an Alternate CD.

Where can I get this cd?

Thanks for the quick replay!

---

### Post by dsi-guy on 2007-03-23
> **jcs_double said:**
> ok, so this may be my first post but i have been using ubuntu for about 3 months now

anywayi encounterd a smiliar problem is i went back into my windows installation and did a quick check disk and a defrag and that fixed everything up

hope that helps

Thanks! I will give it a try!

---

### Post by dsi-guy on 2007-03-23
> **tcrroadie said:**
> I agree HymnToLife.  Download and try installing Ubuntu using the alternate install cd. 

I'm also curious to know if the live cd is loading the opensource nvidia driver "nv".  Maybe that is what is causing your display problems.  You can also try passing a boot option when using the live cd.

Try adding this boot option when booting the live cd. 

```
xdriver=vesa
```

Vesa is a universal video standard that all modern video cards need to meet.

Will do so now!.. Let you know how it goes!

---

### Post by tcrroadie on 2007-03-23
> **dsi-guy said:**
> Where can I get this cd?

Thanks for the quick replay!

See this link.  Choose your download location, then select "Other Installation Options"
[URL="http://www.ubuntu.com/GetUbuntu/downloadmirrors"]
Ubuntu Downloads[/URL]

---

### Post by raja on 2007-03-23
> **dsi-guy said:**
> Where can I get this cd?

Thanks for the quick replay!

You can download the iso for the alternate cd from the same place where you downloaded the live cd. You should find it under 'other installation options'

---

### Post by dsi-guy on 2007-03-23
Thanks guys for the quick replys!

1st, did the defrag.. didnt help!
2nd, did the xdriver=vesa thing, that didnt work! :(
Got out my old monitor 19' compaq tube job from the closet and hooked that up.. still nothing.

Oh I forgot that my Motherboard is a Gigabyte K8NS Pro MB if that helps!!

Thanks!

Dsi-guy

---

### Post by tcrroadie on 2007-03-23
Lets make sure your burned cd is good. 

You will need your Ubuntu laptop for this.

Run this in a terminal to run a md5 check on the disk and compare it with the md5's listed below. 

On my box, my cdrom drive is hdc.  Yours may be different. 

```
md5sum /dev/hdc
```

Compare the resulting number with the md5sum for the disk you are using below.

```
283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso
```

---

### Post by dsi-guy on 2007-03-25
FOUND the problem..

Bad memory stick.

Thanks for the help!

Dsi!

---

