---
title: "Help for an absolute beginner!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by DQuaN on 2008-01-31
Hi all,

I recently installed the latest version of Ubuntu on an old machine with at dual boot setup.  

I've never really used linux before so want to get to know it.

The main problem I have is getting online/connected to the network.  I have a network cable plugged in but it doesn't seem to do anything.  The NIC is a realtek RTL8029 and shows up in device manager, but with unknown vendors.

I also have a NETGEAR WG111T USB wireless dongle.

If anyone could help me get either of these working i would be most greatful!

Thanks

---

### Post by hyper_ch on 2008-01-31
Did you go into the network manager and check if the ethernet is activated?

And can you change the topic title to something more meaningful than a generic "noob here, need help"?

---

### Post by DQuaN on 2008-01-31
ok done.

I found another usb adapter.  This one seems to work with ubuntu.

I now have wireless networking in my network manager.

I still can't seem to connect.  My network runs WPA-PSK.  The only option in ubuntu is WPA Personal.  I tried that and it wont connect.  

Any ideas?

---

### Post by Joeb454 on 2008-01-31
While WPA support is much better, its still a little off target.

However using WPA-Personal should connect you to WPA-PSK, because that's how I connect to my home network :)

---

### Post by DQuaN on 2008-01-31
I have no idea what is going on then.  :(

Once i make the changes i get the little box saying 'Changing interface configuration'

Then once it's gone, i still have no internet access and cannot ping any devices on the network.

---

### Post by Joeb454 on 2008-01-31
So are you wanting to connect through a wired or wireless connection?

Because in the original post you said you had an ethernet cable plugged in. Then went on to say that you have a netgear wireless dongle.

I'm slightly confused :p

---

### Post by DQuaN on 2008-01-31
Sorry!

I want to connect any way I can!

I have a NIC and netgear dongle, both of which have very little support in ubuntu.

Then I fished out a linksys usb adapter that seems to have been recognised.

Now my problem is connecting to the network.

---

### Post by DQuaN on 2008-01-31
My BT Homehub shows that the computer was connected to it at some point!! :S

That is really odd.  It's a shame that it doesn't show when it was connected :(

BTW, how do i change the thread title?

---

### Post by bumanie on 2008-01-31
I have a netgear dongle that works fine with ubuntu. The problem you may be having could be related to the ipv6 stack released some 8-9 months ago. 90% of the time when one can't connect to the internet when using ubuntu 7.1, it is due to this ipv6 issue. To get the internet working in 7.1, I had to blacklist ipv6. If you wish to try this, I will post the codes/instructions below. Be aware that you can always reverse what you have done if it doesn't work.
> gksudo gedit /etc/modprobe.d/blacklist
at the end of the gedit list type
> blacklist ipv6. 
Save and reboot.
To reverse, simply use the first code to obtain the gedit list. Then delete what you added (ie blacklist ipv6) save and reboot. If "the fix" doesn't fix your internet issue, you will be back where you started.

---

### Post by DQuaN on 2008-01-31
OMG!!!  It worked.

With the linksys adapter.

You sir, are a genius!!

:)

---

