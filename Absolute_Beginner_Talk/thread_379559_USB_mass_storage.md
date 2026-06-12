---
title: "USB mass storage"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by merike on 2007-03-08
How do I get it mounted?

At the moment it detects the device, tries to use ehci_hcd and address 5, fails to do so and tries address 6. That seems to be okay. But with which name do I mount it?

Also what character encoding is best for fat32 partition? Since I saw a warning in the log.

---

### Post by az on 2007-03-08
Your device should be automounted when you plug it in.

What device is it?

Either your device (or your usb port/hub) is broken or you should file a bug report.

---

### Post by benfindlay on 2007-03-08
I'd say take a look here: [http://www.ubuntuforums.org/showthread.php?t=283131]("http://www.ubuntuforums.org/showthread.php?t=283131")

and also: [https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
 if you want it to mount at start up. Recommend the script talked about in that last article, It will write all your configs automatically for you!

Hope this helps!

---

### Post by merike on 2007-03-08
It is flash memory stick that works using Windows and the same hub. Automatically mounted should be seen under media? It doesn't display there.

Edit: I can't use that automount script due to not having internet access. I haven't determined yet if that is an issue with network card or just that I need to configure my computer to show different mac address in order to get an ip address from service provider.

---

### Post by doublecheese210 on 2007-03-08
As soon as you stick it in, it should read it. It should open up a window with its contents, and put an icon on the desktop. I would Recommend formatting it and then trying again.

---

### Post by benfindlay on 2007-03-08
> I can't use that automount script due to not having internet access.

How are you online then?

Assuming you are using another computer for internet, you can alwasy save it offline on that machine just by going to the website and transferring it via cd/floppy etc

---

### Post by merike on 2007-03-08
Is that the same script? [http://www.kaarsemaker.net/files/diskmounter](http://www.kaarsemaker.net/files/diskmounter) Because the link in community docs doesn't load for me.

---

### Post by benfindlay on 2007-03-08
I think so. Yeah, the link posted doesn't work for me either!

Give it a try! ;)

---

### Post by merike on 2007-03-08
That script only added my windows partition. It won't open a window for me as doublecheese210 suggested.

BTW: This forum gives the fastest replies I've ever seen :O Too bad I need to go to sleep, otherwise I'll wake up and find myself still sitting on the chair in the morning :D

---

### Post by benfindlay on 2007-03-08
lol I take it you're in Europe too then? Such a great feeling not having to rely on American time-zones for support from the community! And its great to see open source being embraced world-wide!

---

### Post by az on 2007-03-09
> **merike said:**
> That script only added my windows partition. It won't open a window for me as doublecheese210 suggested.



Right.  The problem is not that you need a script to do what should be done automatically.  The problem is that this is not being done automatically, which means that there is a bug or a hardware malfunction.  

Since the device works fine in windows, this is a bug.

Boot your Ubuntu computer and open a terminal.  type 

tail -f /var/log/messages

and then plug in the device for the first time.

Post the output.

---

### Post by xadder on 2007-03-09
Which ubuntu are you using? With my plain edgy ubuntu-desktop USB's get mounted and displayed nicely.

But, with an xubuntu-installation, the USB's don't get mounted. I have to go to
Places - computer and mount from there. After that all is fine. I suspect that xubuntu is using a leaner mode and expects users to mount manually. 

(I also did sudo aptitude install ubuntu-desktop on top of my xubuntu, but this still doesn't restore behaviour to that seen with the clean ubuntu install)

If anybody knows which additional packages would make xubuntu behave like ubuntu in this regard I'd be grateful for tips.

---

### Post by merike on 2007-03-09
> **az said:**
> 
Boot your Ubuntu computer and open a terminal.  type 

tail -f /var/log/messages

and then plug in the device for the first time.

Post the output.

usb 4-3: new high speed USB device using ehci_hcd and address 2
ehci_hcd 0000:00:00.3: Unlink after no-IRQ? Controller is probably using the wrong IRQ.

After that I get three lines like the first one, it switches to address 3, then 4, and 5.

I'm pretty sure that yesterday when I used dmesg it complained about device not accepting something :confused:

Oh, and it switches addresses no matter which port out of three my laptop has I use. Except for 4-2 and 4-1 it doesn't complain about controller.

---

### Post by az on 2007-03-12
> **merike said:**
> usb 4-3: new high speed USB device using ehci_hcd and address 2
ehci_hcd 0000:00:00.3: Unlink after no-IRQ? Controller is probably using the wrong IRQ.



I would think this is a bug in the linux kernel.  Are you able to boot a previous version of Ubuntu's live cd and see if your device is recognized when you plug it in?

Also, are you able to file the bug report?   You can search to see if there is a similar bug filed and add to it, as appropriate.

---

### Post by merike on 2007-03-15
I managed to connect internet and download all updates, including new kernel. I had 2.6.17-10 now I boot with 2.6.17-11. The problem remained. I get error -110 in dmesg log.

Searched and found that someone had very similar problem: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273)

Could somebody explain a bit how this bug tracking works? I understand that I need to sign up, but should I add my problem to this bug and include dmesg? Anything else I should include?

---

### Post by merike on 2007-03-23
Oh, and there is no fix so I just have to hope for new and hopefully fixed kernel?
Please tell me that it's not the case.

---

### Post by merike on 2007-04-07
I got it to work. All I needed was to change
# defoptions=quiet splash
to
# defoptions=quiet splash noapic
in /boot/grub/menu.lst

After that I was able to access it from Places. It didn't display on desktop though and I couldn't umount it without using terminal. After a few cycles of
umount
take out the stick
put the stick back in
it finally displayed on desktop with the option to eject so it would make all changes permanent before removing the stick physically.

My Ubuntu just got a bit better again :)

---

