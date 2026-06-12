---
title: "Installing Lubuntu on a 2003 second edition eMac fails?"
date: 2013-05-24
forum: Apple Hardware Users
---

### Post by Minifig666 on 2013-05-24
Hi Folks,
I've been given a pair of eMacs and I want to try and get one going with Lubuntu. I got the most recent powerpc iso from the lubuntu website, and after removing the paper that had been wedged in the disk tray (art students... :P ) I managed to boot the disk. I've tried the boot options live, live-powerpc, and live-powerpc video=of(iForgot). All the modes run ever so far through the splash screen, then drop to a text display, the last line of which reads "Fixing recursive fault but reboot is needed!"
Before that point there is some mention of looking for sound hardware, but nothing particularly useful. (Well to me anyway!) See [http://25.media.tumblr.com/6399c56ef63ca906ca747396a30637a7/tumblr_mn9vyo8UM01ror2c7o1_1280.jpg](http://25.media.tumblr.com/6399c56ef63ca906ca747396a30637a7/tumblr_mn9vyo8UM01ror2c7o1_1280.jpg) for a screenshot.

I guess it's worth mentioning, I've replaced the HDD that was in the machine with a completely blank WD 40GB disk (non-apple branded) because I don't want to lose the 10.2 install that is on there already. I'm not particularly experienced with apple hardware, but I guess this wouldn't change anything.

Thanks in advance for your help,
-Mini

---

### Post by michiganmac on 2013-05-24
> **Minifig666 said:**
> Hi Folks,
I've been given a pair of eMacs and I want to try and get one going with Lubuntu. I got the most recent powerpc iso from the lubuntu website, and after removing the paper that had been wedged in the disk tray (art students... :P ) I managed to boot the disk. I've tried the boot options live, live-powerpc, and live-powerpc video=of(iForgot). All the modes run ever so far through the splash screen, then drop to a text display, the last line of which reads "Fixing recursive fault but reboot is needed!"
Before that point there is some mention of looking for sound hardware, but nothing particularly useful. (Well to me anyway!) See [http://25.media.tumblr.com/6399c56ef63ca906ca747396a30637a7/tumblr_mn9vyo8UM01ror2c7o1_1280.jpg](http://25.media.tumblr.com/6399c56ef63ca906ca747396a30637a7/tumblr_mn9vyo8UM01ror2c7o1_1280.jpg) for a screenshot.

I guess it's worth mentioning, I've replaced the HDD that was in the machine with a completely blank WD 40GB disk (non-apple branded) because I don't want to lose the 10.2 install that is on there already. I'm not particularly experienced with apple hardware, but I guess this wouldn't change anything.

Thanks in advance for your help,
-Mini

[FONT=Verdana]This should get you past the "recursive..." error:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Type it in at the boot: prompt.

Also, read the wiki. Most questions can be answered there. 
[/FONT]
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

[FONT=Verdana]Good luck![/FONT]

---

### Post by Andre_Strauss on 2013-08-14
Thanks for the advice. That worked great. I now have a working installation of Lubuntu 12.4 on my old emac.

I just cannot get the soundcard to work. I tried both snd-powermac and snd-aoa, but nothing works. Any advice will be appreciated

Thanks

Andre

---

### Post by tgalati4 on 2013-08-14
Does the sound work in 10.2?  It's possible that the sound chips are blown out.  With built-in speakers those old eMacs were often used as jukeboxes.

I presume you tried everything in:  [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

Open a terminal and post the following:

```
lsmod | grep snd
```

---

### Post by pauljwells-m on 2013-08-14
Not sure if it's valid for 12.04, but on 13.04 there's an installer bug that blacklists the sound drivers. Look in /etc/modprobe.d/blacklist.local.conf and comment out the sound driver references (add a # to anything with a 'snd' in it)

---

