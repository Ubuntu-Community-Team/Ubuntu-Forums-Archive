---
title: "Can't change from Pulse dialing"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by MattThLinuxNewb on 2007-02-12
I've almost got my old Conexant dial-up modem working with Ubuntu using a free Linuxant driver and wvdialconf/wvdial, but Ubuntu won't let me set the modem options to tone dialing instead of pulse dialing! It always reverts back as soon as i close and reopen the Networking window from administrative tools. It also keeps reverting to unchecked/disabled (though this doesn't seem to matter to wvdial)

Does anyone know why this is? Really frustrating :confused: 

Thanks, Matt

---

### Post by Bartender on 2007-02-12
Matt - 
I posted about this a few months ago, and entered a bug report.  Well, I tried to anyway.  :) 

Dump Edgy and install Dapper.  Dapper accepts the "Tone" entry instead of changing it.  Dapper also auto-detects the modem if it's external, and the Modem Monitor thingie works fine if you drop it into your panel.
I'm really disappointed that Edgy has dial-up bugs that Dapper doesn't, but that's the way it is right now.

---

### Post by MattThLinuxNewb on 2007-02-12
Cheers i'll try Dapper and see how it goes :)

---

### Post by Stunt Double on 2007-02-12
Matt,
       I had the same problem with my internal conexant modem using the Linuxant driver with Edgy. I found that wvdial was my only option. Entering "sudo wvdial" in a terminal always works and results in a rock-solid internet connection. The set-up, pulse versus tone, seems to be irrevelant when wvdial is used.

---

