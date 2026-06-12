---
title: "Wifi help!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-07-19
Hi All - ive just bought myself a Fujitsu Siemens Amilo PA1510 and unfortunately it comes with windows Vista preinstalled.  Ive run the 7.04 live CD to see if everything works and unfortunately it hasnt picked up my wireless broadband.  I have an orange livebox which I know is working as I borrowed a dell laptop from work running windows XP and it just picked it up.  On the live cd however I get the two little monitors next to the clock with a little red x and it says no network connection.  If I go into networking though through system it shows up that I have a roaming connection enabled. 

Can anyone help with this as Id really like to install Ubuntu and have the wireless broadband!

---

### Post by annda on 2007-07-19
hi!

it seems you need madwifi for your wireless atheros chipset (probably AR5004G, i googled for your laptop, so it's only 99% sure)

madwifi is included in the restricted modules package. of course you will need temporary internet access to install those from synaptic. as you have a laptop, it shouldn't be a problem - some of your friends must have LAN internet and let you connect with an ethernet cable.

once you get there, open synaptic (system>administration>synaptic), hit reload to update information on available packages, search for 'linux' IN NAME ONLY and install the restricted modules for your kernel - you can find out which release you have when you scroll to 'linux-image-some numbers' and see which box is filled/ticked. this is your kernel version and you will need to install 'linux-restricted-modules-the same number'

the only problem is that if you test it from the liveCD, it is not possible to restart without losing the changes... i suppose (i don't have your hardware so i can't test it) that out of the modules supplied by madwifi running this one manually should help:

```
sudo modprobe wlan
```

this is run in the terminal (applications>accessories>terminal)

---

### Post by MikeSz on 2007-07-19
cheers for that il give it a try, I have a desktop with an ethernet connection so il try it on that now...

---

### Post by MikeSz on 2007-07-19
hmm - not sure what I did but that doesnt seem to have sorted it.  would it be better if I connected the laptop up with the ethernet cable?

---

### Post by annda on 2007-07-19
you need to try out the hardware you have - since the wireless you are trying to use sits in your laptop, plug the cable in, boot the feisty live cd and continue as i suggested. actually, it would be a good idea to use the update-manager first (system>administration>update manager) and then the restricted drivers manager (same menu) before you try the other steps.

as i said, the command 'sudo modprobe wlan' may not be perfect. if you had ubuntu installed, you would just need to reboot with the new kernel modules/drivers, but it's not possible with a live cd. i'm guessing here. it could be madwifi or ath instead of wlan, but i really can't tell.

---

### Post by MikeSz on 2007-07-19
ive got atheros.  I could always just try installing ubuntu couldnt I and taking it from there?  I have a rescue CD for vista which I am assuming will restore it should it all go pear shaped.

---

### Post by annda on 2007-07-19
go ahead and install ubuntu! it will be much easier to install and configure stuff.

please search the forums and google for dual booting **vista** and ubuntu. there is a lot of info. it's a bit more complicated than with XP, but not that difficult. dual booting means you get to use both systems on one computer, which is great for people new to linux.

so, welcome and have fun!

---

### Post by MikeSz on 2007-07-19
Thanks - I was actually thinking of ditching Vista completely and just running ubuntu - just checked in Vista and the wireless networking seems to be fine (well, it picked up my livebox anyway!) so im just going to install Ubuntu and use the entire hard disc

---

### Post by annda on 2007-07-19
> **MikeSz said:**
> Thanks - I was actually thinking of ditching Vista completely and just running ubuntu - just checked in Vista and the wireless networking seems to be fine (well, it picked up my livebox anyway!) so im just going to install Ubuntu and use the entire hard disc

what can i say - cool! and good for you! if you can plug in the ethernet cable in the beginning to consult the forums for assistance on setting up wireless, i'm sure you will be happy.

---

### Post by MikeSz on 2007-07-19
well, its installing now so we'll soon find out!!!  (although ive not plugged the ethernet cable into the laptop - im using it for the pc im using at the moment.  Should I have the ethernet cable in or not?)

hopefully once it has installed I can boot up and get the wireless working!! :guitar:

---

### Post by MikeSz on 2007-07-19
Ok - ive installed Ubuntu - all fine.  Ive run the update manager (which took ages) and ive also gone through synaptic to update the restricted modules.  

When I unplug the ethernet cable, I can click on the two little monitors which detect my livebox (does that mean that the wifi is working?) however I cant seem to connect to my livebox.  I also get two little grey dots (like you get at least one grey dot and the blue swirly thing when you plug in an ethernet cable - I take it thats what the icon looks like when its looking for a connection)  So - is it working or do I need to do something else?  It did ask me for my password which I assume is for the broadband, which I entered but the ok button was ghosted out

Any ideas?

---

### Post by MikeSz on 2007-07-20
Well this is curious - I am now writing this message on my laptop on the wireless network!  I havent done anything to it since my last post - simply searched for wireless networks and found one called "netgear" which I am assuming is either a community network or one of the neighbour's, either way, I know its working.  Therefore the password problem I have on my own live box must be something I have to resolve with Orange - would that seem right?  I did write the broadband username and password down when I first got it and I have typed it in exactly as I write it down so I cant understand why its not working.  Anyway, when I get home I will contact Orange and see if I can figure whats up with it.  

I have however noticed that at present, when I tried to connect to a wireless network (like the netgear one I seem to have just stumbled on) I get one green dot out of the two dots (the ones which replace the two monitor symbols) and then after a couple of seconds, both light up and I am then connected.  Curiously, when I am at home and trying to connect to the live box, neither of the lights illuminate - is that a problem?  Or just down to this password issue?

Again, any ideas are much appreciated!!!!

---

### Post by Kralizec on 2007-07-20
I know with network manager when it prompts you for a network's key (password) certain encryption types have specific requirements for passwords, such as a specific length. As you've said you wrote the password down, I assume its correct so its not a length issue; perhaps when it prompts for your password you need to select a different encryption type from the dropdown menu (WEP, WPA, etc.); WPA requires (if I remember right) either an 8 character or 10 character password/key while WEP requires 10 (this may be off, you might want to look into this yourself). 
But it is my best bet that when putting in your password you had the wrong encryption type selected and so its now refusing to let you connect. You could try manually entering the settings of your wireless by left-clicking the network-manager icon next to the clock and clicking 'Connect To Other Wireless Network' and filling in all the fields, being sure to choose the correct encryption type. You should be able to check your encryption type by viewing your router's firmware in a web browser (usually 192.168.0.1, or something similar). Just connect with a physical LAN connection until then.

---

### Post by MikeSz on 2007-07-21
Ah - now theres a good idea!  Thanks for that.  Hadnt thought of that and it would make sense as my password is 7 characters long (and ive checked it with organge) but for some reason it wants a password of 8 characters.  Il try the other option when I get home on Monday.

Thanks for all the help and il let you know how it goes!

---

