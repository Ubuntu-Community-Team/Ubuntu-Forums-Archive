---
title: "Can't connect to other wireless networks; DHCP doesn't work on wirelss!"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-04
Hi,

After a few nights of stride during last week I have finally managed to set up my Broadcom Wireless on my Acer Aspire 5024WLMi. After I set up all the network details MANUALLY everything seemed to work OK.

Thing is that In my house there are 2 wireless networks one of which is unsecured: no encription, no key. I have now tried almost everything but Ubunutu won't connect to the unsecured network.

Besides, when trying to connect with DHCP to the encripted network, which works fine with manual config, it just won't connect. The DHCP client says there are "No working leases!" Well, that's a load of RUBBISH!!! In Windows both networks work 100% fine both manually  and automatically.

Any ideas why this is happening or how can I make this damn thing work?

Also, where is the network configuration file stored?

By the way, I may be new to linux but I'm not a computer rookie. I know very well what I'm doing, especially when it comes to networking. Please keep this in mind and try to give some constructive advice.

Thanks!

---

### Post by GuitarHero on 2006-07-04
give is the output of sudo iwconfig   and sudo cat /proc/modules (only the lines relating to your card)

---

### Post by Ptero-4 on 2006-07-04
What kind of router do you use?

---

### Post by ovimunt on 2006-07-04
My router is a Linksys WAG354G which works 100% fine in Windows and Ubuntu. As for my flatmate's router I don't remember off the top of my head and I can't find out because he's sleeping right now.

Anyway, the two outputs are as follows:

> ovidiu@Ovidiu:~$ iwconfig eth0
eth0      IEEE 802.11b/g  ESSID:"Ender"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:14:BF:94:07:7B
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=183/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and then I guess these are the relevant lines:

> 
ovidiu@Ovidiu:~$ sudo cat /proc/modules
...
acer_acpi 7240 0 - Live 0xffffffff88436000
...
bcm43xx 126668 0 - Live 0xffffffff88185000
...


The entire output is:

> 
ovidiu@Ovidiu:~$ sudo cat /proc/modules
ppp_generic 34784 0 - Live 0xffffffff8848f000
slhc 8320 1 ppp_generic, Live 0xffffffff8848b000
af_packet 27020 4 - Live 0xffffffff88483000
ipv6 298240 10 - Live 0xffffffff88439000
acer_acpi 7240 0 - Live 0xffffffff88436000
rfcomm 44512 0 - Live 0xffffffff8842a000
l2cap 29376 5 rfcomm, Live 0xffffffff88421000
bluetooth 58116 4 rfcomm,l2cap, Live 0xffffffff88411000
ppdev 10760 0 - Live 0xffffffff8840d000
fglrx 453172 8 - Live 0xffffffff8839d000
powernow_k8 12480 0 - Live 0xffffffff88398000
cpufreq_userspace 8544 1 - Live 0xffffffff88394000
cpufreq_stats 7624 0 - Live 0xffffffff88391000
freq_table 5888 2 powernow_k8,cpufreq_stats, Live 0xffffffff8838e000
cpufreq_powersave 2688 0 - Live 0xffffffff882b1000
cpufreq_ondemand 9128 0 - Live 0xffffffff8838a000
cpufreq_conservative 10408 0 - Live 0xffffffff88386000
video 18248 0 - Live 0xffffffff88380000
tc1100_wmi 8520 0 - Live 0xffffffff8837c000
sony_acpi 6548 0 - Live 0xffffffff88379000
pcc_acpi 15488 0 - Live 0xffffffff88374000
hotkey 13128 0 - Live 0xffffffff8836f000
dev_acpi 14724 0 - Live 0xffffffff8836a000
container 5696 0 - Live 0xffffffff88367000
button 8288 0 - Live 0xffffffff88363000
acpi_sbs 24024 0 - Live 0xffffffff8835c000
battery 11656 1 acpi_sbs, Live 0xffffffff88358000
ac 6600 1 acpi_sbs, Live 0xffffffff88355000
i2c_acpi_ec 6400 1 acpi_sbs, Live 0xffffffff88352000
i2c_core 26048 1 i2c_acpi_ec, Live 0xffffffff8834a000
nls_utf8 3008 2 - Live 0xffffffff88293000
ntfs 100736 2 - Live 0xffffffff88330000
dm_mod 62536 1 - Live 0xffffffff8831f000
md_mod 76152 0 - Live 0xffffffff8830b000
sr_mod 19108 0 - Live 0xffffffff88305000
sbp2 27268 0 - Live 0xffffffff882fd000
scsi_mod 159928 2 sr_mod,sbp2, Live 0xffffffff882d4000
parport_pc 40176 0 - Live 0xffffffff882c9000
lp 14464 0 - Live 0xffffffff882c4000
parport 43532 3 ppdev,parport_pc,lp, Live 0xffffffff882b8000
joydev 12544 0 - Live 0xffffffff882b3000
arc4 2816 1 - Live 0xffffffff881bb000
snd_atiixp_modem 18828 0 - Live 0xffffffff882ab000
snd_pcm_oss 58784 0 - Live 0xffffffff8829b000
snd_mixer_oss 19968 1 snd_pcm_oss, Live 0xffffffff88295000
snd_atiixp 23128 1 - Live 0xffffffff8828c000
snd_ac97_codec 109628 2 snd_atiixp_modem,snd_atiixp, Live 0xffffffff88270000
snd_ac97_bus 3456 1 snd_ac97_codec, Live 0xffffffff881fd000
ieee80211_crypt_wep 6784 1 - Live 0xffffffff8826d000
tsdev 9600 0 - Live 0xffffffff88269000
r1000 18752 0 - Live 0xffffffff88263000
snd_pcm 104008 4 snd_atiixp_modem,snd_pcm_oss,snd_atiixp,snd_ac97_codec, Live 0x ffffffff88248000
snd_timer 28424 1 snd_pcm, Live 0xffffffff88240000
irda 220524 0 - Live 0xffffffff88209000
r8169 33352 0 - Live 0xffffffff881ff000
snd 68000 9 snd_atiixp_modem,snd_pcm_oss,snd_mixer_oss,snd_atiixp,snd_ac97_codec ,snd_pcm,snd_timer, Live 0xffffffff881eb000
soundcore 12640 1 snd, Live 0xffffffff881e6000
crc_ccitt 3008 1 irda, Live 0xffffffff881e4000
snd_page_alloc 13328 3 snd_atiixp_modem,snd_atiixp,snd_pcm, Live 0xffffffff881df 000
pcmcia 45728 0 - Live 0xffffffff881d2000
psmouse 39748 0 - Live 0xffffffff881c7000
serio_raw 9156 0 - Live 0xffffffff881c3000
pcspkr 3016 0 - Live 0xffffffff880f3000
sdhci 16448 0 - Live 0xffffffff881bd000
usbhid 42400 0 - Live 0xffffffff881af000
mmc_core 34884 1 sdhci, Live 0xffffffff881a5000
bcm43xx 126668 0 - Live 0xffffffff88185000
ieee80211softmac 32000 1 bcm43xx, Live 0xffffffff8817c000
ieee80211 38664 2 bcm43xx,ieee80211softmac, Live 0xffffffff88171000
ieee80211_crypt 7872 2 ieee80211_crypt_wep,ieee80211, Live 0xffffffff8816e000
yenta_socket 29964 1 - Live 0xffffffff88165000
rsrc_nonstatic 14016 1 yenta_socket, Live 0xffffffff88160000
pcmcia_core 47396 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xffffffff88153000
shpchp 50720 0 - Live 0xffffffff88145000
pci_hotplug 32592 1 shpchp, Live 0xffffffff8813c000
evdev 13888 2 - Live 0xffffffff88137000
ext3 145360 1 - Live 0xffffffff88112000
jbd 70312 1 ext3, Live 0xffffffff880ff000
ide_generic 2176 0 - Live 0xffffffff8804b000
ehci_hcd 35592 0 - Live 0xffffffff880f5000
ohci1394 36684 0 - Live 0xffffffff880e9000
ieee1394 368472 2 sbp2,ohci1394, Live 0xffffffff8808e000
ohci_hcd 23044 0 - Live 0xffffffff88087000
usbcore 146428 4 usbhid,ehci_hcd,ohci_hcd, Live 0xffffffff88062000
ide_cd 35104 0 - Live 0xffffffff88058000
cdrom 40568 2 sr_mod,ide_cd, Live 0xffffffff8804d000
ide_disk 18880 5 - Live 0xffffffff88045000
generic 6724 0 - Live 0xffffffff88042000
atiixp 7888 1 - Live 0xffffffff8803f000
thermal 15884 0 - Live 0xffffffff8803a000
processor 28584 2 powernow_k8,thermal, Live 0xffffffff88032000
fan 5832 0 - Live 0xffffffff8802f000
capability 6536 0 - Live 0xffffffff8802c000
commoncap 9088 1 capability, Live 0xffffffff88028000
vga16fb 14480 1 - Live 0xffffffff88023000
cfbcopyarea 4544 1 vga16fb, Live 0xffffffff88020000
vgastate 9792 1 vga16fb, Live 0xffffffff8801c000
cfbimgblt 3584 1 vga16fb, Live 0xffffffff8801a000
cfbfillrect 5184 1 vga16fb, Live 0xffffffff88017000
fbcon 42496 72 - Live 0xffffffff8800b000
tileblit 3520 1 fbcon, Live 0xffffffff88009000
font 9344 1 fbcon, Live 0xffffffff88005000
bitblit 6784 1 fbcon, Live 0xffffffff88002000
softcursor 3136 1 bitblit, Live 0xffffffff88000000


---

### Post by athiex on 2006-07-05
sudo iwconfig eth0 essid "name of unencrypted network" 

post output of iwconfig after attempting this if you continue to have problems...

dhcpcd eth0 

Assuming iwconfig properly associated w/ unencrypted network.

---

### Post by chrisby on 2007-05-13
try stopping  and starting your wireless card with FN and then your network key on your keyboard.  I was having the same problem with an inspiron 1501 and it worked for me.

---

