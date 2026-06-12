---
title: "How do you verify an ISO download?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-03-23
I'm a little confused about this process. First, on the "BurningIsoHowto" page, there is a link to OpenOffice that tells you how to use md5sum, but this seems to be specifically for OpenOffice, and I'm not sure how it applies to checking the ISO Live CD that I downloaded.

I also looked at "VerifyIsoHowto", but that seems enormously complicated as well. It mentions downloading two files to start with, but I don't know where to find them. Then it runs some commands that I'm not sure would work in Windows, which is what I have right now.

Is there an easy method to use to check the ISO file? The Firefox method seems easy, but again the instructions were for OpenOffice, not Ubuntu. I also downloaded the file md5sum and ran it against my ISO file in a DOS prompt, and this produced a key, but I don't know what to check it against.

Thanks in advance.

---

### Post by user1397 on 2006-03-23
[QUOTE=JohnJSal]I'm a little confused about this process. First, on the "BurningIsoHowto" page, there is a link to OpenOffice that tells you how to use md5sum, but this seems to be specifically for OpenOffice, and I'm not sure how it applies to checking the ISO Live CD that I downloaded.

I also looked at "VerifyIsoHowto", but that seems enormously complicated as well. It mentions downloading two files to start with, but I don't know where to find them. Then it runs some commands that I'm not sure would work in Windows, which is what I have right now.

Is there an easy method to use to check the ISO file? The Firefox method seems easy, but again the instructions were for OpenOffice, not Ubuntu. I also downloaded the file md5sum and ran it against my ISO file in a DOS prompt, and this produced a key, but I don't know what to check it against.

Thanks in advance.[/QUOTE]
Here are some easy quick steps to successfully installing and burning an iso image: get automatix, (use this page: [http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix) ), then inside automatix install gnome baker, then download your iso image to any directory (i always like downloading to the desktop as you can always find stuff easily there), then go to gnome baker, paste the iso image, and click "burn cd image" or "burn dvd image" depending on what you downloaded.  Also make sure the iso image ends in .iso before pasting it to gnome baker. Let me know of any problems.

---

### Post by JohnJSal on 2006-03-23
Thanks for the response. Actually, burning the image file shouldn't be a problem, but I wanted to check it first. Does the process you describe run a check on it?

---

### Post by user1397 on 2006-03-23
No but there is no need for a check! As long as it says blahblahblah.iso you should be fine.  For example, kubuntu-5.10-dvd-i386.iso is available on the kubuntu website.  I am actually downoading it on bittorrent right now!

---

### Post by Chyper on 2006-03-23
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/MD5SUMS](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/MD5SUMS)

i think thats what you asking for

---

### Post by Coelocanth on 2006-03-23
[QUOTE=erik1397]No but there is no need for a check! As long as it says blahblahblah.iso you should be fine.  For example, kubuntu-5.10-dvd-i386.iso is available on the kubuntu website.  I am actually downoading it on bittorrent right now![/QUOTE]

Actually, there is a need to check it. It's not uncommon for a file to be corrupted for whatever reason when you DL it, so checking it before burning a corrupted ISO is never a bad idea.

---

### Post by user1397 on 2006-03-23
[QUOTE=Coelocanth]Actually, there is a need to check it. It's not uncommon for a file to be corrupted for whatever reason when you DL it, so checking it before burning a corrupted ISO is never a bad idea.[/QUOTE]
Really? I didn't know that.  Thanks for the knowledge though :)

---

### Post by user1397 on 2006-03-23
My bad it would be best to install K3B cd/dvd burning application because it just works and gnome baker doesn't always work.  Just type in a terminal :
sudo apt-get install k3b
Then type your password, and then when prompted, type y and press enter.
To use K3B for an iso image, go to tools ==>burn cd image or burn dvd image
and just drag and drop your iso file. That's it!

---

### Post by JohnJSal on 2006-03-23
[QUOTE=Chyper][http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/MD5SUMS](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/MD5SUMS)

i think thats what you asking for[/QUOTE]

Thanks!

---

### Post by rob.webinator on 2007-05-19
Not only could the iso be corrupted, it could also be -- gasp -- infected with some nefarious code.  The correct process is summarized as follows:

1.  Download MD5SUMS and MD5SUMS.gpg from a reliable source, like this secure site:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2.  Get the key used for the signature
3.  Verify the signature
4.  Check the ISO with md5sum

These instructions are laid out here:
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

Relying on k3b to check the hash for you as far as I can tell isn't reliable because it's just computing the hash and checking it against what the iso says it should be.  One should always check against the MD5SUM retrieved separately from a reliable source, see 1) above.  I wonder if k3b can be configured to perform steps 2, 3, 4 using a key downloaded in step 1.  That would be cool.

---

