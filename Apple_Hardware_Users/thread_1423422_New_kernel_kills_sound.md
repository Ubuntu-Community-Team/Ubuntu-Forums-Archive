---
title: "New kernel kills sound"
date: 2010-03-06
forum: Apple Hardware Users
---

### Post by CJN on 2010-03-06
So I figured I'd give a heads up to anyone out there with a MBP 5,3 who updated/wants to update to kernel 2.6.31.20, none of the documented or forum fixes work to get the sound up and running on this one, so I guess either use a different kernel, patch it, or live without sound until 2.6.31.21 (or whenever this gets fixed).

---

### Post by Jasev on 2010-03-06
Same thing here on a MacBook Pro 5,5. Does anyone know of a solution?

---

### Post by gcndavidmn on 2010-03-07
I can confirm that the same happens on a macbook pro 5.4 running 9.10 64bit.

---

### Post by viktara on 2010-03-07
To understand the problem a little:

- Which method have you used for trying to get the sound to work? (The backports method has worked most consistently for me):

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic

Reboot

sudo apt-get install gnome-alsamixer

Run gnome-alsamixer and unmute the front and surround speakers
```

- If you run gnome-alsamixer what is the sound card labelled as?

- Do you get the volume sliders as on the screenshot?:
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound)

- Do you get sound from the headphone socket?

---

### Post by gcndavidmn on 2010-03-07
I don't get that. I just get this [http://farm3.static.flickr.com/2680/4412825613_0f6ea9aa6e_o.png](http://farm3.static.flickr.com/2680/4412825613_0f6ea9aa6e_o.png)

---

### Post by viktara on 2010-03-07
Which version of the backports package (linux-backports-modules-alsa-karmic-generic) is on your system?

---

### Post by Jasev on 2010-03-07
I'm running linux-backports-modules-alsa-karmic-generic 2.6.31.20.33. (and linux-backports-modules-alsa-karmic-generic-pae)

There were no problems with the previous kernel. (I'm using the Backports method you describe). Since upgrading the kernerl (~3 days ago), there is no hardware listed in "Sound Preferences" and (as expected) I get absolutely no sound.

I guess the new kernel is not recognising the sound card for some reason.......?

---

### Post by gcndavidmn on 2010-03-07
> **Jasev said:**
> I'm running linux-backports-modules-alsa-karmic-generic 2.6.31.20.33. (and linux-backports-modules-alsa-karmic-generic-pae)

There were no problems with the previous kernel. (I'm using the Backports method you describe). Since upgrading the kernerl (~3 days ago), there is no hardware listed in "Sound Preferences" and (as expected) I get absolutely no sound.

I guess the new kernel is not recognising the sound card for some reason.......?

That is my best guess too.

---

### Post by viktara on 2010-03-07
> **Jasev said:**
> I'm running linux-backports-modules-alsa-karmic-generic 2.6.31.20.33. (and linux-backports-modules-alsa-karmic-generic-pae)



Should you have the pae version installed? My 5,3 doesn't.

It's a bit tricky for me to verify now however - as I have upgraded to lucid.

---

### Post by gcndavidmn on 2010-03-07
I am new to linux but could we trouble shoot this and work out if it was definitely the kernel update by downgrading to the previous one where we had sound working? I wouldn't know how to do that though.

---

### Post by CJN on 2010-03-07
To add in my situation, I have the backports installed (2.6.31.20.33 same as gcndavidmn) but I see no sliders at all in gnome-alsa-mixer. I also tried the other method (compiling from source it seems...), and nothing happened there either. In alsa mixer I see Cirrus Logic CS4206 sound card in the tab title, but there are NO SLIDERS, not even a master volume.

---

### Post by gcndavidmn on 2010-03-07
I have been trying many many thing, none of which solved the problem, and I encountered the same issue with no sliders. I am trying a fresh install now (I had only just done one so I haven't lost anything) of Ubuntu 9.10 32bit. Its a bit annoying to be honest.

---

### Post by Ronksu on 2010-03-07
Similar situation with CJN. MBP5,5, Karmic, lost sound after latest kernel update (2.6.31-20-generic). Sound card is detected, but mixer elements are missing.

$ alsamixer 
No mixer elems found

DMESG shows this:
[   23.076100] hda_codec: cannot build controlsfor #0 (error -22)

I have tried linux-backports-modules-alsa-2.6.31-20-generic 2.6.31-20.22. When that didn't work, I tried compiling alsa-driver (1.0.22.1) by hand. No help from there either, although [http://ubuntuforums.org/showthread.php?t=1361864&page=2](http://ubuntuforums.org/showthread.php?t=1361864&page=2) suggested it would.

I can provide more info if somebody says what would be usefull.

---

### Post by viktara on 2010-03-07
> **gcndavidmn said:**
> I am new to linux but could we trouble shoot this and work out if it was definitely the kernel update by downgrading to the previous one where we had sound working? I wouldn't know how to do that though.

You could just install the old kernel using synaptic - that should take care of it for you.

---

### Post by viktara on 2010-03-07
> **gcndavidmn said:**
> I have been trying many many thing, none of which solved the problem, and I encountered the same issue with no sliders. I am trying a fresh install now (I had only just done one so I haven't lost anything) of Ubuntu 9.10 32bit. Its a bit annoying to be honest.

I guess the fresh install will work - until you update the kernel to the latest version.

I can verify it is working fine in Lucid (consider upgrading?) - so it seems like it is just the kernel version.

I'm not sure why you have the pae version of the alsa module though - see if it's still installed after your reinstall.

---

### Post by gcndavidmn on 2010-03-07
The plot thickens:
I reinstalled with a 32bit version of Ubuntu that I know worked with the sound. After pulling down all the updates I had the same issue this is the 2.6.31-20-generic-pae version of ubuntu.

I am well out of my depth now :(

---

### Post by viktara on 2010-03-08
> **gcndavidmn said:**
> The plot thickens:
I reinstalled with a 32bit version of Ubuntu that I know worked with the sound. After pulling down all the updates I had the same issue this is the 2.6.31-20-generic-pae version of ubuntu.

I am well out of my depth now :(

Did you try installing the previous kernel? It worked with the older kernel - so maybe just stick with that for now?

You should be able to install the old one using synaptic.

---

### Post by gcndavidmn on 2010-03-08
I will have to have another try at that. Was -19 working with sound? (I ask this just to make sure I don't go heading in the wrong direction from the outset).

---

### Post by rcurts on 2010-03-08
Same problem here with MBP 5,4.  This is a new install, and I haven't tested  any other kernel versions.  Hoping I can get a tip on downgrading to the correct kernel version here.  Cheers.

---

### Post by viktara on 2010-03-08
> **gcndavidmn said:**
> I will have to have another try at that. Was -19 working with sound? (I ask this just to make sure I don't go heading in the wrong direction from the outset).

Just pick the one previous to the current kernel - people only seem to be reporting this with the current version.

---

### Post by Ronksu on 2010-03-08
Booting back to 2.6.31-19, and sound works fine with linux-backports-modules-alsa-2.6.31-19-generic.

If you have just upgraded from -19 to -20, you should still have the option to boot to -19 in grub. Just remember to unmute from mixer if you uninstalled the drivers while trying to get -20 to work.

If someone is interested in digging out the reason why sound does not work with -20, I'm willing to provide more info and act as a guinea pig. Until then, I'll just try to remember to boot to -19 :)

---

### Post by gcndavidmn on 2010-03-08
When I get some free time I will install -19.

You could use something like startup-manager to automatically go into -19 until -20 is fixed.

---

### Post by Jason O on 2010-03-08
I've confirmed that sound works great with the -19 kernel and the alsa backport on a MacBook Pro 5,4. I'll update the Wiki to include a note about this issue.

Thanks!

**How to fix**
Install the following packages through synaptic:

linux-image-2.6.31-19-generic
linux-backports-modules-alsa-2.6.31-19-generic
gnome-alsamixer

- Reboot
- Select the 2.6.31-19 kernel option in grub during boot

You'll probably be running in low graphics mode, don't worry. Just click ok and continue with boot.

Open gnome-alsamixer (Applications >> Sound and Video >> GNOME ALSA Mixer) un-mute everthing and turn up Front Sp.

Sound should now work.

You'll have to reinstall you're Nvidia driver. And if you want to boot into the -19 kernel from now on, install the startupmanager package and run the program then select the -19 kernel from the list.

---

### Post by Jasev on 2010-03-08
Thanks all for comments and ideas.

It's also working fine for me in -19. Hopefully this will be fixed in the next kernel release. Using GRUB to run -19 at the moment.

---

### Post by gcndavidmn on 2010-03-09
Thanks Jason. I will do that this afternoon.

---

### Post by archonro on 2010-03-09
Having the same problem here with an M-audio 2496 after upgrading to -20. Sound card is detected but no modules are loaded. 

Works when booting -19. Worth mentioning that it worked perfectly before upgrading.

I'm still having minor problems with sound partially working, but I may have caused it after recompiling alsa :???:

---

### Post by ZeroLinux on 2010-03-09
Does mic work after this?

---

### Post by gcndavidmn on 2010-03-09
HAHAH! BRILLIANT! Thank you Jason.

I think that the Ubuntu community is the most helpful one on the net.

---

### Post by nmsbaeta on 2010-03-09
I've just installed Ubuntu 9.10 on a MacBook6,1 and upgraded the system.  I now have the -20 kernel and no sound.

To try solving this problem I installed -19 kernel and -19 alsa backport modules.

Now my "big" problem.  How do I choose the -19 kernel in Grub?  I don't get any option to do so :-(

---

### Post by archonro on 2010-03-10
If you're saying that you already installed -19 you should be running that  version.
You can see your kernel version by running uname -r




Can anyone confirm that when booting -19 from grub sound works as it  should? I'm not sure if the problem I'm having (no youtube sound from  firefox or chrome) is because things I did trying to fix the sound with  -20.

---

### Post by miatawnt2b on 2010-03-10
I uninstalled all of the backports and put on kernel 2.6.32-020632-generic.  This fixes all sound issues.

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

-J

---

### Post by gcndavidmn on 2010-03-10
I can confirm that once you boot into -19 and install the correct version of backports sound works perfectly.

I am using a MBP 5.4

---

### Post by raulsan on 2010-03-10
I also confirm sound works good after booting with -19 and unmuting Front Sp and Master in alsamixer.
I am using a Macbook pro 5.5

---

### Post by nmsbaeta on 2010-03-10
Hello!

> **archonro said:**
> If you're saying that you already installed -19 you should be running that  version.
You can see your kernel version by running uname -r




Can anyone confirm that when booting -19 from grub sound works as it  should? I'm not sure if the problem I'm having (no youtube sound from  firefox or chrome) is because things I did trying to fix the sound with  -20.

After messing aroud with Grub's configuration file, I manage to be able  to select the kernel I want to boot (and booted with -19).

I can also confirm that, on my MacBook6,1,  once you boot into -19 and install the correct  version of backports sound works perfectly.

---

### Post by linuxopjemac on 2010-03-11
I am glad to hear that at least one kernel version is doing the right job.

---

### Post by andrejknz on 2010-04-19
I also confirm that sound works with -19 but I have another problem now, my wifi is not working at all even if i reinstall the drivers.
Any help?

---

### Post by Ronksu on 2010-06-29
Has anyone got sound working with a later kernel than 2.6.31-19? -20 was a clear no go, but I haven't had any progress with -21 or -22 either. Anyone else with better skills/luck? =)

Judging from the messages above, putting in 2.6.32 does the trick, but I'd like to remain on the 'official' track with these and minimize the manual hassle.

---

