---
title: "Setting up a Nova-T-500??"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-12-08
Hi there,

I'm trying to set up a nova-t-500 dvb tuner.  I've got quite some way but I still cant quite get it working.  All advice welcome...

so this is where i am now...  I followed [www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
to get this far, so now If I type grep -i dvb /var/log/messages

I get 

Dec  7 08:59:16 tony-desktop kernel: [   21.260000] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
Dec  7 08:59:16 tony-desktop kernel: [   21.260000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Dec  7 08:59:16 tony-desktop kernel: [   21.260000] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Dec  7 08:59:16 tony-desktop kernel: [   21.488000] DVB: registering frontend 0 (DiBcom 3000MC/P)...
Dec  7 08:59:16 tony-desktop kernel: [   22.128000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Dec  7 08:59:16 tony-desktop kernel: [   22.128000] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Dec  7 08:59:16 tony-desktop kernel: [   22.136000] DVB: registering frontend 1 (DiBcom 3000MC/P)...
Dec  7 08:59:16 tony-desktop kernel: [   22.700000] input: IR-receiver inside an USB DVB receiver as /class/input/input4
Dec  7 08:59:16 tony-desktop kernel: [   22.700000] dvb-usb: schedule remote query interval to 150 msecs.
Dec  7 08:59:16 tony-desktop kernel: [   22.700000] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.....

so the card is recognized (as is my mythtv backed) but no channels in myth so I;m trying to get it working in ubuntu first...

if I do this...
sudo apt-get update
sudo apt-get install dvb-utils dvbstream
sudo -s -H
mkdir /root/.tzap
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/se-Skovde > /root/.tzap/channels.conf

then i get no channels found??? (I live in Skovde Sweden)

if I type dmesg | grep dvb
then I get...
[   21.288000] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   21.376000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   22.288000] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   22.288000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   22.956000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   23.528000] dvb-usb: schedule remote query interval to 150 msecs.
[   23.528000] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   23.580000] usbcore: registered new interface driver dvb_usb_dib0700


So why can't I find any channels??
What have I missed?

all help really appreciated

---

