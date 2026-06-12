---
title: "MacBook Pro 7.1 overheating with Ubuntu Mate 14.04"
date: 2015-09-15
forum: Apple Hardware Users
---

### Post by dpdsilva on 2015-09-15
Hi all,

I'm having overheating problems with my Macbook. It starts heating up right after login and reaches around 75-80°C after about 10 minutes. It doesn't seem to matter if I'm actively running any programmes of not. I'm starting to worry the laptop will get damaged by always running so hot.

I installed Ubuntu via usb (which I suppose means its installed in UEFI mode) and after much struggling I managed to get the NVIDIA graphics card working (Nvidia Geforce 320m). I followed the these instructions to use the NVIDIA drivers: [http://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating](http://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating)

Any ideas on how to cool this thing down?
Thanks!

---

### Post by este.el.paz on 2015-09-19
Read the "mactel" sticky at the top of the page . . . and see if there is a link to how to install "macfancntrl" (something like that) . . . .  There is a guy who helped me in a thread a year or so back, can't think of his name, but it was very detailed.  My MBPro 5,1??? still runs "warm" with LM 17.1 Rebecca . . . 14.04 is a little more resource hungry I suppose, as is the straight Ubuntu flavor.  You could try Lu or Xu and see if that is a little cooler.

The fan control issue is one reason why lately I've been saying to run linux as virtual in OSX, then, no worries about heat as the machine is running per design.

e.e.p.

---

### Post by dpdsilva on 2015-10-06
Thanks for the reply e.e.p.

I solved the problem in the end by re-formating. I installed LM 17.2 from a CD (not USB this time!) and got the graphics card working using the same method. It's now usually running at around 50.0°C. That's almost a 30°C temperature drop!

---

### Post by este.el.paz on 2015-10-06
> **dpdsilva said:**
> Thanks for the reply e.e.p.

I solved the problem in the end by re-formating. I installed LM 17.2 from a CD (not USB this time!) and got the graphics card working using the same method. It's now usually running at around 50.0°C. That's almost a 30°C temperature drop!

@dpdsilva:

Thanks for the follow-up, glad you got it worked out . . . .  I took your advice and tried upgrading my LM17.1 MATE to 17.2 . . . couple glitches . . . found "broken packages" . . . ran the install again from Update Manager . . . said all was "successful" . . . then, no wifi . . . .  : - )  Have to keep a sense of humor going at all times . . . but good to see that you tried different approach to the problem . . . .

e.e.p.

---

