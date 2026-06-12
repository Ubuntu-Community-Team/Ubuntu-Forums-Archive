---
title: "Keyboard freezes, slow torrents, shutdown hangs, slow wireless, the list goes on..."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Chamith on 2008-02-12
Hey

So my XP imploded and I decided to give Gutsy a spin (after I toyed with Dapper/Fiesty and gave up) instead of trying to track down a XP CD that works with my DELL tag...

(as a caveat, a LOT of things work well.. including VirtualBox and after MUCH toying with unactivated XP, office 2007, activsync... and really cool eye candy).

There are a few severe problems, some major, and minor annoyances- all of which happened when I switched from a USB ADSL to wireless (linksys).

(MAJOR) - not related to wireless, Gutsy does not recognise the Nikon d40x - it shows up on the devices menu.. but there is no mount or drive that pops up.  I need the camera, is there any solution? same for my Mio PDA but that works in VirtualBox with Outlook..

(MAJOR) The first thing was that** Ubuntu started to hang on shutdown**.  At first, not all the time.. then all the time.  Its very annoying as I use the laptop for work and need to know that the computer shutdowns without having to wait and check.

(SEVERE) When running Miro or Azureus or any torrent programme the** keyboard will occasionally stop working**. no keys are registered and I need to shutdown and restart to get it back.

(MAJOR) When downloading torrents (bittorent, azureus, miro) the rate is VERY slow if at all and the entire internet slows down, fans switches to overdrive, and a restart is needed.  I checked the forums and google and disabled ipv6 (using MANY MANY methods) and just now replaced network manager with Wicd...  no effect.

(MINOR) many..including intermittent dropping of connection, widely varying download speeds within firefox (ranging from 2 to 200), etc, etc.  

(MINOR non networking) - the second partition of my HD does not automatically mount at start and I need to enter a password to access.  can this be automated so its ready at start?

I read that Gutsy has problems with some routers?  could that be it?  its a fairly common Linkys b/g router... if that's the problem then it effectively kills the ability to roam with a laptop and have any certainty that you could access wireless hotspots...

Any suggestions?  

Thanks!

---

### Post by PCFascist on 2008-02-13
I don't use the camera, but I found this...

[http://www.mohdshakir.net/2007/11/06/nikon-d40x-in-ubuntu-linux](http://www.mohdshakir.net/2007/11/06/nikon-d40x-in-ubuntu-linux)

---

### Post by Chamith on 2008-02-13
Thanks, it didn't solve the problem of mounting or accessing the files on the camera.  But once I get that working the script will be helpful in converting the RAW files!

---

### Post by Chamith on 2008-02-13
Following advice on torrents and Linksys routers I changed the router firmware ([http://www.utorrent.com/faq.php#Special_note_for_users_with_Linksys_WRT54G_GL_GS_routers](http://www.utorrent.com/faq.php#Special_note_for_users_with_Linksys_WRT54G_GL_GS_routers)) - which really helped on torrent speeds in XP.

However, I am still facing the keyboard freeze  and painfully slow (less than 1kb) internet connection problems when I try to download torrents (utorrent as well).

If I am on a wired internet connection then the shutdown works as normal, otherwise it hangs after saying "unable to unmount, device is busy"

Any advice?

---

