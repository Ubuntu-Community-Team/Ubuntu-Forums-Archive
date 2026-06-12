---
title: "How do I fix notebook power management?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by jollins on 2007-10-24
Hi

I'm running a new install of Gutsy on an HP dv6500t (has a 2 ghz c2d cpu) and my computer is stuck at running at 2.0ghz. I used [_this guide_]("http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/") to install power management and I don't think I set it up correctly.

Here are the directions I followed

> 4.11 Laptop Mode (Energy Saving)

Note: with current version of laptop-mode and X this feature is not enabled in any case when you switch from AC to battery, despite what is written hereafter. However following this guide you would be able to manually activate it by typing:
sudo laptop_mode start

this will last until next reboot.

Laptop mode is disabled by default in Ubuntu. To enable this open Terminal and type:

Code:

sudo gedit /etc/default/acpi-support

At the bottom of the file, there is the ENABLE_LAPTOP_MODE variable, set this equal to true. A restart is required to enable this setting.
Read through this file to see some of the other options.

    Other power applications can be found in the Extra Repositories. To install them, open Synaptic and install the following packages:
    laptop-mode
    laptop-mode-tools
    laptop-detect
    cpufreqd
    cpufrequtils

Linux can use different power management profiles called “governors.” By default, Ubuntu does not allow you to change which governor it uses, however you can enable the option with one command:

    $ sudo dpkg-reconfigure gnome-applets

    After that, make sure you have the “CPU Frequency Monitor” applet running in your Gnome panel. Right click on the applet and go to the Preferences. Under “Frequency Selector” section, make sure the “Show menu” is selected on “Frequencies and Governors.”

    Then you can left click on the applet and from here, choose which governors or frequencies to use.

You can change this via the command line without having to enable anything. Just go to /sys/devices/system/cpu/cpu0/cpufreq/ (if you have multiple processors/cores/hyperthreading change cpu0 to cpu1, cpu2, etc. for each cpu you have listed) and edit the file (use sudo) “scaling_governor”, just change the governor that is listed to whatever governor you want to use. Available governors are listed in “scaling_avail_governors”

    man laptop-mode.conf

and edit /etc/laptop-mode/laptop-mode.conf

Note: consider installing also powertop which could easily help you reducing energy consumption by analyzing actual energy wasts and give you useful tips on how to save.

in gutsy: sudo apt-get install powertop




I'm able to change the speed profiles using the CPU frequency applet but no matter what I select it stays at 2.0 ghz. Can someone tell me how to make it so my computer throttles speed correctly? 

Thanks.

---

### Post by gustavoavellar on 2007-10-24
Hello jollins,
What's your processor model? I have a Celeron M370 running at 1.5GHz. Intel Celerons doesn't have SpedSteep technology, so you can't change the processor frequency.

---

### Post by jollins on 2007-10-25
> **gustavoavellar said:**
> Hello jollins,
What's your processor model? I have a Celeron M370 running at 1.5GHz. Intel Celerons doesn't have SpedSteep technology, so you can't change the processor frequency.
Thanks for the replay Gustavo
The Processor is a Core 2 Duo running at 2ghz (model T7300), which does support speedstep.

Last week I was running a different install of Gutsy on this same computer (I messed up that install so I reformatted, but thats another story...) and speedstep was working (the CPU was running at 800mhz on battery). I can probably get it working again if someone could please tell me how to undo the changes I made with the posted directions.

Note: I am using the main build of gutsy, no dailies or anything...

---

### Post by jollins on 2007-10-27
I've found a solution. Installing powersaved using Synaptic has restored the automatic speed-governing.

---

