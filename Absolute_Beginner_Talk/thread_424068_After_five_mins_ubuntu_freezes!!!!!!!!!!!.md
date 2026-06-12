---
title: "After five mins ubuntu freezes!!!!!!!!!!!"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by thegondola on 2007-04-26
I boot up ubuntu and everything seems normal then after a few mins everything froze and I had turn the whole thing off with the power button, please help me.

---

### Post by jdietz on 2007-04-26
More info... You are using liveCD right?  Using a known working computer?  Components?

---

### Post by Cypher on 2007-04-26
The more details you provide the better our answers will be..

---

### Post by thegondola on 2007-04-26
I'm not running the live cd, I've installed ubuntu, ubuntu is on the same hdd as winxp, I'm using:
Nvidia Geforce FX,
1gig of RAM,
40 gig HDD

That's about all I know since I just got this comp second hand.

---

### Post by Cypher on 2007-04-26
Are you doing anything in particular when the freeze happens? Or does it freeze when sitting idle? Can you open a terminal and let it sit running "top" to see if that keeps updating as your computer freezes.

Also, are you using Feisty or another version of Ubuntu? Do you have a USB mouse?

---

### Post by Zzl1xndd on 2007-04-26
and to be sure the same thing isnt happen with win Xp right?

---

### Post by rillip on 2007-04-26
Does this happen in Windows?  Hard lock is often an indication of hardware component failure, especially ovehreating on the CPU.

Does this happen after you start/run one particulary program?  Is it very predictable, i.e. it happens every time you boot at a certain time, or is it more difficult?  Does the behavior change if you leave it off for an hour or two and try again?

---

### Post by thegondola on 2007-04-26
Both times it happened, I've been trying to connect wirelessly (failed) I'm using 7.04, no usb mouse. I now do not actually know how to boot windows (I'm using mac for now)

---

### Post by rillip on 2007-04-26
Both times it happened?  You mean when it is a cold boot and a warm boot?  You should see the option to boot to Windows instead of Ubuntu if it's installed, what are you seeing at boot?

---

### Post by thegondola on 2007-04-26
It froze on me two times. At boot all I see is loading grub then ubuntu starts up. I opened the terminal and tryed to connect to wireless network, it freezes and nothing shows up in the terminal?

---

### Post by Zzl1xndd on 2007-04-26
sounds like you might have wiped your windows install if it just goes right to booting Ubuntu

---

### Post by Cypher on 2007-04-26
Does it freeze if you don't bother with the wirless networking?

---

### Post by thegondola on 2007-04-26
No if I don't try to connect to wireless nothing freezes.

---

### Post by rillip on 2007-04-26
Oookay, believe we found the problem then.  My suggestion: don't use the wireless right now! :P

I don't have any particular advice on how to get that particular issue resolved, but if it only locks up when you do that, you can be pretty sure it's some sort of conflict about it.  You may want to post in the networking board that your computer freezes when you try to use your wireless, and let them know what exactly you are doing to try and get it working.

---

### Post by thegondola on 2007-04-26
Ok thanks guys, you cleared up a load of confusion :)

---

### Post by wheredidrealitygo on 2007-04-26
i've experienced this same issue with a clean install of feisty on a working computer. OEM Vista HP, wiped hdd, clean installed Feisty 7.04, install goes without issue and then five minutes in it randomly stops, just freezes. Mouse still works (usb MS Laser Mouse 5000) and i can click different places but eventually just freezes entirely, it might be because of this same issue. i have a working ethernet connection, and pci wireless on this desktop, it might be pci wireless is causing problems.

I can provide detailed specs on hp (HP Pavilion a1730n with a switched out ATI Radeon X1300, and pci wireless Linksys WRT54G card) if anyone has any suggestions.

---

