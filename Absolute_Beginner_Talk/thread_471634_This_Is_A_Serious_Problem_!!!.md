---
title: "This Is A Serious Problem !!!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-12
Hello mates ;)

It's been 6 months that I'm using only ubuntu feisty, (since herd3). I consider myself as a liberated new happy open computer user.

But... There is some thing I would like to talk about. It is power management. I guess you did talk a lot here in this forum, but the gap between windows power management or Linux is huge guys... Too much I think.

When I was on win, I used to have a program called RMClock, that allow me to undervolt my Pentium M, between 0.7v to 1.2  depending on the frequency  (default 0.9 to 1.4).   Using this settings, my old HP laptop had around 2,5 h  3 h of battery life.

Now... I get around **_1 hour of battery life_**... #-o Less than 50% than windows. Come on guys, this sucks... It is something really serious... 

I tried Gusty, witch says (better battery life...)  and there is no changes there.

Can I (SIMPLY) change something to reach my old timelife in Ubuntu? It is possible to undervolt my cpu?  
I found some topics around... But they talk about change and touch something in the kernel level... (I'm just a new user)   **I need and WANT!**  (Sorry, I'm angry)  a simple application like RMCLOCK witch allows me to choose what voltage and frequency I want to use... That, would give me more than a double life under battery and same performance and stability. 


Sorry for my bad english guys, I tried my best.

From Catalonia

---

### Post by Kosimo on 2007-06-12
By the way... If I can undervolt my CPU, the whole system is cooler, and the fan doesn't turn on.. This means more battery life and 0 decibels of noise...  (I forgot to say that another IMPORTANT thing)

---

### Post by george29 on 2007-06-12
here's ome info i found on google by doing a search for 'ubuntu underclocking pentium M' etc. 

[http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking](http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking)

[http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)

