---
title: "setting up remote access for mac"
date: 2010-08-06
forum: Apple Hardware Users
---

### Post by raffi_1970 on 2010-08-06
Hi, My dell notebook runs Ubuntu (Karmic Koala). 

I want to be able to remote access my mom's Mac notebook (I believe it's an Airbook?), so that I can assist her with problems on her computer.

What would I need to do on my computer (and how?)

What would I need to do on her computer (and how?) to set this up?

thanks!

---

### Post by Macskeeball on 2010-08-07
I think you mean MacBook Air.

At any rate, there's a multi-platform screen sharing technology called VNC (not to be confused with VLC, which is a media player). The Mac has a screen sharing server built-in that's normally for Mac-to-Mac, but you can also turn on support for VNC clients. Ubuntu comes with an application called Remote Desktop Viewer, and that supports VNC.

On her Mac:
[list=1][*]Click on the Apple menu at the top left and choose "System Preferences."
[*]Choose "Sharing."
[*]Check the box for "Screen Sharing"
[*]On the right, click "Computer Settings..."
[*]Check the box for "VNC viewers may control screen with password."
[*]Enter a password, preferably something **very** strong (at least 20 characters, randomly generated). We are talking about remote control after all. Your computer will be able to remember the password for you.
[*]Set up dynamic DNS for her computer if you haven't already. That way you'll be able to connect even if her IP address changes or if she takes her laptop somewhere. The steps for that are beyond the scope of these instructions, but a free dynamic DNS service you could go with is [www.dyndns.com](www.dyndns.com)[/list]

On your computer, you will use Remote Desktop Viewer to connect.
[list=1][*]Choose Applications > Internet > Remote Desktop Viewer.
[*]Click connect.
[*]Set the protocol to VNC
[*]For the host field, enter the dynamic DNS domain you set up for her.
[*]Click Connect, and I presume it should then ask for the username/password.
[/list]

I've not actually done this between OS X and Ubuntu before (just OS X to OS X) and I don't have much experience with Apple's built-in VNC server, but the above seems like it should work. Let us know if there are issues.

---

