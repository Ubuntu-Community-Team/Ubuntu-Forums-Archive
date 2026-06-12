---
title: "wifi setup"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by waldick on 2006-01-05
Hi, 
trying to set up the wifi card in my laptop (hp pavilion) checked the win driver and its the broadcom chipset...instelled ndis wrapper and appropriate broadcom driver...when i type in "sudo modprobe ndiswrapper" i get this: 

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
x@ubuntulaptop:~$ "

i have read the other posts but can't seem to find the problem...

when i type: "sudo ndiswrapper -l" i get "Installed ndis drivers:
bcmwl5  invalid driver!"

any help would be appreciated...

j

---

### Post by Zelut on 2006-01-05
Sounds like you don't have quite the right driver.  It is not always the driver from your install CD or always the one you would expect.  I have a linksys card here that works best using a Realtek driver.

give this wiki a read-thru and give it another try..

[http://wiki.ubuntu.com/forum/hardware/ndiswrapper](http://wiki.ubuntu.com/forum/hardware/ndiswrapper)

---

### Post by byen on 2006-01-06
ok. i have a compaq Presario laptop and we pretty much have the same configuration.. To configure and install your Broadcom drivers..i strongly suggest you check this link out. If you have any problems post your questions there or here. Hope this helps.
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by waldick on 2006-01-06
hi,

i did exactly what both the above threads indicate, and since i am using a dual boot machine, i am using the driver that xp uses when i boot up under xp...although, i could only find the .sys driver on the xp portion of the drive and i had to download the .inf portion from the web...i couldn't find even fin the .inf file searching the entire c drive...although i did find the xp setup file for the broadcom chipset with all kinds of other files...

what do i do next ?

---

### Post by waldick on 2006-01-07
ok, i copied all of my steps below...where did i go wrong, all the drivers are on my desktop...

```
juergen@ubuntulaptop:~$ sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.
juergen@ubuntulaptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
juergen@ubuntulaptop:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndisgtk ndiswrapper-utils
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 238kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
juergen@ubuntulaptop:~$
juergen@ubuntulaptop:~$
juergen@ubuntulaptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
juergen@ubuntulaptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
juergen@ubuntulaptop:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

juergen@ubuntulaptop:~$ sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
bash: /etc/ndiswrapper/bcmwl5/*.conf: Permission denied
juergen@ubuntulaptop:~$
juergen@ubuntulaptop:~$
juergen@ubuntulaptop:~$
juergen@ubuntulaptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
juergen@ubuntulaptop:~$ 
```


this is the thread i followed : [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

i pretty much at wits end at this point and would appreciate any and all help...

j

---

### Post by waldick on 2006-01-07
ok, uninstalled all the drivers and re-installed all...made sure nothing was left behind, anyway when i entered "sudo modprobe ndiswrapper" the wifi light came on, i configure the card, it works....yeah.

now however, i have to "modprobe" every time i reboot, tried this:

"Step Five is making this automatically load at boot-time
If everyting works, you need to tell your system to load the module on boot. Two ways you can do this are: 
$sudo ndiswrapper -m

or 
$sudo gedit /etc/modules

add the word 'ndiswrapper' to the end of this file"

added the  "-m", but no luck, and if i try to edit the modules file, get an error message telling me i don't have permission...

help...

j

---

### Post by Zelut on 2006-01-07
It sounds like you're working from my wiki so maybe I can help you...

sudo ndiswrapper -m

should say 'adding modules to...' or 'modules already loaded.  Is this not the case?  What does it say when you use this command?

I just rechecked my /etc/modules file and I actually DONT have the 'ndiswrapper' entry in there.  I have always used the ndiswrapper -m command to get it to load at boot time.

Note: sometimes, for whatever reason, you need a full shutdown for the wireless to come back on at boot.  A simple restart may not always work.  Try this for another option after using the ndiswrapper -m and see if it makes a difference.

---

### Post by waldick on 2006-01-07
yep, -m returns "modprobe config already contains alias directive" 
when i re-boot, it hangs on "configuring network interfaces" and the next entry, so i have to control-c around them.
then i need to modprobe and re-enable the wifi card ...

plus, for some reason the system locks up after 5 or so minutes...only way to re-boot is to pull the battery...

very strange...

but i still can't edit the modules file...

thanks for your help,

j

---

### Post by adssse on 2006-01-08
By any chance is it trying to connect using your ethernet connection eth0 when starting up?

---

### Post by waldick on 2006-01-08
yes, because when i set up the laptop that was the only way i could get to the net....

do i need to disable that somehow, if so how ?

thanks 

j

---

### Post by Zelut on 2006-01-08
Well to edit the modules file you'll want to use:

sudo gedit /etc/modules (sudo giving you the permissions...)

I wonder if you aren't using quite the right driver.  Drivers can be very specific in linux.  Have you tried any others?  Might be worth a shot to avoid that random lockup issue.

---

### Post by adssse on 2006-01-08
I believe you can try by typing 'ifdown eth0', not for sure if it will help but its worth a try.

---

