---
title: "Going to fresh install 15.10 to MacBook Pro 11,1 (mid 2014)"
date: 2015-10-21
forum: Apple Hardware Users
---

### Post by enrico12 on 2015-10-21
Will follow info about issues, peripherals not working and what's changed from 15.04 on my Mac.

Someone would like to share his experiences?

---

### Post by enrico12 on 2015-10-21
Installation finished
- installed without internet connection
- no problems, reboot and Unity is running

Operating
- graphics drivers ok and retina display works fine
- touchpad ok
- bluetooth ok

- wireless not working
   1) installed dkms from USB installation media
   2) installer bcmwrl drivers from USB
   3) wireless detected but unable to connect - work in progress

EDIT: wireless works fine, problems due to temporary failure of my internet provider.

---

### Post by MikeBraxner on 2015-10-22
The [install guide for utopic]("https://help.ubuntu.com/community/MacBookPro11-1/utopic") is still worth while following. All the usual stuff works just fine, except for the camera. A couple of minor minor adjustment suggestions.  

**(1) getting rid of the SPDIF / audio jack red-light**[INDENT]The 'old way' still works as such, i.e. from /etc/rc.local [/INDENT]
[INDENT=2]echo '1' | sudo tee '/sys/module/snd_hda_intel/parameters/power_save' 
[/INDENT]
[INDENT] or cleaner, via /etc/modprobe.d/audio_powersave.conf [/INDENT]
[INDENT=2]options snd_hda_intel power_save=1  

[/INDENT]
[INDENT]However, either way ONLY works, **if tlp is not running**. If tlp is running, then the hooks in /etc/pm/power.d depend on the settings in /etc/default/tlp.  If that's the case, then alter the sound power savings setting there, i.e. set ...     [/INDENT]
[INDENT=2]# Enable audio power saving for Intel HDA, AC97 devices (timeout in secs).     
# A value of 0 disables, >=1 enables power save. 
    SOUND_POWER_SAVE_ON_AC=1     
SOUND_POWER_SAVE_ON_BAT=1
[/INDENT]
[B] 
(2) Instant Resume from Suspend[/B] ([re-posted from here]("http://ubuntuforums.org/showthread.php?t=2299201"))[INDENT]The 11.1 apparently still has the 'instant resume from suspend' problem encountered in earlier releases. In addition to the already  documented XHC1 wake-up issue, wake-ups from LID0 need to be suppressed as well,  ideally in such a way that suspend via lid-close/wake-up on lid-open still works properly.  Thanks to **respiranto**, this is as easy as copy and paste. 
[/INDENT]
[INDENT=2]      (i) suppress XHC1 wakeup call ([see here]("https://wiki.archlinux.org/index.php/MacBook#Suspend_and_Hibernate")). 
    (ii) set up a service to properly handle lid-closing ([see here]("https://bbs.archlinux.org/viewtopic.php?pid=1556046#p1556046")).  (For a cheat-sheet on Systemd, check [here]("http://askubuntu.com/questions/19320/how-to-enable-or-disable-services").) [/INDENT]

**(3) Touchpad**[INDENT]For some time, installation guides for Ubuntu tended to suggest using xmodmap configs for swipe gestures, which works just fine, with two minor draw-backs. First, it can be a pain to personalize settings. Second, the resulting swipe-gestures are global, i.e. no gesture-adjustment on a per-application basis.

Touchegg presents a viable, more conveniently configurable alternative, as long as a simple adjustment for the very sensitive touchpad on the MBPr is done.
(i) Download the [touchegg 1.1.1 source]("http://touchegg.googlecode.com/files/touchegg-1.1.1.tar.gz"), as well as [touchegg-gce for GUI config]("https://github.com/Raffarti/Touchegg-gce/archive/master.zip"), and unpack both.
(ii) Edit *touchegg-1.1.1/src/touchegg/actions/implementation/MoveWindow.cpp* changing lines 47-8 from
[/INDENT]
[INDENT=2]+ attrs.value(GEIS_GESTURE_ATTRIBUTE_DELTA_X).toFloat() * **0.1**,
            + attrs.value(GEIS_GESTURE_ATTRIBUTE_DELTA_Y).toFloat() * **0.1**, 0);
[/INDENT]
[INDENT]to[/INDENT]
[INDENT=2] + attrs.value(GEIS_GESTURE_ATTRIBUTE_DELTA_X).toFloat() * **0.8**,
            + attrs.value(GEIS_GESTURE_ATTRIBUTE_DELTA_Y).toFloat() * **0.8**, 0);
