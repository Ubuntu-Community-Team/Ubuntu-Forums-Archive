---
title: "Feisty install problems"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Carlton1 on 2007-03-14
Can anyone help?  I have tried to have a look at Feisty from a CD, and the following error comes up;

/bin/sh: Can't access tty; job control turned off (initramfs)

Can anyone point me in the right direction?

Many thanks,

Carlton.

---

### Post by igknighted on 2007-03-14
> **Carlton1 said:**
> Can anyone help?  I have tried to have a look at Feisty from a CD, and the following error comes up;

/bin/sh: Can't access tty; job control turned off (initramfs)

Can anyone point me in the right direction?

Many thanks,

Carlton.

Can you give more details?  When do you get this error message, are you using the live CD?  Are you booting the disk on your physical box or in a virtual machine?

---

### Post by Carlton1 on 2007-03-14
I am booting from a live cd.

I restart the computer, and the initial screen comes up.  I choose the option Start or install Ubuntu.

It says 'Loading Ubuntu Kernel, and then I get another screen, with the status bar going back and fore.  It is at this stage everything stops and I get the following message;

udevd-event(2078): run_program:'/sbin/modprobe'
Abnormal Exit

Busybox v1.1.3 (Debian 1:1.1.3-3Ubuntu) Built in shell (Ash)

Enter Help for a list of built in commands.
/bin/sh: Can't access tty; job control turned off (initramfs)

Hope you can help!

Thanks,

Carlton

---

### Post by igknighted on 2007-03-14
Sounds like a bad burn.  Did you check the disk integrity when you get to the menu where you select "install or boot Ubuntu"?  Also, did you check the MD5 sum of the ISO when you downloaded it?

---

### Post by Damo1976 on 2007-03-14
Hi,
I have loaded feisty from the exe file, and got exactly the same problem.

For info - I have a Fujitsu Seimens laptop, 2ghz core duo, 2 x 100GB drives, 256MB graphics, - so a new laptop that should run fine.

Help please.

---

### Post by Carlton1 on 2007-03-14
I just tried to check the integrity by selecting that opiton, and the same error message came up.

Would you suggest re-downloading the file?

Thanks for your help.

---

### Post by hyper_ch on 2007-03-14
I still have no clue what that .exe is for burning... I just download the ISOs and burn them (on windows with Nero) on linux with k3b...
I advice to burn them as slow as possible :) sometimes ISOs get bad when burned at full speed (well, that's what I've read in here... can't confirm it myself)

---

### Post by Kobalt on 2007-03-14
I always advise to burn ISOs at 4x speed max and always check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29"). 
Did you guys try checking the md5sum ?

---

### Post by dptxp on 2007-03-14
It is clearly written in Ubuntu site that to burn properly use Infra Recorder, it is a free download.
Use 'burn image'. Infra Recorder changes the burning speed dynamically and automatically, so you burn your iso fast and right.
So download Infra Recorder and burn (iso :-))

---

### Post by Carlton1 on 2007-03-14
I have tried re burning the image, with the same result.  Also, I have used Md5sum, but can't find a hash number for Feisty.  Can anyone suggest where to find one?

I'll get there in the end!

Thanks,

Carlton

---

### Post by Belyel on 2007-03-14
I had this problem a lot on my machine due to a bad image.  I'm not sure where you can find the Feisty hashes, but since Feisty is still alpha software, I'd suggest you try using edgy (6.10).  You can get the isos everywhere and the hashes will be provided at the host sites.  Check the image before you burn it. Then burn it slow.  Then check the disk before trying to install using the tool on the disk.  By doing this, you have a much higher chance of success.

---

### Post by old_geekster on 2007-03-15
I used GnoneBaker to burn Feisty CD: go to Tools/Burn CD Image (ISO is shown on the CD image to the right).  You can select the speed that you want to use.  I chose 8X, which as I said, worked great.

The kicker, however, is that there was a bug, so I could run the LiveCD, but could not install it.

---

### Post by lamalex on 2007-03-15
[http://cdimage.ubuntu.com/releases/feisty/](http://cdimage.ubuntu.com/releases/feisty/)

select your herd and scroll all the way down.

---

