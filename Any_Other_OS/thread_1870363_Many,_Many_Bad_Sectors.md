---
title: "Many, Many Bad Sectors"
date: 2011-10-27
forum: Any Other OS
---

### Post by meatytaco on 2011-10-27
I'm running Linux Mint 11 on my Sony Vaio laptop.  I've noticed some occasional lag spikes/freezes while using my comp. (usually when opening up programs/games) I remembered after I first installed Mint that I checked a guide that explained how to get Mint to boot faster. One of the 'tweaks' was to stop Linux from checking the hard driver every time the laptop boots by editing the /etc/fstab file. Now, it's been a bit (maybe about a month,)after changing that back with no luck on the lag spikes/freexing I ran the SMART disk utility that checks my hard disk (sda1) and it is telling me I have almost 8 million bad sectors. O.O! I have a Gparted live USB that I used to bring up a terminal and run e2fsck as some people on the internet have suggested, but with no real luck. So my questions would be:

Is this an acceptable number? (If any more than zero is acceptable)

Would be disabling checking the hard drive on boot possibly cause this?

Is there any possible way to fix the bad sectors?

Also a screenshot of the SMART disk utility program showing the bad sectors.

---

### Post by Rubi1200 on 2011-10-27
I strongly advise you to stop what you are doing and backup all important data right now!!!

The chances are the drive is almost dead.

I also recommend that you go to the website of the disk manufacturer and download any disk health monitoring tool available to confirm the status.

If the figures are correct, it is almost certainly time to invest in a new hard-drive or contact the manufacturer if the disk is still within the warranty period.

---

### Post by meatytaco on 2011-10-27
Dang, I was afraid of that. Good news is, I don't have anything on here that is really important, bad news is, It's a laptop, and I have no experience working inside laptops. Desktops are easy lol. Anyone have any knowledge on how easy/difficult it is to change a laptop hard drive? I don't suspect it would be too hard, but I've been wrong many a time before. Also, I won't be too surprised if the hard drive does crap out on me soon, this laptop was actually bought by one of my friends around 5 or so years ago. Is there a chance that it will mess anything else up outside of the hard drive if it completely fails?

Edit: Almost forgot... Thank you for the quick reply :)

---

### Post by tartalo on 2011-10-27
> **meatytaco said:**
> how easy/difficult it is to change a laptop hard drive?

Usually easy, but it depends on the laptop. You better look for disassembling instructions for your model.

---

### Post by coffeecat on 2011-10-27
> **meatytaco said:**
>  Anyone have any knowledge on how easy/difficult it is to change a laptop hard drive?

It's a Vaio. Some are easy to change; others not. Have a look on the back and see if there is a removable access plate about laptop drive size. If there is, undo the screw(s), remove the plate and have a look. The Vaio I changed a drive in was a piece of cake. Four more screws and the hard drive caddy slid out, and another four screws and the drive was free of the caddy. Since it's about 5 years old, check whether the laptop takes a PATA/ide drive or SATA **before** you order the replacement! :wink:

By the way, I agree with Rub1200 that the drive almost certainly needs replacing, but there's something wacky about the Disk Utility data. It says, "Disk has a few bad sectors." Nearly 8 million - a few? :-k. That represents approx 4GB, or about 2.5% of the capacity of the drive. Strange.

---

### Post by meatytaco on 2011-10-27
Alrighty. That's definitely a good idea.

---

### Post by meatytaco on 2011-10-27
yeah 8 million seemed like a big number to me, but i wasn't sure how much of the hard drive that actually accounted for.

---

### Post by Rubi1200 on 2011-10-27
> but there's something wacky about the Disk Utility data. It says, "Disk has a few bad sectors." Nearly 8 million - a few? . That represents approx 4GB, or about 2.5% of the capacity of the drive. Strange.
which is why I also suggested downloading the relevant tool from the manufacturer to see if there is a discrepancy in the results.

---

### Post by Perfect Storm on 2011-10-27
Moved to Other OS/Distro Talk.

---

### Post by meatytaco on 2011-10-27
I feel this really didn't need to be moved considering the issue is with my hardware on my laptop...

---

### Post by meatytaco on 2011-10-27
I can't seem to find any tools from Sony for this, which makes sense to me cause it came with Vista. If all else fails, I'll run off a USB with persistence for a while if need be. Thanks for the input everyone! :)

---

### Post by mips on 2011-10-28
> **meatytaco said:**
> I can't seem to find any tools from Sony for this, which makes sense to me cause it came with Vista.

You won't get that from Sony. You will get diagnostics tools from the hard drive manufacturers sites.

*sudo hdparm -I /dev/sdX* where X is the drive nuber a, b, c etc. will give you the hard drive info. It does not always give the manufacturer but will give you model & serial number. Punching the model number into google should tell you who the manufacturer is. Alternatively open gnome disk utility which will also give you the info.

From the screenshot in your first post you have a **Fujitsu MHV2160BT PL** hard drive which google says is a SATA hard drive but confirm this visualy by eye.

Fujitsu sold it's hard drive division to Toshiba [http://www3.toshiba.co.jp/storage/english/spec/hdd25/05_MHV2XXXBT.htm](http://www3.toshiba.co.jp/storage/english/spec/hdd25/05_MHV2XXXBT.htm)

You can use a dos based utility like MHDD on the drive to scan & test it.

---

### Post by meatytaco on 2011-10-29
Thank you :) this will make figuring out which one I need easier. :)

---

