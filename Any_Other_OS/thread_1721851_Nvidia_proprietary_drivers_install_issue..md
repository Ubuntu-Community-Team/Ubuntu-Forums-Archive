---
title: "Nvidia proprietary drivers install issue."
date: 2011-04-05
forum: Any Other OS
---

### Post by ruien on 2011-04-05
Hi

I have a Toshiba Qosmio G40 laptop with a broken internal monitor so I cant see anything on it. I use vga to connect it to a Samsung 40" LCD TV and it works just fine as long as i dont install the nvidia proprietary drivers for my graphics card. But i want the nvidia driver installed to use hdmi connection to TV but when i try that and reboot it reboots with the internal monitor set as default regardless vga or hdmi cabel connected. Or both. The TV is dead with no signal. My TV auto shuts down when no signal is detected so i cant do anything about it but to reinstall and use only VGA and no nvidia proprietary drivers. In windows i can use hdmi/vga with no issues at all so i think it should be possible with linux also. I do not have windows installed atm. 

I could post lspci and lsusb but it doesnt matter. My question is how i can lock the monitor set to the 40" TV and not the internal monitor when installing nvidia drivers before i reboot and use the new driver? Or at least make nvidia drivers use vga connection so i can get picture on the 40" TV. Then i can set the hdmi out later. 

My nvidia card is a Geforce 8600GT M and Linux Mint 10 standard installed.

*I have posted this before and since then installed win 7 because i haven't got any tip on how to do this. But if anyone had this problem before and solved it  I would realy like to know how to do this *

Thanks

---

### Post by Perfect Storm on 2011-04-05
Try see if this help: [http://www.brighthub.com/computing/linux/articles/31614.aspx](http://www.brighthub.com/computing/linux/articles/31614.aspx)

---

### Post by ruien on 2011-04-05
> **Artificial Intelligence said:**
> Try see if this help: [http://www.brighthub.com/computing/linux/articles/31614.aspx](http://www.brighthub.com/computing/linux/articles/31614.aspx)

Thanks but this guy have an internal monitor to set the right config for the external monitor after installing the nvidia proprietary drivers. I dont because i dont have any internal monitor to use.  What i need is a xorg.conf that works AFTER rebooting when installing proprietary drivers. Then i can get the external monitor up and running with vga and set hdmi after logging in.  I had this laptopp set up like this before the internal monitor broke and it worked just fine with the same TV.

---

