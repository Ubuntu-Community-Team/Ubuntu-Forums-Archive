---
title: "Installed kernel 2.6.19: no more wireless :("
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-08
Hi,

I'm running Ubuntu 6.10 (Edgy) and I just compiled and installed the new linux kernel 2.6.19 because I thought it would make my SD card reader work (it didn't by the way). Also I patched the kernel with linux-phc to underclock my CPU. Everything works fine except that now I have no more wireless :( As I want to keep this latest kernel I'm trying to find how to make wireless work again. Here are the output of some commands:

lspci:
01:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.

lsmod | grep ipw:
ipw2200               154824  0 
ieee80211              35784  1 ipw2200

I think this "issue" is common when compiling/installing new kernels from kernels.org in Ubuntu but I'm not sure how to solve this. From what I could find here and there, here are the different options:

1) The new kernel should look in the "old" folder for the IPW2200 firmware.  This is explained as follow: If you have an Intel IPW2200 wireless card or something else that needs files from /lib/firmware/uname -r the hardware is not working when booting with the new kernel. To fix this create a link to the old directory:

cd /lib/firmware/
sudo ln -s 2.6.17-10-generic `uname -r`
(source: [https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto))

I did that but it didn't work.

2) Compile new ndiswrapper as explained here ([http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source](http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source))

3) Install the new IPW2200 firmware (I think it's version 3.0 now)


Do you know what could prevent the wireless from working when installing the new kernel? Does it mean that the ndiswrapper is not part of the kernel and should be added afterwards as solution 2?

Sorry if this is somewhat confusing, I have troubles to understand all the processes involved here. Probably I should have stick with the old kernel but I like trying new things....and it's only when something doesn't work that we really learn something anyway :)

---

### Post by kilou on 2006-12-08
Or should I install ndisgtk and install the latest windows driver for intel 2200?? (...but is the support of i2200 wireless not already supported in the new kernel?). I don't really understand why I should use ndiswrapper with this Vanilla kernel when I didn't need to with the old "Ubuntu" kernel.

---

### Post by mahy on 2006-12-08
Are you sure you performed all the necessary steps when compiling and installing a new kernel, for example "depmod -a"? Look at Gentoo Wiki, they've got a superb howto over there.

---

### Post by kilou on 2006-12-08
You were right Mahy, I did something wrong during the setup. For some reason the symlink that needs to be created to allow the new kernel to find the IPW2200 firmware (in the old kernel folder) was not created properly so I guess no firmware was found. The step tha needed to be performed was:

cd /lib/firmware/
sudo ln -s 2.6.17-10-generic `uname -r`

I did that but then I checked in the /lib/firmware/ and saw the 2.6.17-10-generic folder (where the IPW2200 firmware is) and a file named 2.6.19-custom. This was a file and not a folder! I just erased that file and retype the above command, what then created the proper folder 2.6.19-custom symlinked to 2.6.17-10-generic folder. After rebooting my wireless is detected and works correctly (well I still have troubles with DNS as before but this is another topic!).

Great :)

---

