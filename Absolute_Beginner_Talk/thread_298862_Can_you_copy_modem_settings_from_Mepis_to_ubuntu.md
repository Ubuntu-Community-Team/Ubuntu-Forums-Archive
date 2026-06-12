---
title: "Can you copy modem settings from Mepis to ubuntu?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by thedude98 on 2006-11-13
My Dell 600m winmodem works with the Mepis (v6.1) live cd, but not in ubuntu installed on my hd.  Can I copy the KPPP settings from Mepis to ubuntu?  Is this one way of troubleshooting?  Any direction would be greatly appreciated! -Jude

---

### Post by towsonu2003 on 2006-11-13
your problem most probably isn't with kppp settings but with missing drivers. Have a look at the wiki page in my signature on how to get your winmodem working again. 

the page is a little bloated, but the index will be helpful in sorting out which sections to read :)

---

### Post by thedude98 on 2006-11-19
Ok, I downloaded the scanModem utility.  I have a SmartLink modem.  The YourSystem.txt states that "Ubuntu is not yet providing pre-compiled drivers for WinModems".  No kidding.  Although the next file starts to talk about kernel compiling.  This is just not a realistic solution.  If that's the road I would need to take I guess I'll just swith over to Mepis until ubuntu ships with winmodem drivers.

---

### Post by towsonu2003 on 2006-11-19
> **thedude98 said:**
> Ok, I downloaded the scanModem utility.  I have a SmartLink modem.  The YourSystem.txt states that "Ubuntu is not yet providing pre-compiled drivers for WinModems".  No kidding.  Although the next file starts to talk about kernel compiling.  This is just not a realistic solution.  If that's the road I would need to take I guess I'll just swith over to Mepis until ubuntu ships with winmodem drivers.

Ok, I believe you should read the *modemdata.txt* as the wiki page tells. Try reading the whole file. (I know it's hard) After the second or third time, you'll probably make sense of what to do next. 

There are two sections in the wikipage about smartlink modems:
[https://help.ubuntu.com/community/DialupModemHowto#head-4be470bbae4b120bd5f6101c9aa218df7518b0c7](https://help.ubuntu.com/community/DialupModemHowto#head-4be470bbae4b120bd5f6101c9aa218df7518b0c7)
and 
[https://help.ubuntu.com/community/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4](https://help.ubuntu.com/community/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4)  which should be helpful after reading the modemdata.txt file.

---

### Post by thedude98 on 2006-11-20
Thanks for trying one more time.  I did this step,

If you can go online with your Ubuntu, you can install the package/daemon by enabling the  multiverse  repository and then install the sl-modem-daemon package.

I queried my modem and it is correctly recognized.  Nothing happens when I use the ubuntu dialer program but using kppp, I receive this error.

"The ppd daemon died unexpectedly!  Exit status:  1"

All of my account settings are correct.

---

### Post by towsonu2003 on 2006-11-20
> **thedude98 said:**
> 
I queried my modem and it is correctly recognized.  Nothing happens when I use the ubuntu dialer program but using kppp, I receive this error.

"The ppd daemon died unexpectedly!  Exit status:  1"

All of my account settings are correct.

I would try wvdial (instructions here: [https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb](https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb) ). It gives a little more information about whats going on. If it doesn't work, try out the different options mentioned in that page for its configuration file.

---

### Post by thedude98 on 2006-11-20
Wow that was great!  It works!

Many thanks, I'm keeping the Dial-up How-To bookmarked for future use.  Little tips like unchecking the carrier-check for SmartLink modems make all the difference.  Thanks for not giving up on me, I'm sold on free software..!

---

### Post by towsonu2003 on 2006-11-20
glad it works. enjoy :)

Little note: I use sl-modem-daemon and experience two difficulties that you might experience as well. Just posting them now, in case they happen to you in the future :)
loosing internet connection if doing cpu intensive work: [https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/47808](https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/47808)
dialing out error: [https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/47809](https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/47809)

---