[http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

---

### Post by Kosimo on 2007-06-12
Thank you george.

But....

THIS


[I] Disclaimer
Warning: Use at your own risk. As far as we know it has been tested only on a few computers. It may very well permanently damage your CPU.

We give no guarantee as to whether it will work for you.
Changing the voltage of a Pentium M CPU is not recommended because it can make it run out of its specifications.
Warning: Please, make sure you've temporarily stopped ANY software which may cause automatic frequency adjustment (for instance cpufreqd from sys-power/cpufrequtils package), so it does not affect your tests (especially while you run voltage-ramp-down.sh script below). Otherwise cpufreqd will overwrite frequency values automatically accordingly to it's rules and won't allow you to set desired frequencies.

That's recommended to have such software disabled for all the time while you play with frequencies and voltages.
(added by Arsen A. Gutsal)

One part of the kernel patch used in this howto is inspired by a similar patch made by Rickard Holmberg (the voltage limitation part). You can see his patch here: centrino-voltages.diff

Thanks to jlinkels for the pointer to this patch.
[edit] Overview
[edit] The advantages of undervolting

    * reduce the power consumption of a laptop
    * extend its battery lifetime
    * lower temperature of the cpu
    * the cpu cooler runs much quieter
    * you can emerge applications at full frequency without heat shock 

[edit] The disadvantages of undervolting

    * it could damage your hardware
    * it could run instable (even though your system doesn't crash) 

[edit] Methods to undervolt a Pentium-M CPU

There are two ways to undervolt a Pentium-M CPU.

    * Hardcoded Method: patch the kernel + change default voltage values of the kernel driver
    * Init Script Method: patch the kernel + let a init-script change the voltage values 

Both methods consist in patching the Linux kernel source code to be able to adjust CPU voltage through a file in the sysfs filesystem.

/sys/devices/system/cpu/cpu0/cpufreq/op_points_table

For both methods you need to know the undervolted but stable voltage for each frequency of your CPU.
[edit] Kernel versions compatibility

The kernel patch may not work with all kernel versions.

A list of compatible kernel versions is included in the patch release tar ball. Read the file kernels.compatibility.list.txt


[edit] Hardcoded Method
[edit] Patching the kernel

To patch your kernel:

    * Download the latest version of the Linux PHC patch
    * Extract the files of the tarball
    * Look in linux-phc-x.y.z/kernel-patch for your kernel version
    * Copy the linux-phc-x.y.z-kernel-vanilla-2.6.w.patch to /usr/src/linux
    * Patch the kernel 


Code: Patch the kernel

patch -p1 < linux-phc-0.2.9-kernel-vanilla-2.6.19.patch

[edit] Configure the Kernel
Linux Kernel Configuration: Set CPUFREQ

-> Power management options (ACPI, APM)
  -> CPU Frequency scaling
    -> CPU Frequency scaling (CPU_FREQ [y]) 

Linux Kernel Configuration: Set CPU

[*] CPU Frequency scaling
[*]   Enable CPUfreq debugging
<*>   CPU frequency translation statistics
[*]     CPU frequency translation statistics details
      Default CPUFreq governor (performance)  --->
---   'performance' governor
<*>   'powersave' governor
<*>   'userspace' governor for userspace frequency scaling
<*>   'ondemand' cpufreq policy governor
<*>   'conservative' cpufreq governor
---   CPUFreq processor drivers
<*>   ACPI Processor P-States driver
< >   AMD Mobile K6-2/K6-3 PowerNow!
< >   AMD Mobile Athlon/Duron PowerNow!
< >   AMD Opteron/Athlon64 PowerNow!
< >   Cyrix MediaGX/NatSemi Geode Suspend Modulation
<*>   Intel Enhanced SpeedStep
[*]     Userspace control of CPU frequency/voltage table
[ ]     Use ACPI tables to decode valid frequency/voltage pairs
[*]     Built-in tables
[*]       Built-in tables for Banias CPUs
[*]       Built-in tables for Dothan CPUs
[*]       Built-in tables for Sonoma CPUs
< >   Intel Speedstep on ICH-M chipsets (ioport interface)
< >   Intel SpeedStep on 440BX/ZX/MX chipsets (SMI interface)
< >   Intel Pentium 4 clock modulation
< >   nVidia nForce2 FSB changing
< >   Transmeta LongRun
< >   VIA Cyrix III Longhaul
---   shared options
[ ]   /proc/acpi/processor/../performance interface (deprecated)

The option

<*>   ACPI Processor P-States driver

is important for cpufreq. Without this you can't load the speedstep-centrino driver and have nothing in

/sys/devices/system/cpu/cpu0/cpufreq/

The option

[ ]     Use ACPI tables to decode valid frequency/voltage pairs

is important for setting the cpu voltage. This is necessary because the driver would load the voltage values from the acpi table. Now you can save your settings.
[edit] Setting the voltages

After configuring the kernel you have to change the voltages for your cpu in speedstep-centrino.c


Code: Edit the speedstep-centrino.c

vim /usr/src/linux/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.c 


There are three different processor types. Banias, Dothan and Sonoma.

Banias CPUs are the first generation of Pentium-M, with a 1 MB L2 cache and 400 MHz FSB manufactured on 0.13 micron process.
File: speedstep-centrino.c - Edit Banias CPUs Example

/* Intel Pentium M processor 1.70GHz (Banias) */
static struct cpufreq_frequency_table banias_1700[] =
{
	OP( 600,  956),
	OP( 800, 1004),
	OP(1000, 1116),
	OP(1200, 1228),
	OP(1400, 1308),
	OP(1700, 1484),
	{ .frequency = CPUFREQ_TABLE_END }
};

The first column are the frequencies and the second are the voltages


Dothan CPUs are the second generation of Pentium-M, with a 2 MB L2 cache and 400 MHz FSB manufactured on 90 nm process.
File: speedstep-centrino.c - Edit Dothan CPUs Example

/* Intel Pentium M processor 755 / 2.00GHz (Dothan) */
static struct cpufreq_frequency_table dothan_2000[] =
{
	OP( 600,  988,  988,  988,  988),
	OP( 800, 1052, 1036, 1036, 1036),
	OP(1000, 1100, 1084, 1084, 1084),
	OP(1200, 1148, 1132, 1132, 1116),
	OP(1400, 1196, 1180, 1180, 1164),
	OP(1600, 1244, 1228, 1228, 1196),
	OP(1800, 1292, 1276, 1276, 1244),
	OP(2000, 1340, 1324, 1308, 1276),
	{ .frequency = CPUFREQ_TABLE_END }
};

The first column are the frequencies and the second are the voltages. The other columns are for reference only (not important for us).


Sonoma CPUs are the third generation of Pentium-M, with a 2 MB L2 cache and 533 MHz FSB manufactured on 90 nm process.
File: speedstep-centrino.c - Edit Sonoma CPUs Example

/* Intel Pentium M processor 750 / 1.86 GHz (Sonoma) */
static struct cpufreq_frequency_table sonoma_1862[] =
{
	OPEX( 798, 133,  988,  988,  988,  988),
	OPEX(1064, 133, 1084, 1080, 1068, 1056),
	OPEX(1330, 133, 1180, 1172, 1132, 1124),
	OPEX(1596, 133, 1276, 1264, 1196, 1192),
	OPEX(1862, 133, 1356, 1356, 1260, 1260),
	{ .frequency = CPUFREQ_TABLE_END }
};

The first column are the frequencies, the second are the base (not important for us) and the third are the voltages. The other columns are for reference only (not important for us).

    * Find your CPU in speedstep-centrino.c
    * Look at the Minimal Safe Voltages table at the bottom of this site * Change the voltages of your cpu 


File: speedstep-centrino.c - Change voltages of Sonoma CPU Example

/* Intel Pentium M processor 750 / 1.86 GHz (Sonoma) */
static struct cpufreq_frequency_table sonoma_1862[] =
{
	OPEX( 798, 133,  700,  988,  988,  988),
	OPEX(1064, 133,  780, 1080, 1068, 1056),
	OPEX(1330, 133,  876, 1172, 1132, 1124),
 	OPEX(1596, 133,  972, 1264, 1196, 1192),
	OPEX(1862, 133, 1068, 1356, 1260, 1260),
	{ .frequency = CPUFREQ_TABLE_END }
};


    * Save the changes
    * Build the kernel
    * Reboot the System 

You can see if the changes take effect with


Code: cat voltages

linux # cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
798000:700,1064000:780,1330000:876,1596000:972,1862000:1068

If you get the correct values, you are ready!
[edit] Init Script Method
[edit] Install the overlay

For the Init Script Mehthod you have to install the sunrise overlay.


Code: Install layman

linux# emerge layman


Code: Add sunrise overlay

linux# layman -a sunrise

[edit] Install linux-phc
Code: Unmask linux-phc

linux# echo "=app-laptop/linux-phc-0.2.9" >> /etc/portage/package.keywords


Code: Install linux-phc

linux# emerge linux-phc

[edit] Configure the kernel
Code: Configure the kernel

linux# cd /usr/src/linux
linux# make menuconfig

    * Follow steps described under Configure the Kernel
    * Build the configured kernel. 

    * Reboot your System. 

Note: If you don't see the options for your CPU, you have manually to patch your kernel
[edit] Getting the current voltage settings

The content of the file /sys/devices/system/cpu/cpu0/cpufreq/op_points_table is the list of all the voltage/frequency pairs currently stored in the CPU frequency table, the voltage is in mV.
Code: Cat the current voltage values

linux # cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
798000:988,1064000:1084,1330000:1180,1596000:1276,1862000:1356

The text displayed by this command is the current list of frequency/voltage operating points of the CPU. The frequencies are in kHz and the voltages are in mV.
[edit] Changing the voltage settings

You need to use the same format as what you get when reading the file (same number of values separated by "," on one single line")

Be carefull when doing this. There are some protections in the code to block you from setting voltage values that are greater than the default settings. But if you set values that are too low, your CPU will freeze and you will have to reboot your computer.


Code: Open the undervolt config file

linux# vim /etc/conf.d/undervolt


Code: Set the CUSTOM_VTABLE variable

CUSTOM_VTABLE="798000:988,1064000:1084,1330000:1180,1596000:1276,1862000:1356"


Code: Change this voltages with your own values

CUSTOM_VTABLE="798000:700,1064000:780,1330000:876,1596000:972,1862000:1068"


Code: Change IS_CONFIGURED to yes

IS_CONFIGURED=yes

[edit] Start the init script

Save the /etc/conf.d/undervolt


Code: Start the init script

linux# /etc/init.d/undervolt start


Code: Check your settings

linux# cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
798000:700,1064000:780,1330000:876,1596000:972,1862000:1068

If you get the correct values, you are ready!
[edit] Trouble Shooting

If you don't get the same thing as what your have writen to the file, have a look at dmesg. If you have enabled cpufreq debug messages in your kernel, you will see errors like the following, that will give you a hint on what you did wrong:
Code: Sample error codes

speedstep-centrino: voltage value 0 is out of bounds: 1724 mV
speedstep-centrino: not setting control value 1 to 0c36 because requested voltage is not lower than the default value
speedstep-centrino: failed to parse voltage value 2

It may also be that the voltages have been rounded to a 16 mV boundary.
[edit] Finding missing frequencies

If you miss some frequencies you want to use check the maxium amount of frequencies your cpu support with
Warning: Warning! The code below is just wrong, the stepping line from /proc/cpuinfo states the version of the processor, not the number of available frequencies! Try cpufreq-info instead!


Code: Maximal supported frequencies steppings

linux # cat /proc/cpuinfo |grep stepping
stepping        : 8

Count the amount of your frequencies after patching your kernel.
File: speedstep-centrino.c - Count amount of frequencies - Sonoma CPU Example

/* Intel Pentium M processor 750 / 1.86 GHz (Sonoma) */
static struct cpufreq_frequency_table sonoma_1862[] =
{
	OPEX( 798, 133,  700,  988,  988,  988),
	OPEX(1064, 133,  780, 1080, 1068, 1056),
	OPEX(1330, 133,  876, 1172, 1132, 1124),
 	OPEX(1596, 133,  972, 1264, 1196, 1192),
	OPEX(1862, 133, 1068, 1356, 1260, 1260),
	{ .frequency = CPUFREQ_TABLE_END }
};

You can see we count only five frequencies but the cpu supports eight. So copy three lines and change only the important frequency and voltage values (described under Setting the voltages)

To find out the missing frequencies looking at the Mininal Safe Voltage table


File: speedstep-centrino.c - Add the missing frequencies - Sonoma CPU Example

/* Intel Pentium M processor 750 / 1.86 GHz (Sonoma) */
static struct cpufreq_frequency_table sonoma_1862[] =
{
	OPEX( 798, 133,  700,  988,  988,  988),
	OPEX(1064, 133,  780, 1080, 1068, 1056),
	OPEX(1197, 133,  828, 1172, 1132, 1124),
	OPEX(1330, 133,  876, 1172, 1132, 1124),
	OPEX(1463, 133,  924, 1264, 1196, 1192),
 	OPEX(1596, 133,  972, 1264, 1196, 1192),
	OPEX(1729, 133, 1020, 1356, 1260, 1260),
	OPEX(1862, 133, 1068, 1356, 1260, 1260),
{ .frequency = CPUFREQ_TABLE_END }
};

[edit] Finding the best voltage settings
[edit] Smallest voltages before the CPU freeze

If you are not afraid to crash your system a few times, you can quickly find the lowest voltages that your CPU can acheive using the following procedure:

   1. Set your CPU to the first frequency you want to test using the userspace or conservative governor (don't try this with ondemand governor - it's not working)
   2. Run the voltage-ramp-down script (the script is at the end of this page)
   3. Wait until your system freeze
   4. Write down the voltage value of the current frequency that was displayed just before the last "OK"
   5. Reboot
   6. If you want to crash your system again set your CPU frequency to the next frequency and go back to step 2 

If you are lucky, your CPU will be able to run at it's lowest frequency using 700 mV.

It is strongly recommended to perform this procedure in console mode with the minimum software running (shut down all the services you can).

Also it not recommended to do this if you do not have a journaled file system. And even with a journeled file system there are still chances that your file system can get corrupted if you have applications writing to the disk.
[edit] Safe voltages

I´m not sure if the method illustrated above gives you safe voltages. I myself used another way to determine the voltages and I think they are safer, than using the lowest ones before crashing your system. This method is also not 100% crash prone, while testing, but I think the voltages you get afterwards are safer.

For using this method under Linux, you will need the patch and mprime. Under Gentoo, just do emerge gimps:


Code: Installing mprime in Gentoo

emerge gimps

When running gimps, note that it requires a working directory to be set explicitly. You can perform the stress test directly by using


Code: GIMPS stress test

/opt/gimps/mprime -t -w/tmp/

Besides Windows you need RMClock [1] and Prime95 [2]. After installing both of the programs run RMClock and choose AC Power Profile "Power Saving" (this tutorial assumes you´re running on AC Power, so plug your laptop in!) then switch to the profile Power Saving. Check "Use P-State Transisitons" right click the box and Add a state. Choose the multiplier you want to test (eventually you will want to test all of them so choose the lowest and work your way up) and set the voltage to the standard voltage of your CPU. Click apply and see under the General tab if your multiplier is used. If it is start prime95 and start a torture test (maximum power consumption). Now switch back to RMClock and see if your multiplier is still unchanged. If your CPU clocked to a higher frequency because of the load something went wrong - you only define one P-State your CPU has to reside in.

Now on to the funny part. From your standard voltage undervolt your cpu one step and click apply - check in the General tab if everything went right. Look into prime if it says it got a rounding error. If it does immediately raise the voltage again (don´t forget apply) as you´re risking a bluescreen here. If nothing went wrong and Prime didn´t complain even after running for a minute with the lower voltage, lower the voltage another step (APPLY!) - repeat this until prime complains. If it does, raise the voltage another step and let prime at least run for another hour or longer after restarting the torture test again (the longer the better).

My laptop threw a rounding error on one multiplier even after a whole hour of testing, that´s why I think the voltages determined with the above script are not safe. Rounding errors are a very bad thing, even worse than crashing your machine, because you won´t know how they affect your machine. Also think about power spikes in your power supply. A stable voltage now doesn´t mean a stable voltage all the time in the future.

After you´re done testing, write down the multiplier/voltage combo, remove the P-State and start again with a new multiplier. This method is really time consuming, I know, but for me it was entirely worth it.

Btw.: Removing the heatpad from your cooler and replacing it with some cooling paste works wonders for temperature also. My dell had a really thick heatpad. Be careful while removing your cooler though, as Pentium-M cpus don´t have a heatspreader and are easily crushed by the cooler - not enough pressure on the cpu by the cooler is bad for your temps though, so be sure you know what you´re doing.
[edit] Minimal safe voltages

The tables below shows the voltage values that are considered safe by some people that have undervolted their CPU The samples are presented in 4 different tables:

    * Pentium M with with FSB at 400 MHz
    * Pentium M Low Voltage with with FSB at 400 MHz
    * Pentium M Ultra Low Voltage with with FSB at 400 MHz
    * Pentium M with with FSB at 533 MHz 


Warning: Remember that there is absolutely no guarantee that these voltages will be safe for your CPU. Use them only as starting point to find your good voltages with caution.

Tip: More informations on Pentium M CPUs you get on Wikipedia
Note: ToDo: Please add the min safe voltages of your CPU in one the tables below especially if it is a model that nobody has reported yet


Pentium M with with FSB at 400 MHz:
Who	CPU Model	600 MHz	700 MHz	800 MHz	900 MHz	1.0 GHz	1.1 GHz	1.2 GHz	1.3 GHz	1.4 GHz	1.5 GHz	1.6 GHz	1.7 GHz	1.8 GHz	1.9 GHz	2.0 GHz	2.1 GHz
?	P-M 705	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	-	-	-	-	-	-
rschwarze	P-M 710	700	-	716	748	780	812	860	892	956	-	-	-	-	-	-	-
DogMatica	P-M 710	700	-	700	-	780	812	860	- 	892	-	-	-	-	-	-	-
?	P-M 715	700	-	700	-	764	-	812	-	-	924	-	-	-	-	-	-
?	Banias 1500	732	-	812	-	908	-	988	-	1068	1116	-	-	-	-	-	-
BP	P-M 725	700	-	700	-	764	-	844	-	908	-	988	-	-	-	-	-
Quandary	P-M 725	700	-	700	-	748	-	812	-	876	-	940	-	-	-	-	-
pumpkin0	P-M 725	700	-	748	-	828	-	892	-	988	-	1100	-	-	-	-	-
teknohog	P-M 725	700	-	700	-	764	-	844	-	908	-	972	-	-	-	-	-
Pyotr	P-M 735	700	 ?	700	 ?	732	 ?	780	 ?	860	 ?	 ?	956	-	-	-	-
c0re	P-M 735	700	 ?	732	 ?	780	 ?	860	 ?	956	 ?	 ?	1084	-	-	-	-
critias	P-M 735	700	 ?	700	 ?	764	 ?	828	 ?	892	 ?	 ?	972	-	-	-	-
foobar	P-M 735	700	 ?	700	 ?	748	 ?	828	 ?	892	 ?	 ?	972	-	-	-	-
ballessay	P-M 745	700	-	716	-	780	-	828	-	892	-	988	-	1084	-	-	-
dgaffuri	P-M 755	700	-	700	-	764	-	844	-	924	-	1004	-	1084	-	1196	-
meynard	P-M 765	700	-	700	-	748	-	812	-	876	-	956	-	1036	-	-	1164

All voltages are in mV


Pentium M Low Voltage with with FSB at 400 MHz:
Who	CPU Model	600 MHz	700 MHz	800 MHz	900 MHz	1.0 GHz	1.1 GHz	1.2 GHz	1.3 GHz	1.4 GHz	1.5 GHz	1.6 GHz
?	P-M 718	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	-	-	-
ailas	P-M 738	700	-	764	-	796	828	860	876	876	-	-
hagan	P-M 738	700	-	732	764	796	828	860	892	924	-	-
?	P-M 758	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	-
?	P-M 778	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?

All voltages are in mV


Pentium M Ultra Low Voltage with with FSB at 400 MHz:
Who	CPU Model	600 MHz	700 MHz	800 MHz	900 MHz	1.0 GHz	1.1 GHz	1.2 GHz	1.3 GHz
bill	P-M 713	700	 ?	 ?	 ?	 ?	780	-	-
?	P-M 723	 ?	 ?	 ?	 ?	 ?	-	-	-
georg	P-M 733	700	-	716	748	780	812	-	-
alex	P-M 733J	700	-	700	716	748	780	-	-
frank	P-M 753	700	n/a	716	732	764	796	828	-
?	P-M 773	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?

All voltages are in mV


Pentium M with with FSB at 533 MHz:
Who	CPU Model	800 MHz	933 MHz	1.07 GHz	1.20 GHz	1.33 GHz	1.47 GHz	1.60 GHz	1.73 GHz	1.87 GHz	2.00 GHz	2.13 GHz	2.26 GHz
BDz	P-M 730	700	-	748	-	828	-	958	-	-	-	-	-
Knefas	P-M 730	700	-	844	-	892	-	908	-	-	-	-	-
heiner	P-M 730	700	-	732	-	796	-	892	-	-	-	-	-
CC1	P-M 740	732	-	-	-	-	-	-	-	-	-	-	-
Eric	P-M 740	700	-	764	-	844	-	-	1052	-	-	-	-
soulwarrior	P-M 740	700	-	732	-	828	-	-	956	-	-	-	-
Martin	P-M 740	716	-	764	796	844	876	908	972	-	-	-	-
Freecoffee	P-M 740	700	-	748	-	844	-	-	1052	-	-	-	-
jwj	P-M 750	700	 ?	780	 ?	876	 ?	940	 ?	1036	-	-	-
Phlogiston	P-M 750	748	 ?	828	 ?	924	 ?	1020	 ?	1116	-	-	-
Alan	P-M 750	748	-	828	-	908	-	1004	-	1100	-	-	-
Arsen A. Gutsal	P-M 750	716	-	796	-	908	-	1004	-	1100	-	-	-
Daniel S.	P-M 750	748	 ?	 ?	 ?	 ?	 ?	 ?	 ?	1132	-	-	-
BaronChaos	P-M 750	700	 ?	764	796	860	892	940	972	1020	-	-	-
cc1 	P-M 750	700	- 	- 	-	- 	- 	940	- 	1020	-	-	-
nedunk	P-M 750	700	- 	780	828	876	924 	972	1020 	1068	-	- 	-
haniz	P-M 750	700	- 	-	-	-	-	-	956	1020	-	- 	-
elm / black hole sun 	P-M 760	700	-	748	-	844	-	924	-	-	1164	-	-
finrod	P-M 760	700	-	796	828	876	908	956	-	1084	1132	-	-
nathan	P-M 770	700	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	1052	-
ThePizzaKing	P-M 770	700	-	764	-	844	-	940	-	1052	-	1164	-
?	P-M 780	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?	 ?
Pyotr	P-M 735*	700	 ?	748	 ?	828	 ?	924	 ?	1036	 ?	 ?	1212
Felix	P-M 735*	716	 ?	796	 ?	876	 ?	988	 ?	1052	 ?	 ?	1260

All voltages are in mV

* this is a Pentium M 735 that has been overclocked by increasing the FSB from 100Mhz to 133Mhz; it runs mprime stable at 38°C on a MSI 915GM Speedster mainboard. Felix: Same applies but in a dell 630m laptop. Temperature around 42°C. on idle (up to 65°C. on load).
[edit] Some handy scripts

As lowering the voltage is likely to crash the system it is safer to perform the tests in console mode to minimize the risks of file system corruption. (Using a journalized file system is also a good idea)

To perform tests in console mode you may want to use some scripts to help you change the voltages and monitor the CPU temperature and the current drawned from the battery. This chater contains some very basic sample scripts you may want to use


[edit] Measuring temperature and current

This script can be used to measure the CPU temperature and the current drawned from the battery in the command line interface. It needs to run quite a long time to have an accurate average of the temperature if there are big variations. And if the temperature does not vary at all the computed average will be no more accurate than the precision of the output of cat /proc/acpi/thermal_zone/THRM/temperature, wich usually is 1 °C.

It produces one line like the followings every 10 seconds:
Code: Output sample

2005/10/21 01:44:52  T = 39.0/40.0 °C  Avg(T) = 38.17681 °C    I = 946/952 mA  Avg(I) = 931.947 mA    F = 798000 MHz
2005/10/21 01:45:02  T = 39.0/39.0 °C  Avg(T) = 38.18414 °C    I = 946/949 mA  Avg(I) = 937.763 mA    F = 798000 MHz
2005/10/21 01:45:12  T = 39.0/39.0 °C  Avg(T) = 38.19142 °C    I = 946/949 mA  Avg(I) = 941.289 mA    F = 798000 MHz
2005/10/21 01:45:22  T = 38.0/39.0 °C  Avg(T) = 38.19562 °C    I = 946/948 mA  Avg(I) = 943.413 mA    F = 798000 MHz

Here is the script:
File: monitor.cpu.power.sh

#!/bin/bash
# Display CPU frequency, temperature and current drawn from the battery
#in (almost) real time

TAlpha=0.99900 # Coeficient used to compute the temperature average
               # Keep it in the ]0..1[ range.
               # Increase it to have a more smooth temperature average
               # And keep the trailing 0 it is important

IAlpha=0.950   # Same as above but for the current

SamplingPeriod=1
DisplayPeriod=10
TempUnit="°C"

echo "Sampling period: $SamplingPeriod s"
echo "Temperature average coefficient: $TAlpha"
echo "Current average coefficient:     $IAlpha"

# Variables initialization
TAvg=`acpi -t -B | cut --delimiter=" " --fields=9`
TMin=$TAvg
TMax=$TAvg
IAvg=`grep 'present rate:' /proc/acpi/battery/BAT1/state | cut  --delimiter=" " --fields=14`
IMin=$IAvg
IMax=$IAvg
TBeta=`echo "1-$TAlpha" | bc`
IBeta=`echo "1-$IAlpha" | bc`
LastDisplay=1

# Main loop
while [ 0 ]
do
  # Get temperature
  T=`acpi -t -B | cut --delimiter=" " --fields=9`
  # Compute temperature moving aveage
  TAvg=`echo "$TAlpha * $TAvg + $TBeta * $T" | bc`
  # Get current
  I=`grep 'present rate:' /proc/acpi/battery/BAT1/state | cut  --delimiter=" " --fields=14`
  # Compute current moving average
  IAvg=`echo "$IAlpha * $IAvg + $IBeta * $I" | bc`
  # Comute min/max values of current display period
  TMax=`echo "a=$T; b=$TMax; if (a > b) a else b" | bc`
  TMin=`echo "a=$T; b=$TMin; if (a < b) a else b" | bc`
  IMax=`echo "a=$I; b=$IMax; if (a > b) a else b" | bc`
  IMin=`echo "a=$I; b=$IMin; if (a < b) a else b" | bc`
  # Get CPU frequency
  Freq=`cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq`
  # Display data
  if [ $LastDisplay -eq 1 ]; then
    Timestamp=`date "+%Y/%m/%d %H:%M:%S"`
    echo "$Timestamp  T = $TMin/$TMax $TempUnit  Avg(T) = $TAvg $TempUnit    I = $IMin/$IMax mA  Avg(I) = $IAvg mA    F = $Freq MHz"
    TMax=$T
    TMin=$T
    IMin=$I
    IMax=$I
  fi
  # Wait until next sampling period
  sleep $SamplingPeriod
  LastDisplay=$(($LastDisplay+$SamplingPeriod))
  if [ $DisplayPeriod -le $LastDisplay ]; then
    LastDisplay=1
  fi
done

[edit] Finding the lowest voltages before the CPU freeze

This script automatically decreases the voltages settings by 16 mV for each MHz setting and will then test if the CPU still runs at all available frequencies.

Beforehand the "userspace" governor has to be set.


Warning: Use with caution. It will crash your system!

Also note that this script has been designed for the sysfs interface of the old patch versions 0.1.x.
The patch versions 0.2.X still implement this old interface for backward compatibility. But it may be removed in the future


File: voltage-ramp-down.sh

#!/bin/bash

# Min voltage value
# Voltages will not be set below than this value
Vmin=700

# Frequence settings
Fall=`cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies`

# run the CPU this many seconds at the given MHz to check if OK
Period=3

echo "Avail. Frequencies: $Fall"

while [ 0 ]; do

	# Get current votages
	CurVoltages=`cat /sys/devices/system/cpu/cpu0/cpufreq/voltage_table | cut --delimiter="," --output-delimiter=" " --fields=1-`
	NewVoltages=""

	# Compute new voltages as current - 16 mV
	for V in $CurVoltages; do
		V=$(($V - 16))
                
                # Ensure that voltage is not below min value
                if [ $V -lt $Vmin ]; then
			V=$Vmin
		fi
    
		if [ $NewVoltages ]; then
			NewVoltages="$NewVoltages,$V"
		else
			NewVoltages="$V"
		fi
	done

	# Display current settings from the sysfs file
        echo " "
        echo "Current settings:   "`cat /sys/devices/system/cpu/cpu0/cpufreq/voltage_table`
        
        # Display the new settings that we are going to write to the sysfs file
        echo "Requested settings: $NewVoltages"
        
        # Force the kernel to write its buffers to the hard disk
        # to reduce the risks of file system corruption in case of CPU freeze
        sync
        
        # Apply new settings
        echo "$NewVoltages" > /sys/devices/system/cpu/cpu0/cpufreq/voltage_table
        
        # now check if all voltages are OK and loop over all frequencies
	for vv in $Fall; do
		# set CPU speed
		#echo "Setting $Fcur"
		echo $vv > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
		
		# sleep to see if cpu groks
		sleep $Period

		# load
		i=0
		while true; do
			i=$((i+1))
			if [ $i -gt 5000 ]; then
				break
			fi
		done
                
		echo "OK " `cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq`
        done
done


[edit] Gentoo init script

This is an init script for Gentoo Linux to set the custom voltage at boot time. (This init script is a slightly modified version of the init script that is presented on this other wiki about CPU undervolting)


There is not yet any ebuild available to install it. So you have to manually copy the init script to your /etc/init.d folder and its configuration to your /etc/conf.d folder. This script is included in the tarball of the patch, in the gentoo folder.


The configuration file looks like the following:
File: /etc/conf.d/undervolt

# Path to the voltage table sysfs interface file
VTABLE_PATH="/sys/devices/system/cpu/cpu0/cpufreq/op_points_table"

# Switch back to DEFAULT_VTABLE if undervoltage is stopped? [yes/no]
SWITCH_BACK="no"

# Default voltages that will be restored at shutdown if SWITCH_BACK=yes
DEFAULT_VTABLE="798000:988,1064000:1116,1330000:1244,1596000:1356"

# Custom voltages that will be applied at boot time
CUSTOM_VTABLE="798000:700,1064000:764,1333000:860,1596000:956"

# Set the following to "yes" when the all the settings are configured
# This is a safety to disable setting the voltages with the default
# values of this file that are probably wrong for your CPU
IS_CONFIGURED="no"

In this configuration file you need to change the voltage tables and set the IS_CONFIGURED flag to "true" when you are done.

The init script may be different for different versions of the patch. Therefore it is no longer available on this howto. You can find the gentoo init script in the release tarball of each version of the patch. The patch is available on the Project Website

An alternative to an init script is to let ACPI handle the switching; the following script will enable undervolting when the system is on battery power and disable it when it's on AC (note: the script also switches the CPU governor to conservative on battery & performance on AC, this part requires cpufreq-utils)
File: /etc/acpi/ac-adapter.sh

#Choose the governor you want to use when laptop is running on ac power
#Set the frequency:millivoltage settings to undervolt your Pentium-M in the last line
#  of the off-line case, default is what I use for my P-M 760
#(performance or ondemand recommended)
#This file created by Ryan Neufeld August 2005
#Undervolt portion added by Nick Andrade May 2006
ONAC_GOVERNOR="performance"
BATT_GOVERNOR="conservative"
range=`cpufreq-info | grep 'Hz -'`
minmhz=`echo $range | gawk '{print $3 $4}'`
maxmhz=`echo $range | gawk '{print $6 $7}'`
acstate=`grep state /proc/acpi/ac_adapter/AC/state | gawk '{print $2}'`;
case "$acstate" in
        on-line)
                #Do stuff when the ac adapter is plugged in
                cpufreq-set -g ${ONAC_GOVERNOR} -u ${maxmhz}
                logger "AC Adapter is plugged in. Setting CPU governor to ${ONAC_GOVERNOR}";
                #get the current speed in KHz
                speed=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq`;
                #throw it to bc and get MHz
                mhz=$(echo "scale=0; ${speed}/1000" | bc -l);
                logger "Current cpu speed is $mhz MHz";

                #set default voltage
                echo "2000000:1356,1600000:1244,1333000:1164,1067000:1084,800000:988" > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
                ;;
        off-line)
                #Do studd when the ac adapter is un-plugged
                cpufreq-set -g ${BATT_GOVERNOR} -d ${minmhz} -u ${maxmhz}
                logger "AC Adapter is un-plugged. Setting CPU governor to ${BATT_GOVERNOR}";
                #get the current speed in KHz
                speed=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq`;
                #throw it to bc and get MHz
                mhz=$(echo "scale=0; ${speed}/1000" | bc -l);
                logger "Current cpu speed is $mhz MHz";

                #undervolt the cpu
                echo "2000000:1164,1600000:956,1330000:876,1067000:796,800000:700" > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
                ;;
esac

[edit] Upgrading from an older version of the patch
Note: This part is out of date!

If your kernel is already patched with an older version of the patch you first need to unpatch your kernel.

Example for the old patch version 0.1.2 of 07/12/2006:

   1. Copy the diff file of the old patch in /usr/src/linux/
   2. In that folder run the command "patch -p1 -R < bdz.undervolt.2006.01.07.patch" 

If you don't have the old patch version 0.1.X that was used to patch your kernel you can download it here:

    * Version 0.1.2 released on 01/07/2006: bdz.undervolt.2006.01.07.patch
    * Version 0.1.1 released on 22/10/2005: bdz.undervolt.2005.10.22.a.patch
    * Version 0.1.0 released on 19/10/2005: bdz.undervolt.2005.10.19.a.patch
    * Version 0.0.0 released on 01/07/2005: bdz.undervolt.2006.01.07.patch 

All later vesions of the patch (0.2.1 and above) should be available on the sourceforge web site: Linux PHC
Retrieved from "http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU"

Category: [/I]




**[COLOR="Red"]Is too long... And probably I'll mistake more than twice... I knew that topics already and the reason I opened this new one, is because I wanted to discuss how can we make it simple and easy.[/COLOR]**

---

### Post by digitalbenji on 2007-06-12
I think that undervolting is far to risky a method to go.  Laptop's aren't cheap, and I don't want to risk messing mine up.  I have a Pentium M as well, btw.  I use cpufrequtils and set a range for CPU frequency scaling, which I think has some positive effect on overall battery performance.

---

### Post by dptxp on 2007-06-12
Operating at a lower voltage is risky, chips can brown out. A small %age reduction in voltage (say 10%) may not harm , maybe 20% may not harm, but I do not want to find out.

---

### Post by Talon2 on 2007-06-12
> **Kosimo said:**
> 
There is some thing I would like to talk about. It is power management. I guess you did talk a lot here in this forum, but the gap between windows power management or Linux is huge guys... Too much I think.

I wish I had an answer for you but I don't.  Power management is simply terrible as far as I'm concerned.  I've reported and contributed to bug reports related to power management but those bugs sit either with a low priority or unconfirmed.  I'm not seeing any serious action being taken.  Of the systems I administer not a single one has suspend or hibernate working fully.  There are related issues like USB not coming back to life after a suspend.  All in all power management is really bad.

There are 3 areas in this os that are just simply subpar:

- Power management
- Video support
- Wireless support

---

### Post by tribaal on 2007-06-12
You might want to try "emifreq-applet" from the repos. It lets you set your CPU's modifier, which is far less dangerous than undervolting, and can get you some extra time on your batteries. 

Hope this helps :)

- Trib'

---

### Post by Mimsy on 2007-06-13
Not sure how helpful this article is to solve your problem, but it does explain a large number of things: [http://spidertools.com/ub_power.php](http://spidertools.com/ub_power.php)

---

### Post by wyth on 2007-06-15
I'd suggest the CPUFreq; there's an applet for it that can sit in the taskbar and allow you to changed the frequency at will.  (I believe you need to remove powernowd).  

Be happy you're getting an hour.  I'm lucky if I get 20 minutes of battery.

---

### Post by ncappel1 on 2007-06-17
applying less voltage than is reccomended on most electronics is taking a risk. It isn't that it just doesn't work easily for ubuntu, there is a reason a voltage is reccomended in the first place!

Also, with lithium ion batteries frequent partial discharges eventually lead to misreadings in battery life meters. It can be helpful for the battery meter to do a full discharge every 30 or 40 charges. This will help keep the battery meter well calibrated.

---

