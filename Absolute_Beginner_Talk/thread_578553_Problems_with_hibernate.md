---
title: "Problems with hibernate"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by jfarhou on 2007-10-17
Hello all, I'm brand new to the forums, and brand new to ubuntu/linux.  I'm pretty much loving the transition from windows, but recently I have been having some problems.  I changed my power options so that my laptop hibernates anytime I close the lid.  Anytime I bring the computer out of hibernation, it acts as though it's booting up, then I get some sort of error message, and then the screen display is basically discombobulated chaos.  After about 5 more seconds ubuntu starts just like normal, and gives me some sort of hibernation error message.  How can I fix this?

Also, on a related note, anytime I leave my computer on for too long and it stays inactive, my external speakers either play no sound, or play at a much quieter level than the max.  I'm clueless, any ideas as to what's wrong?


Cheers

---

### Post by 1337455 10534 on 2007-10-17
Hi! Welcome to the forums!
I had the exact same problem on Feisty, never got fixed (are u using an HP?). Gutsy fixes everything beautifully.

---

### Post by iv2101 on 2007-10-26
I have no error messages on my dell inspiron 1420, but the sound doesn't work after returning from hibernation. In addition, the network manager occasionally freezes and needs to be restarted. I used to have a similar sound problem with Ubuntu 7.04, but it used to fail only sometimes, not after every hibernation.

---

### Post by MegaJim on 2007-10-26
You can see a list of modules for restarting in

```
sudo gedit  /etc/default/acpi-support
```

Try putting your modules for the sound card in the MODULES="" line

---

### Post by iv2101 on 2007-10-26
Seems to work for the sound.

Thank you, MegaJim

---

### Post by iv2101 on 2007-10-27
I lied about the sound: it only worked the first time but doesn't work now:( here is my /etc/default/acpi-support



```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

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
MODULES="
snd_hda_intel         
snd_pcm_oss          
snd_mixer_oss        
snd_pcm            
snd_seq_dummy       
snd_seq_oss          
snd_seq_midi        
snd_rawmidi         
snd_seq_midi_event  
snd_seq             
snd_timer           
snd_seq_device       
snd                 
soundcore       
snd_page_alloc  "

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12
```

---

