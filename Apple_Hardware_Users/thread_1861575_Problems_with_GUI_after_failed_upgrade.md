---
title: "Problems with GUI after failed upgrade"
date: 2011-10-15
forum: Apple Hardware Users
---

### Post by liquidmetalcobra on 2011-10-15
In the middle of upgrading my computer to 11.10 from 11.04, I had a power issue and the computer shutdown. When I turned it back on, I reached a black screen and it wouldn't let me login. 

intel ips 0000:00:1f.6: failed to get i915 symbols,
graphics turbo disabled

Something like this was the issue. However, further tampering with the system made the problem worse. Now the graphics aren't even loaded. Here is the current text that is displayed:

Only access through ALSA is available on amd64 but slamr driver was chosen!
Make sure that an ALSA driver for your chipset is available and is loaded
and that access to SmartLink modem components is supported by it. 
 * Starting disk tempearture monitoring daemon hddtemp: [ OK ]
Rater than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S20plymouth-splash start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S20plymouth-splash
start: Unknown job: S20plymouth-splash
Starting poker server : not configured, abort.
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting the Winbind daemon winbind [ OK ]
 * Starting bluetooth [ OK ]
Starting UPS Power management: apcupsd.
 * PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Enabling additional executable binary formats binfmt-support [ OK ]
 * CHecking battery state... [ OK ] 



However, nothing else happens, and nothing is loaded. Additionally, I can't seem to resume the upgrade via tty1, because of an internal error.
E: Internal Error, could not early remove liblcmsl

I can log on fine though...
 
Please help

---

