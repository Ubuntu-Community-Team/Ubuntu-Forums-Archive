---
title: "Microphone and speakers on Macbook Air 2,1 (Ubuntu 9.10)"
date: 2010-04-28
forum: Apple Hardware Users
---

### Post by cyberco on 2010-04-28
As described here ([https://help.ubuntu.com/community/MacBookAir2-1/Karmic](https://help.ubuntu.com/community/MacBookAir2-1/Karmic)) I've got Ubuntu 9.10 running on my Macbook Air 2,1 but the only things that don't work are the speaker and the built-in microphone. I can get sound using the line out though. I am mainly looking for a way to get my microphone working (I can live with sound only via line-out). Does anybody here have any pointers to a possible solution?

Thanks!

---

### Post by ZeroLinux on 2010-04-29
You can try to use my hint from [here]("http://ubuntuforums.org/showthread.php?t=1439009&highlight=imac")

---

### Post by cyberco on 2010-05-04
Ah, indeed, settings in the alsamixer solved my issue. I had to unmute some channels (I tried the alsamixer before but didn't see that some channels were muted).

Thanks!

---

### Post by heluani on 2010-08-07
> **cyberco said:**
> Ah, indeed, settings in the alsamixer solved my issue. I had to unmute some channels (I tried the alsamixer before but didn't see that some channels were muted).

Thanks!

Wait a second, do you mean that you got the mic working in a macbook Air 2,1 ? which version of Alsa are you using, which model in your alsaconf? what is your codec? 

Thanks, 

R.

---

### Post by cyberco on 2010-08-12
No, mic still doesn't work. That's about the only thing left.

---

### Post by ZeroLinux on 2010-08-12
You can try to install newest alsa according to my [manual]("http://ubuntuforums.org/showpost.php?p=9393397&postcount=20")
I think it is better if you change the kernel number revision to yours 
I mean digits 2.6.32-22 to yours.

---

### Post by heluani on 2010-08-15
> **ZeroLinux said:**
> You can try to install newest alsa according to my [manual]("http://ubuntuforums.org/showpost.php?p=9393397&postcount=20")

Won't work, that's why I was confused with cyberco's post, I wrote the patch to ALSA that shipped on 2.6.34 to add support on 2,1 and its main speaker (by the way ciberco, using mba21 as your model will be better if you really have a Macbook Air 2,1). Couldn't find anyone to fix the mic issue yet, I contacted the Hackint0sh community in the hopes that they'll know what to configure in EFI or if it's some vendor specific verbs on pin 0x20 but to no avail... I'll be the happiest one if this gets solved so that I can get rid of OSX on this machine.

R.

---

### Post by ThommyK on 2011-10-09
Any update on the microphone on the Macbook Air 2,1? 
Thanks

---

### Post by heluani on 2011-10-09
I've been following the Alsa development for a while and didn't see any changes that would make that mic work. I've given up on trying things on pin 0x20. What I've not done lately is to check if Realtek posted the specs of this card. 

R.

---

