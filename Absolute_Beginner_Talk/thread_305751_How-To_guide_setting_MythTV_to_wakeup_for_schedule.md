---
title: "How-To guide: setting MythTV to wakeup for scheduled recordings with nvram-wakeup"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by piec2 on 2006-11-23
I am a newbie to Ubuntu and MythTV and if like me you want your MythTV box to be able to shutdown while not in use and wakeup automatically when it's time to record a show, then this thread is for you.

A large part of this How-To was inspired from the excellent guide written for KnoppMyth ([http://knoppmythwiki.org/index.php?page=WakeupToRecordWithMythWelcome](http://knoppmythwiki.org/index.php?page=WakeupToRecordWithMythWelcome))
A big thank you to the people who wrote it.

STEP 1.
Before going forward, it's good to have handy a bootable linux CD, such as [http://www.sysresccd.org](http://www.sysresccd.org) just in case.
You probably won't need it, but it's always a good thing to be safe.
Also have your motherboard manual at hand: it may come in handy.

STEP 2.
First set is to make sure the option "Power on by RTC Alarm" is enabled in your BIOS. It may be called slightly differently in your particular BIOS, but essentially it allows your motherboard to wakeup to a real-time clock event.
If it's not set, this how-to won't work.

STEP 3.
Next, install in Ubuntu the nvram-wakeup using Synaptics (or use: sudo apt-get install nvram-wakeup)
You must now find the correct settings from your motherboard.  READ THE MAN PAGES.
Run the following command to see if your motherboard is supported. Don't worry, this won't write anything to your BIOS yet:
nvram-wakeup -A

If you motherboard is supported, nvram-wakeup will tell you and you will not have to create manually the /etc/nvram-wakeup.conf file with the process explained below. However the list of supported motherboard is not very exhaustive.
If your motherboard is supported, skip to Step 5.

STEP 4.
If nvram-wakeup reports that your motherboard is not supported, read the man pages and search the internet for the keywords "nvram-wakeup" +"your-motherboard-model".
You can also use the utility provided with nvram-wakeup, which is called guess-helper
However be aware that guess-helper does not always return accurate information (it did not for my motherboard). It was a good start for me, but I found my exact settings on a web site.
Make sure you get the correct config for you motherboard, otherwise YOU COULD DESTROY YOUR BIOS, thereby rendering your 
motherboard useless and unrecoverable (it becomes an expensive freesbie as they say).

Save your motherboard settings in /etc/nvram-wakeup.conf

STEP 5.
A lot of motherboards require a reboot after setting the wakeup time in the BIOS. If your motherboard does not require a reboot, you can skip to Step 6.

If yout motherboard requires a reboot, edit the Grub config file (it's always a good idea to make a backup copy of it beforehand):
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk
sudo vi /boot/grub/menu.lst

Look for an entry that reads:
default 	0

If the "default" entry does NOT read '0', then please take note of the number, since you will need it later.
Comment this line out and enter a new line that reads: 
default 	saved

Add the end of menu.lst add the following lines. If your previous "default" entry was not '0' then use the default number you had instead of '0'. 
title           PowerOff
savedefault 0
cat /boot/grub/default
halt

Now you need to figure out which menu entry this represents in menu.lst, by counting from the first "title" line you see.
Menu entries start at 0 and you first entry probably reads like:
title 	Ubuntu, kernel 2.6.17-10-generic

For the sake of this example, we will assume the new PowerOff menu entry is entry number 3 (i.e. it's the fourth one in the list).

STEP 6.
It's now time to try it out manually.
Run the following command which will set your machine to reboot in 15 minutes. Note: only use the "-C /etc/nvram-wakeup.conf" if your motherboard was not supported and you created a config file for nvram-wakeup during Step 4:
sudo nvram-wakeup -A -C /etc/nvram-wakeup.conf -s $((`date +%s` + 900))

If nvram-wakeup says that you need a reboot, then you will need to invoke your special PowerOff entry you just added at Step 4. This will reboot your machine, then power it off right afterwards. This allows the wake-up time to be recorded in the BIOS.
Here's the command (assuming our PowerOff entry in menu.lst is the fourth entry):
sudo grub-set-default 3 ; sudo /sbin/reboot

The system should reboot and then immediately shutdown again. 

If your motherboard deosn't need rebooting after the wake-up time is set, you can simply do:
sudo /sbin/poweroff

No wait 15 minutes (900 seconds) and the computer should then wakeup and boot normally.
Congratulations!  You've just proven that your wake-up feature works nicely.
If somethings goes wrong, see the "Troubleshooting" section below.

STEP 7.
Now let's setup MythWelcome and MythTv to use your nvram-wakeup setup.
Type the following to start the MythWelcome configuration:
mythwelcome --setup

If your motherboard requires a reboot, edit the settings so they look like this (MythTV 0.20):
nvram-wakeup Command: sudo /usr/sbin/nvram-wakeup -A -C /etc/nvram-wakeup.conf 
nvram-wakeup Restart Command: sudo /sbin/grub-set-default 3
Command to reboot: /sbin/reboot
Command to shutdown: /sbin/poweroff
Command to run Xterm: xterm
Command to run to start the Frontend: /usr/bin/mythfrontend

If your motherboard does not require a reboot, edit the settings so they look like this (MythTV 0.20):
nvram-wakeup Command: sudo /usr/sbin/nvram-wakeup -A -C /etc/nvram-wakeup.conf 
nvram-wakeup Restart Command: <leave blank>
Command to reboot: /sbin/poweroff
Command to shutdown: /sbin/poweroff
Command to run Xterm: xterm
Command to run to start the Frontend: /usr/bin/mythfrontend


STEP 8.
Run mythtv-setup. Go to General and the Shutdown/Wakeup Options screen and set the following: 

Startup command: <leave blank>
Block shutdown before client connected: checked
Idle timeout (secs): 30
Max wait for recording (min): 15 <= or whatever you prefer
Startup before rec. (secs): 300
Wakeup time format: yyyy-MM-ddThh:mm
Set wakeuptime command: sudo mythshutdown --setwakeup $time
Server halt command: sudo mythshutdown --shutdown
Pre Shutdown check-command: sudo mythshutdown --check


IMPORTANT:
You might want to set "Idle Timeout" to something higher to test first... otherwise the system might go into a reboot loop with only 30 seconds for you to stop it. What this does is that when you exit MythTV Front-end then MythWelcome will run. If MythTV is not recording anything (i.e. it's sitting idle) then after 30 seconds the machine will shutdown.
MythWelcome will indicate the countdown on it's screen.
Once you feel at ease with your setup, you can set it to any other value you want, but 60 seconds is probably fine.
Setting it to zero disables it, so the machine will never shutdown my itself.


Note: the knoppmyth-preshutdown command will be called every "idle timeout" seconds. The shorter the idle time, the more often the script is called, but the quicker the machine will shutdown after going idle. 


STEP 9.
Give the mythtv user access to nvram-wakeup and grub-set-default. To do so, type:
sudo vi /etc/sudoers <= or whathever your favorite text editor here instead of vi 

Add a line at the end:
mythtv ALL=NOPASSWD:/usr/sbin/nvram-wakeup,/sbin/grub-set-default,/usr/bin/mythshutdown,/sbin/halt,/sbin/reboot,


STEP 10.
Almost done!  Now that everything is setup, you will want to start mythwelcome rather than MythTV when the system does auto-login.
If you followed the MythTV installation instructions found in [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) then what you need to do is edit /usr/local/bin/mythtv.sh and replace the "mythfrontend&" with "mythwelcome&"


STEP 11.
Enjoy ! 

Note that for the wakeup time to be set correctly, you must always shut down the computer by exiting the frontend and letting the backend complete the shutdown. 

If ever you started mythwelcome manually and you are trying to figure out how to get out of it, hit 'm' on your keyboard. It displays a pop-up menu that allows you to exit. For more info, see the mythwelcome documentation on the MythTV.org wiki.



Troubleshooting:
================
* You set the wake-up time with nvram-wakeup, but your machine does not wakeup.
- make sure you enabled the "Power on RTC alarm" feature in your BIOS (refer to your motherboard manual)
- your motherboard may require rebooting after setting the wakeup time, so please refer to the instructions above
- if your motherboard requires a reboot after setting the wakup time, make sure that you have set "default saved" in your /etc/boot/menu.lst file.

* Your machine won't even POST (i.e. the BIOS messages don't even appear when booting)
- well, I did not experienced this myself, so I assume this is what would occur if you trashed your BIOS because you entered inccorect values in your /etc/nvram-wakeup.conf
Some motherboard manufacturer have a way to restore the BIOS (either automatically or through manual steps). Refer to your motherboard manufacturer's web site or your motherboard manual. 
But be aware that a lot of motherboard manufacturer don't have a way to recover from a corrupted BIOS and nvram-wakeup may just have created a very expensive freesbie for you...

* You set the wake-up time with nvram-wakeup, but your machine does not wakeup.
- make sure you enabled the RTC wakeup feature in your BIOS (refer to your motherboard manual)
- your motherboard may require rebooting after setting the wakeup time, so please refer to the instructions above

* Something is terribly wrong with the booting (boot to wrong entry, etc.)
If you can get to a boot prompt, then simply go back to your /boot/grub/menu.lst file and check it fully against the instructions above.
It may be that your "savedefault " entry in the PowerOff does not refer to the proper entry number (remember they are numbered starting from zero).

If you cannot get to a boot prompt, then grab your bootable linux CD (such as SystemRescueCd [http://www.sysresccd.org](http://www.sysresccd.org)) and boot from it.
Then mount your hard disk with a command such as:
mkdir /mnt/hda1
mount /dev/hda1 /mnt/hda1

Now go back to look at the steps previously describes on how to edit the /mnt/hda1/boot/grub/menu.lst
There's probably error in there or you forgot something. If you cannot find it, then simply revert your menu.lst to what it was before, then reboot.

---

### Post by piec2 on 2006-11-24
I realized I made a mistake after posting this :( 

At step 7: you shoud use "sudo" for the /sbin/poweroff and /sbin/reboot as well.

At step 9: you must also add /sbin/poweroff at the end of the sudoers line indicated (so it ends with "/sbin/reboot,/sbin/poweroff"

I also figured out that nvram-wakeup will by default wakeup 5 minutes earlier than any time you set it for. However since you already set "Startup before rec." time at step 8, this means that it will wake up earlier than you thought.
To avoid this, you can add the option "-w 0" to the nvram-wakeup command line at step 7.

That will work fine.

---

### Post by Roebi on 2007-01-25
Thank you for the excellent guide.

Just one remark.
You write:
> **piec2 said:**
> 
STEP 5.
Add the end of menu.lst add the following lines. If your previous "default" entry was not '0' then use the default number you had instead of '0'. 
title           PowerOff
savedefault 0
cat /boot/grub/default
halt


If you have created a seperate partition for /boot, the cat command should state:
cat /grub/default

That's it.


Roebi

---

