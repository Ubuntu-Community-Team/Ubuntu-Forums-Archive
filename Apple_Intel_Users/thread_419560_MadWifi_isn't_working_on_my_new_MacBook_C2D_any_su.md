---
title: "MadWifi isn't working on my new MacBook C2D any suggestions?"
date: 2007-04-23
forum: Apple Intel Users
---

### Post by thenetduck on 2007-04-23
Hi, 
   I just saw the post on the MacBook wiki that you can use that latest MadWifi drivers to get wireless working on at new MacBook withough installing ndiswrapper and using the XP Drivers. The link to it is here.

[http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/](http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/)

I used the one made in April because that is the latest one, however I don't know if it is working correctly. I am using my mac partition right now on my wireless because the madwifi will pick up local networks etc but when I specifiy my network it doesn't connect. Does anyone have any ideas on why it could be doing this? or how to fix it? 

 My network has a Hidden name and now encryption. Could it be that the new drivers can't connect to hidden networks yet? 

 Thanks, 

 The Net Duck

---

### Post by gmc on 2007-04-23
Hi,

I'm in the same boat, with my Macbook too. The driver is very very alpha and I've only successfully connected to my wireless router when there is no encryption (WAP/WPA/WPA2) with the current version. 

We'll just have to be patient, Or perhaps you might want to contact the developer an see if you can assist with debugging.

Gord

---

### Post by thenetduck on 2007-04-23
Hum. I like that I might see if I can contact him/her.. Ok, I have just concluded that in order for it to work, you must have the SSID brodcasted and no encryption. Can't wait for new updates! Does anyone know if anyone is packaging the madwifi for the macbooks for updates etc? If not, I would like to help, I guess I would have to learn first though ;) It just seems frivilus to not have it working on MacBooks right out of the box or after updating once when they are such good machines. Also, does anyone have a good solution for making the resolution look nicer? Everything seems a little, err... whiteish or too light. I think its something to do with resolution. The macbook wiki had a thing on it but broke my xorg.config file once so im a little scared to try it again. Thanks

 The Net Duck

---

### Post by ronocdh on 2007-04-23
> **thenetduck said:**
> Hum. I like that I might see if I can contact him/her.. Ok, I have just concluded that in order for it to work, you must have the SSID brodcasted and no encryption. Can't wait for new updates! Does anyone know if anyone is packaging the madwifi for the macbooks for updates etc? If not, I would like to help, I guess I would have to learn first though ;) It just seems frivilus to not have it working on MacBooks right out of the box or after updating once when they are such good machines. Also, does anyone have a good solution for making the resolution look nicer? Everything seems a little, err... whiteish or too light. I think its something to do with resolution. The macbook wiki had a thing on it but broke my xorg.config file once so im a little scared to try it again. Thanks

 The Net Duck
Last things first, regarding your "resolution" problems, have you installed the restricted ATI driver? I personally love the look of my 15" glossy in Linux, although at times it is a bit too bright, and the F1 and F2 keys don't work by default for me. Perhaps this is what looks "too light" for you?

I am in the same boat as you with the madwifi drivers; I gave them a spin last night, but unfortunately I couldn't connected to my WEP router, which does have its SSID broadcast (I don't live downtown, it's fine). So, humbug on that. In Edgy getting wireless up was a very simple ndiswrapper procedure, but I haven't had the same luck in Feisty. The command **ndiswrapper -l** yields "net5416: driver installed" but I can't do anything with it! With madwifi at least I was able to see my wireless card in Network Manager, but still, couldn't do anything with it. And of course, [in light of recent news]("http://arstechnica.com/news.ars/post/20070422-child-porn-case-shows-that-an-open-wifi-network-is-no-defense.html"), I'm not about to take off even the shoddy WEP encryption.

So, blah. I encourage anyone and everyone to post with whatever minimal progress they may make toward encrypted Wireless. I remember Greywhind saying that WEP worked with madwifi, but WPA didn't. Hm. And Tyrdium, if you're reading this, is your network protected? I remember you got madwifi working well.

---

### Post by thenetduck on 2007-04-23
About the resolution... I should have mentioned what kind of mac I have. Its a MacBook Core 2 Duo 2.0 ghz with 1gb ram. So it would have the intel chipset. Out of the box, it looks fine, just..err well too light. Desktop effects work out of the box too so im happy with that. I do notice it slows down just a tad with desktop effects but hey one button enable? nice feature in my opinion. 
    The weird thing is that the wiki says to do this to get resolution working fine. 
