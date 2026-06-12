---
title: "Access Ubuntu Desktop with MacBook"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by andou on 2007-07-30
Gear:

Wireless Router: [NETGEAR WGR614]("http://www.netgear.com/Products/RoutersandGateways/GWirelessRouters/WGR614.aspx?detail=Specifications")
Desktop Mobo : [DFI nF4 Ultra-D]("http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=US")
Laptop : [MacBook]("http://www.apple.com/macbook/specs.html")

Plan:

I've got Ubuntu 6.10 installed on my desktop. I'd like to set it up so that I can access my desktop through my MacBook. For example, if I have some movie or picture files on my desktop, I'd like to be able to show them - on my desktop - but while sitting on my sofa across the room with my MacBook.

I'm pretty new to computers and I'm not sure where to begin. Any suggestions, advice, guidance towards the right tutorials, etc... would be greatly appreciated.

---

### Post by rich.bradshaw on 2007-07-30
VNC.

System menu, remote desktop is somewhere, turn it on.

On mac download chicken of vnc, connect to ubuntu pc, done.

---

### Post by andou on 2007-07-31
Thanks for the reply.

I checked it out... but I couldn't seem to get it to work.

I had no problem with finding the place to turn on remote desktop on Ubuntu.
Also, no problem with running Chicen of the VNC on my MacBook.

I didn't see any places to connect, except for Localhost, which gives me a message:
"Could not connect to server localhost:5900
connection refused:connect()"

So, I tried playing around a bit and I'm not really sure where to put in the info I get from ubuntu.

I am really new at this, so sorry for my inability to use initiative. And thank you for your help so far.

:)

---

### Post by irish_flu on 2007-07-31
VNC and shared desktops are pretty cool.

DEpending on what would work better for you, you could also make a "share" on your desktop computer and view a folder (say, your "home" folder) over the network.

To do that, you would go to System ---> Administration ---> Shared Folders.  Ironically, you want to install "SMB" for "Windows" network shares.

Set that up how you please, and you'll be able to use "connect to server" on your Mac to view the share.

Post back if you have issues, it's been awhile since I've worked with OSX and I might be remembering something incorrectly....

---

### Post by johann_p on 2007-08-01
I am trying to achieve the same thing, but I want to access the desktop from a different LAN computer running either Linux or Windows.

After enabling the "Remote Desktop" preference, the GUI for enabling it shows:
"Users can view your desktop using this command: vncviewer localhost:0"

However, even on the same machine, this does not work.
And of course, "localhost" will never work on a different machine.

Do I have to re-login in order for this to work? If yes, the GUI should tell me that.

---

### Post by andou on 2007-08-01
> **johann_p said:**
> 
After enabling the "Remote Desktop" preference, the GUI for enabling it shows:
"Users can view your desktop using this command: vncviewer localhost:0"


I'm wondering about this as well. Where / How can users use this command?

---

### Post by andou on 2007-08-04
I don't know if I'm supposed to have a network 'setup' or not. and I'm also not sure if I do or not.

I have my Desktop plugged into my router, which is plugged into my Internet modem. Both my MacBook and my Desktop connect to the Internet through the router. That's as much as I know about this. Is this a network?

Do I need to do something different to set up something so that my computers are able to share on 'the network?'

Sorry for my newbness... I'm not even sure how to ask the question that I'm trying to ask, so I hope it makes sense.

Anyway, I can't seem to connect through Chicken of the VNC as stated above, and I'd like to figure this out.

Also, even with a "Share Folder", wouldn't the computers have to be 'networked' for that to work? How do I do that?

---

### Post by andou on 2007-08-04
> **irish_flu said:**
> 
To do that, you would go to System ---> Administration ---> Shared Folders.  Ironically, you want to install "SMB" for "Windows" network shares.


I tried to install "SMB" for "Windows", but it said: Could not apply changes. Fix broken packages first.

---

