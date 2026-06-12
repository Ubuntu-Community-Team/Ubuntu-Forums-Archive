---
title: "Does Ubuntu Degrade with time?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-09-28
Hello everyone,
I installed Dapper (32bit) on my brand-new Acer notebook about 2 months back. Heres my machine config:
Acer Aspire 5004, AMD Turion 1.8 Ghz, 256 MB (shared) memory...out of this 220 is available..rest is for the video card. The motherboard has an SiS chipset, with the crappy sis-760 video card. 
I know the RAM is less..However, when i installed Ubuntu- i was quite impressed by my machine. I can say this because i can compare it with a machine with a higher config (2ghz, 1gb ram, IBM thinkpad)...and my acer ran ubuntu much faster. 
However, my machine has started to slow down..I have installed quite a few apps..too many to list here..but the major ones are Beagle, DrScheme, Swiftfox, Wine, etc. 
I now feel that my system has slowed down..a lot..and i dont think its due to the less RAM. Heres why:
I constantly monitor my CPU and Memory usage (using the gnome-applets) ..and for some strange reason, ubuntu now has started to work my processor really hard. Comparing between the past and present: earlier, during the launch of an application, CPU usage would peak for a very short time at around 20% .. but now...even when im not doing anything..it is 50%! and then all of a sudden it will go back to 0%...Similiarly, i find that programs take *much* longer to start.. It is also worth mentioning that th boot-time has increased by about 5 seconds ..earlier ubuntu booted-up in 50 seconds. Forget Multitasking, but even such simple tasks as using gedit (as im doing now) seem very sluggish..theres considerable lag in that too!
So, summing up: I am really disappointed..since one of the major reasons i wanted to use linux was because i had heard it doesnt degrade with time like windows. Has my ubuntu degraded? Can i repair it to make it as fast as when it was freshly installed? Does anyone know of any advanced process/memory monitoring tools using which i can single out the "bad" program? 
Thanks..

[PS: I use minimal eye-candy...wall-paper turned off etc...just in case you think thats the reason of the slowness.]

---

### Post by Josh1 on 2006-09-28
> **kitt said:**
> Hello everyone,
I installed Dapper (32bit) on my brand-new Acer notebook about 2 months back. Heres my machine config:
Acer Aspire 5004, AMD Turion 1.8 Ghz, 256 MB (shared) memory...out of this 220 is available..rest is for the video card. The motherboard has an SiS chipset, with the crappy sis-760 video card. 
I know the RAM is less..However, when i installed Ubuntu- i was quite impressed by my machine. I can say this because i can compare it with a machine with a higher config (2ghz, 1gb ram, IBM thinkpad)...and my acer ran ubuntu much faster. 
However, my machine has started to slow down..I have installed quite a few apps..too many to list here..but the major ones are Beagle, DrScheme, Swiftfox, Wine, etc. 
I now feel that my system has slowed down..a lot..and i dont think its due to the less RAM. Heres why:
I constantly monitor my CPU and Memory usage (using the gnome-applets) ..and for some strange reason, ubuntu now has started to work my processor really hard. Comparing between the past and present: earlier, during the launch of an application, CPU usage would peak for a very short time at around 20% .. but now...even when im not doing anything..it is 50%! and then all of a sudden it will go back to 0%...Similiarly, i find that programs take *much* longer to start.. It is also worth mentioning that th boot-time has increased by about 5 seconds ..earlier ubuntu booted-up in 50 seconds. Forget Multitasking, but even such simple tasks as using gedit (as im doing now) seem very sluggish..theres considerable lag in that too!
So, summing up: I am really disappointed..since one of the major reasons i wanted to use linux was because i had heard it doesnt degrade with time like windows. Has my ubuntu degraded? Can i repair it to make it as fast as when it was freshly installed? Does anyone know of any advanced process/memory monitoring tools using which i can single out the "bad" program? 
Thanks..

[PS: I use minimal eye-candy...wall-paper turned off etc...just in case you think thats the reason of the slowness.]

How many applications are running in the background?

---

### Post by darrenm on 2006-09-28
You're swapping to disk. When you install stuff that will also run a service more memory is taken up. My work PC has about 220MB free after shared VGA and if I run Apache/MySQL etc. then I start swapping.

Chuck an extra 256MB in there and you'll be fine.

---

### Post by kitt on 2006-09-28
Applications running in the background: Beagle. Thats it..nothing much.

---

### Post by darrenm on 2006-09-28
can you post ps -ef?

---

