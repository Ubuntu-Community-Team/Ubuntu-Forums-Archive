---
title: "Can't boot-is it my hardware?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by johnwillyums on 2007-05-16
Hi. I'm beginning to think my pc just won't run Linux. Over the last few days I installed a free distro of Mandriva. It installed but would only get so far in the boot process before stalling. I had plenty of help from the nice folk on the Mandriva forum but in the end they suggested that it might be a hardware problem and that I should try a distro with a newer kernel such as Ubuntu.
By spooky coincidence the cd of Feisty I had requested from Shipit came through my door this morning so I have just tried to run it several times with no success.
Everything seems to go fine-lots of "oks" etc and the orange bar moves across but then I get to some rapidly moving pages of text. These swiftly reach a point and then stop at a page with several mentions of "do_page_fault+0x0/0x5fo"
 The final two lines are as follows-
[100:338510]   [<c010234b>] work_notifysig+0x13/0x18
[100:338510]  ==========================

I have tried several times and it stalls on the same message although the initial number is different.
My equipment is about two years old. I have a Celeron R 3.06 cpu, an 80gb IDE c. drive with Windows XP on half of it and my failed Mandriva install on the other half plus a 120gb d. drive which is 3/4 full of music and photographs. I also have an Nvidia 6600 graphics card plus a Canon printer  attached. I connect to the internet through a BT 240 ADSL router via an ethernet cable.

Can anyone help? It seems that my hardware is neither ancient nor exotic. Why won't Linux work for me?

Thanks, John Williams

---

### Post by overdrank on 2007-05-16
> **johnwillyums said:**
> Hi. I'm beginning to think my pc just won't run Linux. Over the last few days I installed a free distro of Mandriva. It installed but would only get so far in the boot process before stalling. I had plenty of help from the nice folk on the Mandriva forum but in the end they suggested that it might be a hardware problem and that I should try a distro with a newer kernel such as Ubuntu.
By spooky coincidence the cd of Feisty I had requested from Shipit came through my door this morning so I have just tried to run it several times with no success.
Everything seems to go fine-lots of "oks" etc and the orange bar moves across but then I get to some rapidly moving pages of text. These swiftly reach a point and then stop at a page with several mentions of "do_page_fault+0x0/0x5fo"
 The final two lines are as follows-
[100:338510]   [<c010234b>] work_notifysig+0x13/0x18
[100:338510]  ==========================

I have tried several times and it stalls on the same message although the initial number is different.
My equipment is about two years old. I have a Celeron R 3.06 cpu, an 80gb IDE c. drive with Windows XP on half of it and my failed Mandriva install on the other half plus a 120gb d. drive which is 3/4 full of music and photographs. I also have an Nvidia 6600 graphics card plus a Canon printer  attached. I connect to the internet through a BT 240 ADSL router via an ethernet cable.

Can anyone help? It seems that my hardware is neither ancient nor exotic. Why won't Linux work for me?

Thanks, John Williams


Hi have you tried the alternate cd
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
Scroll down to the alternate cd and be sure to follow the how to in burning the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hope this helps good Luck !

---

### Post by dstew on 2007-05-16
If you are having problems getting the Live CD to run, there are boot options you can try that sometimes will fix problems like yours. You get to the boot options line by pressing F6 at the startup page of the Live CD. Press F1 for a Help menu to look at what boot options are available. Options like "noapic" and "nolapic" have been helpful. And, of course, the Alternate CD will almost always work to install Ubuntu.

---

### Post by BHelts on 2007-05-16
i would suggest running a memory test.  most page faults are memory related and any kind of installation bombing out is a strong indication of bad ram.

---

### Post by johnwillyums on 2007-05-16
Thanks folks. I have managed to delete all my non NTFS partitions and therefore removed my failed Mandriva install. I now seem to have a new partition which shows up as a K. drive in my computer. I tried to extend my C. drive into it with Diskpart in Windows disk management but it won't do it for some reason, Oh well at least I can access it now. I'm currently waiting for Wubi to download. I've been following Wubi for months and figure if this doesn't work I'm going to have to give up on Linux. That's a real shame and I don't understand why my machine won't do it. As I said above it's neither that old nor exotic in any way. I'll let you know how I get on with Wubi but after two different distros not working I'm not that hopeful. 
Cheers, John Williams

---

### Post by Terl on 2007-05-16
I pasted bits of your error message into google and got some hits--all hardware related.  I would recommend you check some of the errors out via googling.  One pointed to a possible network card issue and other hits pointed to a video card (tv card actually) issue.  With just the last bits of the codes it is hard to tell exactly.  Have you googled a bit?

Have you run the memory test suggested earlier?

