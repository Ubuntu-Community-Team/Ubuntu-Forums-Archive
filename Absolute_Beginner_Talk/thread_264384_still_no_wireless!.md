---
title: "still no wireless!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by harperd on 2006-09-24
I have a Packard Bell Centrino laptop (dual boot WinXP/Kubuntu) and I can connect to my wireless access perfectly with XP but not with Kubuntu. I'm not very technical but I thought that wireless was supported 'automatically' and I would'nt have to do anything special.

I've searched the forums and have altered settings with KWIFI Manager and Wireless assistant for hours with no success. Any advice would be appreciated.

---

### Post by tymek666 on 2006-09-24
What's 'iwconfig' result?

---

### Post by harperd on 2006-09-24
lo        no wireless extensions.

eth0      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

---

### Post by happy-and-lost on 2006-09-24
Your radio is off.

I have a Dell with one of those cards, and the driver works a charm once you've got the radio on. I found a way to switch it on in the BIOS. Have a fiddle around in the BIOS and see what you can find.

---

### Post by harperd on 2006-09-24
Thanks. There's nothing relevant in the BIOS. I get the 'radio off' message from wireless Assistant and turn it on but it seems to remain disabled. Despite all of this I'm also getting indications from KWIFIManager thats there's a network detected. Confused? Very! There's a keyboard function key combination for turning the radio on/off but it makes no difference. This issue is one of the last I need to resolve before dumping Windows and it's getting to be a real pain. Midnight here now so I'll get off to bed and decide whether to give up or not tomorrow!

---

### Post by harperd on 2006-09-25
Found out by Googling that my Packard Bell laptop perhaps cannot switch on radio by without special software. There is something I found on Sourceforge which I hope will do the trick.

---

