---
title: "Fan control script"
date: 2009-03-21
forum: Apple Hardware Users
---

### Post by Joushou on 2009-03-21
I've been having a really hot laptop in ubuntu, like i had in OS X before i installed fan-control.
I looked around the net, and figured i wasn't alone, but i could only find 1 script (SantaRosaFanControl i believe), which i didn't quite like...

So, i wrote my own, which also counts fans and sensors by itself, so it should work on anything that the applesmc module supports :)
All settings are in the top (min/max fan-speeds, min/max temp, so forth), though i wouldn't suggest setting the manFanControl flag to true... if applesmc wants the fans to spin, it probably have a good reason ;)

It's probably not the prettiest thing in the world (haven't been scripting in a while...), but i hope someone will have use of it :)

By the way, is there anyone who knows which sensor is which on MBP3.1?

Anyway, enjoy :)

Description:
This script is designed to automatically recognize fans and sensors on any Apple computer that uses the applesmc kernel module for fans and temperature sensors.
It will also take temperature-input from the coretemp kernel-module if loaded.
It might be very buggy, though!

So far, i'm aware of successful use on various MacBook Pro's and MacBook's...

Changelog:```

0.1: First version
0.2: Added fatal function, and the debugTo variable
0.2.1: Zipped it with an init and install script
0.2.2, Install script now starts smcfancontrol after install
0.3: Added cornelius2's coretemp/gradual-update-patch, and included a readme, together with a simple fix for the random suicides...
0.3.1: Typo...
0.3.2: Fix potential non-laptop bug
```

Sorry for the lack of interest in my script, but i'm not using Ubuntu as heavily as i used to (Actually, i screwed up GRUB when i installed Snow Leopard, so i haven't booted it in a while ;) )
UPDATE: I installed Karmic on top of my old install, so i'm up and running on Ubuntu again! But now i'm screwed, 'cause i lost my custom keymap 'n stuff... D': (The DK-Mac keymap is actually just the usual DK map, which doesn't work well on a Mac keyboard...)

---

### Post by sands on 2009-03-27
Thanks for sharing the script. :)

Are those the actual max and min temperatures in the script??

I started the script and it started with max fan speed... and it never goes to lower speed.

Mine is macbook 3,1

I guess I need to tweak the values.

These are my current temperatures from libsensors applet
temp1 - 27
2 - 37
3 - 36
4- 43
5-37
6- 65
7-51
8 - 36
9 - 36
10 - 36

---

### Post by Joushou on 2009-03-27
Well, i'm glad someone wanted to use it! :D

Min and max temperature values set when it should stop cooling, and when it should prepare for take-off (Full-speed).

If you copy-pasted this script, it should run fine... thats the exact copy of my currently running script... and thats on my MBP3,1 :)

What temperatures is it reading when it goes to max fan-speed? Paste a couple of debug lines where it's at max-speed with a too low temperature, and if you changed the values at the top, give me them aswell, so i can see whats going wrong :)

---

### Post by sands on 2009-03-27
Output:

sudo ./fan.sh 
27/03 03:27:30: Fans: 1 
27/03 03:27:30:   Min fan-speed: 2000
27/03 03:27:30:   Max fan-speed: 5000
27/03 03:27:30: Sensors: 10
27/03 03:27:30:   Limited by user to 6
27/03 03:27:30: Laptop: true
27/03 03:27:30:    ACPI-State: online
27/03 03:27:30: Temperature: 65, Fan-speed: 5000, ACPI-State: online


temps are almost the same as in the above post.
I didn;t chage any values in the script.. [edit]oops, I changed 6000 to 5000[/edit]

By the way, I like your signature. Who said that?

---

### Post by Joushou on 2009-03-27
Thanks, it's just one i liked from bash.org... can't remember who it was, i saw it 2-3 months ago or something  (For some reason, i got static quote memory, while i can't remember time at all )

To fix your problem, set "sensorsUsed" to 4 or 5. Your sensor 6 seems to be as hot as my sensor 7 (Which is why i implemented the sensor limit... so it wouldn't have to run at 6000RPM always :)).
"sensorsUsed" limits the number of sensors to use, 6 means it would use sensor 1-6... and your sensor 6 is always hot, so it will run at max speed.

You could also change it to use the "average" temperature calculation, but i prefer my "highest" calculation (Takes the highest temperature, so no components get too hot... with average, 1 sensor could be 20 degrees, while another could be 80... then it would cool as if it was 50 degrees, and the second component could maybe be damaged).

Changing fanMaxSpeed to 5000 is OK... Just don't put it too low, or the script won't give much cooling :)

I have just changed sensorsUsed to be 5 in the first post, so we won't have that problem again with macbooks :)

---

### Post by sands on 2009-03-27
Thanks. It is working now. :)

I added a link to this page in Arch Linux wiki - macbook

