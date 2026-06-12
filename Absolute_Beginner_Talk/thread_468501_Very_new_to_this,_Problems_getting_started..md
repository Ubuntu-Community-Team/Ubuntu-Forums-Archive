---
title: "Very new to this, Problems getting started."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by fwuffycloud on 2007-06-08
I just burnt my Ubuntu to a disk, using a guide.
But each time i get onto the Ubuntu screen (with options such as Check CD for defects, or Start or install ubuntu) each option i choose, i get put onto a screen thats just black but with text at the very bottom saying:

Kernel alive
Kernel direct mapping tables up to 1000000000 @ 8000 - d000 (or something like that, the bottom half was cut off.)


It just stays on that screen and nothing happens.

Can anyone help me?

---

### Post by Nythain on 2007-06-08
try downloading and burning the alternate install iso... making sure check the iso for errors if you know how (i dont, i have never really needed to mess with checksums and all that jazz) and BURN AT THE SLOWEST SPEED POSSIBLE!!!

if you still encounter problems we can trouble shoot from there

(the alternate install iso is like gods gift to ubuntu installations... its not pretty, but it gets the job done almost all the time)

---

### Post by yurimxpxman on 2007-06-09
> **fwuffycloud said:**
> I just burnt my Ubuntu to a disk, using a guide.
But each time i get onto the Ubuntu screen (with options such as Check CD for defects, or Start or install ubuntu) each option i choose, i get put onto a screen thats just black but with text at the very bottom saying:

Kernel alive
Kernel direct mapping tables up to 1000000000 @ 8000 - d000 (or something like that, the bottom half was cut off.)


It just stays on that screen and nothing happens.

Can anyone help me?
On a typical router setup, corrupt packets occur approximately every 3GB. This is not normally a problem with day-to-day web browsing, but it often comes into play when downloading large files. Bram Cohen  recognised this problem when he developed Bittorrent, so he decided to include a tool to automatically check for corrupted data in downloaded files (this is known as a hash). When a corrupt piece of data is found, it simply dumps that portion and re-downloads it. This way, we know that we have the exact same data as the original source when we download files via torrents.

HTTP and FTP downloads do not implement this automatically. In fact, even though GNU/Linux distributions often post the hashes on the download pages, the user would have to re-download the entire disk image if the checksums did not match.

For this reason, I heavily discourage users from downloading Ubuntu via HTTP. Instead, use the torrent.

---

### Post by logicalmind on 2007-06-09
> **yurimxpxman said:**
> On a typical router setup, corrupt packets occur approximately every 3GB. This is not normally a problem with day-to-day web browsing, but it often comes into play when downloading large files. Bram Cohen  recognised this problem when he developed Bittorrent, so he decided to include a tool to automatically check for corrupted data in downloaded files (this is known as a hash). When a corrupt piece of data is found, it simply dumps that portion and re-downloads it. This way, we know that we have the exact same data as the original source when we download files via torrents.

HTTP and FTP downloads do not implement this automatically. In fact, even though GNU/Linux distributions often post the hashes on the download pages, the user would have to re-download the entire disk image if the checksums did not match.

For this reason, I heavily discourage users from downloading Ubuntu via HTTP. Instead, use the torrent.

Are you serious? TCP, the protocol on which bit torrent and HTTP are built has built-in error-free data transfer.
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Error-free_data_transfer](http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Error-free_data_transfer)

Are you saying that there is one corrupt data packet(correct TCP checksum, but wrong data) once in every 3GB of transfer. If this is true I'd love to see a reference.

BTW, the hashes are provided for security. They verify that the image(binary or source) has not been altered(rootkit installed, etc) in the distribution process. Every hash at every distributor should match at every point including the original provider.

---

### Post by yurimxpxman on 2007-06-09
> **logicalmind said:**
> Are you serious? TCP, the protocol on which bit torrent and HTTP are built has built-in error-free data transfer.
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Error-free_data_transfer](http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Error-free_data_transfer)

Are you saying that there is one corrupt data packet(correct TCP checksum, but wrong data) once in every 3GB of transfer. If this is true I'd love to see a reference.

