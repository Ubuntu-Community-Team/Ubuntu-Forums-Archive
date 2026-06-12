---
title: "how to find sound modules snd, powerpc Quantal"
date: 2012-10-10
forum: Apple Hardware Users
---

### Post by 2blue on 2012-10-10
iBook G4, 2005. 

I have been through the [PPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F") and the [pages]("https://help.ubuntu.com/community/Loadable_Modules") it links to for further detail with out any success in making alsamixer launch. I have been on the subject for many days and with out being able to get anywhere. I may have made an awful mess, hopefully managable. 


The initial problem was alsamixer would not launch in terminal even if all the packages and seemingly approapriate drivers where loaded (they probably were not though). Something has changed in Quantal I am not able to track down. Does anyone now how to go about this? 

This is what I get when trying to launch alsamixer at the moment: 

:~$ alsamixer
cannot open mixer: No such file or directory
taoseeker@taoseeker:~$ alsa -b
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
taoseeker@taoseeker:~$ alsa -a
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
taoseeker@taoseeker:~$ alsa -a reload
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
taoseeker@taoseeker:~$ alsa force-reload
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 135: /sbin/alsa: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-aoa-fabric-layout snd-aoa-soundbus snd-aoa snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).

---