[http://wiki.archlinux.org/index.php/MacBook#Fan_Speed](http://wiki.archlinux.org/index.php/MacBook#Fan_Speed)

---

### Post by hellmitre on 2009-03-28
Am I correct in assuming I should make it executable and copy it to /init.d/ to be run at boot with update-rc.d?

---

### Post by sands on 2009-03-28
I added it to rc.local

---

### Post by Joushou on 2009-03-28
@sands: Good, then arch-users can enjoy the fruits of my bashfu... or something :D


@hellmitre: Well, it would work for starting it, but when it attempts to stop it, it would be started again instead of killed.

I've just zipped the script with a modified version of "fancontrol"s (PWM-fan controller) init-script, and an installer script.
Remember to run the installer script as root, or it will yell at you.

---

### Post by hellmitre on 2009-03-28
I think you left out a $ in one of the last lines of the script, as well as an 's' at the end of defaults:
```
update-rc.d $initscript default**s** **$[B]**[/B]scriptrlevel || fatal "Failed to install rc-scripts"
```
When I ran the script as root, it told me that it failed to install the rc-scripts. I added the $ to scriptrlevel and it ran.

---

### Post by Joushou on 2009-03-28
> **hellmitre said:**
> I think you left out a $ in one of the last lines of the script, as well as an 's' at the end of defaults:
```
update-rc.d $initscript default**s** **$[B]**[/B]scriptrlevel || fatal "Failed to install rc-scripts"
```
When I ran the script as root, it told me that it failed to install the rc-scripts. I added the $ to scriptrlevel and it ran.

Yeah, i forgot, i never tested the install script... i just fixed it :)
I was toying around with the rc script too late at night, so i accidently wrote "rm -rf rc*.d smcfancontrol" instead of "rm -rf rc*.d/smcfancontrol"... i wrote the install script after i had reinstalled all the rc script, so i was a bit tired ;)

Anyway, thanks for telling me :)

---

### Post by sands on 2009-04-26
Hi Joushou, 

Sometimes the script dies after running for a long time for some reason. 
Sometimes it happens after I wake up my computer from suspend.
I added it to my rc.local, and am not using it as a daemon. Is it because of that?

I am using it on Arch linux.

Does any of you know if this fan speed bug got solved in the latest versions of the kernel?

Thanks.

---

### Post by Joushou on 2009-04-26
What fan speed bug? The not-so-great fan-speed-control is not a bug ;)

But back to my script:
Does it die after a certain amount of time, or is it random (Try to run it manually with "sudo time /usr/local/sbin/smcfancontrol", it will time how long it runs)?
Do the logs say anything? (It will print if it failed to read sensors or set fans to /var/log/smcfancontrol.log, and to stderr)
Running it as a daemon makes no difference, it's just a bash script afterall...

Anyway, if you could tell me if the logs give any info, it would help finding the problem alot :)
I'll look at the script again, and see if i left something stupid in it...

---

### Post by sands on 2009-04-26
```
26/04 00:16:34: Detecting configuration
26/04 00:16:34:   Fans: 1 
26/04 00:16:34:     Min fan-speed: 2000
26/04 00:16:34:     Max fan-speed: 6000
26/04 00:16:34:   Sensors: 10
26/04 00:16:34:     Limited by user to 4
26/04 00:16:34:   Laptop: true
26/04 00:16:34:     ACPI-State: online
26/04 00:16:34: Configuration detected
26/04 00:16:34: Temperature: 53, Fan-speed: 5404, ACPI-State: online
26/04 00:16:55: Temperature: 52, Fan-speed: 5256, ACPI-State: online
26/04 00:18:05: Temperature: 51, Fan-speed: 5108, ACPI-State: online
26/04 00:19:21: Temperature: 50, Fan-speed: 4960, ACPI-State: online
26/04 00:20:37: Temperature: 49, Fan-speed: 4812, ACPI-State: online
26/04 00:23:54: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:24:19: Temperature: 49, Fan-speed: 4812, ACPI-State: online
26/04 00:24:24: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:28:32: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:30:48: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:31:03: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:31:13: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:34:41: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:34:46: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:34:51: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:34:56: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:35:06: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:35:26: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:35:36: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:35:41: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:35:51: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:35:56: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:36:07: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:36:12: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:36:17: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:36:27: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 00:36:37: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 00:38:38: Temperature: 46, Fan-speed: 4368, ACPI-State: online
26/04 00:40:04: Temperature: 45, Fan-speed: 4220, ACPI-State: online
26/04 00:42:25: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:42:30: Temperature: 45, Fan-speed: 4220, ACPI-State: online
26/04 00:42:41: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:55:43: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:55:48: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:56:04: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:56:09: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:56:14: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:56:19: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:56:29: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:56:34: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:56:44: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:56:49: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:56:54: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:56:59: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:57:14: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:57:29: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:57:45: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:57:50: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:57:55: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:58:00: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:58:50: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 00:59:00: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 00:59:10: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 01:00:46: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 01:00:56: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 01:01:02: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 01:01:07: Temperature: 43, Fan-speed: 3924, ACPI-State: online
26/04 01:01:12: Temperature: 44, Fan-speed: 4072, ACPI-State: online
26/04 01:05:35: Temperature: 45, Fan-speed: 4220, ACPI-State: online
26/04 01:05:45: Temperature: 46, Fan-speed: 4368, ACPI-State: online
26/04 01:05:50: Temperature: 45, Fan-speed: 4220, ACPI-State: online
26/04 01:07:16: Temperature: 46, Fan-speed: 4368, ACPI-State: online
26/04 01:07:21: Temperature: 45, Fan-speed: 4220, ACPI-State: online
26/04 01:07:26: Temperature: 46, Fan-speed: 4368, ACPI-State: online
26/04 01:08:42: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 01:08:57: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 01:09:02: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 01:10:34: Temperature: 51, Fan-speed: 5108, ACPI-State: online
26/04 01:10:39: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 01:10:49: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 01:12:05: Temperature: 56, Fan-speed: 5848, ACPI-State: online
26/04 01:12:10: Temperature: 51, Fan-speed: 5108, ACPI-State: online
26/04 01:12:15: Temperature: 50, Fan-speed: 4960, ACPI-State: online
26/04 01:12:20: Temperature: 49, Fan-speed: 4812, ACPI-State: online
26/04 01:12:25: Temperature: 54, Fan-speed: 5552, ACPI-State: online
26/04 01:12:30: Temperature: 52, Fan-speed: 5256, ACPI-State: online
26/04 01:12:35: Temperature: 50, Fan-speed: 4960, ACPI-State: online
26/04 01:12:45: Temperature: 49, Fan-speed: 4812, ACPI-State: online
26/04 01:12:56: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 01:13:01: Temperature: 47, Fan-speed: 4516, ACPI-State: online
26/04 01:14:27: Temperature: 48, Fan-speed: 4664, ACPI-State: online
26/04 01:17:34: FATAL: Failing at: 
26/04 01:17:34: Attempting to set fans to safe values
26/04 01:17:34: Commit suicide. Bye.
```

