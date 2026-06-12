---
title: "Installing ubuntu 12.04 on 2012 Macbook AIr"
date: 2012-09-15
forum: Apple Hardware Users
---

### Post by Bradskey on 2012-09-15
Hello,
I recently bought the 2012 Macbook Air and I've been trying to install ubuntu 12.04 on it as a partition.
I have been following this guide ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)) to the letter and I have installed rEFIt. However, when I start up the mac and choose the to boot from the USB, it starts to run but then says "kernel panic not syncing timer doesn't work through interrupt-remapped io-apic".and then hangs. Ive searched over the net but can't seem to get it going . any help would be very appreciated, thank you.

---

### Post by asting on 2012-09-15
There is another thread on this very issue. I haven't devoted the time to messing with it yet, but see this thread:
[http://ubuntuforums.org/showthread.php?t=2006289](http://ubuntuforums.org/showthread.php?t=2006289)

Basically, you need to add the nointremap boot option in order to get past that.
What guide were you using in order to configure refit?

When you get it installed please update on how usable it is. I'm hoping to put it on my '12 MBA.

---

### Post by pratnala on 2012-09-15
When you see the icon, press 'enter', then select "English", then press F6 and select noapic. Press esc and install ubuntu

---

### Post by Bradskey on 2012-09-15
> **asting said:**
> There is another thread on this very issue. I haven't devoted the time to messing with it yet, but see this thread:
[http://ubuntuforums.org/showthread.php?t=2006289](http://ubuntuforums.org/showthread.php?t=2006289)

Basically, you need to add the nointremap boot option in order to get past that.
What guide were you using in order to configure refit?

When you get it installed please update on how usable it is. I'm hoping to put it on my '12 MBA.

I've seen that thread but I get stuck at the part where it says to add the boot function. I don't know where I add this boot option to. I'm very new to all of this.
I don't think I've configured rEFIt, I just downloaded and installed it. Do I have to add nointremap to a file in rEFIt?

I apologise for being so clueless #-o

---

### Post by Bradskey on 2012-09-16
I suppose my real questions is "Where can I find Boot Options?"

---

### Post by orthodoc on 2012-09-16
@Bradskey: FOllow the instructions on this post: [http://ubuntuforums.org/showthread.php?t=2039799](http://ubuntuforums.org/showthread.php?t=2039799)

It's quite detailed and will help you install Ubuntu and also set it up.

---

### Post by Bradskey on 2012-09-17
> **orthodoc said:**
> @Bradskey: FOllow the instructions on this post: [http://ubuntuforums.org/showthread.php?t=2039799](http://ubuntuforums.org/showthread.php?t=2039799)

It's quite detailed and will help you install Ubuntu and also set it up.

This post saved my life. Thanks so much for leading me to that. The method in there worked perfectly and now ubuntu's working great on it.

And @asting, 
It seems to work quite seamlessly. The only thing that is bothering me is that I normally have my thumb resting on the trackpad and direct the pointer with my index finger. However every time I have 2 fingers on the trackpad, it locks the mouse in place and only lets me scroll. It's a minor issue but it interferes with my normal trackpad usage a bit.

---

