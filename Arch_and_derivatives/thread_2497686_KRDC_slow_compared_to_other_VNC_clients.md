---
title: "KRDC slow compared to other VNC clients"
date: 2024-05-14
forum: Arch and derivatives
---

### Post by &amp;KyT$0P# on 2024-05-14
Trying to revive my setup for SSH-tunneled VNC.  In the current landscape of VNC clients, KRDC is the only one I got to try where all functionality I'm seeking works.  But the only way I've found to get reasonable performance from KRDC is to use the lowest quality setting.  But the other VNC clients I've tried don't require such low quality setting to perform well over the same connection.

The VNC server is X0tigervnc on Xubuntu 22.04, started manually with the command from [this post]("https://ubuntuforums.org/showthread.php?t=2480595&p=14118382&viewfull=1#post14118382").  Client is running Arch Linux, using the flatpak version of KRDC, but I remember previously getting similar results on a Xubuntu client.  The connection is over the same LAN.

The other VNC clients I've tried are:
[LIST]
[*]GNOME Connections: scrolling doesn't work
[*]TigerVNC client: scaling is not implemented (yet?), which is awkward since the server machine's resolution is bigger than the client machine's monitor.  TigerVNC client can only either change server's resolution (not wanted) or, if resolution changes are blocked on the server, display at full size with scrollbars (sometimes desirable but not most of the time).
[/LIST]

When I had this issue in Xubuntu client, I solved it by switching to Vinagre.  But it seems Vinagre is now EOL, I would prefer to use a supported VNC client available as flatpak on Flathub.

Is it possible to get KRDC performance on par with these other VNC clients while using at least medium quality option?

Thanks :)

---

### Post by &amp;KyT$0P# on 2024-05-15
Might have stumbled on something that helps? -

Even though the "Local Cursor" option was initially selected, I think the remote cursor was being used.  Because after I got KRDC to un-select and then re-select "Local Cursor", KRDC performance on Medium quality seems quite a bit improved.

Not sure yet whether this is the solution - need to use it more to be sure.

---

