---
title: "Sound Failing after Reboot"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by squizzi on 2008-02-10
Today I decided to apt-get autoremove a few packages, and after reboot no longer had sound in any applications.  I read through the ALSA guide, but am pretty confused on installing the drivers for it, although my audio devices are showing up in terminal, and I made sure nothing was muted in alsamixer.

My device is a nVidia Conexant HD Internal Soundcard - on my HP dv2000 Laptop

The sound works in Vista so I know its just Ubuntu. ( I am dual booting ).

I'm running Ubuntu 7.10 Gutsy.

I really have no where else to turn, and am a pretty big Linux noob.

Any help would be appreciated.

---

### Post by spiderbatdad on 2008-02-10
you might try ```
asoundconf list
asoundconf set-default-card Result
```
Where Result would be a parameter obtained from the first command. It should be a parameter like:ICH8002CH3, not just a device name. Also:```
man asoundconf
```may provide you with useful information. You may need to reboot after setting default, for some reason it doesn't seem to modprobe on it's own.

---

### Post by jwmislan on 2008-02-10
> **squizzi said:**
> Today I decided to apt-get autoremove a few packages, and after reboot no longer had sound in any applications.  I read through the ALSA guide, but am pretty confused on installing the drivers for it, although my audio devices are showing up in terminal, and I made sure nothing was muted in alsamixer.
  I'm running Ubuntu 7.10 Gutsy.
 Any help would be appreciated.

Hi squizzi 
apt-get --autoremove should not remove any needed/important packages.

Take a look at synaptic ( apt-get gui ) by your keyboard keys, (alt) + (F2) and type in, sudo synaptic
answer password with your login password

When you are in synaptic, click search, and type in 
alsa
you will then see all the alsa - libalsa - applications, and libraries that are currently installed  (green boxes), along with  un-installed alsa related apps - ( white boxes ).

If you select/highlight any installed, or un-installed application here, you  will see explanations/comments/details ( bottom box ), about what they are.

You can get a good perspective - overview from doing this, and also become a little more familiar with your Ubuntu Os.

Hope this is of some help to you - Happy Ubuntuing ! : -

JWM

---

### Post by squizzi on 2008-02-10
Thanks for the help guys, spider, that worked, thanks!

---

### Post by spiderbatdad on 2008-02-10
woot!

---