[/INDENT]
[INDENT](iii) compile both according to their respective guides, i.e. [touchegg]("https://code.google.com/p/touchegg/wiki/CompileSourceCode") and [touchegg-gce]("https://github.com/Raffarti/Touchegg-gce").
(iv) If you'd like to give it a try, copy this sample config to ~/.config/touchegg/touchegg.conf
```
<touchégg>
    <settings>
        <property name="composed_gestures_time">300</property>
    </settings>
    <application name="All">
        <gesture type="DRAG" fingers="4" direction="LEFT">
            <action type="SEND_KEYS">Control+Alt+Right</action>
        </gesture>
        <gesture type="DOUBLE_TAP" fingers="4" direction="">
            <action type="MINIMIZE_WINDOW"></action>
        </gesture>
        <gesture type="DRAG" fingers="5" direction="UP">
            <action type="SEND_KEYS">Super+s</action>
        </gesture>
        <gesture type="DRAG" fingers="4" direction="DOWN">
            <action type="SEND_KEYS">Super+w</action>
        </gesture>
        <gesture type="DRAG" fingers="4" direction="UP">
            <action type="SEND_KEYS">Super+Shift+w</action>
        </gesture>
        <gesture type="TAP" fingers="3" direction="">
            <action type="MOUSE_CLICK">BUTTON=2</action>
        </gesture>
        <gesture type="DRAG" fingers="3" direction="ALL">
            <action type="MOVE_WINDOW"></action>
        </gesture>
        <gesture type="DRAG" fingers="4" direction="RIGHT">
            <action type="SEND_KEYS">Control+Alt+Left</action>
        </gesture>
    </application>
    <application name="Chrome-browser, Firefox, Google-chrome-stable, Navigator, Chromium-browser">
        <gesture type="DRAG" fingers="3" direction="RIGHT">
            <action type="SEND_KEYS">Control+Tab</action>
        </gesture>
        <gesture type="DOUBLE_TAP" fingers="3" direction="">
            <action type="SEND_KEYS">Control+w</action>
        </gesture>
        <gesture type="DRAG" fingers="3" direction="LEFT">
            <action type="SEND_KEYS">Control+Shift+Tab</action>
        </gesture>
        <gesture type="DRAG" fingers="3" direction="DOWN">
            <action type="SEND_KEYS">Control+r</action>
        </gesture>
    </application>
    <application name="nautilus, Kpat, Dolphin, Nautilus">
        <gesture type="DRAG" fingers="3" direction="ALL">
            <action type="DRAG_AND_DROP">BUTTON=1</action>
        </gesture>
    </application>
</touchégg>
```

(v) Assuming you're still using synclient, run in a terminal
[/INDENT]
[INDENT=2]synclient ClickFinger3=0
synclient TapButton3=0
[/INDENT]
[INDENT](vi) start touchegg-gce, select a language, load the configuration file, and immediately save it again (starts touchegg).
[/INDENT]
[INDENT=2]Now you'll have ...
Two Finger  - Scroll
Three Finger - Move Window[INDENT]except in Dolphin, Nautilus, Kpat, where it's Drag'n'Drop
[/INDENT]
[INDENT] and Chrome, Chromium, Firefox where it's 
[/INDENT]
[INDENT=2]Left/Right -> prev/next Tab
Down -> refresh Page
[/INDENT]
 Four Fingers -[INDENT]Left/Right -> prev/next workspace
[/INDENT]
[INDENT]Down -> show windows current workspace
                    Up     -> show windows all workspaces
[/INDENT]
 etc.
FYI: If you want to adjust to other applications you'll need their WindowClass. To get this, start the application, then from a terminal run 
[/INDENT]
[INDENT=3]xprop | grep "WM_CLASS(STRING)"[/INDENT]
[INDENT=2]and just click on the application window.
[/INDENT]
(vii) To start touchegg automatically, create an ~/.xprofile with ...[INDENT]    synclient ClickFinger3=0
    synclient TapButton3=0

    touchegg &
[/INDENT]
[INDENT]... reboot, and touchegg works.
[/INDENT]

Finally, a personal preference, install [TimeShift]("http://www.teejeetech.in/p/timeshift.html") ... it just might save your sanity at some point ;-)

---

### Post by Jethro_Borsje on 2015-10-23
This sounds good. Are you able to shutdown your MBP properly or do you still have to hold the power key to really shut it down?

---

### Post by enrico12 on 2015-10-23
Sorry for long pause...too much things to do!

Some problems of flickering are disturbing my 15.10 experience.
I don't know why initially I had none. I'll try later to reinstall graphics driver.

```
lspci | grep VGA
``` gave me this output:

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)



@Jethro_Borsje

Yea, shut down works fine

---

### Post by Jethro_Borsje on 2015-10-23
This is what I get from
```

[COLOR=#000000][FONT=Ubuntu Mono]lspci | grep VGA

```

On 15.04 running on a MBP mid 2015.

