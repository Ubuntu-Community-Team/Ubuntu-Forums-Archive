---
title: "Microphone fix messes up iSight?!"
date: 2011-01-21
forum: Apple Hardware Users
---

### Post by cdnaerogeek on 2011-01-21
I loaded Skype onto my Macbook Pro 5,5 under Ubuntu and initially the video worked just fine, but the microphone did not (based on Skype's internal testing of the configuration). Taking the advice of [this thread]("http://ubuntuforums.org/showthread.php?t=1439009"), I installed the PulseAudio packages, played with the settings and the microphone worked.

However, when I went to test the video again it stopped working. I tried rebooting the computer but that didn't fix the problem. Furthermore, the /dev/video0 folder (which Skype linked to before) just disappeared. As I said, the iSight camera seemed to work out of the box, but the only change that I recall making to the system was the PulseAudio install above.

Has anyone else had this problem? How do I get iSight working again?

---

### Post by Hatsune Miku on 2011-01-21
> **cdnaerogeek said:**
> I loaded Skype onto my Macbook Pro 5,5 under Ubuntu and initially the video worked just fine, but the microphone did not (based on Skype's internal testing of the configuration). Taking the advice of [this thread]("http://ubuntuforums.org/showthread.php?t=1439009"), I installed the PulseAudio packages, played with the settings and the microphone worked.

However, when I went to test the video again it stopped working. I tried rebooting the computer but that didn't fix the problem. Furthermore, the /dev/video0 folder (which Skype linked to before) just disappeared. As I said, the iSight camera seemed to work out of the box, but the only change that I recall making to the system was the PulseAudio install above.

Has anyone else had this problem? How do I get iSight working again?


Your going to look at my like im crazy but i had the same problem on a Macbook pro 5,4

iSight will not work because there is not enough power for the USB buss on the Mac itself. I fixed this problem by rebooting and using ALSA. Just install gnome-alsamixer and check the recording tab under the microphone.

I know it sounds odd, but thats wat PowerTop told me (You can install this from repositories) Along with a few log entries from the Linux kernel itself.

---

### Post by cdnaerogeek on 2011-01-21
Thanks for the tip. Power does seem to be an issue. I got rid of my earlier PulseAudio installation and I can detect the camera again. However, it's still flaky -- the camera doesn't want to "turn on" anymore even though it has been detected in both Skype and Cheese.

Any other hints?

---

### Post by Hatsune Miku on 2011-01-21
> **cdnaerogeek said:**
> Thanks for the tip. Power does seem to be an issue. I got rid of my earlier PulseAudio installation and I can detect the camera again. However, it's still flaky -- the camera doesn't want to "turn on" anymore even though it has been detected in both Skype and Cheese.

Any other hints?

Usually a reboot fixed this for me. Yes, a lot of rebooting lol.

---

### Post by cdnaerogeek on 2011-01-21
Strangely, several reboots and one try of turning it off and on again don't produce any improvement. Occasionally, I even regress into losing /dev/video0/ again.

I also downloaded powertop, but I can't make much sense of the output. Here's a sample:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (12.1%)         2.53 Ghz     1.9%
polling           6.9ms ( 0.0%)         2.13 Ghz     0.1%
C1 mwait          0.1ms ( 0.0%)         1.87 Ghz     0.6%
C2 mwait          0.5ms ( 3.1%)         1.60 Ghz     0.2%
C4 mwait          2.3ms (84.8%)          798 Mhz    97.2%

Wakeups-from-idle per second : 437.8    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  12.6% ( 58.5)D  skype
  19.5% ( 90.4)   [kernel scheduler] Load balancing tick
  12.2% ( 56.3)   [extra timer interrupt]
   8.7% ( 40.2)   [eth1, HDA Intel] <interrupt>
   8.1% ( 37.5)   pulseaudio
   6.1% ( 28.0)   USB device  2-5 : Card Reader (Apple)

Suggestion: Enable USB autosuspend for non-input devices by pressing the U key


```

Let me know if anything jumps out at you. I'll keep playing around in the meantime.

---

### Post by Hatsune Miku on 2011-01-21
> **cdnaerogeek said:**
> Strangely, several reboots and one try of turning it off and on again don't produce any improvement. Occasionally, I even regress into losing /dev/video0/ again.

I also downloaded powertop, but I can't make much sense of the output. Here's a sample:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (12.1%)         2.53 Ghz     1.9%
polling           6.9ms ( 0.0%)         2.13 Ghz     0.1%
C1 mwait          0.1ms ( 0.0%)         1.87 Ghz     0.6%
C2 mwait          0.5ms ( 3.1%)         1.60 Ghz     0.2%
C4 mwait          2.3ms (84.8%)          798 Mhz    97.2%

Wakeups-from-idle per second : 437.8    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  12.6% ( 58.5)D  skype
  19.5% ( 90.4)   [kernel scheduler] Load balancing tick
  12.2% ( 56.3)   [extra timer interrupt]
   8.7% ( 40.2)   [eth1, HDA Intel] <interrupt>
   8.1% ( 37.5)   pulseaudio
   6.1% ( 28.0)   USB device  2-5 : Card Reader (Apple)

Suggestion: Enable USB autosuspend for non-input devices by pressing the U key


```

Let me know if anything jumps out at you. I'll keep playing around in the meantime.

You stil have pulse audio install >.>

---

### Post by cdnaerogeek on 2011-01-24
I noticed that, but I don't know what to do about it. Under Synaptic, if I mark the main pulseaudio package for removal, the ubuntu-desktop package also wants to be removed, and I REALLY don't want to touch that one.

---

### Post by cdnaerogeek on 2011-01-25
Ok, I solved my own problem. Downloading the appropriate isight-firmware-tools package from the Mactel support repository (which I had not done previously) and then turning off the laptop and on again makes the camera work. Now I can use cheese and skype without any issues.

---