---

### Post by johnwillyums on 2007-05-16
Hi. No I haven't tried the memory test yet. Do you mean from the live disk? I just tried to install from Wubi. It seemed to be going really well, lots of progress bars, installing kernel, software etc and then it got to finishing installation. Suddenly there were some text overlays in white which were to rapid to read other than "the system is going down" which it did and began a reboot. I chose Ubuntu in the boot menu but the progress bar only moved a few centimetres then stopped. I checked my new K. drive and the Wubi folder is there but I don't know what to do next. I suppose I should go onto the Wubi forum.
By the way I don't have a tv card and don't really know what to do if its my network card. Don't really know much do I? This is most disappointing but it's looking like I'm going to have to give up on the whole Linux idea. I am not very technical and have only been using a computer for a couple of years so my knowledge of Windows is basic and self taught. Oh well. John Williams

---

### Post by Terl on 2007-05-16
> **johnwillyums said:**
> Hi. No I haven't tried the memory test yet. Do you mean from the live disk? I just tried to install from Wubi. It seemed to be going really well, lots of progress bars, installing kernel, software etc and then it got to finishing installation. Suddenly there were some text overlays in white which were to rapid to read other than "the system is going down" which it did and began a reboot. I chose Ubuntu in the boot menu but the progress bar only moved a few centimetres then stopped. I checked my new K. drive and the Wubi folder is there but I don't know what to do next. I suppose I should go onto the Wubi forum.
By the way I don't have a tv card and don't really know what to do if its my network card. Don't really know much do I? This is most disappointing but it's looking like I'm going to have to give up on the whole Linux idea. I am not very technical and have only been using a computer for a couple of years so my knowledge of Windows is basic and self taught. Oh well. John Williams

The memory test is an option from the live cd menu.

Is this a pc you built or was it custom made?  If not do you have a make/model?  I only did a quick search pasting parts of the errors into google so what I did may/may not help.  Pasting error messages usually does get some answers.

I do not know much about Wubi so I cannot help you there.

---

### Post by johnwillyums on 2007-05-16
Hi Terl. I had the pc built for me by a local shop. I do not know much about what's inside it other than what I already put in my first post. Is there a way of finding such info out through Windows? cheers,John Williams

---

### Post by johnwillyums on 2007-05-16
Hello again. I've run the memory test then tried to reboot from the live disk. It's taken ages to write out the full page on which it stalled.
The memory test went as follows-
Celeron(0.09) 3063MHz
L1:Cache:16k 18790MB/s
L2:Cache:256k 18790MB/s
Memory:1023 1685MB/s
Chipset:Intel i848/i865 (ECC:Disabled)-FSB:133MHz-PAT:Enabled
Settings:RAM:133MHz (DDR266)/CAS:2.5-4-4-8/Dual Channel(128bits)

The test took quite a while and finished up PASS and no errors.

I then escaped and tried to boot from disk. I got into the boot choices but could not find a way to type in noapic nolapic .
I did get a text boot which stalled on this page-

[189.756643][<c01053507>] do_invalid_op+0x0/0xb0
[189.756787][<01053f27>] do_invalid_op+oxa2/0xb0
[189.756932][<c011ddac>] kmap_atomic+0x5c/0xa0
[189.757076][<c027fa87>] memcpy_toiovec+0x37/0x60
[189.757222][<c011e678>]__wake_up+0x38/0x50
[189.757366][<c0298aed>]netlink_recvmsg+0x1fd/0x320
[189.757512][<c02e3776>]unix_dgram_recvmsg+0x196/0x2a0
[189.757659][<c02eeb4c>]error_code+0x7c/ox90
[189.757803][<c027007b>]show_scaling_available_governors+0xbb/0xc0
[189.757953][<c011ddac>]kmap_atomic+0x5c/0xa0
[189.758097][<c0163930>]unmap_vmas+0x180/0x5c0
[189.758245][<c0166dc7>]exit_mmap+0x77/0xf0
[189.758389][<co123e08>]mmput+0x38/0xa0
[189.758531][<c01292e2>]do_exit+0xf2/0x800
[189.758676][<c0129c16>]do_group_exit+0x26/0x80
[189.758820][<c0133139>]get_signal_to_deliver+0x2a9/0x420
[189.758968][<c02f0370>]do_page_fault+0x0/0x5f0
[189.759112][<c0102803>]do_notify_resume+0x93/0x720
[189.759262][<c02f070f>]do_page_fault+0x39f/0x5f0
[189.759466][<c018424b>]sys_select+0x4b/0x1a0
[189.759551][<c02f0370>]do_page_fault+0x0/0x5f0
[189.759695][<c010334b>]work_notifysig+0x13/0x18
[189.759841]===============
[189.759936]agpgart:AGP aperture is 128M@0xfooooooo

