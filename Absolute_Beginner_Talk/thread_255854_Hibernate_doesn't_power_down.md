---
title: "Hibernate doesn't power down"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by RobsterUK on 2006-09-12
When using the hibernate function, there is some HD activity then the monitor goes into standby, but after about 10 seconds the monitor comes back on with a password box.

When I log back in I get a system notification saying Hibernate has not worked and suggeting I check the Gnome power manager FAQ, which I did but it wasn't much help. Any ideas?

PS Ubuntu seems to work with my PCs power management as it automatically powers down when i do shut down.

---

### Post by xyz on 2006-09-12
I had some problems with this as well and this here got it to work for me.
Hope it helps:
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

---

### Post by RobsterUK on 2006-09-12
I'm not too sure about the instructions on that link, rebuilding the kernel sounds like something I shouldn't play with if I'm not sure what I'm doing.

Is there no automated patch I can download? btw I don't have a laptop if that makes any difference.

---

### Post by RobsterUK on 2006-09-12
bump

If someone could talk me through how to do this I would be grateful

---

### Post by xyz on 2006-09-12
Hi-
Try and run in a console:
```
hibernate -h
```
It explains lots of things! Check it out and try! Come back and ask if need be.

Also run:
```
 sudo gedit /etc/hibernate/hibernate.conf

```
You can use any editor you like instead of gedit.

Bits and pieces of it:
> Choose your Suspend method. You currently have 3 choices:
###
###    suspend2            Software Suspend 2 (requires kernel patches from
###                        [http://www.suspend2.net/](http://www.suspend2.net/))
###
###    sysfs_power_state   Uses /sys/power/state to suspend (activates pmdisk
###                        on kernels < 2.6.8, or vanilla swsusp otherwise).
###
###    acpi_sleep          Uses /proc/acpi/sleep to activate swsusp, or other
###                        ACPI sleep state supported by your machine.

Lots more there to find out!

Also go to */usr/share/doc/hibernate*
Click on "READ.Debian" and "README.gz"

See what you can find out and let us know.

Also go to [http://www.suspend2.net/](http://www.suspend2.net/)
to check on known bugs, latest patches,what kernel you need..

To find out what kernel you use, run
```
uname -r
```

---

### Post by RobsterUK on 2006-09-13
Ok I tried these various things. It seems that hibernate does not exist as a command and the directories and files you mentioned to not exist.

I'm guessing I need to install it?

---

### Post by xyz on 2006-09-13
Hi there,
When you click on System at the top of the screen and scroll down to "Quit" athen one click on it...do you have an 'hibernate icon' in the window that opens?

Clicking on it doesn't do anything, I guess?
Open Synaptic and 'Search' for "hibernate" and see what it says.
Good luck

---

### Post by RobsterUK on 2006-09-13
I have the icon but when I click on it the result is as per my first post.

I've now checked in synaptic, and hibernate wasn't installed. Having installed it the result is the same. I'll try your command line suggestions again.

What I'm expecting to happen is that the the computer turns itself off, and when I switch the system on again its in the same state with all the programs I had open....am I expecting too much?

---

### Post by xyz on 2006-09-13
That's what it's supposed to do!!

What does it say...the first few lines...in
```
sudo gedit /etc/default/acpi-support
```

---

### Post by RobsterUK on 2006-09-13
acpi-support says this:
> # Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

---

### Post by xyz on 2006-09-13
Again in Synaptic, I found "kpowersave"
which does, among other things...
* trigger suspend to disk/ram and standby

---

### Post by xyz on 2006-09-13
Also in a console: (as root)
```
root@luser:~# man
What manual page do you want?
root@luser:~# hibernate

```

This will reveal whether or not you have  Software Suspend 2 support compiled in. If not, follow the instruction on how to compile Software Suspend into your kernel.
What is your kernel version? Type:
```
uname -r
```
My kernel: 2.6.15-26-386
No problems with hibernate.

Also type:
```
man hibernate
```

---

### Post by RobsterUK on 2006-09-13
> Your kernel does not appear to have Software Suspend 2 support compiled in.
Please follow the HOWTO linked from [http://www.suspend2.net/](http://www.suspend2.net/) for instructions
on how to compile Software Suspend into your kernel.
hibernate: Aborting.

Kernel version
2.6.15-26-386

---

### Post by xyz on 2006-09-13
Try using the hibernate attachement.deb
HowTo .deb:
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

I tried uploading the **hibernate_1.12-1ubuntu1_all.deb** which you may need but it didn't work! Can't upload .debfiles. Sorry.

Just to change conversation for a while, how's the weather where you live?

---

### Post by xyz on 2006-09-13
To download it here:
[http://packages.ubuntu.com/dapper/utils/hibernate](http://packages.ubuntu.com/dapper/utils/hibernate)
or again here for the latest hibernate script:
[http://www.suspend2.net/](http://www.suspend2.net/)
Look for: "Latest hibernate script"

---