```

sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution

```
The first problem I encountered with this is it doesn't reconize software-properties as even being a command. So I decided well.. ill just go to the next step, So I updated and installed the 915resolution but it crashed my X. (That time I forgot to backup xorg so it was big pain never again though) So interested to see if anyone has any feedback about that. 

 The Net Duck

---

### Post by ronocdh on 2007-04-23
> **thenetduck said:**
> About the resolution... I should have mentioned what kind of mac I have. Its a MacBook Core 2 Duo 2.0 ghz with 1gb ram. So it would have the intel chipset. Out of the box, it looks fine, just..err well too light. Desktop effects work out of the box too so im happy with that. I do notice it slows down just a tad with desktop effects but hey one button enable? nice feature in my opinion. 
    The weird thing is that the wiki says to do this to get resolution working fine. 
```

sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution

```
The first problem I encountered with this is it doesn't reconize software-properties as even being a command. So I decided well.. ill just go to the next step, So I updated and installed the 915resolution but it crashed my X. (That time I forgot to backup xorg so it was big pain never again though) So interested to see if anyone has any feedback about that. 

 The Net Duck
Hm well in Feisty one can alter repositories by going to System>Admin>Software Sources, which I think it a nice addition. So there you can either add or remove the Universe repo, as needed. Very, very odd that 915resolution crashed you, I've never heard of that happening before. Can you post output?

---

### Post by Technoviking on 2007-04-23
Try this:
[http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)

---

### Post by Tyrdium on 2007-04-23
> **ronocdh said:**
> And Tyrdium, if you're reading this, is your network protected? I remember you got madwifi working well.Nah, university has an open network. That help documentation for madwifi I linked to earlier does have information on connecting to WEP networks, though.

---

### Post by ronocdh on 2007-04-23
> **Tyrdium said:**
> Nah, university has an open network. That help documentation for madwifi I linked to earlier does have information on connecting to WEP networks, though.
Yes, it didn't work for me. I momentarily shut off WEP and left my network open, and then I connected OK. But that's no good.

I shan't give up, though!

---

### Post by avalonpimp on 2007-04-23
Hi, I also tired the latest snapshots of madwifi. They worked with my AP, but not with WPA. I went back and tired to install ndiswrapper-utils-1.9 using the bootcamp drivers, and could connect to AP with networkmanager - wouldnt work with WPA, but would without.

Here is how i got WPA to work with Ndiswrapper-utils-1.9 - c2d Macbook
  (I did a bunch of steps, so i dont knw which ones made it work, but it does)
    - sudo modprobe wlan_tkip
   - sudo aptitude install wpasupplicant

  - using network manager - i tired to connect to my WPA AP, and it worked! Hope this helps

---

### Post by thava on 2007-04-23
i having the same problem i can't get my wirless work.

my wireless card:
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

/ Thava

---

### Post by ronocdh on 2007-04-23
> **thava said:**
> i having the same problem i can't get my wirless work.

my wireless card:
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

/ Thava

Have you tried Mike's how-to listed above? I haven't yet but it looks promising. I'll probably give it a whirl sometime late tonight.

---

### Post by ronocdh on 2007-04-24
> **Mike said:**
> Try this:
[http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)
This unfortunately did not work for me. I did a fresh installation of Feisty just to test it. Anyone else want to give it a crack? I got the driver installed fine, but instead of seeing:
```
net5416 : driver installed
device (168C:0024) present
``` as the guide says I should, I see only:
```
ragnarok@DragonBoat:~$ sudo ndiswrapper -l
net5416 : driver installed
ragnarok@DragonBoat:~$ 

```
Argh! Now watch this. I try to manually associate the driver with my pciid of my card. When I run **lspci -n** I get a readout of **168c:0024** for my card; note that the C is lowercase:
```
03:00.0 0280: 168c:0024 (rev 01)

``` 
Well, I use that:
```
ragnarok@DragonBoat:~$ sudo ndiswrapper -a 168c:0024 net5416
driver 'net5416' is used for '104C:8025'
ragnarok@DragonBoat:~$ 
```
Uh, that **104C:8025**? That's my freaking firewire card, according to lspci and lspci -n. But OK. Maybe it's not working because I'm not capitalizing the C, so let's try doing it their way:
```
ragnarok@DragonBoat:~$ sudo ndiswrapper -a 168C:0024 net5416
couldn't create symlink for "104C:8025.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0023.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0032:168C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0033:168C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0429:1468.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0430:1468.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:13C0:10CF.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:7125:144F.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:FF1C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:FF1D.5.conf": File exists -
installation may be incomplete
driver 'net5416' is not installed (properly)!
ragnarok@DragonBoat:~$ 

```
What?!

