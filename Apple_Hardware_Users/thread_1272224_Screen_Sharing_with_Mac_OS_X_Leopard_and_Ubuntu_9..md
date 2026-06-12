---
title: "Screen Sharing with Mac OS X Leopard and Ubuntu 9.04"
date: 2009-09-21
forum: Apple Hardware Users
---

### Post by arejay on 2009-09-21
I was trying to use the built-in screen sharing technology in Mac OS X to connect from my Mac to my Ubuntu machine.  I was having the problem where the screen would just sit at the connection dialog and nothing would happen.  Well here's how I got it working.

On the Ubuntu Machine:
System > Preferences > Remote Desktop

Make sure the following if set
Check "Allow other users to view your desktop"
Check "Allow other to control your desktop"
Check require the user to enter this password (And enter a password)  NOTE: This is the option I didn't check and it was not working without a password.

close the dialog

On the Mac:

Open the finder application
Select the Go menu and select Connect to server...
Server address field put vnc://ip to ubuntu server
Click connect button.

You should be prompted for a password.  Enter the password from the Ubuntu settings.
Click ok to the dialog box about support for encryption and you are done.

Hope this help someone and saves them hours of Google searching.

---

### Post by prtc on 2009-09-30
I'm not managing. I did exactly as it is described, but when I attempt the connection I get

"Connection failed to "nymeria"
Please make sure that Screen Sharing ... is enabled etc etc"

I get the error message even before prompting for the password.

Any ideas?
thx

---

### Post by pedrogent on 2009-11-03
> **arejay said:**
> I was trying to use the built-in screen sharing technology in Mac OS X to connect from my Mac to my Ubuntu machine.  I was having the problem where the screen would just sit at the connection dialog and nothing would happen.  Well here's how I got it working.

[...]

Check require the user to enter this password (And enter a password)  NOTE: This is the option I didn't check and it was not working without a password.

[...]

Hope this help someone and saves them hours of Google searching.

Brilliant! Thanks very much.

One problem tho' is that when I navigate around it displays on the Ubuntu screen but the navigation doesn't happen on my MacBook screen. Any idea how I might fix this?

---

### Post by ottobar on 2009-11-22
> **pedrogent said:**
> Brilliant! Thanks very much.

One problem tho' is that when I navigate around it displays on the Ubuntu screen but the navigation doesn't happen on my MacBook screen. Any idea how I might fix this?

I had this same problem and found in a comment somewhere that screen sharing will appear frozen unless the visual effects are turned off (System > Preferences > Appearance...then select None in the Visual Effects tab).

---

