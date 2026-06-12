---
title: "hda intel sound still not working"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by mikekrell on 2007-04-10
I think ive tried just about everything I could find to get my sound card working..still to no avail. Im running ubuntu (fiesta) and it just wont play sound. Ive checked alsamixer to see if they were muted, reinstalled the drivers for the hda and alsa. need some help.

Thanks,
Mike

---

### Post by dan171717 on 2007-04-10
what model is your sound card? how old is it?

---

### Post by mikekrell on 2007-04-10
the card is new, its a brand new acer aspire 5580 laptop. REALTEK ALC883

---

### Post by oddin85 on 2007-06-07
i have an acer aspire 5580, to get the sound to work, add a volume control applet to a panel and then go to preferences on the applet:
select HDA Intel (Alsa mixer)
then select Surround

this applet will control the volume on the front speakers and to get he buttons on the keyboard to control the front speakers instead of the headphones go to System > Preferences > Sound
and under Devices where it says Default Mixer Tracks choose HDA Intel (Alsa mixer) as the Device, and choose Surround

:D

---

### Post by dragon_heart on 2008-02-11
> **oddin85 said:**
> i have an acer aspire 5580, to get the sound to work, add a volume control applet to a panel and then go to preferences on the applet:
select HDA Intel (Alsa mixer)
then select Surround

this applet will control the volume on the front speakers and to get he buttons on the keyboard to control the front speakers instead of the headphones go to System > Preferences > Sound
and under Devices where it says Default Mixer Tracks choose HDA Intel (Alsa mixer) as the Device, and choose Surround

:D


I have the same laptop as you do, and I also have the same problem. The sound works with headphones but not with the speakers. 

What volume control applet do I have to add? Where do I download this if ever? To which panel do I add this? I am using Ubuntu 7.06. I have set the HDA Intel to surround but still no luck.

Thanks in advance.

---

### Post by now switched to linux on 2008-02-11
i dont know the details of this sound issue but every person with ububtu that i have met have faced the problem with sound.
here is the process by which i get sound on my pc
forst i install latest alsa from alsaproject(i took 14 version and latest is i think 16)
i do this after reading a thread on this alsa stuff
than shut down not restart my computer
remove ac power cord and start laptop
so now everytime i boots to ubuntu,to get sound i start with battery powered

hope this helps ...though just to listen sound:)

---

### Post by gwpritch on 2008-02-11
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by stchman on 2008-02-11
> **mikekrell said:**
> I think ive tried just about everything I could find to get my sound card working..still to no avail. Im running ubuntu (fiesta) and it just wont play sound. Ive checked alsamixer to see if they were muted, reinstalled the drivers for the hda and alsa. need some help.

Thanks,
Mike

I have a script that will install the latest ALSA drivers.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

It has worked for others.

---