BTW, the hashes are provided for security. They verify that the image(binary or source) has not been altered(rootkit installed, etc) in the distribution process. Every hash at every distributor should match at every point including the original provider.

As I said, it's purely a router configuration. It's a very poor configuration, but it's common. I first heard about it in one of Bram's speeches, but I can't find the video at the moment (I believe it was at Stanford; if anybody can find it, I'd be grateful).

Anyways, no, the hash in a torrent file is not for security. It's a redundancy error check. See [http://en.wikipedia.org/wiki/Hashing_algorithm#Error_correction](http://en.wikipedia.org/wiki/Hashing_algorithm#Error_correction)

---

### Post by logicalmind on 2007-06-09
> **yurimxpxman said:**
> As I said, it's purely a router configuration. It's a very poor configuration, but it's common. I first heard about it in one of Bram's speeches, but I can't find the video at the moment (I believe it was at Stanford; if anybody can find it, I'd be grateful).

Anyways, no, the hash in a torrent file is not for security. It's a redundancy error check. See [http://en.wikipedia.org/wiki/Hashing_algorithm#Error_correction](http://en.wikipedia.org/wiki/Hashing_algorithm#Error_correction)

If this is a "common" problem then it would be widespread. For what you say to be true the router would have to corrupt the data and then re-generate a TCP checksum, which they do not due since they work at the network level(IP).
[http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)

RE: the hash, I was referring to the hashes available with the download of any iso/binary/source file. Like here:
[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

Every download has a sig/signature. Which is a hash. You can use this sig to verify your download, regardless of the protocol.

Hashes in bit torrent are used to verify that the chunks of a larger file have not become corrupt since each participant creates the chunks. TCP could not detect this because the participant believes he is passing legitimate data. The client expects to see a certain hash, then downloads a chunk and verifies that hash. That isn't because of any network problems though.
[http://en.wikipedia.org/wiki/Bit_torrent#Creating_and_publishing_torrents](http://en.wikipedia.org/wiki/Bit_torrent#Creating_and_publishing_torrents)

---

### Post by fwuffycloud on 2007-06-09
Ok, thanks for suggestions, so do you reccomend that i just download ubuntu again (i must say the first download was a bit dodgy because i think it got a couple errors but i carried on anyway)

 and then burn at a very slow speed? (i burnt at x16)

---

### Post by stalkingwolf on 2007-06-09
try burning the ISO you have again.  4x or slower.

---

### Post by fwuffycloud on 2007-06-09
Ah, ok will do. :)

I'll post if i get any problems.

---

### Post by fwuffycloud on 2007-06-09
Tried that, but got the same problem.

So i am now downloading it again, shall i download that MD5sum program once it has finished?

---

### Post by Nythain on 2007-06-09
yeah... i would definately do that... and like i said, you could probably also try downloading the alternate install iso if you encounter anymore problems

---

### Post by Roger Gundberg on 2007-06-09
Have you considered a cleaning of the read/write lens on your burner? I use a product called Allsop  Multimedia  CD Rom  Lens Cleaner. It resembles a  CD Rom with a  little brush  on the bottom.  You can use it on your home  entertainment  unit as well. Good luck!

---

### Post by fwuffycloud on 2007-06-09
I wouldnt think that my burner needs cleaning because this is pretty much the first time i have even opened it.

Im about to try the new burn, but if i still get the same problem where can i find the alternate install iso?

---

### Post by fwuffycloud on 2007-06-09
Ok yeah, tried it again but to no avail, just keeps going to that blank screen with the 2 lines of text at the bottom.

Wheres this alternate Iso?  and how is it different from the one i have now?

thanks.

---

### Post by fwuffycloud on 2007-06-09
Sorry for the bump, but i really would like to start using Ubuntu soon.

---

### Post by fwuffycloud on 2007-06-09
Can anyone tell me where to find the alternate install Iso (stated in above posts)?

---

### Post by bone43 on 2007-06-09
> **fwuffycloud said:**
> Can anyone tell me where to find the alternate install Iso (stated in above posts)?

Yes its right here..

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

here is some info on installing

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

burning..

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

have fun:D

---

### Post by fwuffycloud on 2007-06-09
aw wow, thanks a lot man, been hoping someone would post for ages now :)