> 
[/FONT][/COLOR][FONT=monospace][COLOR=#000000]00:02.0 [/COLOR][COLOR=#FF5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: Intel Corporation Crystal Well Integrated Graphics Controller (rev 08)[/COLOR]
[/FONT]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by MikeBraxner on 2015-10-23
[[COLOR=#000000]@Jethro_Borsje[/COLOR]]("http://ubuntuforums.org/member.php?u=1998759"): 
Shutdown and suspend work just fine, with two notes. (i) Suspend apparently needs the above outlined fix. (ii) In case you auto-start-up a **cairo-dock**, you'll need to add **X-GNOME-Autostart-Delay=20** to *~/.config/autostart/cairo-dock.desktop* in order to be able to shutdown/suspend *from the top-bar menu*. 


@enrico:
While I get the identical lspi output, I have not once experienced a 'flickering' of any sort using 15.10. (A possible difference might be that I installed the last beta, and just kept upgrading.)

---

### Post by berglh on 2015-10-23
I'm not sure if I should start a new thread for MBP11,5. Under 4.2 Kernel on a MacBookPro11,5 (Mid-2015), I can report all of the issues mentioned in this thread in Ubuntu Gnome 15.10. A few other observations:

(1) There is no back-light control, screen just runs at full brightness. This was working fine under 3.19. 
(2) Thunderbolt support works but only if you boot the MBP with the devices plugged in. Hot plugging Thundrebolt is still detrimental to system stability, even if I turn off the external displays in configuration, the Windows of the applications I'm running don't return to the retina display. Need to restart to resolve this problem.
(3) fglrx and fglrx-updates causes MBP to fail on start-up. Almost anything that creates a DKMS kernel module seems to have this issue, perhaps there is something wrong with this component.

On the plus side, keyboard back-light and touch pad were working out of the box, although the multi-gesture support mentioned above looks particularly useful.

I tried the sleep fix mentioned in **@MikeBraxner** (2), after trying all systemd scripts and toggle XCH1, I still experience issues with Power Off and Sleep via Lid Close. The screen turns off, system fans turn on to full speed. I am unable to wake the system from sleep. This is the same whether or not XCH1 is disabled. During sleep the USB devices have turned to low power mode. When I activate the system, the external keyboard and mouse power on, but the retina display stays off. As the MBP11,5 runs the AMD graphics, I wonder if this is the critical difference with the system going to sleep and waking up. One thing working now is the hibernate feature, however, on hibernate the the system does not power down, I still need to manually hold the power button to stop the machine from running. On power on, the system restores the hibernate state. I guess this is a step forward, but there still seems to be a critical step missing for power off on the MBP 11,5.

---

### Post by MikeBraxner on 2015-10-24
@berglh:
(1) Backlight control ... does the backlight control function if you address it manually via */sys/class/backlight/[interface]/brightness*?

(2) Suspend ... (And this is nothing but a stab in the dark) ... a while back, a similar issue arose due to the wireless driver/network manager. Would you mind trying to unload either/both before a suspend call?

---

### Post by berglh on 2015-10-24
[B]@MikeBraxner 

[/B]Thanks for your reply

(1) Backlight control: Keep in mind I have the AMD adapter, my backlight files are in both **/sys/class/backlight/gmux_backlight/brightness** and **/sys/class/backlight/radeon_bl0/brightness**
When setting this value I get (Permission denied) even when running the echo command as sudo. When logged in as root, change the value has no effect on the backlight at all of both files. I suspect the radeon will be the actual control seeing as this appears as my display adapter.

```

  *-display               
       description: VGA compatible controller
       product: Venus XT [Radeon HD 8870M / R9 M270X/M370X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 83
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:80000000-8fffffff memory:b0c00000-b0c3ffff ioport:3000(size=256) memory:b0c40000-b0c5ffff

```

(2) Suspend: As per your suggestion, and it was certainly worth trying, I unloaded the NetworkService, networing unit files from systemd and also unloaded the brcmfmac driver:
  
```

*-network UNCLAIMED     
       description: Network controller
       product: BCM43602 802.11ac Wireless LAN SoC
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b0800000-b0807fff memory:b0400000-b07fffff

```

In all instances the power behaviour is the same. Sleep causes screen to blank and external devices to enter low power mode, unable to wake, system fans still running.
In the case of system halt and power off, the screen and usb devices turn off, but system fans keep running and increase to full speed and then slowly throttle down, never turning off.

Is there some kind of debugging I can do on shutdown and sleep mode to get more useful diagnostic data?

---

### Post by berglh on 2015-10-24
Here is my syslog during shutdown, maybe your ideas on NetworkManager are not too far off. After the shutdown I get the fan spinning still. Any forceful software power off command always results the same state of system fans still running and then increasing in speed.

```

Oct 24 18:26:30 berg systemd[1]: Stopping Daemon for power management...
Oct 24 18:26:30 berg NetworkManager[839]: <warn>  error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (0) Authorization check failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message
 recipient disconnected from message bus without replying
Oct 24 18:26:30 berg systemd[1]: Starting Store Sound Card State...
Oct 24 18:26:30 berg dbus[779]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkitd.service'
Oct 24 18:26:30 berg systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Oct 24 18:26:30 berg NetworkManager[839]: <warn>  error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (0) Authorization check failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Me
ssage recipient disconnected from message bus without replying
Oct 24 18:26:30 berg systemd[1]: Starting Unattended Upgrades Shutdown...
Oct 24 18:26:30 berg NetworkManager[839]: <warn>  error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (0) Authorization check failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message
 recipient disconnected from message bus without replying
Oct 24 18:26:30 berg systemd[1]: Stopping User Manager for UID 121...
Oct 24 18:26:30 berg NetworkManager[839]: <warn>  error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (0) Authorization check failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Me
ssage recipient disconnected from message bus without replying
Oct 24 18:26:30 berg systemd[1]: Stopping Disk Manager...
Oct 24 18:26:30 berg systemd[1216]: Stopped target Default.
Oct 24 18:26:30 berg systemd[1216]: Stopped target Basic System.
Oct 24 18:26:30 berg systemd[1216]: Stopped target Paths.
Oct 24 18:26:30 berg systemd[1216]: Stopped target Timers.
Oct 24 18:26:30 berg systemd[1216]: Stopped target Sockets.
Oct 24 18:26:30 berg systemd[1]: Stopping Authenticate and Authorize Users to Run Privileged Tasks...
Oct 24 18:26:30 berg systemd[1216]: Reached target Shutdown.
Oct 24 18:26:30 berg systemd[1]: Stopping RealtimeKit Scheduling Policy Service...
Oct 24 18:26:30 berg systemd[1693]: Starting Exit the Session...
Oct 24 18:26:30 berg systemd[1216]: Starting Exit the Session...
Oct 24 18:26:30 berg systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Oct 24 18:26:30 berg systemd[1]: Stopped target Graphical Interface.
Oct 24 18:26:30 berg systemd[1]: Stopping GNOME Display Manager...
Oct 24 18:26:30 berg systemd[1]: Stopping Accounts Service...
Oct 24 18:26:30 berg systemd[1]: Stopped target Multi-User System.
Oct 24 18:26:30 berg systemd[1]: Stopping Make remote CUPS printers available locally...
Oct 24 18:26:30 berg systemd[1]: Stopped Initialize hardware monitoring sensors.
Oct 24 18:26:30 berg systemd[1]: Stopping LSB: automatic crash report generation...
Oct 24 18:26:30 berg systemd[1]: Stopped target Login Prompts.
Oct 24 18:26:30 berg systemd[1]: Stopping Getty on tty1...
Oct 24 18:26:30 berg gdm[1169]: Tried to look up non-existent conversation gdm-launch-environment
Oct 24 18:26:30 berg gdm[1169]: Freeing conversation 'gdm-launch-environment' with active job
Oct 24 18:26:30 berg gdm[1169]: Freeing conversation 'gdm-password' with active job
Oct 24 18:26:30 berg rsyslogd: [origin software="rsyslogd" swVersion="8.12.0" x-pid="833" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

I also tried the systemd debug-mode shutdown and was unable to get to the debug terminal before the screen switched off. This makes me wonder if it's more of a power management compatibility issue. it also happens on the LiveUSB version of Ubuntu, so it's a consistent problem with this machine. I've also reset the SMC just in case.

---

### Post by MikeBraxner on 2015-10-24
@berglh:
Backlight ... **Two** active interfaces in /sys/class/backlight. You might want to try booting with kernel parameter *acpi_backlight=vendor* ... have a look at the [Backlight Wiki]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight").

Suspend ... I can only spitball, but if powermanagement might be an issue, have you considered installing tlp? Maybe someone who actually knows what their talking about could step in.

---

### Post by ssj71 on 2015-11-06
I'm having similar trouble with my 11,3 MBP with nvidea driver. Only 1 interface (/sys/class/backlight/gmux_backlight) but changing it has no effect. Also the max_brightness says -1. dmsg does have some entries for it though. I was able to control it though backlight/acpi_video0 before.

---

### Post by MikeBraxner on 2015-11-07
@ssj71: Two brief thoughts on ... *"nvidea driver. Only 1 interface (/sys/class/backlight/gmux_backlight) but changing it has no effect."* 

First, this could be a timing-issue with apple-gmux de-registering all interfaces but gmux, while the system/DE simply does not refresh it's initial list of interfaces. [Have a look here for an old patch and script]("http://ubuntuforums.org/showthread.php?t=2006475&p=12309146#post12309146") (should still work, even if you have to fiddle by hand).

Second, as pointed out in the final comment in that posting, I would suggest trying to adjust the brightness ***after** a suspend* ... used to work back then ;-)

---

