---
title: "I'm trying to install sound drivers manually without a package"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by NeptuneUK on 2008-04-02
Which is difficult for a newbie.
I've had a look through a couple of installation guides but can't find anything relevant enough to help.
The drivers come with a readme

```
STEPS TO BUILD DRIVER
================================================================================

  1. Backup the Config.in and Makefile in the sound driver directory
     (/usr/src/linux/driver/sound).
     The Configure.help provide help when you config driver in step
     4, please backup the original one (/usr/src/linux/Document) and
     copy this file.
     The cmpci is document for the driver in detail, please copy it
     to /usr/src/linux/Document/sound so you can refer it. Backup if
     there is already one.

  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above
     directory.

  3. Change directory to /usr/src/linux

  4. Config cm8338 driver by 'make menuconfig', 'make config' or
     'make xconfig' command.

  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI
     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.
     For driver option, please refer 'DRIVER PARAMETER'

  6. Compile the kernel if necessary.

  7. Compile the modules by 'make modules'.

  8. Install the modules by 'make modules_install'


INSTALL DRIVER
================================================================================

  1. Before first time to run the driver, create module dependency by
     'depmod -a'

  2. To install the driver manually, enter 'modprobe cmpci'.

  3. Driver installation for various distributions:

    a. Slackware 4.0
       Add the 'modprobe cmpci' command in your /etc/rc.d/rc.modules
       file.so you can start the driver automatically each time booting.

    b. Caldera OpenLinux 2.2
       Use LISA to load the cmpci module.

    c. RedHat 6.0 and S.u.S.E. 6.1
       Add following command in /etc/conf.modules:

       alias sound cmpci

```

As an experienced windows user this is alien to me!
first off I can't write any files to the src folder through drag and drop because I don't have permission to do so apparently. And I don't know of any other way to do so.

Note I have just put a new soundcard in, it works but the incorrect driver is installed and I think this is causing my skype problems.


This cheapo soundcard is most likely supported by ALSA so I will try and uninstall the existing drivers and try reinstalling ALSA properly...

---

### Post by taavikko on 2008-04-02
First of all, what card you have?
```
lspci
```

Is it already recognized?
```
lsmod |grep snd
```

Is it detected
```
asoundconf list
```

---

### Post by NeptuneUK on 2008-04-02
Its a Genius 5.1 sound card, but the driver is a C-media one...
I need to remove the existing driver and reinstall the correct one from ALSA
But I could do with some advice to point me in the right direction please.

---

