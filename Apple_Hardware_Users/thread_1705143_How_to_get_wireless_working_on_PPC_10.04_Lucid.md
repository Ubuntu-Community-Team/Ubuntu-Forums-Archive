---
title: "How to get wireless working on PPC 10.04 Lucid"
date: 2011-03-11
forum: Apple Hardware Users
---

### Post by rsavage on 2011-03-11
I've put this together to hopefully help new users. It is based on my experiences using an Airport Extreme card, but I could do with some feedback particularly regarding the Airport classic cards. Please point out any errors or your own experiences. Hopefully with a comprehensive list of solutions we can update the FAQ wiki.
 
So here goes....
 
Firstly, make sure you've read the relevant section of the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#Will%20my%20wireless%20work?]("https://wiki.ubuntu.com/PowerPCFAQ#Will%20my%20wireless%20work?")
Follow any advice it gives regarding your card. So for an airport extreme card you need to run the command "sudo aptitude install b43-fwcutter" at a terminal, but an airport classic card doesn't need this command. To run this command you need to be plugged into an Ethernet cable.
 
Next, check you have the correct user settings:
Go to System -> Administration -> Users and Groups -> Advanced Settings -> User Privileges
Make sure "Connect to wireless and ethernet networks" is ticked.
 
Unplug your Ethernet cable and reboot the machine.
 
Right click on the network applet icon (right click is F12 on my machine because I only have one button on my trackpad) and tick 'Enable Networking', 'Enable Wireless' and 'Enable Notifications'.
 
Now normal/left click on the network applet icon and select your network from the list. 
 
You will be asked for the security type and network password. Enter them and click 'Connect'. You should now be online. Check by opening firefox.
 
Right click on the network applet icon again and select 'Edit Connections...'. Go to the Wireless tab and select your network from the list. Click "Edit...". Enter your Ubuntu user account password if prompted. Make sure "Connect automatically" and "Available to all users" are ticked. Click Apply and then Close. You are done!
 
If you start the computer one day and you have unexpectedly lost your connection then going through the above steps is a good problem solving exercise. More than likely 'Enable Networking' or 'Enable Wireless' will have unchecked themselves. 
 
If you don't have wireless still (this is highly likely for airport classic because of this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/715438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/715438)) or you are losing connections repeatedly then try installing wicd:
 
*** Airport classic users can try an additional workaround at this point . See Workaround 1 at the bottom of the document. ***
 
At a terminal type the following commands (note, you need to be plugged into an Ethernet cable):
 
sudo aptitude install wicd
sudo aptitude remove network-manager
 
You will get some message about network-manager-gnome that it asks if you want to remove too. You should reply yes to this. 
 
Next, open up WICD which should be in your applications area, find your network, click properties and enter the password in. Click connect.
 
Still no wireless? Then reboot without the Ethernet cable connected. It may be a cliché, but turning it off and on again does work sometimes :-)
 
If you think the wicd applet icon is ruining the look of your desktop then it can be removed. System > Preferences > Startup Applications. Untick the wicd applet.
 
Still no wireless? If you have Airport classic then try Workaround 2 or 3 at the end of the document.
 
For the technically minded, you can find further information and answers about airport classic at [http://linuxwireless.org/en/users/Drivers/orinoco](http://linuxwireless.org/en/users/Drivers/orinoco) (see the known issues section). For airport extreme see [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
 
So that is all I know! It has been written from memory and is how I think the process should unfold. There are bound to be mistakes or problems. My own experience was much more around the houses because I couldn't find a good guide. I can confirm that the default network manager and wicd both work with airport extreme using WPA security. Please provide your own experiences to help others. 
 
 
***** Workaround 1 - Airport classic only *****
 
An additional workaround exists for Airport classic users. This is based on this file which contains the firmware:
 
/lib/firmware/agere_sta_fw.bin
 
A similar method is here [http://ubuntuforums.org/showpost.php?p=9241613&postcount=12](http://ubuntuforums.org/showpost.php?p=9241613&postcount=12) .
 
It has been reported that if this file (*some people also move agere_ap_fw.bin although I don't think it is used*) is moved out of the firmware folder or renamed then the airport card uses it's own flashed firmware. To work with WPA it has to be v9.42 or greater. Therefore, you may have to do a firmware upgrade for your card from within Apple OS to use this workaround. Also, note for WPA you must set the algorithm to TKIP (the earliest algorithm and usually the default) instead of AES (the newest). 
 
To rename the files type at a terminal:
 
sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak
 
Then restart the computer a couple of times, checking if you have gained wireless and everything that needs to be ticked is still ticked on each reboot. Following a reboot, you can find the version of flashed firmware by typing this at a terminal:
 
dmesg | grep airport
 
If this workaround doesn't work then move onto wicd, but you will have to rename the files back first:
 
sudo cp /lib/firmware/agere_sta_fw.bin.bak /lib/firmware/agere_sta_fw.bin
 
 
***** Workaround 2 - Airport classic only *****
The package linux-firmware-nonfree contains versions of the airport firmware which may be different from the default files. You can install them and try them with wicd (or maybe the default network manager?). Feedback is needed about which versions work (are there corrupt/non-corrupt versions?) and if this workaround adds functionality in Ubuntu.
 
sudo apt-get install linux-firmware-nonfree
 
You can also download agere_sta_fw.bin directly from here [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=history;f=agere_sta_fw.bin;h=bae000f5a7162f5a5b052a2f5b78016e95f825c5;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=history;f=agere_sta_fw.bin;h=bae000f5a7162f5a5b052a2f5b78016e95f825c5;hb=HEAD) .
 
 
***** Workaround 3 - Airport Classic Manual Config *****
You can manually configure wpa_supplicant like they do in CRUX [http://cruxppc.org/Airport](http://cruxppc.org/Airport) .

---

### Post by linuxopjemac on 2011-03-13
Instead of b43-fwcutter, I would use firmware-b43-installer. It does all automatically.

---

### Post by rsavage on 2011-03-13
Thanks for the comment.  The reason I used b43-fwcutter is because all the documentation I have read uses this.  For example, "*In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you*".  I assume this also includes the b43legacy cards, as legacy models are listed as being supported in this documentation: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers").  Also, I don't think firmware-b43-installer is available in Ubuntu.

---

### Post by linuxopjemac on 2011-03-13
maybe not for Lucid Lynx, bit for newer versions of Ubuntu:
[http://packages.ubuntu.com/maverick/kernel/firmware-b43-installer](http://packages.ubuntu.com/maverick/kernel/firmware-b43-installer)

---

### Post by imackan on 2011-09-25
Thank you very much for this post! The Workaround 1 worked perfectly on my old iBook G3 and Ubuntu 10.04 Lucid Lynx with original Airport card.

---