Ideas welcome, I'm going to bed. ;)

P.S. And before you chastise me, I followed the guide to the T, meaning I did remove all ndiswrapper junk before setting off on my quest.

:guitar: :guitar: :guitar: :guitar:  There, those guys make me feel a little better.

---

### Post by gmc on 2007-04-24
> **thenetduck said:**
> Hum. I like that I might see if I can contact him/her.. Ok, I have just concluded that in order for it to work, you must have the SSID brodcasted and no encryption. Can't wait for new updates! Does anyone know if anyone is packaging the madwifi for the macbooks for updates etc? If not, I would like to help, I guess I would have to learn first though ;) It just seems frivilus to not have it working on MacBooks right out of the box or after updating once when they are such good machines. Also, does anyone have a good solution for making the resolution look nicer? Everything seems a little, err... whiteish or too light. I think its something to do with resolution. The macbook wiki had a thing on it but broke my xorg.config file once so im a little scared to try it again. Thanks

 The Net Duck

Hi, Yes you are correct. I have an Acer5672 laptop with an Intel 3945 wireless chipset and on both the Macbook and the Acer, I have to have the SSID broadcast otherwise I can't establish a connection. As for encryption, again you're correct. The Acer can handle WAP/WPA/WPA2 but the only way I could get the Macbook to talk on the network was to disable the encryption. Unfortunately, in my area there are lots of wireless users so I can't/won't run my network without encryption.

Sorry I can't help with your other question, other than to suggest turning down the brightness on the display (gnome's power management has a slider to control the brightness) when running on the mains or the battery.

Gord

P.S. As has been mentioned, you might not have 915resolution installed. I did have a problem with that. I had to replace the "auto" to "5c" and specify 1280 x 800 resolution in the /etc/default/915resolution configuration file, to get my Mac to boot in it's native 1280x800 resolution. Just an after thought...

P.P.S. The instructions in the Howto pointed out by Mike do in fact work but only on the 32 bit version of Ubuntu. Alas I bought a C2D to run 64 bit software, so I'm still stuck waiting for the native driver.

---

### Post by ronocdh on 2007-04-24
> 
P.P.S. The instructions in the Howto pointed out by Mike do in fact work but only on the 32 bit version of Ubuntu. Alas I bought a C2D to run 64 bit software, so I'm still stuck waiting for the native driver.
D'oh! That would be the problem, I suppose. Yeah, come to think of it, ndiswrapper worked without a hitch in Edgy, but I was running the i386 build. =(

Well, we wait.

---

### Post by Azathoth_ on 2007-04-24
> **ronocdh said:**
> Last things first, regarding your "resolution" problems, have you installed the restricted ATI driver? I personally love the look of my 15" glossy in Linux, although at times it is a bit too bright, and the F1 and F2 keys don't work by default for me. Perhaps this is what looks "too light" for you?

I am in the same boat as you with the madwifi drivers; I gave them a spin last night, but unfortunately I couldn't connected to my WEP router, which does have its SSID broadcast (I don't live downtown, it's fine). So, humbug on that. In Edgy getting wireless up was a very simple ndiswrapper procedure, but I haven't had the same luck in Feisty. The command **ndiswrapper -l** yields "net5416: driver installed" but I can't do anything with it! With madwifi at least I was able to see my wireless card in Network Manager, but still, couldn't do anything with it. And of course, [in light of recent news]("http://arstechnica.com/news.ars/post/20070422-child-porn-case-shows-that-an-open-wifi-network-is-no-defense.html"), I'm not about to take off even the shoddy WEP encryption.

So, blah. I encourage anyone and everyone to post with whatever minimal progress they may make toward encrypted Wireless. I remember Greywhind saying that WEP worked with madwifi, but WPA didn't. Hm. And Tyrdium, if you're reading this, is your network protected? I remember you got madwifi working well.

You can connect to encrypted wirelesses with wifi-radar
I use it on my C2D MB and with my PC with ndiswrapper in both

---

