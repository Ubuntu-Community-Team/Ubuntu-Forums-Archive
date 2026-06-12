---
title: "Ups"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by thejerryguy on 2006-12-04
Need to buy a UPS for my Deasktop computer running UBUNTU 6.1. The software from most manufacturers says it will run under Linux. Does this mean it will work with UBUNTU?

jerry

---

### Post by Malta paul on 2006-12-04
Yes a USB will work with Ubuntu 6.10, just plug it in and it will be detected. Good luck:)

---

### Post by phido on 2006-12-04
UPS =/ USB
[http://en.wikipedia.org/wiki/Uninterruptible_power_supply](http://en.wikipedia.org/wiki/Uninterruptible_power_supply)

@jerry
- could you give some examples so we can have a look
- theres the uspd package in the repos to monitor such devices, but I have no experience with them
justmy2cents

---

### Post by wpshooter on 2006-12-04
> **thejerryguy said:**
> Need to buy a UPS for my Deasktop computer running UBUNTU 6.1. The software from most manufacturers says it will run under Linux. Does this mean it will work with UBUNTU?

jerry

If there is, it must be a very recent development.  Because when I looked at this just recently, I could not find any UPS manufacturer's software that would run on a Ubuntu O/S.  I even called several of them including APC.  

The UPS will function fine as a hardware device but I don't think you are going to be able to find any automatic monitoring and shutdown software that will work **properly**.

But good luck to you.

---

### Post by infoseeker on 2006-12-04
Just as a matter of interest, do you get UPS's with a USB data cable?

---

### Post by thejerryguy on 2006-12-04
I can get the UPS with a USB or SERIAL cable and Linux software. But as others have pointed out, I don't believe the UPS will shut down the UBUNTU pc when the power fails. I think a frien plans to buy a UPS for his Windows XP machine, I will ask to try it out first and let you know if it works.

Thanks for all the responses.

jerr

---

### Post by drphilngood on 2006-12-04
I use an APC brand UPS that connects using a USB cable with Ubuntu and it works fine.  The only way you know it is there is once in a while it performs a self-test and lets me know how long it can supply power if there is a power failure and of course, if there really is a power failure.

---

### Post by wpshooter on 2006-12-04
> **drphilngood said:**
> I use an APC brand UPS that connects using a USB cable with Ubuntu and it works fine.  The only way you know it is there is once in a while it performs a self-test and lets me know how long it can supply power if there is a power failure and of course, if there really is a power failure.

It may work fine as far as providing you with back up power as long as the battery lasts, but if you don't have a proper working software installed, the computer is not going to be shutdown after a specified time period to prevent your computer from being dropped like a hot potato when the UPS's battery runs out !!!  Or are you saying that you have a software installed that will perform this vital function ???

Thanks.

---

### Post by yabbadabbadont on 2006-12-04
apcupsd is in the repositories...  it works fine for monitoring and shutting down the system in case of a sustained failure.

It is specifically for APC ups's though.

---

### Post by wpshooter on 2006-12-04
> **yabbadabbadont said:**
> apcupsd is in the repositories...  it works fine for monitoring and shutting down the system in case of a sustained failure.

It is specifically for APC ups's though.

I recently called APC about this software and they told me that it is NOT recommended for use on their UPSs.

---

### Post by kakalaky on 2006-12-04
They just say that because the software wasn't written by them.  It works fine.

---

### Post by Bigbluecat on 2006-12-04
I use APCUPSD with an APC UPS device and it works fine. Go for it.

---

### Post by drphilngood on 2006-12-04
> **wpshooter said:**
> It may work fine as far as providing you with back up power as long as the battery lasts, but if you don't have a proper working software installed, the computer is not going to be shutdown after a specified time period to prevent your computer from being dropped like a hot potato when the UPS's battery runs out !!!  Or are you saying that you have a software installed that will perform this vital function ???

Thanks.


[ATTACH]20559[/ATTACH]

You are most welcome.

---

### Post by dvarsam on 2006-12-04
Dear "thejerryguy",

[QUOTE=thejerryguy]I can get the UPS with a USB or SERIAL cable and Linux software.[/quote]

I have an **APC** (USB connected) **Back-UPS RS500**. 

[quote=thejerryguy]But as others have pointed out, I don't believe the UPS will shut down the UBUNTU pc when the power fails.

I think a friend plans to buy a UPS for his Windows XP machine, I will ask to try it out first & let you know if it works.[/QUOTE]

One day, there was power outage...

The UPS lasted for 17 minutes & when it's battery reached 10%, my Ubuntu _automatically_ shut down!

So, YES, I can confirm that it was achieved!

And from the **Top Panel**:

1. Right-click on it & select "**Add to Panel...**"

2. Under the section "System & Hardware", select the icon named "**Battery Charge Monitor**".

3. Click on the button named "**Add**" & then on "**Close**".

A battery icon will appear on your Top Panel.

When you move your mouse on it, a pop up will say:

> System is running on AC power
No Battery present

Now, at some time in the past, I installed a package designed for UPS & that package would also provide in the above output the percentage your UPS is charged to...

But I don't remember the name of the package...

I thought that this appeared by default...

I only noticed that the "**Battery % Charged**" did NOT appear, when I had already formatted & re-installed my Ubuntu PC.

So, if I find what package offered this ability, I will post here.

But, it _is_ possible!

Good Luck!

P.S.> Don't expect to get the same functionality as in Windows, but at least you can always view the "**Battery % Charged**" & your Ubuntu PC will shutdown if your Battery runs out. But that is enough for me anyway...

---

### Post by dvarsam on 2006-12-04
Hello again!

I guess i made a mistake!

That thing I suggested you add on your "Top Panel" is NOT for UPS use...

I thought that it was a package I installed... that did all this, but it was NOT!

It is what user "drphilngood" has suggested:

From the Menu:

1. Select "**System\Preferences\Power Management**".
   (in there you can set your preferred settings)

2. To add an icon on your Top Panel, select Tab named "**General**".

3. Under the "Notification Area", select "**Always display icon**".

4. Click on the button named "**Close**".

On your Top Panel, a battery icon should appear.

If you move your mouse on it, you will get the following pop up:

> Computer is running on AC power
UPS fully charged (100%)

And if your UPS gets discharged for some reason, your Ubuntu will shut down!

Sorry for my previous misleading post, but I didn't remember how I had done it - I thought that it was achieved with a UPS package I had installed...

But when I tried out what user "drphilngood" suggested, I realized that it was NOT due to package installation, as I previously believed...

Good Luck!

---

### Post by msak007 on 2006-12-30
I'm using apcupsd with my APC BackUPS Pro 500 via USB and it works fine. I can monitor the status and get it to shut down when critical. The only thing is, as a KDE user, there's no built-in power management module to control UPSes like the one that's been suggested (at least not that I can find). I did however find a GUI for apcupsd called [Gapcmon]("http://gapcmon.sourceforge.net/"). I see no mention of it anywhere in the forums and it took me a while to find it, but it's a great tool. It has an optional System Tray icon for the Control Panel and / or each UPS connected to the system, gives you the status of your UPS by hovering over the tray icon, and clicking on it gives you very detailed info, charts, and historical data. I had to compile it from source though because there's no package for it in the repos and it required a lot of Gnome libraries, but I would definitely recommend it.

---

