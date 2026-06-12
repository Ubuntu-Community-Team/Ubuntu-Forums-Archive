---
title: "Procedure for burning Ubuntu CD, info confusing"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by dderolph on 2006-06-18
Yesterday, I downloaded Ubuntu 6.06 and am trying to understand the procedure for burning it to CD.  [https://wiki.ubuntu.com/GettingUbuntu](https://wiki.ubuntu.com/GettingUbuntu) has a link to [BurningIsoHowto]("https://wiki.ubuntu.com/BurningIsoHowto").  Oddly, this, link refers to OpenOffice.  The reference to OpenOffice makes no sense to me whatsoever.  Right now, I'm exploring ubuntu, not OpenOffice; that can come later.

Anyway, the referenced link, [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html), talks about how you verify MD5 Checksums under Windows.  I downloaded digestIT as instructed, and installed it.  Using Windows Explorer, I then browsed to the ubuntu file I downloaded yesterday, ubuntu-6.06-desktop-i386.iso, right clicked on it, and selected digestIT 2004, Verify MD5 Hash.  I see panel labeled "Message Digest to Verify" open with a box to "Enter the message digest string to verify against".  If I enter something in that box and click OK, I get an error message that says "This does not appear to be a valid message digest".  

Can someone help me make some sense of this?

---

### Post by arochester on 2006-06-18
What program do you have for burning CDs?

Look at something like [http://iso.snoekonline.com/iso.htm](http://iso.snoekonline.com/iso.htm) which tells you how to burn an ISO using various programs.

If all else fails listen to a podcast which is aimed at newbies at [http://www.linuxreality.com/](http://www.linuxreality.com/)  Episode 7 is about burning ISOs

---

### Post by demonicdude on 2006-06-18
When i was doing this i used this website

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

It is a very informative website. IT uses cdburnerXp (which is free download) to burn it.

BAscially you downloaded an .iso file. It looks like an archive file though (well mine did lol). You can use cdburner xp wriste disc from iso and click the file u downloaded. worked like a charm.  Just Follow the website :)

Also, when you are goignt o boot from that cd, make sure that it boots from the cd drive. Mine automatically had that happening, but i had a dvd drive and then a regular cd-rom drive. Make sure to try both of em. I was stuck for like an hour trying to figure out why it wasn't booting :D.

---

### Post by dderolph on 2006-06-18
I think you've both missed my point.  I haven't gotten to the actual burning yet.  I'm asking the verify MD5 Checksums procedure both [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html) and [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) talk about.

---

### Post by hashimoto on 2006-06-18
[QUOTE=dderolph]...
Anyway, ...talks about how you verify MD5 Checksums under Windows.  
...Can someone help me make some sense of this?[/QUOTE]

Get another program for checking md5sum from here: [http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/). 
Instructions included. 

Good luck!

---

### Post by dderolph on 2006-06-18
Thanks for the link,  hashimoto, but I think I may not need to download another program for this.  I think the problem is that the explanation of how to use a md5sum tool is poorly written.  Apparently, I'm supposed to get, from the download source, a code, non-sensically called a "message digest", and enter that into the panel that pops up when I try to use verify the MD5 hash.  I have not seen such a code, or message digest, from the download source.  If I recall correctly, I downloaded my ubuntu file from [http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/).

I also have the impression this MD5 hash verification procedure is entirely optional.  Is that correct?

---

### Post by user1397 on 2006-06-18
[quote=dderolph] I also have the impression this MD5 hash verification procedure is entirely optional.  Is that correct?[/quote]yes it is, its just a way to check if your download is the correct one, not a fake or malware.    The verification md5sums can be found here: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/MD5SUMS](http://mirror.cs.umn.edu/ubuntu-releases/6.06/MD5SUMS)

---

### Post by catlett on 2006-06-18
You have to have the md5sum from the download site to compare it to. I am surprised the directions don't make it clear. 

You get the md5sum "numbers" from the download site where you get the iso. You run the program to verify the md5sum. 
That program gets the md5sum from the iso. It does not know the md5sum from the original site. What it wants you to do is enter the md5sum numbers you have from the original iso in the "panel". It will them compare the 2 and tell you that they match. If they don't match then the burn was corrupted and the disk is no good.
It appears you are entering a random number or no number, therefore it is saying the md5sums don't match.

In case you are still confused, here are the md5sums for all the ubuntu isos. Find your version and use that where it asks you for the corresponding "digest".
> df03811bfc9f2a73672887a36d531965  ubuntu-6.06-alternate-amd64.iso
b2e9120f06d70cc076c1852c6c04654e  ubuntu-6.06-alternate-i386.iso
12bd53a48d7afbcfb0eae6794a1ac02f  ubuntu-6.06-alternate-powerpc.iso
722b8b4a75f977a76a722d4a2b071b19  ubuntu-6.06-desktop-amd64.iso
e2e5e0bfb2edffd2ce02dd77bda4558e  ubuntu-6.06-desktop-i386.iso
410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
02772b8b3461c246a2154aa6e699335b  ubuntu-6.06-server-amd64.iso
4c7c835d244453b9a29d397e5cd973fd  ubuntu-6.06-server-i386.iso
c1f9c3dc78572bc2ce76d44776949fcc  ubuntu-6.06-server-powerpc.iso
82da246064785adb7b87e5aa0cb5764c  ubuntu-6.06-server-sparc.iso

P.S. This is not a necessary part of burning an iso. It is just a "safety" measure to make sure you have burned the iso correctly. You can just put the disc in without running a md5sum check. You are just taking a little bit of a gamble. 
What's more the Ubuntu install disc has a prompt where it will check the integrity of the disk for you. It will take a couple of minutes and then you will know if it is corrupted or if it is fine to procede with the install. So you don't  even have to do what you're doing if it is becoming too much aggravation.

---

### Post by dderolph on 2006-06-18
Thanks, catlett and erik1397.  The MD5SUM for the file I downloaded yesterday would not verify.  I downloaded the file again and this time it did verify.

---

### Post by Lord Illidan on 2006-06-18
Someone should edit the wiki to add the md5 checksums..

---

### Post by user1397 on 2006-06-18
[quote=Lord Illidan]Someone should edit the wiki to add the md5 checksums..[/quote]definitely

---

### Post by AndyCooll on 2006-06-18
[QUOTE=dderolph]Thanks, catlett and erik1397.  The MD5SUM for the file I downloaded yesterday would not verify.  I downloaded the file again and this time it did verify.[/QUOTE]

I must admit that I rarely bother going as far as an MD5SUM check (perhaps I should, but I don't). I usually just download it from one of the linked websites and then immediately burn it.

:cool:

---

### Post by user1397 on 2006-06-18
yeah its just a security concern or a concern about whether the cd is corrupted or not, but i stil do it.  you only really need to do it from the ftp links.  if you use bittorrent, i think its almost impossible for the file to be corrupted.

---

### Post by aysiu on 2006-06-18
[QUOTE=AndyCooll]I must admit that I rarely bother going as far as an MD5SUM check (perhaps I should, but I don't). I usually just download it from one of the linked websites and then immediately burn it.

:cool:[/QUOTE]
AndyCooll, I'm glad that works for you, but when you've seen as many "My installation freezes at 52%" threads as I've seen, you always recommend an MD5SUM check for new users... always.

---

