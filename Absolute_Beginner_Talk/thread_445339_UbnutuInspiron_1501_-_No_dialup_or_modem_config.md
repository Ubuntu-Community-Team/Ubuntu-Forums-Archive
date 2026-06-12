---
title: "Ubnutu/Inspiron 1501 - No dialup or modem config"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by nw53 on 2007-05-15
I'm new to linux and dialup is all I have to the net. There is no cable or DSL in my area. My modem is a Conexant HSX and downloaded the drivers from linmodem. The problam is the gnome-ppp will not install and I don't know what port the modem is on or even if it is config for anything. Dell is planning to offer Ubuntu but there is no support it right now. Thanks for any help you can gave me.

---

### Post by terdon on 2007-05-16
First of all have you run ScanModem and followd it's instructions?
[http://132.68.73.235/linmodems/index.html#scanmodem](http://132.68.73.235/linmodems/index.html#scanmodem)

This tool will help you identify your modem's chipset and what tools to use in order to make it work.

---

### Post by amaurynieto on 2007-07-22
Actually, for Dell's conexant modem (integrated with the audio chipset) the folks over at dell Support have come up with a DEB file with the appropriate conexant drivers. Granted, only "official" for the 1505n model, but when looking into the chipset on either model (1501 and 1505n), we find it's the same D110 chipset. You run the DEB file, it installs, you reboot. Viola! 

Link: [http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en)

---

