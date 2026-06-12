---
title: "Startup"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-11-06
****



Hi all,

My question is simple:  In the way ubuntu boots up, is there anything I can do to speed up the boot process maybe through a terminal prompt or like the equivilent of M$ stopping things from starting so you have a faster booting up process?

---

### Post by Pumalite on 2007-11-06
Sudo apt get install sysv-rc-conf

General - HowTo: Speed up ubuntu boot process - the way you can feel it. - updated - 2 Weeks Ago 

This HowTo is for those who complaint ubuntu boot-up speed is pretty slow but not willing to install any alternative tools to speed up. The way I use here is not the altimate solution by any means but it does make differences and it does work. Everything done below is by tuning the boot process itself and because everyone's computer might be different, there is a little risk that something below might break your system. Take your own judgment before you perform a change and always good to do a backup for the /etc dir.

**This HowTo is mainly for laptops and desktops, not for servers.**

Suggestions for this HowTo:
1. I hope you learn something from here but not just a simple copy. So please, **DO NOT** follow exactly what I did and copy to your box. Read the descriptions of services and use your own judgment to determine if you need to keep them on or not. For instance, I turned GDM off on mine to boot to console, but if you do not feel confortable to see console at all, you should keep GDM or KDM on to boot directly to GUI.
2. If you have a question about a boot up service and not really sure what it does, post a question here and see if anybody can help you. Ask before you do if you don't know. The bottom line to be safe is to leave a service on rather than turn it off if you do not understand.
3. If you see a boot up service that you have but not in here, let us know what it does just like what I did here - give some descriptions and suggestions on whether it should be on or off on a normal laptop or desktop environment.

Color reference : service I turned on
service I turned off

I. Install a tool - sysv-rc-conf. It is a perl based boot process adjustment tool.
Code:
sudo apt-get update
sudo apt-get install sysv-rc-conf
It gives you a way to esaily config the boot process and runlevel configuration, but its not necessary if you want to do it manually by linking/unlinking the files... Its up to you.

II. Ok, that's all we need. Now let's fire it up by
Code:
sudo sysv-rc-conf
and analyze each service one by one. **Note:** Some services I have here you might not have, perfectly ok. If some you have but I don't, then you will need to investigate on your own or ask here... But this HowTo should cover most of them...

Throw a littel bit of runlevel knowledge here before we start messing them up.... All the boot processes are executed in sequence as following:
runlevel S: the first runlevel in boot process. /etc/init.d/rcS script will be invoked to start and all the processes underneath /etc/rcS.d will be executed.
runlevel 1: the single user mode. All processes underneath /etc/rc1.d will be executed.
runlevel 2,3,4,5: in debain system, the multi-user env, may not may not include GUI. The same, processes under each of the corresponding dirs will be run. **Note** this is different than RedHat, SuSE, and other RPM based systems.
runlevel 0: computer shutdown.
runlevel 6: computer reboot.

ok, back to sysv-rc-conf:

1. acpi-support - You'd better leave it on "X" at S runlevel.
2. acpid - The acpi daemon. These two are for power management, quite important for laptop and desktop computers, so leave them on.
3. alsa - If you use alsa sound subsystem, yes leave it on.
4. alsa-utils - On my system, this service supercedes the alsa, so I turn off the alsa and turn this on at S level. **Note**, I mean "turn off" is to remove all "X" at all runlevels. If you don't have it on your system, no problem. Just keep going.
5. anacron - A cron subsystem that executes any cron jobs not being executed when the time is on. Most likely you've probably turned your computer off when a certain cron job time is ready. For example, updatedb is scheduled at 2am everyday, but at that moment, you computer is off, then if anacron service is on, it will try to catch up that updatedb cron... I turn it off cause it didn't turn my laptop off very offen, but its totally up to you for this one.
6. apmd - This is the one that confused me a quite bit. I have acpid on already and what's the benefits of having apmd on too? If you computer is not that old which can't even support acpi, then you may try to turn this off. I did anyway.
7. atd - like cron, a job scheduler. I turned it off.
8. binfmt-support - Kernel supports other format of binary files. I left it on.
9. bluez-utiles - I turned it off. I don't have any bluetooth devices.
10. bootlogd - Leave it on.
11. cron - Leave it on.
12. cupsys - subsystem to manager your printer. I don't have so I turned it off, but if you do, just leave it on.
13. dbus - Message bus system. Very important, leave it on.
14. dns-clean - Mainly for cleaning up the dns info when using dial-up connection. I don't use dial up, so I turn it off.
15. evms - Enterprise Volumn Management system. I turned it off.
16. fetchmail - A mail receving daemon. I turned it off.
17. gdm - The gnome desktop manager. I turned it off anyway since I get use to boot to console first. This is up to you if you want to boot directly to GUI.
18. gdomap - Actually I have no idea why this one should on. I didn't see any other systems have this daemon, so I turned it off and I don't feel I lose anything. Any benefits to have it on a loptop or desktop?
19. gpm - Mouse support for console. If you feel you'd better have a mouse on console, go turn it on at runlevel 1 and 2. That's all you need.
20. halt - Don't change it.
21. hdparm - tuning harddisk script. I removed the 2,3,4,5 runlevel but add it to S runlevel. I feel that opening DMA, 32bit I/O, etc eariler will benefit the rest of the processes. Also I changed the original script to a very simple one that I made myself. I feel useless to put all those redundant checks if I know what I am doing. The configuration file is /etc/hdparm.conf.
22. hibernate - If your system support hibernate, leave it on. Otherwise, its useless for you.
23. hotkey-setup - This daemon setup some hotkey mappings for Laptop. Manufacturers supported are: HP, Acer, ASUS, Sony, Dell, and IBM. If you have a laptop in those brands, you can leave it on, otherwise, this might not have any benefits for you.
24. hotplug and hotplug-net #activating hotplug subsystems takes time. I'd consider to turn them off. I did some changes in my /etc/network/interfaces file. Instead of mapping my wireless card during hotplug process, I set it up to auto. So I can turn them off. I've tested even I turned them off, ubuntu can still detect my usb driver, my digital camera, etc. So I think its pretty safe to turn them off. **Note** If you find your sound card doesn't work after turning hotplug service off, you can turn it back. Or edit /etc/modules file to add your sound card's driver module. Tested out the later one is faster.
25. hplip - HP printing and Image subsystem. I turned it off.
26. ifrename - network interface rename script. Sounds pretty neat but I turned it off. Mainly for managing multiple network interfaces names. Since I have a wireless card and an ethernet card, they all assigned eth0 and ath0 from kernel, so its not really useful for me.
27. ifupdown and ifupdown-clean - Leave it on. They are network interfaces activation scripts for the boot time.
28. inetd or inetd.real - take a look your /etc/inetd.conf file and comment out any services that you don't need. If there aren't any services there, then its very safe to turn them off.
29. klogd - Leave it on.
30. linux-restricted-modules-common - You need to see if you really have any restricted modules loaded on your system. Since I need madwifi ath_pci module, so I left it on. The restricted modules can be found from /lib/linux-restricted-modules. If you find that you are not using any of the restricted modules, then its ok to turn it off.
31. lvm - I don't use it so I turned it off. Leave it on if you *DO* have lvm.
32. makedev - Leave it on.
33. mdamd - Raid management tool. I don't use it so I turned it off.
34. module-init-tools - Load extra modules from /etc/modules file. You can investigate your /etc/modules file and see if there is any modules that you don't need. Normally, this is turned on.
35. networking - bring up network interfaces and config dns info during boot time by scaning /etc/network/interfaces file. Leave it on.
36. ntpdate - Sync time with the ubuntu time server. I don't need it on boot time so I turned it off.
37. nvidia-kernel - I compiled the nvidia driver by myself, so its useless for me now. If you use the ubuntu nvidia driver from the restrict modules, just leave it on.
38. pcmcia - Active pcmcia device. I changed it to start on S runlevel instead of on each 2,3,4,5 cause I feel its better to have hardware device ready at first. Also, useless if you are using desktop which doesn't have pcmcia card. So in that case, turn it off please.
39. portmap - daemon for managing services like nis, nfs, etc. If your laptop or desktop is a pure client, then turn it off.
40. powernowd - client to manage cpufreq. Mainly for laptops that support CPU speed stepping technology. Normally, you should leave it on if you are configuring a laptop, but for desktop, it might be useless.
41. ppp and ppp-dns - Useless to me. I don't have dial-up.
42. readahead - **Thanks mr_pouit!** It seems readahead is a kind of "preloader". It loads at startup some libs on memory, so that some programs will start faster. But it increases startup time for about 3-4 seconds. So, you can keep it... or not . **update**, I tested and I just didn't feel difference loading programs. So I decided to turn it off. If you have a reason to keep it on, please do so.
43. reboot - Don't change it.
44. resolvconf - Automatically configuring DNS info according to your network status. I left it on.
45. rmnologin - Remove nologin if it finds it. It wouldn't happen on my laptop, so I got rid of it.
46. rsync - rsync daemon. I don't use it on my laptop, so turned it off.
47. sendsigs - send signals during reboot or shutdown. Leave it as it is.
48. single - Active single user mode. Leave it as it is.
49. ssh - ssh daemon. I need this so I turned it on.
50. stop-bootlogd - stop bootlogd from 2,3,4,5 runlevel. Leave it as it is.
51. sudo - check sudo stauts. I don't see any good to run it everytime on a laptop or desktop client, so I turned it off.
52. sysklogd - Leave it as it is.
53. udev and udev-mab - Userspace dev filesystem. Good stuff, I left them on.
54. umountfs - Leave it as it is.
55. urandom - Random number generator. Might not useful but I left it on.
56. usplash - Well, if you really want to see the nice boot up screen, leave it as it is. I just turned it off anyway. If you want to turn it off, you also need to edit /boot/grub/menu. lst file to comment out the splashimage line and get rid of the splash kernel boot option.
57. vbesave - video card BIOS configuration tool. Its able to save your video card status. I left it on.
58. xorg-common - setup X server ICE socket. I moved it from starting at runlevel S to runlevel 2,3,4,5. Since I don't need this if I boot to single user mode. This way it wouldn't occupy time during the initial booting.
59. adjtimex - This is a kernel hw clock time adjusting too. Normally, you shouldn't see this on your boot up list. In very rare case if you do see its on your boot up process, then there might be a reason why it is on, so better leave it that way. In my case, it is off.
60. dirmngr - A certification lists management tool. Work with gnupg. You will have to see if you need it or not. In my case, I turned it off.
61. hwtools - A tool to optimize irqs. Not sure what's the benefits of turning it on. In my case, I turned it off.
62. libpam-devperm - A daemon to fix device files permissions after a system crash. Sounds pretty good, so I left it on.
63. lm-sensors - If you matherboard has builtin some sensor chips, it might be helpful to see hw status via userspace. I ran it and it said "No sensors found", so I turned it off.
64. mdadm-raid - The same as mdadm service. Its to manage the RAID devices. If you don't have RAID, then its ok to turn it off.
65. screen-cleanup - A script to cleanup the boot up screen. Well, turn on or off is up to you. In my case, I left it on.
66. xinetd - A inetd super daemon to manage other damons. In my system, the xinetd is managing chargen, daytime, echo and time (find them from /etc/xinetd.d dir), I care none of them, so I turned it off. If you do have some important services configured under xinetd, then leave it on.