As you can see there are a number of errors showing. Can anyone give me a simple way to proceed from here.
Thanks in anticipation, John Williams

just realized it's getting late in the UK so I'll have to go to bed. I'll be back online at about 7pm GMT cheers J

---

### Post by dstew on 2007-05-16
> *I got into the boot choices but could not find a way to type in noapic nolapic*To get the line for boot options, press F6 when the Live CD first screen appears. A line appears that starts **boot:** Just type the boot options at the end of the line.

---

### Post by johnwillyums on 2007-05-17
Hi. Ok I managed  to get into the boot options and added commands as you suggested so the line read as follows-
Boot Options:/casper/initrd.gz quiet splash--noapic nolapic

This seemed to get me a bit further than before. It stopped on a page for about a minute then eventually stopped on one with several do_page_ fault lines and a couple of error code lines.
There was a line of these =========== and then some code-2e 65a etc and then-
[391.687622]EIP:[<c011ddac>]kmap_atomic+0x5c/0xa0 SS:ESP 0068=f37b3ebc
[391.687826]<6>note:udevd[6535]exited with preempt_count 1

Am I getting anywhere?

Thanks for your help, John Williams

---

### Post by dstew on 2007-05-17
Maybe. Also try the boot option **ide=nodma**.

---

### Post by johnwillyums on 2007-05-17
Thanks do you mean as well as noapic nolapic. John Williams

---

### Post by johnwillyums on 2007-05-17
Hi DStew. I tried what you suggested and added noapic nolapic and ide=nodma to the boot line. This definitely had a positive effect and I've been watching pages of text flash past at high speed for an hour and a half now. At first I thought this was going to succeed but I became concerned that it was going on for so long and did a hard shutdown to consult you(or any body else out there). The numbers on the left had reached 7880+ and the process showed no sign of stopping. Should I have left it to continue? Hopefully this is a step forward or maybe I should not have been so impatient and it would have eventually booted. Please advise me. Thanks for your support, John Williams

---

### Post by johnwillyums on 2007-05-17
Hi. I noticed you are in the US so I don't know what time it is there. Here it's late at night and I have to sleep. Will be back online tomorrow day time UK GMT. Thanks for your help. John Williams

---

### Post by dstew on 2007-05-17
Well, you have been a good sport trying to get the Live CD to boot. Sometimes, the Live CD encounters a hardware configuration it can't handle. This might be the case with your custom box.

At this point, I would strongly recommend using the Alternate Install CD. You can order one, or download the .iso and burn the image to a disk. The Alternate Install CD installs the same Ubuntu system as the Live CD, but it uses a text-based interface that works more reliably. You can find the .iso [here]("http://www.ubuntu.com/getubuntu/download"). You get the alternate by checking the box at the bottom before you start the download. The instructions are [here]("http://users.bigpond.net.au/hermanzone/"). Best wishes, and don't give up.

---

### Post by johnwillyums on 2007-05-19
Hi Dstew. I've been trying Wubi, which uses the alternative ISO. That has installed (or seems to have) but won't boot. I downloaded the alternate ISO but don't want to try it yet as it'll mess with this Wubi thing.
I'm getting some support from a couple of people on the Wubi Forum (3 distros-my pc won't boot Linux) but I don't think we're really getting anywhere.

It's beginning to look like I'll just have to stick with Windows. Damn shame.
Thanks for your support, John Williams

---

### Post by mailbinoy on 2007-06-14
> **johnwillyums said:**
> Hi DStew. I tried what you suggested and added noapic nolapic and ide=nodma to the boot line. This definitely had a positive effect and I've been watching pages of text flash past at high speed for an hour and a half now. At first I thought this was going to succeed but I became concerned that it was going on for so long and did a hard shutdown to consult you(or any body else out there). The numbers on the left had reached 7880+ and the process showed no sign of stopping. Should I have left it to continue? Hopefully this is a step forward or maybe I should not have been so impatient and it would have eventually booted. Please advise me. Thanks for your support, John Williams

sounds to me like your vfat partition is being checked. i would disable the checks from /etc/fstab. Or wait for it to finish (may take hours). I'm not an expect but the numbers(7880...) certainly remind me of that

---

### Post by mailbinoy on 2007-06-14
a friend of mine had a similar problem and fixed it by removing the ATI card and modem. 
 [ 121.161086]  [<c02f0370>] do_page_fault+0x0/0x5f0

[ 121.161185]  [<c010334b>] work_notifysig+0x13/0x18

[ 121.161291]  ==================

---