### Post by Azathoth_ on 2007-04-24
> **ronocdh said:**
> This unfortunately did not work for me. I did a fresh installation of Feisty just to test it. Anyone else want to give it a crack? I got the driver installed fine, but instead of seeing:
```
net5416 : driver installed
device (168C:0024) present
``` as the guide says I should, I see only:
```
ragnarok@DragonBoat:~$ sudo ndiswrapper -l
net5416 : driver installed
ragnarok@DragonBoat:~$ 

```
Argh! Now watch this. I try to manually associate the driver with my pciid of my card. When I run **lspci -n** I get a readout of **168c:0024** for my card; note that the C is lowercase:
```
03:00.0 0280: 168c:0024 (rev 01)

``` 
Well, I use that:
```
ragnarok@DragonBoat:~$ sudo ndiswrapper -a 168c:0024 net5416
driver 'net5416' is used for '104C:8025'
ragnarok@DragonBoat:~$ 
```
Uh, that **104C:8025**? That's my freaking firewire card, according to lspci and lspci -n. But OK. Maybe it's not working because I'm not capitalizing the C, so let's try doing it their way:
```
ragnarok@DragonBoat:~$ sudo ndiswrapper -a 168C:0024 net5416
couldn't create symlink for "104C:8025.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0023.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0032:168C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0033:168C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0429:1468.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:0430:1468.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:13C0:10CF.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:0024:7125:144F.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:FF1C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "168C:FF1D.5.conf": File exists -
installation may be incomplete
driver 'net5416' is not installed (properly)!
ragnarok@DragonBoat:~$ 

```
What?!

Ideas welcome, I'm going to bed. ;)

P.S. And before you chastise me, I followed the guide to the T, meaning I did remove all ndiswrapper junk before setting off on my quest.

:guitar: :guitar: :guitar: :guitar:  There, those guys make me feel a little better.

First, install wifi-radar:
```
sudo apt-get install wifi-radar
```
You can remove /etc/ndiswrapper directory, then enter in you ndiswrapper directory and make uninstall && make clean and after compile it again:
```
sudo rmmod ndiswrapper
sudo rmmod ath_pci
REMOVE ALL YOU MADWIFI MODULES:
sudo rm -r /lib/modules/*your_kernel*/madwifi/*
sudo rm -r /etc/ndiswrapper
cd ndiswrapper
make && sudo make install
cd you_net5416_directory
sudo ndiswrapper -i net5416.inf
sudo modprobe ndiswrapper
sudo wifi-radar
```

Configure your encrypted configuration. You can change you MAC adress in ndiswrapper in /etc/ndiswrapper/net5415/file_which_is_loaded_by_ndiswrapper  chenging XX:XX:XX:XX:XX:XX to your fake MAC adress

And now add to your /etc/rc.local after exit line:
```
modprobe ndiswrapper
wifi-radar -d
```

Or you can remove modprobe ndiswrapper line and create a modprobe module:
```
sudo ndiswrapper -m
```
or  
```
sudo ndiswrapper -ma
```

but this two last make boot slower

---

### Post by ronocdh on 2007-04-24
Azathoth,

Thanks a lot for the detailed reply. I'll try your recommendations out tonight. Also, I like your name. ;)

---