---

### Post by bone43 on 2007-06-09
> **fwuffycloud said:**
> aw wow, thanks a lot man, been hoping someone would post for ages now :)

You are welcome also this is another good site..

[http://users.bigpond.net.au/hermanzone/#top_index/](http://users.bigpond.net.au/hermanzone/#top_index/)

---

### Post by fwuffycloud on 2007-06-09
Out of curiousity what is the difference between the normal and alternate methods?

And is installing pretty much the same as the previous one, because i couldnt find a guide on how to use the alternate iso in

 [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by RelativelyQuantum on 2007-06-09
Make sure the downloaded ISO matches your device; when I was downloading Edgy for the first time I burnt the 64 bit Intel option to disk, only to find that it wasn't compatible with my machine. I'm not certain weather this type of thing would produce the message you described, but Just something to keep in mind ;)

---

### Post by fwuffycloud on 2007-06-09
I've been downloading the 64bit AMD one, i think that is the right one since im using an AMD athlon 64 dual core 4200+ .

---

### Post by geedew on 2007-06-09
just so you guys know, this error happens in select few systems do to the acpi timer not being able to read.... when you boot you have to put in acpi=off as an option and it will pass that screen.

---

### Post by fwuffycloud on 2007-06-09
oh really?

So where abouts do i type acpi=off? I'm not too familiar with the start up options.

---

### Post by geedew on 2007-06-09
1. boot from cd
2. when you get the menu, fit f6 (should pop up a white text area below menu)
3. hit the home key and tye acpi=off and a space.  hit enter and it should load :)

---

### Post by fwuffycloud on 2007-06-09
ah right, thanks a lot.

So i can do that using one of the many burned CD's i have of the standard Iso, instead of waiting for this alternate one to download?

I shall try it now.

---

### Post by geedew on 2007-06-09
should work on any of em

---

### Post by fwuffycloud on 2007-06-09
my god, that didnt seem to work either, hit f6, then home and type acpi=off then enter, and it did the same thing.

---

### Post by geedew on 2007-06-09
wow, very interesting indeed... when you hit f6 did you see the little area pop up that you were typing in?  Make sure acpi=off is followed by a space..

---

### Post by fwuffycloud on 2007-06-09
Ah i didnt have a space after it, i'll try that now

---

### Post by geedew on 2007-06-09
sorry about the specification :P

---

### Post by fwuffycloud on 2007-06-09
Ok, well its working, thanks for that, im posting from ubuntu, my mouse has stopped working, is that something to do with the USB ports?

I have to press tab alot of times to get anywhere at the moment...

---

### Post by geedew on 2007-06-09
um... don't know... the cd may not have the driver installed for your mouse.. try another one if you have it?

---

### Post by fwuffycloud on 2007-06-09
Hmm, this is so much trouble.

How would i get the drivers onto the CD?

Thing is, when i first started it the mouse worked fine, only after 5mins or so the mouse just stopped working altogether, and wouldnt light up or anything.

---

### Post by Mark Martin on 2007-06-09
i don't know if this will help but i have amd 64 also and had some problems with 64 bit version so i downloaded 32 bit alternate cd using bit torrent  and used text base install ,now everything working fine.

---

### Post by fwuffycloud on 2007-06-09
Ah right ok, thanks.

All seems to be working at the moment, but im finding it dificult getting into it, its like 'Now what?'

I want to see if i like it, but i dont really know how to do much, can you only import music and stuff if you have it installed?

Any tips on kind of, getting started?

---

### Post by fwuffycloud on 2007-06-09
yeah the mouse problem is back, please post any suggestions, i'll be back in an hour or so to try them out.

---

### Post by fwuffycloud on 2007-06-09
Are these problems just the Live session exclusive? or do people get them even when ubuntu is installed to the hard drive?

---

