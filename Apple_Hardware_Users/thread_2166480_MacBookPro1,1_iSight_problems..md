---
title: "MacBookPro1,1 iSight problems."
date: 2013-08-09
forum: Apple Hardware Users
---

### Post by Michael_Alexander_Owens on 2013-08-09
I've looked all over, and the best, most detailed walkthrough which appeared to get me farthest is here, [The MactelSupportTeam/AppleiSight wiki]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight"). As I said, it got me the farthest, but I have not been able to complete its setup with this walkthrough.

Where I seem to run into a brick wall, is after extracting the firmware, installing the firmware, and then shutting down and booting up the Macbook Pro again. Once I do this step, typing ```
ls /lib/firmware/isight.fw
``` into the terminal does appear to indicate that the isight firmware is loaded/installed. However, I cannot seem to go on to the next step in this wiki; however I happen to copy the isight.fw  file, I cannot create a script to save in the folder where the isight.fw originally happened to be. Also, if you will notice, someone appears to have edited the wiki with some chit-chat, indicating that possibly this final step of copying the driver, which is already installed, to another random folder and creating script in the driver folder which points to it, is not necessary? So it is a little confusing to me. At any rate, I cannot seem to create this script, and nothing other than the terminal check seems to indicate that the iSight is even installed. Cheese, Ekiga, Skype, nothing sees the iSight at all. I am certain I have followed all steps before this point properly, and I don't know how to proceed with the instructions as written on the page. I am running Ubuntu 12.04.

Help?

---

### Post by Silviu_Dimulete on 2013-08-09
[FONT=arial]Hello,
I also have a Mac and I got the video working almost following the guide :)
What I did, and worked for me, was install the isight-firmware-tools and during the install pointing the extraction towards a directory in my /home/user/AppleWebCam/ where i had the [COLOR=#333333]AppleUSBVideoSupport (if you don't have it search for it on the web) and... that's it. Power off.. and stared using Skype after power on :) (Yes! I deleted MacOSX for good... and now only running GNU/Linux)[/COLOR][/FONT]

---

### Post by Michael_Alexander_Owens on 2013-08-09
Hold on, did you create the script and drop it in the folder where the isight.fw was originally installed, as the guide says? Or did you just create the extraction to that different location to start with? I am also using this laptop without MOSX, as the hardware only supports as recently as 10.6.x and I don't wish to stay so far behind.

---