III. Alter the /etc/inittab file
Code:
vi /etc/inittab
then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.

IV. Ok, now, we can reboot our box and see how it goes. From what I've tested, before I got tons of services stopped, the whole process is about 85 secs to 90 secs to boot to console. (At that time, I also has samba and nfs services turned on which I shouldn't. Apparently, I turned them off too). After this change, the whole boot up process took about 50 secs. I have a P4M 1.8G CPU laptop. Some of the high-end desktops or laptops should take even less time.

**UPDATE**: speed up/clean system reboot or shutdown process.
1. start sysv-rc-conf by issuing:
Code:
sudo sysv-rc-conf
2. ok, open your eyes and look very carefully for those SERVICES DO NOT HAVE "X" ON ALL RUNLEVELS (All runlevel means 1,2,3,4,5,6, and S), write them down one by one. Don't make mistakes here. Double check after you've done.
3. quit sysv-rc-conf.
4. 
Code:
cd /etc/rc0.d
- This is for the system shutdown process.
5. ok, now, 
Code:
 ls K*
will list all links starting from UPPERCASE letter "K". Compare with your list, change each of the filename containing the service name in your list to start from a lowercase "k". For example, in your list, you have ppp service (which means ppp is turned off at all runlevels), then you can do like: 
Code:
sudo mv K00ppp k00ppp
. You just change the UPPERCASE K to lowercase k, keep the rest the same. Do this on all of the services in your list.
6. 
Code:
cd ../rc6.d
- This is for the system reboot process.
7. ok, you should see similar things here too. So do the same thing here as you did on rc0.d.
8. Now, you reboot and shutdown process should be cleaned up and faster.

The explanation for what you did is pretty simple. The /etc/rc and /etc/rcS scripts run start on each link on each runlevel by scaning if it is starting with a UPPERCASE "S" and run stop on each by scaning if it is starting with a UPPERCASE "K". So for reboot and shutdown runlevels, the most thing we care is the "K" links cause for those services not running on all runlevels, its just not needed to stop them. They are not runing at all. If some day you want to turn some of the services back on, just change the lowercase "k" to UPPERCASE "K". That's all.

Anyway, it is not intend to work on servers, but I did try on one of my servers has 2.7G P4 and 1.5G mem. It brought the boot process down to 31 secs. I calc'ed it with my watch. Besides, this is with my ftp server and nfs server started on boot time.


FOR DAPPER AND NEWER
Boot Profiling and readahead
Improve bootup speed by reprofiling bootup

(1) At the bootup menu (GRUB), select your default kernel. You may need to press ESC to see this menu.

(2) Press e for edit.

(3) Choose the first line (it should start with "kernel"). Press e again.

(4) Move to the end of the line, then add the word profile. Press enter.

(5) Press b to boot.

(6) Let the system boot to the login screen, and wait for all disk activity to stop. Remember, during this one bootup, you've told Ubuntu to keep track of all disk activity going on, in order to build that list. Don't be surprised if it's significantly slower than your ordinary bootups -- that's why it's not activated by default, remember?

(7) Reboot your system, and enjoy the results.

(8) Perform the above profiling procedure. It is important that the order is correct, else this form of readahead won't do a thing!

(9) Use your favorite text editor (under sudo or root privileges) to open /etc/rcS.d/S01readahead

(10) Find line 21, which reads:

Code:
if /sbin/start-stop-daemon --start --quiet --background \

Remove the --background, so that it reads:

Code:
if /sbin/start-stop-daemon --start --quiet \

(11) Save, reboot.

---

### Post by oldos2er on 2007-11-06
> vi /etc/inittab

 Feisty and Gutsy no longer have/use inittab.

---

### Post by Pumalite on 2007-11-06
Good to know. Thanks. I'll remove that link.

---

