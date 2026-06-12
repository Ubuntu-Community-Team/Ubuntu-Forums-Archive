---
title: "[SOLVED] Headphone Jack Problems on Laptop"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-10
I'm not sure where to start with this one, but on my Acer Extensa 5620 Laptop, the speakers work fine, but when I plug in a pair of headphones to the front jack (the only jack mind you), sound keeps coming out of the speakers and not the headphones. Does anyone know how to get Kubuntu to automatically detect the headphones and switch sound output to them?

---

### Post by neurostu on 2008-03-10
I don't think it is an issue with the hardware. I actually think the hardware is wired to redirect audio to the headphone jack when headphones are present. You might want to check the support forums for your laptop.

---

### Post by spacefreak86 on 2008-03-10
I gathered it wasn't a hardware issue as I'm dual booting in XP Pro and don't have an issue with it. Do I need to install or enable something in Kubuntu to get to software to tell the hardware to make that switch?

---

### Post by neurostu on 2008-03-10
hmm....

That is really weird. I have never heard of this problem before.....  do you have the same problem when you boot from the live cd?

---

### Post by edd07 on 2008-03-10
I have exactly the same problem on an Acer Aspire 3680. Works fine in Windows.
Yeah, this is really weird, and I've looked everywhere for the answer, but no luck :-(

---

### Post by spacefreak86 on 2008-03-10
Running from LiveCD now, and not a single sound does work. Granted, I'm having to base that off of Wikipedia sounds since Amarok won't play MP3's on the partition that holds my music files (or play MP3s at all since I'd need the codec for it on Kubuntu), but yeah, nothing.

---

### Post by edd07 on 2008-03-10
Are you sure your sound isn't muted? At least on my laptop, which is having the same problem as yours, I had to unmute the Surround channel for sound to play when running from liveCD or running for the first time since installation.

---

### Post by spacefreak86 on 2008-03-10
I'm not that much of a newb to Linux. But yes, I did check the master volume to make sure that it was set to max. No sound came out of neither speakers nor the headphones. When I'm back on the regular run (installed on HD), sound works fine with the speakers. But there are times that I'd prefer to use headphones rather than the speakers, and right now, I'd like to figure out (or have some help in figuring out) how to get the headphones to work when I plug them into the 3.5 mm headphone jack on the front of my laptop.

---

### Post by pastalavista on 2008-03-14
I have the exact opposite problem on my Acer Aspire 3050. No sound from the speakers but works fine through the phone jack (SPDIF). I'm sure it's a driver problem because they both work with Vista.

---

### Post by rine238 on 2008-03-14
This problem I have on my laptop Acer Extensa 5210, and my brother on Asus A6100!
I have tried Ubuntu 7.10, Kubuntu 7.10 and Fedora 7, and always was the same problem, no sound on headphones!
And that lasts 9 months.

---

### Post by (((X))) on 2008-03-14
Me too, sound in both earphones and speakers on both my computers.

---

### Post by smurphy_it on 2008-03-14
I used to have this problem with my laptop HP Dv2000 series.  I no longer have this problem as it seems standard on alot of the newer distros theses days, but I still get it with some distros.

It had something to do with the way my specific video card sound was setup.  In my case I had to download the alsa drivers, and re-load them in with a special command in the build line.

./configure --snd-hda-intel or something strange like that.

