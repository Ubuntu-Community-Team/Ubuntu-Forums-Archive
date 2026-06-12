---
title: "Making a device location static"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2008-01-05
I have a tv card that comes with its own dsp driver. I'm also using a USB microphone which creates a dsp driver. Or it could be my webcam doing that, but I can't imagine why.

On that note, the tv card also creates a /dev/videoN entry, as does the webcam.

This becomes a problem because they tend to switch their indexes around after a reboot, forcing me to go through drawn-out reconfigurations of mythtv whenever I want to watch.

Here's my device layout at the moment:

/dev/dsp1: Logitech Microphone
/dev/dsp2: pcHDTV 5500 Audio Device
/dev/video0: Logitech Quickcam
/dev/video1: pcHDTV 5500 Video Device

I'd like to keep it this way. Is there a way to do this?
Thanks.

---

### Post by kidders on 2008-01-06
Hi there,

I'd recommend a slight variation on what you've suggested. My personal preference would be to let Ubuntu carry on arbitrarily reordering your audio/video devices, and configure additional symlinks with fixed names (eg /dev/pteri498/logitech_mic, /dev/pteri498/logitech_cam, etc.) that point to the correct "real" /dev paths. This approach is similar to the way the symlinks in /dev/disk/by-uuid or /dev/disk/by-label would continue pointing to the correct partitions, even if /dev/sda1 suddenly became /dev/sdc1.

There's plenty of help on doing this sort of thing available, but to get you started...
[LIST]
[*]Take a look at /etc/udev/rules.d ... you should find a collection of rulesets provided by Ubuntu, used to configure your device interfaces. The numbers at the start of the filenames dictate the order in which the files are processed.
[*]I would strongly recommend *against* altering any of these, for a variety of reasons. Instead, you should create one of your own.
[*]You can use the SYMLINK directive to set up rules that create symbolic links with fixed, easily recognisable names.
[*]Unfortunately, you may need to reboot to force udev to re-evaluate the device names for anything you can't unplug (eg a PCI sound card), so I would suggest playing around with your webcam first. Once you've got the hang of how udev works, you'll hopefully be able to get your TV card right in one shot.[/LIST]Some additional notes...

[SIZE=1]I - You might find you'd like to create two new rulesets, rather than just one. I'm using two on my box (one with a low number at the start, and one with a high one), so I can control when my custom udev rules get processed.

II - Modifying Ubuntu's own udev rules can have unpredictable long-term side effects, especially if a future system update were to include an update to udev. Another good reason for creating your own is so you can have a self-contained config file you could burn onto a CD (along with your xorg.conf, and other useful files). That way, should you ever want to reinstall Ubuntu, or perhaps try a different Linux distro, making your webcam & TV card work the way you like them again would be a simple matter of copying a file.

III - Some (badly written) software uses the _names_ of /dev nodes to decide what sort of devices they point to. As a result, you might find /dev/dsp9 a better symlink name for your TV card than /dev/tvcard, because it follows the general form "dsp" + number. It's much less friendly-looking, but is less likely to cause irritating problems.
[/SIZE]
Anyhow, I hope that helps.

---