### Post by kitt on 2006-09-28
heres the output of ps -ef :
-------------------------------------------------------
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 17:21 ?        00:00:01 init [2]
root         2     1  0 17:21 ?        00:00:00 [migration/0]
root         3     1  0 17:21 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 17:21 ?        00:00:00 [watchdog/0]
root         5     1  0 17:21 ?        00:00:00 [events/0]
root         6     1  0 17:21 ?        00:00:00 [khelper]
root         7     1  0 17:21 ?        00:00:00 [kthread]
root         9     7  0 17:21 ?        00:00:00 [kblockd/0]
root        10     7  0 17:21 ?        00:00:00 [kacpid]
root       113     7  0 17:21 ?        00:00:00 [pdflush]
root       116     7  0 17:21 ?        00:00:00 [aio/0]
root       115     1  0 17:21 ?        00:00:00 [kswapd0]
root       704     7  0 17:21 ?        00:00:00 [kseriod]
root      1828     7  0 17:21 ?        00:00:00 [khubd]
root      1848     7  0 17:21 ?        00:00:00 [kacpid-work-0]
root      1964     1  0 17:21 ?        00:00:00 [kjournald]
root      2210     1  0 17:21 ?        00:00:00 /sbin/udevd --daemon
root      3021     1  0 17:21 ?        00:00:00 [shpchpd_event]
root      3043     1  0 17:21 ?        00:00:00 [pccardd]
root      3235     7  0 17:21 ?        00:00:00 [wrapper_wq]
root      3566     1  0 17:22 ?        00:00:00 [kjournald]
root      4141     1  0 17:22 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4261     1  0 17:22 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4263     1  0 17:22 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
root      4286     1  0 17:22 ?        00:00:00 /usr/sbin/gdm
root      4287  4286  0 17:22 ?        00:00:00 /usr/sbin/gdm
root      4290  4287 10 17:22 tty7     00:08:44 /usr/bin/X :0 -br -audit 0 -auth
hplip     4319     1  0 17:22 ?        00:00:00 /usr/sbin/hpiod
hplip     4323     1  0 17:22 ?        00:00:00 python /usr/sbin/hpssd
104       4376     1  0 17:22 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4391     1  0 17:22 ?        00:00:01 /usr/sbin/hald
root      4392  4391  0 17:22 ?        00:00:00 hald-runner
108       4397  4392  0 17:22 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4447  4392  0 17:22 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4457  4392  0 17:22 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4458  4392  0 17:22 ?        00:00:00 /usr/lib/hal/hald-addon-storage
prateek   4469  4287  0 17:22 ?        00:00:00 x-session-manager
root      4517     1  0 17:22 ?        00:00:00 /sbin/dhcdbd --system
prateek   4543  4469  0 17:22 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
root      4544     1  0 17:22 ?        00:00:00 /usr/sbin/NetworkManager --pid-f
root      4559     1  0 17:22 ?        00:00:00 /usr/sbin/NetworkManagerDispatch
prateek   4565     1  0 17:22 ?        00:00:00 /usr/bin/dbus-launch --exit-with
prateek   4573     1  0 17:22 ?        00:00:00 dbus-daemon --fork --print-pid 8
root      4603     1  0 17:22 ?        00:00:01 /usr/sbin/powernowd -q
prateek   4663     1  0 17:22 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
root      4672     1  0 17:22 ?        00:00:00 hcid: processing events
root      4676     1  0 17:22 ?        00:00:00 /usr/sbin/sdpd
root      4694     1  0 17:22 ?        00:00:00 [krfcommd]
root      4710     1  0 17:22 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
dhcp      4745  4517  0 17:22 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/d
daemon    4750     1  0 17:22 ?        00:00:00 /usr/sbin/atd
root      4763     1  0 17:22 ?        00:00:00 /usr/sbin/cron
root      4863     1  0 17:22 tty1     00:00:00 /sbin/getty 38400 tty1
root      4864     1  0 17:22 tty2     00:00:00 /sbin/getty 38400 tty2
root      4865     1  0 17:22 tty3     00:00:00 /sbin/getty 38400 tty3
root      4866     1  0 17:22 tty4     00:00:00 /sbin/getty 38400 tty4
root      4867     1  0 17:22 tty5     00:00:00 /sbin/getty 38400 tty5
root      4868     1  0 17:22 tty6     00:00:00 /sbin/getty 38400 tty6
prateek   4880     1  0 17:22 ?        00:00:00 /usr/bin/gnome-keyring-daemon
prateek   4882     1  0 17:22 ?        00:00:00 /usr/lib/bonobo-activation/bonob
prateek   4884     1  0 17:22 ?        00:00:02 /usr/lib/control-center/gnome-se
prateek   4891     1  0 17:22 ?        00:00:00 /usr/bin/esd -nobeeps
prateek   4920     1  0 17:22 ?        00:00:00 /usr/bin/esd -nobeeps
prateek   4931     1  0 17:22 ?        00:00:18 /usr/bin/metacity --sm-client-id
prateek   4940     1  0 17:22 ?        00:00:13 gnome-panel --sm-client-id defau
prateek   4942     1  0 17:22 ?        00:00:05 nautilus --no-default-window --s
prateek   4946     1  0 17:22 ?        00:00:00 gnome-volume-manager --sm-client
prateek   4955     1  0 17:22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
prateek   4963     1  0 17:22 ?        00:00:44 beagled --debug /usr/lib/beagle/
prateek   4969     1  0 17:22 ?        00:00:01 gnome-power-manager
prateek   4981     1  0 17:22 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
prateek   4989     1  0 17:22 ?        00:00:01 /usr/lib/gnome-panel/sensors-app
prateek   4991     1  0 17:22 ?        00:00:00 /usr/lib/gnome-applets/multiload
prateek   4993     1  0 17:22 ?        00:00:01 /usr/lib/gnome-applets/mixer_app
prateek   4998     1  0 17:22 ?        00:00:00 /usr/lib/gnome-panel/clock-apple
prateek   5002     1  0 17:22 ?        00:00:02 /usr/lib/gnome-netstatus/gnome-n
prateek   5012     1  0 17:22 ?        00:00:00 /bin/sh /usr/lib/swiftfox/swiftf
prateek   5016  5012  0 17:22 ?        00:00:00 /bin/sh /usr/lib/swiftfox/run-mo
prateek   5021  5016  3 17:22 ?        00:02:48 /usr/lib/swiftfox/swiftfox-bin
prateek   5035     1  0 17:22 ?        00:00:02 gnome-screensaver
dhcp      5051     1  0 17:23 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
prateek   5063     1  0 17:23 ?        00:00:00 /usr/lib/evolution/evolution-dat
prateek   5073     1  0 17:23 ?        00:00:00 /usr/lib/evolution/2.6/evolution
prateek   5105  4963  2 17:24 ?        00:01:49 beagled-helper --debug /usr/lib/
syslog    5367     1  0 17:29 ?        00:00:00 /sbin/syslogd -u syslog
prateek   5564     1  1 18:04 ?        00:00:38 /usr/bin/../lib/../bin/wine-prel
prateek   5567     1  0 18:04 ?        00:00:17 /usr/bin/../lib/../bin/wineserve
prateek   5570  5564  0 18:04 ?        00:00:00 /usr/bin/../lib/../bin/wine-prel
root      5883     7  0 18:41 ?        00:00:00 [pdflush]
prateek   5919     1  2 18:45 ?        00:00:00 gnome-terminal
prateek   5927  5919  0 18:45 ?        00:00:00 gnome-pty-helper
prateek   5928  5919  1 18:45 pts/0    00:00:00 bash
prateek   5948  5928  0 18:45 pts/0    00:00:00 ps -ef

