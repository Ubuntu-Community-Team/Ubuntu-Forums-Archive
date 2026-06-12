---
title: "Installation - Losing the will to live!!"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-03-30
I am new to ubuntu and linux and am really finding the change over from windows hard.

I recently put Ubuntu onto a new computer, it seemed to install OK but trying to get connected to the internet seems impossible.

I have a router set up and connected to a PC running windows XP and I want to connect my new PC through this router.

I gave up trying to use a USB wireless adapter, when I read that they are difficult to set up with Linux and then tried an cable between my PC and the router, this doesn't even work.

I tried entering
sudo pppoeconf into the terminal and got this messge.

NO INTERFACE FOUND
Sorry, no working ethernet card could be found. If you do have an interface card which was not autodetected so far, you probably wish to load the driver manually using the modconf utility.
Run modconf now?
Yes     No

I select Yes and nothing happens, the same screen just flickers and re-appears.

Would someone please help guide me through the rest of the installation, I am really close to giving up and I am not usually easily beaten.

My sound card doesn't work either but that's for another day I guess!

Thanks in anticipation

---

### Post by aberry5555 on 2007-03-30
you should be able to do it all from the setup menu. I cant remember the exact route to it but if you look in the options there should be something about network configuration. Turn your ethernet card to DHCP and restart, it should probably work. Sorry Im being vague but my pc has been bust for about two months now and my ubuntu-ing is limited these days :S

---

### Post by OldDog11 on 2007-03-30
I was only given the option to do that when I had my USB wireless adapter connected. In network setting now there is only a Moden Connection to configure and this does not ask for DHCP

---

### Post by OldDog11 on 2007-03-30
Please can someone help!

Why doesn't the modconf utility work or shouldn't I even need this?

---

### Post by compmodder26 on 2007-03-30
If you are connecting to the router via an ethernet cable, you have no need for any modem utilities.  It sounds like your ethernet card isn't being recognized, which is weird because the vast majority of ethernet cards work out of the box.

---

### Post by compmodder26 on 2007-03-30
Type "ifconfig" in a terminal and post the output here.

---

### Post by Gaunty on 2007-03-30
Are you connecting to your router using ethernet, if so you need to get your ethernet adapter running.  Do you know what the make and model is?

Hehe, you wait hours and three answers come at the same time.  I need to learn to type faster!

---

### Post by OldDog11 on 2007-03-30
Result from entering ifconfig

david@david-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45536 (44.4 KiB)  TX bytes:45536 (44.4 KiB)

---

### Post by OldDog11 on 2007-03-30
Hi Gaunty

My ethernet adapter is on my Asus M2N motherboard

---

### Post by justin whitaker on 2007-03-30
> **OldDog11 said:**
> Result from entering ifconfig

david@david-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45536 (44.4 KiB)  TX bytes:45536 (44.4 KiB)

I don't think your Ethernet card is working. I could be wrong (probably am) but there should be another line or two in addition to the lo loop back.

---

### Post by Gaunty on 2007-03-30
> **OldDog11 said:**
> Hi Gaunty

My ethernet adapter is on my Asus M2N motherboard
Is the ethernet card turned on in your BIOS?

---

### Post by OldDog11 on 2007-03-30
How do I get it working?

---

### Post by Gaunty on 2007-03-30
> **OldDog11 said:**
> How do I get it working?

It's probably not that if its working under Windows(?)  i'm guessing it does.

I've found this thread that looks like the same problem as yours.
[http://ubuntuforums.org/archive/index.php/t-274472.html](http://ubuntuforums.org/archive/index.php/t-274472.html)

---

### Post by OldDog11 on 2007-03-30
I do not have windows on this PC

My LAN card is set to {Auto} in the bios

Onboard LAN Boot ROM is Disabled - should this be enabled?

---

### Post by charles.g.moore on 2007-03-30
> **OldDog11 said:**
> I do not have windows on this PC

My LAN card is set to {Auto} in the bios

Onboard LAN Boot ROM is Disabled - should this be enabled?

No, you doin't enable that I think it has something to do with network booting.

---

### Post by compmodder26 on 2007-03-30
It appears that somebody else with an Asus M2N mobo had problems as well: [http://ubuntuforums.org/showthread.php?p=2073864](http://ubuntuforums.org/showthread.php?p=2073864)

The person in that post had their problem fixed by using Feisty.  I'll look elsewhere for other solutions.  Just wanted to post this to confirm that Edgy and below seem to have issues with recognizing the onboard components of this motherboard.

---

### Post by OldDog11 on 2007-03-30
Thanks compmodder26

You may have been a life saver!!

It is looking as though it could be my motherboard, there does seem to be others with my problem. I know I'm new to Linux but I was beginning to think that it really was not for me, at least now I have some hope, at least for a little while.

I am a little nervous about trying a beta version of something I know little about but, hey, what the hell, in for a penny in for a pound as they say. I certainly hope this old dog can learn a few tricks or else Bill Gates will get even more of my hard earned cash!!

---

### Post by compmodder26 on 2007-03-30
Don't be too intimidated by Feisty being beta.  It has been quite stable for the vast majority of users for quite a while now, including myself.  Now, having said that.  I give no guarantees that it will remain stable and nothing will go wrong.

---

### Post by lamalex on 2007-03-30
yeah feisty is pretty stable right now, I would say expect maybe one or two more breaks but nothing that won't get fixed quickly. My ethernet doesn't work on my ASUS mobo either, is yours an nforce4 chipset? They seem to have some issues with linux. I added nolapic to my boot line and that fixed some of my issues with my ASUS mobo. Might want to try adding that.
go into /boot/grub/menu.lst and add nolapic to your boot options.

---

