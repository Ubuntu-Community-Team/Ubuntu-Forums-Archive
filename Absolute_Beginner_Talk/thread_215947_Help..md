---
title: "Help."
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by ArjunD on 2006-07-14
Okay, I'm running a 64bit processor but its not a AMD64. It's a Intel Pentium D Processor, which is the low end Intel dual-core processors.

Which should I get? The AMD64 version of Ubuntu, or the original?

I have already downloaded the AMD64 one, but I don't mind downloading the other either as my DL speed is very quick.

Right now I have the AMD64 Ubuntu, but its as a RAR file. I know you have to burn it to a CD but what file do I burn? The whole Rar file?

Also how do I make it so that I can have a dual startup. Meaning when I press the on button it gives me a selection if I'd like to access WXP or Ubuntu. I know you have to create a partition but I'd really appreciate some help on that matter.

So yeah, those are my questions, thanks for the help everyone.

---

### Post by bruce89 on 2006-07-14
If your processor can handle AMD64 instructions, you can use it.  Many people who could, don't, as certain things don't work on the AMD64 edition.

I am not sure what you mean by having a *.RAR file, it should be an *.ISO file.  See this - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Could you be more specific in your thread titles in future?

---

### Post by ArjunD on 2006-07-14
Okay. 

I downloaded the normal Ubuntu successfully and its an .ISO file. I'm going to burn it in a second (after I'm done my vaccuming) but I'd like to know how to do what I asked for before.

Also how do I make it so that I can have a dual startup. Meaning when I press the on button it gives me a selection if I'd like to access WXP or Ubuntu. I know you have to create a partition but I'd really appreciate some help on that matter.

I don't want to completely remove WinXP from my system or the files in the drive, but I'd also like to start Ubuntu from scratch. 

How would I go along doing this?

---

### Post by Sef on 2006-07-14
To dual boot read this:  [How to dual boot.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Jagot on 2006-07-14
Burning the disk:

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

Installing and dual-booting:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by ArjunD on 2006-07-14
Thank you very much. I will post again and tell you how it goes later on.

I read the tutorial that he gave me and it seems really easy to do. I'm goign to wait about an hour, because of my girlfreind and such..But yeah by the end of today I should have Ubuntu :D

---

### Post by ArjunD on 2006-07-14
I don't understand what to burn to the CD?

I downloaded the file from the TUT its a RAR file and its called ubuntu-6.06-desktop-i386.

When I open it up I get;
[img]http://upit.be/uploads/images/dd7931.jpg[/img]

And I've already tried just burning the whole RAR file on to a CD, and it won't boot from there.

I don't know what to do now.

---

### Post by aysiu on 2006-07-14
It's not a rar. It's an ISO. Look at the extension.

Then read this (which was linked to earlier):
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by skale on 2006-07-14
I'm not sure, but I'm convinced it's not a rar file. Dies the file have the extension .rar at the end or .iso? Check by rightclicking and clicking "open with" and it should say it somewhere (I don't remember, its been so long since I used it!). What WinRAR does is it taes over the icons for dozens of extentions and file types and sticks its own icon on it. If it is .iso, use whatever software you have to burn it to CD, if it's .rar (which I doubt) go ahead and extract it. You do *not* want to extract files from the ISO. Post what happens.

---

### Post by ArjunD on 2006-07-14
Yes I read that, but it mentions this;

[quote=Article]
[img]http://psychocats.net/ubuntu/images/w2u05.gif[/img]
[img]http://psychocats.net/ubuntu/images/w2u06.gif[/img]
Instead of a webpage, you'll see a text file in your browser. In the left column, you'll see a bunch of gibberish. In the right column, you'll see the names of different Ubuntu .ISO files. Highlight the line that corresponds to the version of Ubuntu you're downloading. In this example, I'm downloading the Beta live ISO, so I copied that line. 

Paste that line into a Notepad document. 

If you don't know where Notepad is in Windows, just press (and hold down) the Windows key and press R. A "Run" dialogue will pop up. In that dialogue, type notepad.

When you save this text file, the name should be the exact same as the .ISO you're downloading but with a .md5 at the end.[/quote]

I don't get what the hell there talking about.

Also I tried just burning the "ISO" file (The file I downloaded) straight out of installation but when I try to boot from CD it doesen't work.

---

### Post by ArjunD on 2006-07-14
It has a .Rar extension, I checked witht he open with thing.

---

### Post by skale on 2006-07-14
Go ahead and extract it with winRAR. be sure to keep the compressed file just in case. Is the extracted file an ISO?

---

### Post by aysiu on 2006-07-14
> **ArjunD said:**
> It has a .Rar extension, I checked witht he open with thing.
Doesn't look like a .rar extension to me.

If you have WinRAR installed, it will automatically associate .iso extensions with the WinRAR program, but I can assure you it is an ISO and should be burned as a disk image.

It should not be extracted or decompressed. Please follow these instructions step by step. Do not skip steps--otherwise you'll get confused.

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

The MD5 is a text file, and it's available on the download page.

---

### Post by ArjunD on 2006-07-14
The extracted file is what I posted previously;
[img]http://upit.be/uploads/images/dd7931.jpg[/img]

---

### Post by skale on 2006-07-14
the md5checksum thingy is (I think) for error checking, I don't know how useful it will be on Windows, or if it burns the same way as an ISO. Someone else can step in.

edit: I'm kinda confused. You want to burn the ISO to CD with whatever CD burning software you have, as a _CD image_ file. You need the ISO.

---

### Post by aysiu on 2006-07-14
> **skale said:**
> the md5checksum thingy is (I think) for error checking, I don't know how useful it will be on Windows, or if it burns the same way as an ISO. Someone else can step in.
I'm going to post the link a third time in the hopes that people will actually read it:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

This outlines **in Windows** how to download an ISO, verify that the download is good, and how to burn the ISO properly. This is all **in Windows**.

The link does require you to download and install two programs (MD5SUMMER and CDBurnerXP), but both are free and the links to them included in the tutorial.

---

### Post by ArjunD on 2006-07-14
Yeah I saw the .Iso extension at the top too but look at this;
[img]http://upit.be/uploads/images/dsds1044.jpg[/img]

---

### Post by aysiu on 2006-07-14
What's your point? The context menu is giving you the option to make it a .rar or extract it. That does not mean it has a .rar extension.

---

### Post by skale on 2006-07-14
could you printscreen the Open With?

---

### Post by ArjunD on 2006-07-14
[img]http://upit.be/uploads/images/sdsd9429.jpg[/img]

Okay heres the open with. I see the .ISO extension a lot now. I burned this to a CD with CDBurnerXP and I got a whole bunch of errors when trying to boot from the CD.

---

### Post by aysiu on 2006-07-14
You have to burn it as a disk image.

You can't just burn it as a data CD or as a "bootable" CD.

---

### Post by skale on 2006-07-14
It's an ISO, man. not a RAR. Do what the other guy said, burn it as an image.

---

### Post by aysiu on 2006-07-14
This is the really important part of the tutorial.

---

### Post by ArjunD on 2006-07-15
****! YES! It worked :D Thank you. Time to boot from CD :D

---