This is the log. I am running it manually after it crashes.. :p
What is this bug related to :-?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550)

---

### Post by Joushou on 2009-05-05
Okay, now i know why, sometimes it seems that you can't read the sensors (no idea why that happens though, seems random)
Quick fix is to just comment out the contents of the fatal-function.
I'm gonna rewrite the fatal-function to retry the commands 3-5 times, waiting something like 5 secs in between, but it actually requires me to do some thinking, and as you might have noticed, that's not something i'm used to ;)

Oh, and you meant the serious heating was a bug? thought you meant the non-existing fan-control :P

---

### Post by cyberdork33 on 2009-05-05
> **Joushou said:**
> Oh, and you meant the serious heating was a bug? thought you meant the non-existing fan-control :P
I think the bug covers both aspects of this.

---

### Post by sands on 2009-05-06
Thanks, I will do that for now and will wait for your bashfu.

---

### Post by slackerprimer on 2009-05-12
Excellent catch hellmitre. Thanks for that!

---

### Post by tiagobt on 2009-05-12
The install script is still missing an "s" on line 40:
```
update-rc.d $initscript default[COLOR="Red"]**s**[/COLOR] $scriptrlevel || fatal "Failed to install rc-scripts"
```

Other than that, the script seems to work well on my MacBook 2,1.

I'm just curious, what difference does it make to change the number of sensors used? Why is the default 4?

Thanks,
Tiago

---

### Post by cornelius2 on 2009-05-13
Thanks a lot Joushou for the great script and others for the corrections!
One more annoyance eliminated :)