### Post by magnus07 on 2007-04-27
I have a similar problem here.
This HW was working well with Edgy.
I wiped the HDD0 and made a clean install of Feisty. Bios stayed the same. The only thing I changed is that now I have a lvm as suggested by the Feisty installer.
Besides usual video card problems (old Nvidia) that I fixed by reconfiguring, looked like working perfect but after some minutes (5-10 didn't check really) it hangs completely.
I mean, I can see the display but mouse and keyboard aren't working. No keys combination works.

Looking at disks with gparted Isee it gives warnings on the lvm. cannot recognize the partition. Is this correct? I see there is a small boot ext3 then an extended that gparted says has no mounted logical partition, then inside it the unknown lvm flagged section (that is my primary disk in reality).
I'm puzzled...

Any hint/help apreciated

---

### Post by magnus07 on 2007-04-27
Some additional infos...
It looks related to the network usage.
I lost my network connection then it froze.
So I decided to look around and lastly I went to the Network Configuration and the "new" location feature...
**_I named my unnamed location and since then I've experienced no freeze despite some hours of heavy networking and usage._**
I'll keep you posted.

---

### Post by KrazyPenguin on 2007-04-27
> **magnus07 said:**
> Some additional infos...
It looks related to the network usage.
I lost my network connection then it froze.
So I decided to look around and lastly I went to the Network Configuration and the "new" location feature...
**_I named my unnamed location and since then I've experienced no freeze despite some hours of heavy networking and usage._**
I'll keep you posted.

Also please include hardware.

Stupid Question: Where is the Network Configuration with the "New" location feature?

I don't see it and I am using wireless.

Thanks.

---

### Post by magnus07 on 2007-04-27
OK, unfortunately I was wrong.
But the issue seems related to network and firefox. It's the whole machine that hangs not only the interface since all my network traffic disappeared.

---

### Post by KrazyPenguin on 2007-04-27
> **magnus07 said:**
> OK, unfortunately I was wrong.
But the issue seems related to network and firefox. It's the whole machine that hangs not only the interface since all my network traffic disappeared.

Did you try turning 3d effects OFF and then editing your /boot/grun/menu.lst file as mentioned in the other posts about this subject.  Just add noapic nolapic at the end as mentioned here:
[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)
Go half way down page and try each of those options one at a time.

Do you get the pci=assign-busses error in /var/log/messages???
(do a search, it is long)

Also see if you can crash it without connecting to the internet.

2 hours with Beryl today and I am still trying to Freeze my system.


Here is my stanza:
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=70d0a61f-7453-46d4-85ad-1373ef99813a ro quiet splash noapic nolapic pci=assign-busses
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Notice the 3 things added to the end of the kernel:
Seems noapic and nolapic are important here for some reason.

Good luck!!!

;-)

---

### Post by kittyhawk63 on 2007-04-27
Just tagging this for future reference. I have video freezes with my ATI Radeon 9200SE. I am presently using WinXP. Never had a freeze in WinXP or WinMe with this card.
kh

---

### Post by Arcadian on 2007-04-27
> **magnus07 said:**
> OK, unfortunately I was wrong.
But the issue seems related to network and firefox. It's the whole machine that hangs not only the interface since all my network traffic disappeared.

Hi All,

