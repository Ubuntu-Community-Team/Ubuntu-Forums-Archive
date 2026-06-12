---
title: "How best to move files from an old Mac to a new Ubuntu box?"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by watchpocket on 2010-06-10
Last fall I got a new Linux desktop computer from System76.  Before  that, I had a 1997-era beige G3 Mac.  (This Mac is [COLOR=Blue]**pre**[/COLOR]-USB  plugs.)

I still have files on that old Mac that I need to move to  the new machine.  Some are text files and various other kinds of files,  but mostly, they're image files, and there's a lot of them.

The  Mac has a SCSI port and an Ethernet port.  No Firewire, no USB.

My  question: What's the best way to move the files from the old to the new  machine?

(I think it would be a hassle to try to e-mail them, as  I have quite a lot of image files on the Mac.)

Also, if some of the files (like text-files?) that are in Mac format can't be read once on a Linux OS, how would I make the necessary conversions?

Thanks for  any tips.

---

### Post by lindsay7 on 2010-06-10
Well if you can live with 2 gigs to transfer at a time, I would install DROPBOX on both computers.  A 2 gig account is free but you can pay for more.  Once you put files into your Dropbox you can download them to any computer.  Keep doing this until all of your old files are transfered.

[https://www.dropbox.com/](https://www.dropbox.com/)

---

### Post by lukeiamyourfather on 2010-06-10
I'd try to transfer them over a network since the machine has an Ethernet port. As for converting files before transferring, hard to say. You might try opening one of them on your new machine to see what it does, even a floppy should suffice for a quick test. Cheers!

---

### Post by watchpocket on 2010-06-10
> **lukeiamyourfather said:**
> I'd try to transfer them over a network since the machine has an Ethernet port.

Although it does have an Ethernet port, I don't think my old Mac (which is running MacOS 8.1) will accomodate software to connect to the network via anything other than dialup, which would make both the above suggestions less than optimal.

I'm thinking I might try to get a cable with the right male SCSI plug on one end (to connect to the Mac) and a male USB plug on the other to plug into a standalone hard drive, and transfer the files into the drive, then move the files from the standalone drive into my Ubuntu box.

Does this sound sensible?

---

### Post by lukeiamyourfather on 2010-06-10
> **watchpocket said:**
> Although it does have an Ethernet port, I don't think my old Mac (which is running MacOS 8.1) will accomodate software to connect to the network via anything other than dialup, which would make both the above suggestions less than optimal.

What about booting a live version of Linux? Looks like an older release of Ubuntu has a live disc for PowerPC.

[http://old-releases.ubuntu.com/releases/5.04/](http://old-releases.ubuntu.com/releases/5.04/)

That would work if you have enough memory. Cheers!

---

### Post by steveneddy on 2010-06-10
Burn a CD of your data - easy peasy

---

### Post by lukeiamyourfather on 2010-06-11
> **steveneddy said:**
> Burn a CD of your data - easy peasy

Not really that easy. Burners were pretty rare back in 1997, especially for Mac. There are a few burners around for SCSI like on eBay but I doubt you could find one with the software for Mac still.

---

### Post by v1ad on 2010-06-11
rip the hard drive out and plug it into your current machine.

or live cd && network

---

### Post by 3rdalbum on 2010-06-11
Set up an FTP server on the Ubuntu machine and use "Connect To Server" on the Mac OS machine to connect. If you don't have Connect To Server, then download Fetch onto the Mac (or some other FTP client) and access it that way, through an Ethernet cable and setting a static IP on both computers (or plugging into a router which will set IP addresses for you).

Alternatively, you could remove the hard disk from the Mac and get an IDE-to-USB enclosure. Ubuntu should, if I remember correctly, be able to automount your HFS+ hard drive.

---

### Post by Frobber on 2010-06-11
If that is really an Ethernet port on the Mac, why not use a crossover cable between both machines?

---

### Post by tenuki on 2010-06-12
I agree with v1ad - if you've got spare space in your new machine, then transferring HD is the way I'd go: direct, easy, no need for new cables/hardware.

---

### Post by lukeiamyourfather on 2010-06-13
> **tenuki said:**
> I agree with v1ad - if you've got spare space in your new machine, then transferring HD is the way I'd go: direct, easy, no need for new cables/hardware.

Unless its SCSI which is what Apple was using at the time in their Mac systems.

---

### Post by watchpocket on 2010-06-13
> **lukeiamyourfather said:**
> Unless its SCSI which is what Apple was using at the time in their Mac systems.

In which case, you would do -- what?  Get a SCSI-to-USB cable and  move the files to a standalone HD and then to the Ubuntu box?

That's what I'm currently thinking of doing.  (It is, btw,  a SCSI port on the old G3 Mac.  And I need a portable drive anyway.)

---

### Post by derWalter on 2010-06-13
i would go for the ftp server solution.

why?


first of all: TIME - you can do it instantly
second: nothing can go wrong at all
third: its the most cheap method - nothing to buy etc.
4th: its the easiest option of all - no screws no disks nothing - pure digital work



-but hey, i am a newb! so what have i to say? ):P

---

### Post by watchpocket on 2010-06-13
> **derWalter said:**
> i would go for the ftp server solution.

If you're talking about hooking the two machines together directly with an Ethernet cable, and using an FTP client on the Mac to access an FTP server on the Ubuntu box (or vice versa), that might be possible.  (Though I don't really know, I've never done it.)

If you're talking about connecting the Mac to the phone lines / Internet, and running FTP client-server software that way (over the net), the only way I can do that is via dialup for the Mac, and I'd have to renew (at least for a month, probably) the dialup account that I recently let expire when it came up for renewal.

I could do it, and it would even be worth it if I can accomplish what I need to, though the dialup speeds might make it all a bit slow and clunky.

Which way were you referring to?

Thanks for the input.

(As for pulling the hard drive out of the mac and connecting it directly to Ubuntu box, which others have suggested, I might be able to do that, and I may try it, though I have a feeling I'd bungle it.)

---

### Post by JohnAtilano on 2010-06-13
> **Frobber said:**
> If that is really an Ethernet port on the Mac, why not use a crossover cable between both machines?
This was my thought.  Plug the cross-over cable into both machines, set up an ad-hoc network (if it doesn't automatically) and transfer the files.

---

### Post by 3rdalbum on 2010-06-14
> **lukeiamyourfather said:**
> Unless its SCSI which is what Apple was using at the time in their Mac systems.

I think they'd switched to IDE for internal drives, and were only using SCSI for external drives.

It's virtually impossible to bungle the removal of the old hard disk, assuming that you don't still need the G3 computer itself. I'd recommend getting an external drive enclosure because:

a. No need to mess around with "master/slave" settings, which can be a pain in the backside for some BIOSes.
b. The enclosure itself will come in handy if someone else needs data transferred off an IDE drive
c. You can copy off the contents of the drive onto your new computer, and then store the old drive inside the enclosure as a kind of backup.

---

### Post by watchpocket on 2010-06-14
I think this might be the preferred solution.  Thanks to all for the tips & suggestions.

---