Changes are it is your sound card (and it's support in Linux).  As a test, download a different linux live distro and try out your sound.  A small one would be Damn Small Linux which is only 50 MB and can be installed to a USB Flash drive.  I bet you'll have the same problem with that.

Again, to fix this issue, you may have to re-compile your sound.  I'd personally become a member of the [Alsa Bugtracking website]("https://bugtrack.alsa-project.org/alsa-bug/login_page.php"), and have a look in their forums.

Honestly, it took my like 6+ months to get the sound issues fixed with my laptop.  Right now, the two best distros I've tried for sound support on my laptop are Ubuntu & Pc-LinuxOS.

Good luck.

---

### Post by tangibleorange on 2008-03-14
If you have an acer laptop, try this:

```
echo 'options snd-hda-intel model=acer' | sudo tee -a /etc/modprobe.d/alsa-base
```

If you don't have an acer laptop, try putting your model in place of 'acer'. I know 'hp' works, and also '3stack' and 'auto' if neither of those work for you.

You will then need to reboot.

---

### Post by spacefreak86 on 2008-03-15
No response when I entered that it, it just spit this back at me:

```

options snd-hda-intel model=acer

```

I may have gotten it to work through a post on the kubuntuforums.net, which directed me towards some support that Dell wrote up for their Ubuntu laptops with headphone problems. I don't have a pair of headphones with me right now to test it, as I'm on the road, but I think it did work, I just have to check it later.

Here's the link :[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Add-on_Packages)

---

### Post by spacefreak86 on 2008-03-15
No response when I entered that it, it just spit this back at me:

```

options snd-hda-intel model=acer

```

I may have gotten it to work through a post on the kubuntuforums.net, which directed me towards some support that Dell wrote up for their Ubuntu laptops with headphone problems. I don't have a pair of headphones with me right now to test it, as I'm on the road, but I think it did work, I just have to check it later.

Here's the link  [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Add-on_Packages)

---

### Post by tangibleorange on 2008-03-16
Well I can't comment on the packages in the link, but what that command does is add that line to the end of your /etc/modprobe.d/alsa-base file. If you do this:

```
gksu gedit /etc/modprobe.d/alsa-base
```

You should see that line at the end of the file. That means the command has worked - it is supposed to return that.

---

### Post by spacefreak86 on 2008-03-16
Alright, after installing all of the ALSA packages (because I wasn't sure which one I would need), and d/l and installing the above .deb package, I have headphone support, and it automatically switches over when the headphones are pulled out.

---

### Post by Patrick-Ruff on 2008-03-16
I saw a setting in volume control (maybe it was in the other tab or something) but it said 'headphone detectoin' and you could check it . . . maybe try that if your install has it?

---

### Post by tangibleorange on 2008-03-17
> **spacefreak86 said:**
> Alright, after installing all of the ALSA packages (because I wasn't sure which one I would need), and d/l and installing the above .deb package, I have headphone support, and it automatically switches over when the headphones are pulled out.

OK then. Remember to mark threads as solved :).

---

### Post by andradx on 2008-03-17
I noticed the alsa-mixer, when you try to mute the headphones it also mutes the speakers and if you mute the speakers you mute the headphones so trying to switch off one or the other through alsa is no use as they are the same 'channel'.

I tried reconfiguring the alsa module in /etc/modprobe.d/alsa-base
snd-hda-intel position_fix=1 model=laptop
But it still happens

It is not an hardware problem as most laptops came with a W*n whatever installed and the speakers turned off when the headphones were plugged in. That's what's missing to say 'Ubuntu on my laptop tiptop'

Running Gutsy Gibbon on an LG E500
the output of cat /proc/asound/card0/codec#* | grep Codec is

Codec: Realtek ALC883
Codec: Generic 11c1 Si3054

Any help?Please...

---

### Post by tangibleorange on 2008-03-18
> **andradx said:**
> I noticed the alsa-mixer, when you try to mute the headphones it also mutes the speakers and if you mute the speakers you mute the headphones so trying to switch off one or the other through alsa is no use as they are the same 'channel'.

I tried reconfiguring the alsa module in /etc/modprobe.d/alsa-base
snd-hda-intel position_fix=1 model=laptop
But it still happens

It is not an hardware problem as most laptops came with a W*n whatever installed and the speakers turned off when the headphones were plugged in. That's what's missing to say 'Ubuntu on my laptop tiptop'

Running Gutsy Gibbon on an LG E500
the output of cat /proc/asound/card0/codec#* | grep Codec is

Codec: Realtek ALC883
Codec: Generic 11c1 Si3054

Any help?Please...

Could you please start a new thread for this issue as this current thread has been marked solved for a different issue. Thanks.

---

