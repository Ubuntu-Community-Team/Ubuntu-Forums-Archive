---
title: "Bad iso on mirrors?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2005-12-13
Ive downloaded ubuntu-5.10-install-amd64 from 2 different mirrors and burned CDs and the install errors out

Alt F4 indicates an issue reading the CD.  (Code 1)

I run the CD Check on the install menu and both CDs fail at

./pool/main/p/patch/patch/patch_2.5.99.-2-amd64

I cant install Ubuntu :(

---

### Post by Mustard on 2005-12-13
Did you burn them at the lowest possible speed?

---

### Post by GQed76 on 2005-12-13
my writer goes up to 24 X

I burned it at 8X

---

### Post by Mustard on 2005-12-13
Often people strike problems with burning there own CD's when they burn them at something other than the lowest possible speed.  This could be the problem.

Another angle you could look at is running an md5sum check on the ISO that you downloaded and comparing it to the md5checksum that is available through a link on the page you downloaded from.  It will be a series of numbers and letters.  Freeware md5sum checkers are available for download online.

If the checksum returned by the md5sum check software does not match that which is  found on the site you downloaded from, then the ISO has been corrupted during the download.

---

### Post by GQed76 on 2005-12-13
Yeah the check sums are different.  Thanks for the suggestion for the windows checker.

Ive downlaoded 2 different Isos and burned 4 copies

Im trying it on my laptop now.

Thanks for the help!

---

### Post by GQed76 on 2005-12-13
Interesting.  it isnt the burn.

I mounted the Iso file in windows.  I compared THAT ISO to that on the server and thats wrong..So it isnt the burn process.

The files dont match their checksums

---

### Post by BoyOfDestiny on 2005-12-14
[QUOTE=GQed76]Interesting.  it isnt the burn.

I mounted the Iso file in windows.  I compared THAT ISO to that on the server and thats wrong..So it isnt the burn process.

The files dont match their checksums[/QUOTE]

Hi, an easy way to avoid re-downloading the whole thing (apart from someone making a patch for you), is to download it via bittorrent. Choose the file you already have, it will "repair/redownload" only what is needed... When it says it's done, it's done and verified (BT does hash checking, SHA1 I think)

---

### Post by GQed76 on 2005-12-14
I torrented it and it still didnt work, Burned it from the laptop and it installed!

Not sure why I couldnt burn it on this box the cd writer is fine.

Now..to get the netgear wireless card to work :)

Thanks for your help, Im sure I will see you all on other forums

---

### Post by anil_robo on 2005-12-14
Generally speaking, it's always a good policy to check md5 checksums. Unfortunately, not many people do this as they don't know how to do it (I'm one of them too :() or they just feel lazy about it.
 
I read somewhere that files downloaded through torrents have a fewer corruption issues. Also, Linux torrents are much faster than "regular" torrents for some reason.
 
Check if your CD writing program is passing on some unnecessary arguments while writing the ISO. (though I'm not very sure myself)
 
You could also order shipit CDs so that not only you, but also others around you can enjoy the power of Ubuntu.

---

