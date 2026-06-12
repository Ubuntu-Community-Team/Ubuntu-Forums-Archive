---
title: "Macbook Pro 8,1 WiFi cutting out 18.04"
date: 2019-08-20
forum: Apple Hardware Users
---

### Post by grahamdcarter on 2019-08-20
My wifi seems generally to work but I am getting frequent cut outs which I can solve by turning wifi off and on again. Sometimes it solves itself after a little while. Sometimes I can watch the visible networks in my wifi settings jumping around, cutting in and out or moving my home network up or down the list in a strange way as though it is working too hard.

I ran "lspci -nn -d 14e4:" to establish that my pci.id is "Broadcom Corporation BCM4306 802.11bgn Wireless Network Adapter [14e4:4331]" and have tried installing firmware-b43-installer as  suggested on the Broadcom sticky thread.

Any great ideas where to start diagnosing and solving this issue. I have some experience with Ubuntu but should be safely treated as a bit of a noob.

Thanks!

---

### Post by chili555 on 2019-08-20
Is your wireless dropping and failing to reconnect because your router is set to auto channel select and, although you were perfectly connected on channel 6, the router decided that it needs to switch to channel 8?

Is your wireless dropping and failing to reconnect because your router is set to auto select between WPA and WPA2?

Is your wireless dropping and failing to reconnect because your router is set to auto select between 20 and 40 MHz in the 2.4 GHz band?

In each of these cases, the arbitrary switch by the router often causes issues with many Linux drivers.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

After making these changes, please report back and tell us if the behavior has improved.

---

### Post by slickymaster on 2019-08-20
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by grahamdcarter on 2019-08-20
Thanks so much for the reply. It was exactly the reply I was fearing (i.e., "check your router", which fills me with fear especially as it always ends up with me disconnecting my household from the internet) so I've held off on the router settings for the moment until the rest of the house is in bed. I have set my regulatory domain now following your instructions. I restarted my computer about 10 minutes ago and have only just had my first cut out and it came back online within a couple of seconds. This, believe it or not is an improvement!

Are there any downsides to fixing which channel my router uses?

Also, does anyone know what the following wireless network modes mean and which might help my situation? "Auto", "54g Auto", "54g Performance", "54g LRS" and "802.11b only". LRS stands for Limited Rate Support apparently.

UPDATE: I've now reset the router setting the channel to 6 and the mode to 54g Performance (sounded the most promising of my choices!). Changing the regulatory domain without making the changes to the router settings *did not *fix the issue. I will test tomorrow to see if the router settings have helped.

---

### Post by grahamdcarter on 2019-08-21
Well... I think setting the channel and wireless network mode seems to have stabilised things... Will come back if I have spoken too soon, but for now, muchas gracias!

---

### Post by grahamdcarter on 2019-08-21
Ah no, spoke too soon! I was online for a good while (maybe an hour), but the problem is still there.

Other searches have suggested that it might be something to do with the network manager turning wifi off for power saving? But tonight, my laptop is plugged in so surely that would make no difference?

> Well... I think setting the channel and wireless network mode seems to have stabilised things... Will come back if I have spoken too soon, but for now, muchas gracias!

---

### Post by chili555 on 2019-08-21
Please try this: [https://unix.stackexchange.com/questions/269661/how-to-turn-off-wireless-power-management-permanently](https://unix.stackexchange.com/questions/269661/how-to-turn-off-wireless-power-management-permanently)

---

### Post by grahamdcarter on 2019-08-21
Thanks again. Seen and understood, will report back.

---

