---
title: "NTP time sync sites - why Ubuntu ???"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-03-03
I noticed that when I was installing and configuring the NTP time sync feature in Feisty that at the **bottom** of the listing of available servers to use to sync with was apparently a Ubuntu server.  And, it was CHECKED/choosen by default.

Why would Ubuntu want to use their server facilities to do this function when there are apparently many other servers/services doing this ?  Would not their facilities be better used to service download offerings and services other than time synching everyone's machine ?

Thanks.

---

### Post by houstonbofh on 2007-03-03
Dlink used to think the same way you do.  Then this happened...
[http://www.lightbluetouchpaper.org/2006/04/07/when-firmware-attacks-ddos-by-d-link/](http://www.lightbluetouchpaper.org/2006/04/07/when-firmware-attacks-ddos-by-d-link/)

Eventually this happened...
[http://www.theregister.co.uk/2006/05/11/d-link_time_dispute_settlement/](http://www.theregister.co.uk/2006/05/11/d-link_time_dispute_settlement/)

This is why you never default your product to a time server you don't have explicit permission to use.

---

### Post by wpshooter on 2007-03-04
> **houstonbofh said:**
> Dlink used to think the same way you do.  Then this happened...
[http://www.lightbluetouchpaper.org/2006/04/07/when-firmware-attacks-ddos-by-d-link/](http://www.lightbluetouchpaper.org/2006/04/07/when-firmware-attacks-ddos-by-d-link/)

Eventually this happened...
[http://www.theregister.co.uk/2006/05/11/d-link_time_dispute_settlement/](http://www.theregister.co.uk/2006/05/11/d-link_time_dispute_settlement/)

This is why you never default your product to a time server you don't have explicit permission to use.

Are you saying by this that I should NOT check any of the other time servers on the listing in the Ubuntu O/S NTP function other than the one that is being serviced by Canonical/Ubuntu ?

And if Canonical is offering these time sync services, are they being performed by a piece of hardware that is dedicate to just that function or is it being done by server(s) that are also performing other services such as making updates to the Ubuntu O/Ss available to the public ?

Thanks.

---

### Post by houstonbofh on 2007-03-07
You can choose whatever you want.  However, sending a distribution to millions with an NTP server belonging to someone else is a different story.  Personally, I use us.pool.ntp.org for my systems.

---

### Post by coxc24 on 2007-03-07
Have a look at [http://www.pool.ntp.org/](http://www.pool.ntp.org/) to find some local NTP servers if you require them.

---

