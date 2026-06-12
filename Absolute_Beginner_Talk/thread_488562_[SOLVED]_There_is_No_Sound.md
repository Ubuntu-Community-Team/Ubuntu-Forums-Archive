---
title: "[SOLVED] There is No Sound"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by GeigerBC on 2007-06-30
I am using Feisty Fawn Live CD and can't seem to get any sound to play,  I've tried System>Preferences>Sound and there are about 6 options to test with, none of which produce any sound.

On the desktop there is an examples folder that also has sound which will not play.  I havn't gotten to getting drivers for mp3s and such as I wouldn't be able to tell if they are playing or not.

My system is in my sig.

Thanks for any help.

---

### Post by Keisad on 2007-06-30
Right click on the volume icon in the top bar on your desktop, and go to "open volume control" and make sure that the volume is coming through from their.

If that doesn't work, go to file - change device and select a different one. 

Post back

---

### Post by GeigerBC on 2007-06-30
I had two options there, neither would produce sound.  I had the example folder's Aseop's fables running in the background to test it as well.

Thanks so far.

---

### Post by Thermal_unit_alpha on 2007-06-30
I am pretty new to Ubuntu; I have been using Debian for quite some time now:popcorn:. I am not sure if this will work on Ubuntu. In Debian there was a command line program called alsa-config, try running it. It will allow you to manually set up your sound card. I am not certain if this package has been ported to Ubuntu or not. If it is, this may help.

Another thing to be aware of is, if you are using more than one sound card in your system. If so and your sound is not working properly, you may consider disabling one of your sound devices; if you do not need to use it. If you are stuck using two cards, as I am, you may try adjusting your debconf priority. By setting it to medium your system will automatically resolve most hardware and software issues. Again, I am not certain if this  program has been ported to Ubuntu or not.

Hope this helps ;). 

Thermal_unit_alpha

---

### Post by GeigerBC on 2007-06-30
"bash: alsa-config: command not found"
Is the message I get back when I tried to run it in the terminal.

I only have one sound card in my computer.

Thanks so far.

---

### Post by Thermal_unit_alpha on 2007-07-02
I  apologize for taking so long to reply. I just realized that you are using an X-fi. As of yet there is not support for the X-fi under Linux. :( Do you have the option of using onboard sound? If so, try enabling it and using that. It may not sound as nice; at least it will work.

I am using an X-fi Extreme Music myself. It is a shame Creative has decided not released the specs to ALSA or OSS.  There are rumors that they will release closed source drivers some time in late Q3 or Q4 this calender year. I am skeptical; we will see.

Good Luck 

Thermal_unit_alpha

---

### Post by GeigerBC on 2007-07-02
Thanks for the info.  At least I know where I stand.  I think I'll keep researching some of my other questions like dual screens but not go full time on Ubuntu till I try again next summer.

[http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)

---