### Post by thava on 2007-04-24
still not working for me.. :(

> sudo rmmod ndiswrapper
sudo rm -r /etc/ndiswrapper
cd ndiswrapper
make && sudo make install
cd you_net5416_directory
sudo ndiswrapper -i net5416.inf
sudo modprobe ndiswrapper
sudo wifi-radar

After these step above I can see my  SSID.

But after done of all the step in howto and reboot then wifi radar can't show any SSID. Whet I start wifi-radar it say no wireless card found.

Thanks in advance
Thavarajah Sabanathan

---

### Post by ronocdh on 2007-04-24
Azathoth, thanks once again for the post, but I have to ask: are you using the i386 build or 64-bit? I bleed 64-bit, but no wireless is killing me; I'm considering reinstalling with i386 just until I hear of testable Atheros 5416/8 drivers that are native to 64-bit.

Maybe I'll start a poll, I'd like to see how many people here on C2Ds bother with 64-bit....

---

### Post by Azathoth_ on 2007-04-25
> **ronocdh said:**
> Azathoth, thanks once again for the post, but I have to ask: are you using the i386 build or 64-bit? I bleed 64-bit, but no wireless is killing me; I'm considering reinstalling with i386 just until I hear of testable Atheros 5416/8 drivers that are native to 64-bit.

Maybe I'll start a poll, I'd like to see how many people here on C2Ds bother with 64-bit....

I think 64bits version is not too much stable to install it. I use 32 bit version for my PC and MB because with 64 version ndis drivers make kernel panics and madwifi is only a alpha. Try it in next Ubuntu version. I will try it also, but not in Feisty (too much soon)

---

### Post by Azathoth_ on 2007-04-25
And i had problems with azathoth    Because i could not make threads and i had to create azathoth_    :(
Nowadays i use magarto as my nick name... because my web ;)

---

### Post by Azathoth_ on 2007-04-25
> **thava said:**
> still not working for me.. :(



After these step above I can see my  SSID.

But after done of all the step in howto and reboot then wifi radar can't show any SSID. Whet I start wifi-radar it say no wireless card found.

Thanks in advance
Thavarajah Sabanathan

Try:
```
ndiswrapper -l
```

```
You must have driver installed
*file_which_is_loaded *   device present
```

If not, try to do again, and this might be that you don't use a properly .inf file or you don't modprobe it sucessfully
Check your /etc/rc.local or your /etc/modules or your /etc/modprobe.d/ndiswrapper

In ONE of these you must have ndiswrapper  (a repeat only one and i prefer in /etc/rc.local to have modprobe ndiswrapper BEFORE exit (0)

Last one and very important is if you have correctly configured wifi-radar:
```
sudo nano /etc/wifi-radar.conf
```

Check you device. It must be **wlan0**

I have added to the last reply one line and this is for removing all madwifi modules which MUST be removed because ndiswrapper module cannot modprobe if they exist. And i'm sure this is your issue

---

### Post by gmc on 2007-04-25
> **Azathoth_ said:**
> I think 64bits version is not too much stable to install it. I use 32 bit version for my PC and MB because with 64 version ndis drivers make kernel panics and madwifi is only a alpha. Try it in next Ubuntu version. I will try it also, but not in Feisty (too much soon)

YMMV but I've found the 64bit version of Ubuntu to be rock solid. Admittedly it's not a 1-2-3-click install for things like flash (there's a great howto flash in the 64bit forums). I do a lot of video encoding/decoding with my machine and the 64bit version has been able to handle everything with the same ease as the 32bit version.

To each their own... at least it's still linux and not that other OS... :-)

Gord

---

### Post by Azathoth_ on 2007-04-25
> **gmc said:**
> YMMV but I've found the 64bit version of Ubuntu to be rock solid. Admittedly it's not a 1-2-3-click install for things like flash (there's a great howto flash in the 64bit forums). I do a lot of video encoding/decoding with my machine and the 64bit version has been able to handle everything with the same ease as the 32bit version.

To each their own... at least it's still linux and not that other OS... :-)

Gord

Great. Then report me in a future your experience with 64 bits version and then, i will install it. (i have installed ubuntu like 20 times in my 2 computers :Þ  and i make it with a script)

It would be great if we could compare these two versions. Do you know how to do it?

Do you use ndiswrapper drivers? And they work properly? Do you use then the 5416.inf driver)

Please answer them and THANKSSS

---

### Post by gmc on 2007-04-25
> **Azathoth_ said:**
> Great. Then report me in a future your experience with 64 bits version and then, i will install it. (i have installed ubuntu like 20 times in my 2 computers :Þ  and i make it with a script)

It would be great if we could compare these two versions. Do you know how to do it?

Do you use ndiswrapper drivers? And they work properly? Do you use then the 5416.inf driver)

Please answer them and THANKSSS

Let me answer that in reverse order. I found that I needed both 5416.inf and 5416.sys files to get ndiswrapper working in 32bit and that worked perfectly with my wpa2 encrypted router. As I understand it, if we could find the 64bit version of those files, we could use ndiswrapper. As it stands now, there is limited wireless capability in 64bit, in 32bit either native drivers exist and work on C2Dv1, C2Dv2 (mine) can only use ndiswrappers. Hope that's as clear as mud :-0 ;-)

As for comparing the two versions... having run both on the macbook, there really is little difference, though for me, encoding video is considerably faster in 64bit. Other than the wireless situation is really the only big "gotcha" with 64bit mode.

I'm hopeful the 64bit driver matures and in the meantime, I'll just run a cable to the macbook when I need net access.

Gord

---

### Post by Azathoth_ on 2007-04-25
> **gmc said:**
> Let me answer that in reverse order. I found that I needed both 5416.inf and 5416.sys files to get ndiswrapper working in 32bit and that worked perfectly with my wpa2 encrypted router. As I understand it, if we could find the 64bit version of those files, we could use ndiswrapper. As it stands now, there is limited wireless capability in 64bit, in 32bit either native drivers exist and work on C2Dv1, C2Dv2 (mine) can only use ndiswrappers. Hope that's as clear as mud :-0 ;-)

As for comparing the two versions... having run both on the macbook, there really is little difference, though for me, encoding video is considerably faster in 64bit. Other than the wireless situation is really the only big "gotcha" with 64bit mode.

I'm hopeful the 64bit driver matures and in the meantime, I'll just run a cable to the macbook when I need net access.

Gord

Thanksss. When madwifi or net5416 are ok for 64 bits version, i will use it. Thanks

---

