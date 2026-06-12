---
title: "Questions about Ubuntu LiveCd"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by GtzDutyRider88 on 2006-02-13
What is md5sum and why do I need to use it? Where can I get it? Is burning a LiveCd at 8x a good speed to burn at. Do I have to do anything when Ubuntu is loading(like using a command line)?

---

### Post by lenny45 on 2006-02-13
[QUOTE=GtzDutyRider88]What is md5sum and why do I need to use it? Where can I get it? Is burning a LiveCd at 8x a good speed to burn at. Do I have to do anything when Ubuntu is loading(like using a command line)?[/QUOTE]
 i have 4 coasters of ubuntu. i tried it all and nothing works for me--so far. ironically, Mepis burned the first time successfully at 32x......

still awaiting my Ubuntu disks....:-k

---

### Post by Joeb on 2006-02-13
[QUOTE=GtzDutyRider88]What is md5sum and why do I need to use it? Where can I get it? Is burning a LiveCd at 8x a good speed to burn at. Do I have to do anything when Ubuntu is loading(like using a command line)?[/QUOTE]

The md5sum is a checksum to verify that the ISO image you are trying to burn isn't corrupt.  There are individual programs to read/compare them and some burning programs do them on the fly.

As for burning at 8x speed, that just depends.  The simple answer is that it should be fine, however it really depends on a number of things.  What operating system are you using, what speed is the media rated for, what else is the computer being used for while the burning is going on, etc.  If you can normmally burn other CDs at 8x then you should be fine.

As for doing anything while Ubuntu is loading, I assume you are referring to the LiveCD.  The answer is "Nope, just sit back and wait."  The only time you would need to use the command line (CLI) is if you have specific issues (and the live cd doesn't boot normally).

Have fun and enjoy!

Joeb

---

### Post by byen on 2006-02-13
> What is md5sum and why do I need to use it?
To put it in plain words..md5sum is a checksum utility used to check the integrity of the download. To make sure the ISO has been downloaded properly.
>  Where can I get it?
You can get one [here]("http://www.nullriver.com/index/products/winmd5sum")
Just make sure the output of the program matches the one posted at the site from which you downloaded the ISO.
>  Is burning a LiveCd at 8x a good speed to burn at
Yes.Burning at slower speed helps! Infact..I make it a point to use slower speed levels! You can use any CD-writing program you want...but if you dont have one..I strongly recommend [DeepBurner]("http://www.download.com/DeepBurner/3000-2646_4-10447242.html?tag=lst-0-1"). Its free and safe.
 > Do I have to do anything when Ubuntu is loading(like using a command line)?
Nope. Just press ENTER! 
Im not sure if there is an option as such..but If you have an option to boot with ACPI-off from the select screen...I suggest using that as It takes care of some hardware/acpi compatibility issues (if any)

Hope this answers your question. Please feel free to ask. 
Welcome to Ubuntu and Goodluck!

---

### Post by Bartender on 2006-02-13
GTZ -
I've been prying into this whole md5 issue for a coupla weeks.  Latest diatribe below, which also links to another thread on the subject.

[http://www.ubuntuforums.org/showthread.php?t=125091](http://www.ubuntuforums.org/showthread.php?t=125091)

Also, do a Search and you'll find many posts.  Judging by the sheer number of new folks asking about this, there's a need for a clear, step-by-step guide.  It's important to understand that only one md5 checksum will be created from the .iso download because it is one file.  The CD that you burn from that .iso download (at 2X or maybe 4X) will have several files, and will generate numerous md5's.  That's where it gets a bit more confusing, especially since there's not a list at the download website for verification.  At least as far as I know there isn't.  That's why I attached the list (in that other post) that I got from my Ubuntu i-386 CD.  If you have any other CD (Kubuntu, Ubuntu for Apple, Ubuntu for AMD64, etc.) the md5's will NOT repeat NOT be the same.   

Linux has md5 checksumming built into it, Windows doesn't.  There are dozens of md5 checkers for Windows.  Some are easy, some are less so.

Don't use cheap generic CD's.  Several folks have reported failure with cheesy CD's, then success with higher quality media.

lenny45, have you had any luck yet?

---

