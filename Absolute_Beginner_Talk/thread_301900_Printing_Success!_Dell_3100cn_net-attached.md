---
title: "Printing Success! Dell 3100cn net-attached"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by ArtechnikA on 2006-11-17
First, I'm a little surprised there isn't a main section for printing issues, since it always seems to be a problem...

In Any Case - after searching all over the web I found enough bits to put it all together. Hopefully this will be helpful to someone.

All the CUPS configuration documentation seems directed to either locally attached printers (I haven't had one of those for a long time) or printing through another Ubuntu/Linux workstation (client/server) to a printer that's locally attached and shared there (not my situation either).

I tried a LOT of things and it's working now, after having been through all the issues everybody else seems to have experienced -- jobs that auto-cancel themselves forever, jobs that auto-print garbage forever - that kind of thing.

Tried adding printers through the GUI (Administration | Printing) and directly via CUPS (at localhost:631) with pretty much equivalent (bad) results, until a few minutes ago.

My suggestion is - despite what the CUPS prompt suggests, avoid using '-' in your printer name.  I don;t think that was really the problem, but it's one of the things I changed along the way and I'm not going to be good about changing it back to test...

I believe the *real* issue was: although the GUI printer configuration *and* CUPS configuration give you a LOT of ways that you -might- establish a network connection to a net-attached printer (Dell 3100cn in my case) it's hard to find the exact protocol that *does* work...

The Postscript PPD file is available on the 3100 CD, and I also found it as part of my Windows install (I installed both the 'native PCL' and Postscript versions...) and it's on the Dell website if you know where to look.  There are breadcrumbs on the web, but for now I figure if you've got eh printer, you've got the CD that came with it...

Like I said, the protocol is the thing.  I installed it through CUPS and specified 'ipp' and then - *this is the important part* - gave it the path "socket://192.168.1.100:9100" (192.168.1.100 is the static IP where my 3100cn is installed - Your Mileage May Vary).  The important part is to specify socket: as the access method and to append the port.

Printed a Test Page and - I gotta tell you - it's pretty nice :-)

When I went back to recheck the settings, Administration | Printing right-click | Properties | Connection tells me it's using "HPJetDirect" and CUPS just tells me it's using the socket I designated.  But it's working... (!)

Sp - Network attached printers *can* be made to work - you just need to know the (undocumented) magick incantation.

I also got the GRUB default boot to be what I wanted today, so it was a good day...

---