Here is a patch to make the change to the fan speed gradual (you can make the change as slow as you want), to add support for coretemp sensors, and to fix the typo in install. The first sensors in the array are used for coretemp (CPU) sensors, so when you set sensorsUsed=2 on a dual core machine, you'll be using only CPU sensors. You can apply the patch by: ```
gunzip gradual-change-and-coretemp-support.patch.gz
cd smcfancontrol
patch -p1 <../gradual-change-and-coretemp-support.patch
```

---

### Post by tiagobt on 2009-05-13
Thanks, cornelius2! I'm using your patch now. The gradual change seems to work well.

So there's no point in setting sensorsUsed greater than 2 in a dual-core machine, right? (At least if you consider that the CPU sensors are the only useful ones for the script.)

Tiago

---

### Post by cornelius2 on 2009-05-15
> **tiagobt said:**
> So there's no point in setting sensorsUsed greater than 2 in a dual-core machine, right? (At least if you consider that the CPU sensors are the only useful ones for the script.)

Well, the CPU temperature seems to rise and drop very quickly. Therefore, some of the appleSMC sensors may reflect the temperature you feel under your palms better (which changes more slowly). So, using a few appleSMC sensors (though I don't know which one is which) in addition to CPU sensors to set the fan speed might not be a bad idea.

---

### Post by tiagobt on 2009-05-15
I've made some experiments and I've noticed a big difference using 2 or 4 sensors.

If I use 2 sensors, the temperature reported in the log is around 25-30 degrees, and the fan speed is very low (2000 rpm).

If I use 4 sensors, the temperature reported in the log is around 50-56 degrees, and the fan speed is around 4800-5000 rpm.

The temperatures measured with 4 sensors look more realistic to me. I'd say using 4 sensors is safer. What do you think?

---

### Post by cornelius2 on 2009-05-16
I think both are safe enough. Laptops are just designed such that some part will be warmer (and will tolerate more heat) than other parts. Also, you're not limited to only tweaking that parameter, you can play with the other parameters there too. Though, at the end your parameter choices will come down to which one of these you prefer: heat or fan noise.

---

### Post by cyberdork33 on 2009-05-16
the default speed for my macbook pro in OS X is about 2000 rpms, and I force it up when plugged into an external power source.

---

### Post by MattFinck21 on 2009-06-03
wow, i just realized you have to cd into the "smcfancontrol" folder, then execute the install script...i also added the "s" on this line.. update-rc.d $initscript default**s**[/B] $scriptrlevel || fatal "Failed to install rc-scripts"

---

### Post by Joushou on 2009-07-28
It *should* work OK now...

---

### Post by WillJeffery on 2009-07-28
> **Joushou said:**
> when i installed Snow Leopard

Apologies for going off-topic, buy how do you have Snow Leopard? Are you an Apple dev? Torrent?

---

### Post by Joushou on 2009-07-29
If you an Apple Premium/Select member, you get access to their developer seeds. You can also receive a download-ticket from someone with such account, and get access to it with a free account (They got a certain amount of tickets to share).

Not that i have Premium/Select membership, nor a ticket... ;) (Yeah, it was a torrent... After buying my Segway, i didn't have $3499 left for the membership, but i swear i'm going to buy the release!)

---

### Post by amd-64 on 2009-08-19
this excellent script still quits sometimes. As a workaround I scheduled a cron job to restart it every 4 minutes. Now lappy is nice and cool. 


I added the following line to /etc/crontab

*/4    *   * * *   root    pkill smcfancontrol && /etc/init.d/smcfancontrol.sh start

---

### Post by Nikos.Alexandris on 2009-09-09
> **Joushou said:**
> 
...
UPDATE: Install script now starts smcfancontrol after install
...



Hi! Thanks for the script. I have the following questions:

 * Anybody tried this on a MBP5,1?
 * How do you "cleanly" uninstall it?

Regards, Nikos

---

### Post by Nikos.Alexandris on 2009-09-09
> **Nikos.Alexandris said:**
> Hi! Thanks for the script. I have the following questions:

 * Anybody tried this on a MBP5,1?
 * How do you "cleanly" uninstall it?

Regards, Nikos

I am not able to run the script!

Is it the smcfancontrol or the (shell script) smcfancontrol.sh that has to be ran? Running the shell script does not output anything. Running the smcfancontrol like:```
sudo ./smcfancontrol
``` I get ```
./smcfancontrol: line 109: *online=true: command not found
```

**UPDATE:** I just had a look. This is checking for battery which is not in its place on my system. I use AC always while at home. I'll comment it out and see whether it works or not.
**UPDATE 2:** Nothing happens. The error message is away but it just waits and waits...

(shrug!) So I break it with Ctrl+C. Any help?

---

### Post by amd-64 on 2009-09-10
Try running as

sudo /etc/init.d/smcfancontrol.sh start 

Before you do so, you should change sensorsUsed=2  to sensorsUsed=25 or so. You basically need to monitor GPU temperature, and it is way down the list of sensors.  The default is to monitor the CPU temperature which is not as high as the GPU.   

To uninstall,  I think deleting the two files /etc/init.d/smcfancontrol and /usr/local/sbin/smcfancontrol.sh and deleting the links under all the run levels rc0.d, rc1.d, etc,  should do it.

**Joushou**, you did a very good job with this script, thanks.

---

### Post by Nikos.Alexandris on 2009-09-10
> **amd-64 said:**
> Try running as

sudo /etc/init.d/smcfancontrol.sh start 

Before you do so, you should change sensorsUsed=2  to sensorsUsed=25 or so. You basically need to monitor GPU temperature, and it is way down the list of sensors.  The default is to monitor the CPU temperature which is not as high as the GPU.   

To uninstall,  I think deleting the two files /etc/init.d/smcfancontrol and /usr/local/sbin/smcfancontrol.sh and deleting the links under all the run levels rc0.d, rc1.d, etc,  should do it.

**Joushou**, you did a very good job with this script, thanks.

Thanks! I'll try it out within the next days. I am checking for the moment mfc-daemon.

Regards, Nikos

---

### Post by Nikos.Alexandris on 2009-09-11
> **amd-64 said:**
> ...

Before you do so, you should change sensorsUsed=2  to sensorsUsed=25 or so. You basically need to monitor GPU temperature, and it is way down the list of sensors.
...

All and all the sensors reported on the MBP51 are 20 (that's what the command [b]sensors[/s] gives).

Comparing the output of the command **sensors** and the **Thermal Monitor** of Nvidia X Server Settings application, the sensor # **8** corresponds to the GPU (using the "default" Nvidia 9600 graphics chip).

I guess the value of **sensorsUsed** should be set to 20 (?).

---

### Post by amd-64 on 2009-09-11
Yes, use 20. It should not affect the results. The number should be high enough to include all sensors. For me, on a MBP 5,3 the GPU is always the governing sensor.

---

### Post by Nikos.Alexandris on 2009-09-12
> **amd-64 said:**
> Yes, use 20. It should not affect the results. The number should be high enough to include all sensors. For me, on a MBP 5,3 the GPU is always the governing sensor.

Using it since yesterday (sensorsUsed=20 and fanMinSpeed=2999). The result is that the GPU is kept at 69~70 deg. while the CPU's at 57~60 deg. The difference is not too much but it is something. I might need to modify something (more).

I want to note that the same level of temperature is achieved by using the mfc-daemon.

Anyhow, thanks to the author(s) for the(ir) script(s).

---

### Post by Nikos.Alexandris on 2009-09-12
> **Nikos.Alexandris said:**
> Using it since yesterday (sensorsUsed=20 and fanMinSpeed=2999). The result is that the GPU is kept at 69~70 deg. while the CPU's at 57~60 deg. The difference is not too much but it is something. I might need to modify something (more).

I want to note that the same level of temperature is achieved by using the mfc-daemon.

Anyhow, thanks to the author(s) for the(ir) script(s).

OK, leaving it for a while brings the GPU down to 66 degrees. That's better now :-)

---

### Post by amd-64 on 2009-09-12
Nikos,

Here is the output from sensors, the machine is not doing anything intensive at this time and has been up for 2 hrs. 

```

#sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +41.0°C  (high = +100.0°C, crit = +100.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :2739 RPM  (min = 2739 RPM)
Right side :2742 RPM  (min = 2739 RPM)
temp1:       +30.0°C                                    
temp2:       +30.0°C                                    
temp3:       +30.0°C                                    
temp4:        +0.0°C                                    
temp5:       +46.8°C                                    
temp6:       +40.0°C                                    
temp7:       +42.8°C                                    
temp8:       +53.5°C                                    
temp9:       +42.5°C                                    
temp10:      +38.8°C                                    
temp11:      +44.8°C                                    
temp12:      +45.8°C                                    
ERROR: Can't get value of subfeature temp13_input: I/O error
temp13:       +0.0°C                                    
temp14:      +47.0°C                                    
temp15:      +45.2°C                                    
temp16:      +49.0°C                                    
temp17:      +40.5°C                                    
temp18:      +45.8°C                                    
temp19:      +28.2°C                                    
temp20:      +35.2°C

```


As you can see it is significantly cooler. BTW the cpu is a P8800 not a T9xxx and I am running Nvidia-185 driver. I removed cpufreq, powersave, cpudyn. I use powernowd and both CPU and GPU scale down properly.

My GPU temps would only get above 60 when Firefox and Flash hog the CPU, which happens occasionally with firefox 3.5 on certain sites. 

I use ksensors to dock CPU and GPU temps and fan speeds so I keep an eye on these.

On occasion, smcfancontrol quits, I think because of failing to read one of the sensors, this is why I created a cron job to restart it every few minutes until someone writes a cleaner fix. Since then, it has been maintenance-free and the fans are not noisy.

---

### Post by daladheri on 2009-09-29
I have been using these fan scripts for the past three days now and I notice a big difference.

 However, a colleague of mine mentioned that fan control scripts could potentially not regulate the fans correctly and fry everything or some spots may be cool and others may be hot. 

With the nature of applesmc and these scripts, does this have the potential of bricking your computer? Does this truely override the built in fan control?

---

### Post by Nikos.Alexandris on 2009-10-02
> **daladheri said:**
> I have been using these fan scripts for the past three days now and I notice a big difference.

 However, a colleague of mine mentioned that fan control scripts could potentially not regulate the fans correctly and fry everything or some spots may be cool and others may be hot. 

With the nature of applesmc and these scripts, does this have the potential of bricking your computer? Does this truely override the built in fan control?

Anybody experiencing something like that (irregular fan up's and down's, or dead fans) using the script?

The last two days I use the MBP non-stop and I've seen strange noise in the monitor and after that kind of a freeze (it happened 2-3 times after a very long period of flawless working). Don't know if it has to do with compiz or the like.

Nikos

---

### Post by Nikos.Alexandris on 2009-10-02
> **amd-64 said:**
> I removed cpufreq, powersave, cpudyn. I use powernowd and both CPU and GPU scale down properly.

I also did that. Indeed, it feels different, =faster. Thanks!

---

### Post by inphektion on 2009-10-03
after installing powernowd did you do any configuration or no?

---

### Post by Nikos.Alexandris on 2009-10-03
> **inphektion said:**
> after installing powernowd did you do any configuration or no?

No. I feel that the system has become more responsive. Whether this really is caused by better management of powernowd I have no idea.

---

### Post by crocowhile on 2009-10-03
> **Nikos.Alexandris said:**
> I also did that. Indeed, it feels different, =faster. Thanks!

Well, cpuscaling is for you to save power when the cpu is not needed so badly: by disabling it you may gain performance, but you will lose battery life.

---

### Post by Nikos.Alexandris on 2009-10-03
> **crocowhile said:**
> Well, cpuscaling is for you to save power when the cpu is not needed so badly: by disabling it you may gain performance, but you will lose battery life.

It is supposed that cpufreqd will get the job done (including scaling Nvidia GPU) but, as I experienced it with the MBP51, powernowd does a damn good job and results in faster responses. Powernowd scales depending solely on CPU load [1]. I work most of the times without the battery attached at all. Hence it is more than ok.

About cpudyn, I didn't really observed/ tested. I just installed cpudyn to see how it is going.

Can we have powernowd when on power and cpufreqd/ cpudyn when on battery?


[1] [http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html)

---

### Post by hellmitre on 2009-10-30
[SIZE="5"]FIX BELOW[/SIZE]
> This fails in karmic on my Macbook Pro 3,1, sadly. Here's the /var/logs/smcfancontrol.log output:
```
30/10 02:15:30: Detecting configuration
30/10 02:15:30:   Fans: 1
30/10 02:15:30:     Min fan-speed: 2000
30/10 02:15:30:     Max fan-speed: 6000
30/10 02:15:30:   Sensors: 3
30/10 02:15:30:     Limited by user to 2
30/10 02:15:32:   Laptop: true
30/10 02:15:32:     ACPI-State: online
30/10 02:15:32: Configuration detected
30/10 02:15:32: Temperature: 57, Fan-speed: 5996, ACPI-State: online
30/10 02:15:32: FATAL: Failing at: setting fans
30/10 02:15:32: Attempting to set fans to safe values
30/10 02:15:32: Commit suicide. Bye.
```
I really like this script. Without it, the cores hover around 57*C with fans running at 2000 RPM. I want cooler.
I also don't know how to fix it, sadly. Dunno where the system stores its information about temps and fanspeed.

[SIZE="4"]Found a fix[/SIZE]; it works fine for now and keeps everything cool. 
[LIST=1]
[*]Install the hal-applesmc and applesmc-dkms packages from the Mactel PPA (there aren't karmic versions of this; add the intrepid repo).

[*]I manually loaded the applesmc module with 'sudo modprobe applesmc', which created a /sys/devices/platform/applesmc.768 directory and put everything where smcfancontrol wants it to be in order to change fanspeed values.


[*]Put this in a text file:
```