--------------------------------------------------
Running swiftfox, wine, and terminal..

hope this helps.. :)

---

### Post by darrenm on 2006-09-28
yeah you're right, you don't run much.

what does top say your free memory is?

---

### Post by kitt on 2006-09-28
Heres what top outputs:
Mem:    222276k total,   220252k used,     2024k free,     1956k buffers
Swap:  2032180k total,    28988k used,  2003192k free,    56140k cached

I have also noticed that most of my cpu% is taken by Xorg...

---

### Post by darrenm on 2006-09-29
Yeah you're definitely swapping.

What driver are you using for X ? And are you using Xgl / AIGLX?

and if you reboot does it still take loads of CPU or is it only after being on for a while?

---

### Post by akshaysrinivasan on 2006-09-29
Well i found a trick.Now since you have some crappy old sis VGA ,i guess you wouldn't mind turning off dri ,mesa?I actually found a decrease of 40 MB in Memory consumption after doing this.
Here is the code:-
sudo /etc/init.d/gdm stop
(Don't copy and paste the command until you've finished reading this fully)

sudo dpkg-reconfigure xserver-xorg

In the configuration part turn off all the options in the xorg modules(space bar)Configure the others as usual.

sudo /etc/init.d/gdm start
 

Now you probably will find your system hogging less memory.You can't play games like tuxracer though!

---

### Post by kitt on 2006-09-29
> Yeah you're definitely swapping.

What driver are you using for X ? And are you using Xgl / AIGLX?

and if you reboot does it still take loads of CPU or is it only after being on for a while?

How do i know which driver i use? Whats the command for that..? I havent really changed anything much..mostly default settings.

And no, it doesnt take all the CPU all the time..its actually very chaotic..for example: sometimes even while text-editing..the cpu usage goes up like mad..
and contrasting this..now i am doing pretty heavy multitasking, and the cpu usage is very low, and machine is very resposive.

Im really confused :(

---

### Post by skymt on 2006-09-29
When the CPU use starts going up, open a terminal, run "top" and see what process is causing the trouble.

---

