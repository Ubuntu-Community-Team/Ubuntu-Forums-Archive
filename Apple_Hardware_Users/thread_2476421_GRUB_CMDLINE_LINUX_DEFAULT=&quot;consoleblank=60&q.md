---
title: "GRUB_CMDLINE_LINUX_DEFAULT=&quot;consoleblank=60&quot; not working anymore on iMac 2017"
date: 2022-06-25
forum: Apple Hardware Users
---

### Post by StefSOFT on 2022-06-25
Hello dear Ubuntu users,

This is my first post and I am fairly new to using Ubuntu server 22.04.

Last week I installed Ubuntu server 22.04 on my iMac 27" 2017 to run a Minecraft server. After some issues with the network driver I was finally able to get it properly running. Since it is an iMac I searched for an option to have the display power off since I don't use it that often since I am using SSH and the iMac is beneath my desk. After a few Google searches I found out I could edit a GRUB file so the display powers off after 60 seconds. I edited the file "/etc/default/grub" and added the following line:

GRUB_CMDLINE_LINUX_DEFAULT="consoleblank=60"

This worked perfectly for a week, until yesterday.

Yesterday my Ziggo (Dutch ISP) router/modem restarted during a Minecraft session and I first thought it had to do with my iMac. I pressed the power button of my iMac shortly which resulted in a shutdown and powered it on again. Since then the display won't power off after 60 seconds, it always stays on and I don't know how I could resolve this. I restarted the iMac a couple of times, edited and updated the GRUB file, disconnected the power cable of the iMac, but the issue remains. I don't know how after a reboot the display won't behave the way intended. Does anyone know how I could resolve this issue?

Thanks in advance.

---

### Post by StefSOFT on 2022-06-26
Ok, I finally found out what I did wrong. I had put down two GRUB_CMDLINE_LINUX_DEFAULT lines in /etc/default/grub. The last one I added had to do with trying to resolve a network driver bug. I thought you could stack these entries but in the end it only uses the last entry. I found out I had to put the commands in one line.

My issue is resolved.

---

### Post by Doug S on 2022-06-26
Thanks for reporting back, both here and on [AskUbuntu]("https://askubuntu.com/questions/1415895/grub-cmdline-linux-default-consoleblank-60-not-working-anymore-on-imac-27-201").

---