#!/bin/bash
sudo modprobe applesmc
done

```
[*]Save that as (yournamehere).sh and make it executable with 'sudo chmod +x (yournamehere).sh'. Then run 'sudo update-rc.d (yournamehere).sh defaults' and it will add your script to be run at boot, loading your applesmc module.
[/LIST]
I couldn't figure out why simply adding 'applesmc' to the list of modules to be loaded in /etc/modules.conf didn't work, but having it load the script at boot keeps things cool, fanspeeds and temperatures show up in my hardware monitor panel applet, smcfancontrol reports that it's workin in the log.
 
Here comes the however. According to the release notes, HAL is being deprecated in favor of some new systems, a clue of whose inner workings I don't have the foggiest.

tl;dr, above fix works for now, probably for a few more distro releases, but may not at some point in the indeterminate future.

---

### Post by Joushou on 2009-10-31
Hi everyone...

I haven't checked this thread in a long time, and since i don't use Ubuntu on my laptop at the moment (Still haven't been bothered to fix GRUB... Haven't really had the time), i haven't really developed the script any further.

I'm glad you all like the script, but it might be buggy... It was written in a rush (Really, my laptop was becoming hot when i wrote it :O)...

The main reason it might quit, is that i've put in some "traps", which was intended to make a proper shutdown of the script, that would reset the values... Unfortunately, what i didn't know when i wrote those, was that it had a tendency to fail to read some sensors occasionally, meaning it would falsely trip my failure-detection, and pull the script into it's death, as seen in the logs (It says "Committing suicide. Bye!" :D).
This should be fixed if you comment out the "|| failure", or what i called the function. It should then ignore the failure, and maybe temporarily freak out, because it's missing a value to calculate the average (If that's what you set it to use.).

Also, when restarting a suspended session, it will recall the previous values, and if it was hot, freak out for a second with the fans... It will quickly change back to current values, though.
Also, depending on the configuration, the script will react quickly to increases in temperature, and that will probably also seem like odd bursts of fan-speed... This is normal, though, and don't worry.

Also, to the person asking if this could damage the computer (Sorry, i forgot your name when i was just about to write it :( ), that's a lie.

I'm controlling all found fans simultaneously, and since there's only 2 in current MBP's, i can't change the flow of air. Also, the intention of this script is to cool way more aggressively than normally, so, unless you change the configuration to cool it less, it will definitely not be hotter than before using it! ;)

If you've tried my mid-'07 laptop when running OS X, with stock fan-control, you'll know that the laptop can take much more heat than my script will allow ;) (I've been above 80 degrees celsius once... Which is why i don't use stock fan-control :D).

When i get back to Ubuntu (I still run it on my Server, but since that's not a Mac, that doesn't help here :P), i'll maybe take a look and update the script... But if anyone feels like changing something, feel free to update it, and do whatever you want with it. Though, if you improve it in anyway, i would like if you posted it here, for everyone to enjoy... There's no fun in a laptop, hot enough to vaporize your skin! (I'm talking from experience, here.)

Well, i wonder why my thread-subscription didn't tell me about all these updates... Odd.

---

### Post by Joushou on 2009-10-31
I just fixed the typo that was giving Nikos problems...

Again, thanks to everyone using the script! I'll *try* to remember to fix grub, and/or just install a clean version of Karmic on top, so i can get my script tested and cleaned up! :)

But if there's anyone wanting to get a patch into the main script, write the patch here, or PM me... I still get mails when i get PM'd, even when the subscription thing goes nuts! :)

---

### Post by Joushou on 2009-11-09
Fixed a bug that would result in ratio being undefined on non-laptop Apple's...

I just took a look on mfc-daemon, and the pros of it seems to be that it's written in C... The cons is that it only uses the coretemp sensors, it doesn't care wether you're plugged in or not, and it almost got no degree of customizability for the user...

I think my script handles the problem nicer, even though it might use up a few more system resources! ;)

I wonder if we should get a "Guide to fancontrol" thread stickied? Or, just add a note about mfc-daemon in the first post, and sticky this? It seems like there's a lot of people around here upset with Ubuntu because of this simple problem, and at least one who thinks it's a hardware problem... So i think we should announce a fix to the problem, wether it's this script or mfc-daemon...

---

### Post by Sergio Ruocco on 2010-03-01
I have a 2007 Mac Pro on which I run Ubuntu 9.10. Until now I managed the HD fan speeds "by hand", changing the speed of the IO fan via the script below. 

Then I found this nice script, but when I run it on my Mac Pro, it puts the fans to full speed. 

1) Does anyone has a version of the script adapted for Mac Pro the workstation and not Mac Pro the laptop?!

2) To check temperature of my HDs I use the hddtemp command, which in turn uses SMART.. can this script adapted to source temperature readings from HDs via SMART?

Thanks,

 Sergiop


[sergio 16:35 ~/bin]$ cat hdfancontrol
#!/bin/sh

if [ $# -ne 1 ]; then
    echo -n "Hd fan speed is: "
    cat /sys/devices/platform/applesmc.768/fan2_min
    echo "Usage: $0 <hdfanspeed(0-4000)>"
    exit 1
fi

echo -n "Hd fan speed was: "
cat /sys/devices/platform/applesmc.768/fan2_min

sudo sh -c "echo $1 > /sys/devices/platform/applesmc.768/fan2_min"

echo -n " and now is: "
cat /sys/devices/platform/applesmc.768/fan2_min

---

### Post by linuxopjemac on 2010-03-01
> I have a 2007 Mac Pro on which I run Ubuntu 9.10. Until now I managed the HD fan speeds "by hand", changing the speed of the IO fan via the script below.

Then I found this nice script, but when I run it on my Mac Pro, it puts the fans to full speed.

1) Does anyone has a version of the script adapted for Mac Pro the workstation and not Mac Pro the laptop?!

2) To check temperature of my HDs I use the hddtemp command, which in turn uses SMART.. can this script adapted to source temperature readings from HDs via SMART?

Thanks,

Sergiop

I would have a look at the Debian wiki and try their fan speed control script:

[http://wiki.debian.org/DebianOnIntelMacPro](http://wiki.debian.org/DebianOnIntelMacPro)

---

### Post by Joushou on 2010-03-01
> **Sergio Ruocco said:**
> I have a 2007 Mac Pro on which I run Ubuntu 9.10. Until now I managed the HD fan speeds "by hand", changing the speed of the IO fan via the script below. 

Then I found this nice script, but when I run it on my Mac Pro, it puts the fans to full speed. 

1) Does anyone has a version of the script adapted for Mac Pro the workstation and not Mac Pro the laptop?!

2) To check temperature of my HDs I use the hddtemp command, which in turn uses SMART.. can this script adapted to source temperature readings from HDs via SMART?

Thanks,

 Sergiop


[sergio 16:35 ~/bin]$ cat hdfancontrol
#!/bin/sh

if [ $# -ne 1 ]; then
    echo -n "Hd fan speed is: "
    cat /sys/devices/platform/applesmc.768/fan2_min
    echo "Usage: $0 <hdfanspeed(0-4000)>"
    exit 1
fi

echo -n "Hd fan speed was: "
cat /sys/devices/platform/applesmc.768/fan2_min

sudo sh -c "echo $1 > /sys/devices/platform/applesmc.768/fan2_min"

echo -n " and now is: "
cat /sys/devices/platform/applesmc.768/fan2_min

I can't tell you what's going on if you don't give me the logs from the script.

There's no such thing as a laptop Mac Pro, it's called a MacBook pro, and if my script is doing it's thing right, it should work for any Mac using the applesmc kernel module.

Yes, you can adapt that code-snippet, just use awk or something to parse hddtemp's output

---

### Post by Maletor on 2010-07-07
I'm on a MacBook and temp16 seems to be stuck at 65.
How can I get smcfancontrol to ignore this while still using the highest temp instead of average?
TTF0:        +65.0C

I looked it up in the wiki and it says this temperature is unknown...

Is it the hard drive maybe?

---

### Post by Joushou on 2010-07-07
You could do something like this in update() if temp16 isn't your last sensor... If it's your last sensor, or you don't care about the sensors after it, just limit the amount of sensors used with "sensorsUsed" in the beginning of the script.

[PHP]
...
if [[ $tempCalc == "highest" ]]
then
	counter=0
	temp=0
	until [[ $counter == $sensorsUsed ]] || [[ $counter == $sensors ]]
	do
		((counter++))

		if (($counter == 16 ))
		then
			((counter++))
		fi

		[[ ${tempSensor[$counter]} > $temp ]] && temp=${tempSensor[$counter]}
	done
	[[ $oldTemp != $temp ]] && stateChange=true && oldTemp=$temp

...
[/PHP]

(Warning: I'm high on anesthetics, coke, my gf and Linkin Park right now, so it may or may not work... :P)

---

### Post by Maletor on 2010-07-08
Yes, I know...

I'd rather the applesmc kernel bug was fixed. But what can I say?


What has worked well for me is setting the APM... (sudo hdparm -B 1 /dev/sda) to 1. Putting it on 254 makes my wrist burn off.

---

### Post by ChrisBuchholz on 2010-08-17
Hey guys,

I stumbled upon this script and thought it was so great, that I decided that I was gonna (try to) improve upon it. I have create a git repository for it and tweaked it for my liking, among also adding a uninstallation script.

I hope you guys like it, and if you have any additions to it, please push it! :D

[http://github.com/ChrisBuchholz/smcfancontrol](http://github.com/ChrisBuchholz/smcfancontrol)

---

### Post by samuaz on 2011-05-08
the script I have stopped working, the fans are at 6200 rpm and the macbook to 43 degrees Celsius, it could have happened? any help please

---

### Post by kosumi68 on 2011-05-09
Perhaps this dkms package solves the problem. It contains a patch that ignores unused sensors. Cheers!

---

### Post by samuaz on 2011-05-09
> **kosumi68 said:**
> Perhaps this dkms package solves the problem. It contains a patch that ignores unused sensors. Cheers!

thank you very much, I did a sudo apt-get purge applesmc-dkms to uninstall the previous one, and then install the new one with sudo dpkg-i

restarts, but my fan is at 6200 rpm and my CoreTemp to 48 degrees Celsius :confused::confused: cry cry

---

### Post by nevius on 2011-05-09
> **samuaz said:**
> thank you very much, I did a sudo apt-get purge applesmc-dkms to uninstall the previous one, and then install the new one with sudo dpkg-i

restarts, but my fan is at 6200 rpm and my CoreTemp to 48 degrees Celsius :confused::confused: cry cry

Have you installed macfancontrold from here: [https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

If you run the command below does your fan speed drop?

```
sudo echo 3000" > /sys/devices/platform/applesmc.768/fan1_min
```

---

### Post by samuaz on 2011-05-09
> **nevius said:**
> Have you installed macfancontrold from here: [https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

If you run the command below does your fan speed drop?

```
sudo echo 3000" > /sys/devices/platform/applesmc.768/fan1_min
```

the speed not drop 6200 rpm

I turn off the computer if I leave a few minutes off, when turned on, the fan returns to normal, but upon reaching 60 degrees starts to rise and being at 6200 rpm does not drop, although the temperature has already fallen: S
(macbook 4,1 core2duo)

I formatted and reinstalled ubuntu 15 times thinking that was installed wrong: S


in mac osx leopard 10.5.8 works fine, 
PD image of osx all temp sensors and fan speed, in this moment 57 celcius and fan 1798 rpm

ILOVE UBUNTU BUT **** SMC FAN CONTROL ITS KILLME

---

### Post by samuaz on 2011-05-10
I've solved! [http://ubuntuforums.org/showthread.php?p=10795052#post10795052](http://ubuntuforums.org/showthread.php?p=10795052#post10795052)

---

### Post by Joushou on 2011-05-11
Nevius, that command would only work assuming the module doesn't have the manual parameter set, and the kernel module haven't decided that a sensor is too hot. Oh, and if you add the missing quote. The min temperatures are just that to the kernel module - Minimum temperatures. While this is my normal approach to change fan speeds, it's not a direct control. It just sets what the fans are supposed to do when the kernel module thinks it's fair enough to idle. If the kernel module thinks the sensors are too hot, it will pick a speed between _min and _max, most likely just _max. To actually change the speeds, you need to enable manual mode. (Done with the manFanControl=true setting in my script.)

I never had any issues using the auto mode, though, but apparently some do. It may be due to one sensor being very hot in general, and the kernel module just gets confused. (Some of the sensors tend to report things like 70 degrees celsius when the laptop is idle and cold, which is why I added ways to select specific sensors to use in the script.)
The problem would then be that the AppleSMC kernel module is completely ignorant of how many sensors *I* use for my calculations, the module itself just looks at all the sensors accessible by the SMC, and if one is hot (GPU, for example), it will spin the fans up if it's not in manual mode. On my old MacBook Pro, I believe the GPU die sensor (sensor 7 I think) reported around 70 degrees celsius when the laptop was cold, and you may have a similar issue, seeing manual mode fixed it. However, watch out when you're only using the coretemp sensors - The fans will only spin up when your CPU gets hot. If you GPU gets toasty, it won't react till the GPU heats the CPU up enough for the fans to start spinning... Which is why I prefer using auto-mode, and as many sensors as possible.

I'm glad the people still find the script useful, even years after I touched it last time. I never expected anyone to use it! Also glad to see that some are picking it up and doing some cleaning (the github repo doesn't work, though)...

---

### Post by jakswa on 2011-07-12
For anyone else with macbook pro (mine is 6,2) running natty, I installed several of the packages from the mactel ppa and my fans started responding to temperatures correctly!  I just put my cpu under stress (googled 'flash cpu stress' and picked one) and watched my fan speed climb to around 4200 before backing off.

Here's the PPA listing packages for natty only:
[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty)

Now if only I could get my brightness controls working...

---