Please see my post here [http://ubuntuforums.org/showpost.php?p=2549107&postcount=40]("http://ubuntuforums.org/showpost.php?p=2549107&postcount=40")

I followed Magnus07's idea & it seems to have paid off for me. 

Good luck!

Arcadian :KS 

P.s. One other thing I've also done is disabled Network Manager & gone back to the tradition ifup/ifdown method of controlling my network interfaces. The reason for that is I found it was the only way I could get my RT2500 wireless card to talk properly (WEP) with the delivered Ubuntu driver (gave up on the serialmonkey one). It would just never connect with Network Manager, which is a shame because it looks really good. That "may" be another factor if this simple fix doesn't help. Maybe...

---

### Post by whee on 2007-04-27
Freezes can also be caused due to faulty videocards. I used to have Ubuntu freeze every 5 minutes after which i had to reboot. It was due to a nvidia 6600GT videocard which had manufacturing errors.(there was a whole batch that had manufacturing errors i wasn't the only one with such a card with the exact same manufacturing errors)
But boy was it frustrating, it took quite a while before i was sure it was due to the videocard, tried to isolate the problem and am happy i found out the faulty video card was causing it.
Finally i removed the faulty videocard and the freezes stopped completely.

---

### Post by Arcadian on 2007-04-27
Bugger! :( 

OK folks, last one today.

Looks like I may have spoken too soon, I was able to lock it up again but giving Firefox severe scrolling grief. Same symptoms (loss of network, audio drop, total freeze).

However, I have to say, doing these things has made it a little more stable. Lockups were sporadic before, but now only happen when I push things.

pci=assign-busses added to the kernel boot options in /etc/boot/grub/menu.lst does seem to make things a little snappier too I have to say.:-k 

So, what I've just tried now is adding a line to /etc/X11/xorg.conf (in bold)

Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 420]"
    Driver         "nvidia"
**    Option         "NvAGP" "1"**
EndSection

As I've said previously, this worked for me under SUSE. And seems to be okay so far.

Will shut up now & report progress tomorrow!

Cheers All!

Arcadian :KS

---

### Post by magnus07 on 2007-04-28
Arcadian, thanks, but unfortunately we had both the same unfulfilled hope...
I have tried also to change grub loading parameters (noapic, nolapic, ....) but didn't work. Thanks KrazyPenguin.

My HW is PIII 667, 384MB, video agp integraded with NV Aladdin TN2, integrated SIS900 PCI fast ethernet. I'm using the standard NV drivers not nvidia.

It looks related to the networking since if I start using it hangs no matter what program is but with a preference for the mule.

Now I'll mess up the HW with some old networking and video card.
I'll post...

---

### Post by magnus07 on 2007-04-28
For now, I'm not changing the HW.
Instead looking into the daemon.log I see there is a network manager warning where it says there are no  wireless network stored.
Anybody has a guess? I have no wireless network here installed...
Where is the interface for the network manager?

---

### Post by magnus07 on 2007-04-28
I tried to add another ethernet card but messed things up and switched back to the old hw config.

Don't know what elso to do.

This Feisty looks seroiusly bugged for my old HW. Edgy was marvellous in comparison.

---

### Post by GSF1200S on 2007-04-29
Ive been having random freezes as well, and its starting to get really annoying. Sometimes Ubuntu will work for hours, sometimes minutes, than it will completely freeze. The only way I can shut it off is holding the power button. 

It all started 2 days ago when my Xwindow crashed, and I had to create a new Xorg.conf file. I reinstalled my video drivers, added the dbe module and visuals for Beryl. It doesnt make any difference whether im using beryl or metacity, it will just randomly freeze. I never had a problem with this before.

---

### Post by magnus07 on 2007-05-01
My feedback...
I switched back to the 606 LTS.
Works perfectly.
I'll get back to 704 when needed and stabilized (at least for my old PIII.

---

### Post by wheredidrealitygo on 2007-05-02
I finally fixed the problem I was having with it freezing by adding another SATA drive and using it instead of the OEM one, installed grub on the other hdd.

---

### Post by GSF1200S on 2007-05-02
I dont know whats up, but I fixed my freezing problem the moment I switched to KDE. Give KDE a try- its awesome if youve got the hardware for it.

---

### Post by daka on 2007-05-05
Hi

I too am having lots of freezes... different times, different programs... I suspect maybe has something to do with sound server because I get the following message after booting (but sound seems to work fine :

"sound server .. fatal error ... cpu overload ... aborting" ... 

I carry on with programs for a while but often end up hanging.

Any ideas

Daka

---

### Post by snailian on 2007-05-06
> **GSF1200S said:**
>  The only way I can shut it off is holding the power button. 


Instead of using the power button try holding ALT+PrintScreen/SysRq and  typing "S U B" to sync your disks and reboot. You should wait 10 or so seconds between letters to make sure the disks are synced before rebooting.

---

