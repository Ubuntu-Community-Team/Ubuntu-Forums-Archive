---
title: "Network card problems"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by poser on 2006-03-24
I recently updated my sytem, and everything was working fine.  Since then I have shut down the computer and turned it back on.  Now the Network cards won't work.  I don't really use the wired nic, but I do use the wireless.  When starting the computer it has trouble starting the network devices.  

In Kubuntu I checked the System Settings -> Network settings and both eth0 (ethernet) and eth1 (wireless) are disabled.  If i go into administrator mode I have the option to Enable the Interface, but at soon as I do that it disables again.

Also in the networking settings section it shows both eth1 and eth0 active (which wouldn't really make sense since they are both disabled)

Anyone have any information that could help me?

---

### Post by poser on 2006-03-25
I've checked several other threads, but none seem to mention eth1 which is my wireless.  Still in the dark as to how to get this activated yet.  Any help would be much appreciated.

---

### Post by Titus A Duxass on 2006-03-25
Try switching off but do not unplug,
Remove wireless card,
Restart,
Switch off but do not unplug,
Replace card,
Restart.

Bizarre I know but it works for me when I have similar happenings.

---

### Post by poser on 2006-03-25
Unfortunately I can't try that.  I forgot to mention that it is a laptop with built in wireless

---

### Post by katarot on 2006-03-25
poser: try this it was the only one that work for me that will i keep a copy of it on disc lol

Step 1: sudo apt-get install ndiswrapper-utils



    * ndiswrapper is the program that allows us to use XP drivers under Linux.



Step 2: lspci | grep 802.11 (note of the 8-10 digit number)



    * lspci is a utility for displaying information about all PCI buses in the system.



Step 3: lspci -n | grep (append with 8-10 digits from step 2)



    * lspci -n shows the device codes (ie; PCI ID) that we need.



Step 4: Submit your PCI ID into the search engine below. It will return any known information or suggested drivers from the ndiswrapper listings.



    Google

    	

    DATABASE



Step 5: Unzip the driver file and save the .inf and .sys files. Take note of where you save these.



    * If you use file-roller (archive manager) to unpack your file it defaults to /tmp. You can unpack this file anywhere you like just as long as you remember where.



Step 6: sudo ndiswrapper -i {driver.inf}



    * The -i used above &#145;installs&#146; the the windows driver.



Step 7: sudo ndiswrapper -l



    * The -l &#145;lists&#146; the installed drivers. At this point we want to see &#145;hardware present, driver present&#146;. Anything else and we&#146;ve either missed a step or installed an incompatible driver.



Step 8: sudo modprobe ndiswrapper



    * This command adds the ndiswrapper utility as a module in the kernel. This allows the kernel to communicate with the wireless card, etc.



Step 9: sudo ndiswrapper -m



    * This adds ndiswrapper as a regular addition to the kernel (ie; it will now load automagically at boot!)



Step 10: Setup your wireless access point, WEP/WPA, etc.



    At this point, assuming everything went well, you should be just about done. Can&#146;t hurt at this point to shutdown and restart (some cards have issues with soft reboot. shutdown is sometimes needed to re-load the card).



    Assuming this works for you feel free to share this link with friends, relatives, dignitaries and people who may be inclined to give me money (j/k). If you have any questions just shoot me an email. We&#146;ll see what we can do for you.



#you  might think this looks like the other guides but it not the same 
hope this helps

---

### Post by poser on 2006-03-25
to do the sudo apt-get install command, would I not have to have an internet connection?

Also if it matters, the wireless has been working for over a month.  I don't think it is a problem with it not finding the drivers.  It just seems to not want to enable them anymore.

---

### Post by poser on 2006-03-25
I figured out the problem, but it doesn't really make any sense.

I had been connected on my laptop that dual boots to XP and ubuntu.  XP worked fine, so I figured that the probem was in ubuntu somewhere.

XP has been working all day for me.
then I couldn't connect with XP either.  Checked all connection settings in XP and everything seemed ok.  So I rebooted the router.  That fixed XP.  So I took a shot in the dark and tried Ubuntu.  It was also working again.  

What I dont understand is why ubuntu would disable the nic just because it wouldn't connect.  It made me totally misread the situation.

---

