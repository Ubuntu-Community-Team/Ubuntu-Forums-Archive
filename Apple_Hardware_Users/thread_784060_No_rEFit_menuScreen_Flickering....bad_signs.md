---
title: "No rEFit menu/Screen Flickering....bad signs?"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-06
Hi,
Ok, this is a dual boot setup on my 24" aluminum iMac. I installed rEFit first thing. Then, using Boot Camp Assistant, I made the partition.

I restarted and installed Ubuntu 8.04 -- the Ubuntu install finished ok but my screen was flickering half the time, not a good sign maybe. (I'm hoping maybe later after activating the accelerated driver, it might fix itself??) 

Then I rebooted and No rEFit menu showed up AT ALL. The reboot took me straight into my Apple Desktop. Now I do see the change in available hard drive room is there, so the partition seems to have taken place.

I'm going to boot with the CD as help here and choose 'Boot from First Hard Drive' and see how far I can get....from there I have no idea.

I do appreciate any pointers or help.
Thanks, ...Frank B.

---

### Post by thenes on 2008-05-06
Did the refit menu appear when you mounted the install CD, or any time before your installation?

Did you install refit through a dmg-file (automatically) or manually as described [here]("http://refit.sourceforge.net/doc/c1s1_install.html")?

If it was installed automatically, is the folder named efi in Macintosh HD?

---

### Post by thenes on 2008-05-06
By the way, if you reboot holding the option (alt) key, does that allow you to boot into Ubuntu?

---

### Post by Brightbelt on 2008-05-06
Hi Thenes, Thanks for responding.
Here are the facts right now:

-I installed rEFit automatically. I'll try the other method here in a bit; 

-I got no rEFit menu EVER, neither before nor after installing Ubuntu; holding down 'Alt' on a reboot gives me a Mac Hard Drive icon to press enter for, and that's all I get;

-I tried to re-install rEFit automatically, but it hangs on 'Preparing to Install'. 

- I have just now uninstalled rEFit and will try the other method you mentioned;

-I'm stuck trying to install the bcmwl5.inf with ndiswrapper; I had installed ndiswrapper common, ndiswrapper utilities and unrar,all with deb files. I got a message 'install may not be complete'. 

-The screen has stopped flickering; that might have been the bluetooth mouse because when I switched my mouse to a regular usb and rebooted, the flickering stopped;

That's all I know for now...Thanks for helping, I have to leave in a little bit for a 12 noon appt so I might not be fully responsive until say 3 Pm today. Thanks, 
Frank B.

---

### Post by thenes on 2008-05-06
Can you look in your Macintosh HD if you have a folder named efi . This folder has information that refit use to boot the menu at startup. If it is there, does it have an contents?

Did you install ndiswrapper in Ubuntu or in os x? If you installed in ubuntu, does that mean that you are able to boot into ubuntu somehow?

Since you only find Mac Hard Drive if you hold down the option key, I would check through a disk utility that there is something installed on your other partition. This can be done using gparted on your live CD or through Disk Utility in os x.

---

### Post by benanzo on 2008-05-06
You need to rerun the refit installation script from with OS X.  Boot into OS X, open a terminal and do:
```

$ sudo /efi/refit/enable-always.sh

```

Then at the refit menu select the option that allows you to re-sync your MBR/GPT.

---

### Post by Brightbelt on 2008-05-06
Thanks guys, I now have the rEFit menu showing up when I boot AND I am now able to boot into Ubuntu.

I think the Macs tend to freak out about all this until the Partitions are synced through the Partition Editor. This happened in a similar way on my Macbook Air...I couldn't get a boot into Ubuntu to work until the partitions were synced.

I installed Ndiswrapper into Ubuntu of course; actually I thought I was successful installing the bcmwl5.inf driver and the terminal even says: 

```
bcmwl5.inf driver installed
```

when I do 'sudo ndiswrapper -l'. Then I did these commands:

```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

And I added 'ndiswrapper' to the list in the /etc/modules file to get ndiswrapper booting at startup. 

But I restarted and ZILTCH....no wireless. Did I do something wrong here? I had tried doing the install from just the bcmwl5.inf file sitting on my desktop, but it didn't work, so...

I had an old 'Drivers' folder that I had made for a backup a year ago and it must be from XP because the folder had the bcmwl5.inf file in it. And when I did the install with the directory running through that folder, the install seemed to work....

But still no wireless. The only thing I haven't tried is a full shut down/restart into Ubuntu. The restart didn't help, so we'll see.

I appreciate any help or assistance, Thanks, ...Frank B.

---

### Post by Brightbelt on 2008-05-06
Oh No!! Well guys, after doing a full shut down, no rEFit menu appears, not even if I hold the option key down. 

So I'm now doing a 'Duh' thing here and I'm unplugging 2 external hard drives which I had hooked up. These could have confused rEFit. Yes, I know - I should have done that first thing - I may be getting too used to Macs being trouble free.

I'll run the rEFit code again and see if that helps. 

Thanks, Frank

---

### Post by cyberdork33 on 2008-05-06
what was the output of 'ndiswrapper -l' ?

what is the output of 'ifconfig'?

yes, more than the inf file is required. It isn't obvious though.

External drives do confuse rEFIt. I cannot boot my iMac if my iPod is attached.

---

### Post by Brightbelt on 2008-05-06
Hi Cyber, Thanks for chiming in. I must not have been clear when I mentioned this above; when I do:

```
sudo ndiswrapper -l
``` 

I get something close to this:

```
bcmwl5.inf driver installed
```

I have to reboot to Ubuntu to do the ifconfig, so I'll post it in a few minutes.

Many Thanks for helping, ...Frank B.

---

### Post by blurg on 2008-05-06
With respect to your wireless, sometimes the native linux driver for broadcom wifi chipsets grabs access to that chipset before ndiswrapper gets its hands on it.  Not quite sure why that sometimes happens but I have had that experience. If you modprobe remove ssb and ndiswrapper and then modprobe ndiswrapper then ssb it comes back to life - or at least it worked for me :) The order is important because ssb (part of the linux b43 driver setup which works on earlier broadcom wifi cards) grabs the card but then can't do anything with it but doesn't let go.

Anyway try that:
```
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

And see if it helps re wifi. Also I take it you got the wifi working in the first place? you need the .inf and .sys files from a Windows driver - ndiswrapper gets given the .inf but needs the .sys too.

---

### Post by Brightbelt on 2008-05-06
Thanks Blurg - that's very useful information. I'll try that - but no, I never got this wireless going at all. I had these files (inf and driver backup folder) leftover from previous installs last year on another computer. But it's the same Win XP drivers etc.

For Cyber, here's what I got from ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:63:95:e0:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81800 (79.8 KB)  TX bytes:81800 (79.8 KB)

```

Also, just so you guys know, the rEFit menu is still only intermittently functional. To really be sure that it will appear, I have to run benanzo's code again:

```
sudo /efi/refit/enable-always.sh
```

Also, Cyber, for the record, when I type ndiswrapper -l, I get this:

```
bcmwl5 : driver installed
```

I ran it again just to get it exact.

Many Thanks for all you guys' help and follow through..., Frank B.

---

### Post by blurg on 2008-05-06
Just a very quick check - did you install 32bit or 64bit ubuntu? And if 64bit, are the drivers 32bit? I'm guessing its not your problem but always good to eliminate possibilities :)

---

### Post by Brightbelt on 2008-05-06
Hi Blurg, I installed the 32-bit Ubuntu. And it's the same CD I've used successfully setting up dual boots on 2 laptops just recently.

I did run your code for Ndiswrapper just now. And every line worked except the 3rd line:

```
sudo modprobe ndiswrapper
```

This is what I got back from that line:

```
FATAL: Error running install command for Ndiswrapper.
Syntax Error ";" unexpected
```

Now I did NOT type a semi-colon anywhere, so I have no idea where that syntax error came from.

I appreciate any help,...this gets tiring after a while. :(

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-05-06
Also, I'm 99% sure the drivers I used were 32-bit as well. I've never owned or run XP 64-bit, so I have no idea where I would have gotten 64-bit drivers.

Thanks for the check though...:)
Frank B.

---

### Post by blurg on 2008-05-06
Hmmm... Have you tried installing the ndisgtk package using synaptic (or whatever you use) and using it to select the .inf file? (It appears in System->Admin->Windows Drivers or something similar)

---

### Post by Brightbelt on 2008-05-06
Good idea Blurg, one thing though -  I'm not connected here in Ubuntu. I am connected to Ubuntu on my laptop....Is there a way I could download the package and get it onto a flash drive or something?

Or could I download it to my Mac HD maybe and access it from the other partition?

Thanks for any ideas,....Frank B.

---

### Post by blurg on 2008-05-06
Yea it is [http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk)

I had to do that myself - did it in OS X (make sure you put it somewhere accessible from Ubuntu in the OS X file system) also check on dependencies and get them too or you'll end up switching back and forth a lot :)

Then mount OS X partition from Ubuntu and go into the directory using from the gnome desktop and you can double click on the downloaded packages to install (in correct order obviously)

---

### Post by Brightbelt on 2008-05-06
I'm not sure how I would find the dependencies. I just googled it and downloaded the Ndisgtk Deb file and put it in the Mac HD.

I installed it in Ubuntu just fine and it seemed to install the bcmwl5 ok, but I caught one interesting thing.....

It showed the driver had been installed and then said 'Hardware Present: No'.

So Ubuntu is not even detecting the wireless card or whatever. 

I'm at a loss I guess....Any ideas?? Frank B.

---

### Post by cyberdork33 on 2008-05-06
wrong driver.

---

### Post by Brightbelt on 2008-05-06
Ok, Cyber,...I almost posted a question on that. What is the right driver? 

I'm pretty sure I'm using a bcmwl5.inf from a windows xp folder. Is there something else I should use?

Many Thanks for suggestions here...I did check my iMac hardware specs and it shows this:

```
AirPort Card Information:

  Wireless Card Type:	AirPort Extreme  (0x14E4, 0x88)
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	Broadcom BCM43xx 1.0 (4.170.46.5)
  Current Wireless Network:	**network name**(security blocked)
  Wireless Channel:	11
```
 
The firmware says it is a Broadcom BCM43XX, so I would think this is the right driver....
Any Suggestions?

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-05-06
I actually have Windows XP Pro running on a Parallels virtual machine on this iMac, so I thought "why not find the INF file there?"

It seems logical, but every trace brings me to 'Parallels Network'.  So it seems Parallels has subsumed that function...and I did look just to be safe and unfortunately, I saw no INF file.

Am I up against a brick wall here? Please let me know because I'm rusty anyways having been away from Ubuntu for a while and I need to know if this is fixable and not just something that's going to suck up my time etc etc...

Many Thanks for your help,
Frank B.

---

### Post by cyberdork33 on 2008-05-06
parallels emulates the hardware, it does not utilize "real" hardware.

there is more than one bcmwl5.inf out there... for the MBA you have to use the driver that comes from the restore DVD. It is the only one know to work.... (well that and the one in the recent BootCamp update).

---

### Post by Brightbelt on 2008-05-06
Keep in mind I'm on a 24" iMac. I actually have my Macbook Air up and running wireless fine...so I'll try that file. Many Thanks, Frank

---

### Post by cyberdork33 on 2008-05-06
> **Brightbelt said:**
> Keep in mind I'm on a 24" iMac. I actually have my Macbook Air up and running wireless fine...so I'll try that file. Many Thanks, Frank
oh you switched machines on me. ok, then there are more options, but that one should work as well.

---

### Post by Brightbelt on 2008-05-06
Sorry if I was unclear. Anyways,...using the broadcom folder from the Macbook Air, I DID get the right driver installed.

At least it sees the Device and all is present. But there's ONE BIG hurdle I just discovered....

Earlier, when I was getting desparate, I tried this fix from the Macbook Air Community directions, adding this code to /etc/modprobe.d/ndiswrapper:

```
install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-
install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd
```

But this is only supposed to be used on the 2.6.24-11 Hardy Kernel and I have no idea WHAT my kernel number is. (Like I said, I was getting desparate).

To add to this, when I was typing and trying the regular instructions, I saw references to the above code lines and it said 'You should delete that' and it referenced line 868 for the Ndiswrapper-1.9 file in the /usr/sbin folder. 

But I couldn't find the exact code to delete, SO,....I decided to simply copy the same Ndiswrapper-1.9 file from my Macbook Air and replace it into the same folder for my iMac, since I had not done that code in the Macbook Air file.

BAD IDEA. :confused: 

Now I get statements that there are No Ndiswrapper Utilities, and yet there IS a Ndiswrapper-1.9 file in the /usr/sbin folder.

Is there anything I can do to undo this, short of reinstalling Ubuntu?

I appreciate any help....I'm getting exhausted and don't know how much longer I can work on this....Many Thanks,

Frank B.

---

### Post by cyberdork33 on 2008-05-06
well I don't really know why that would mess things up so much...

check that the permissions are correct:
```
sudo chmod 755 ndiswrapper*
```if that doesn't help things, then try reinstalling ndiswrapper:
```
 sudo aptitude reinstall ndiswrapper-utils-1.9
```also it looks like /etc/modprobe.d/ndiswrapper doesn't even exist for me, so just delete it. There were ussues with module conflicts, and ndiswrapper needed to be loaded before others. That seems to be what that was trying to fix.

---

### Post by Brightbelt on 2008-05-07
HEY HEY !!!! I'm online and wireless! Many Thanks Cyber...What I had to do was uninstall the ndiswrapper-utils-1.9 in the synaptic package manager, which also let me know that Ndisgtk ALSO had to be uninstalled for it to work right.

Once I did that and re-installed the Deb packages for these two items, my Network was there and ready without even a restart needed.

WOW. Boy am I tired. Many Thanks Cyber and Blurb and all you guys for your help. 

I'm about ready to leave this now until tomorrow. Again, Thanks for sticking with me Cyber,...:) 

Frank B.

---

### Post by blurg on 2008-05-07
Glad you got it working :)

---

### Post by Brightbelt on 2008-05-07
Many Thanks for all your help Blurg!!:)

---

