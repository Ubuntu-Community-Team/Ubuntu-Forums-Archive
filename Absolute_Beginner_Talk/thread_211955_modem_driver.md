---
title: "modem driver"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-07-09
I have breezee installed but it doesnt see my modem,Intel(R)536EP
I have downloaded the driver on another machine Intel-536EP-4.71.tgz.I copied it to a R/W disc and put it in the home Dir on the other machine.When typing tar xzf Intel-536EP-4.71.tgz I get an error message gzip: stdin:not in gzip format tar:child returned status 1 tar:error exit delayed from previous errors.One other thing is I am getting on now 71 and the terminology used is like a foreign language when it says to install build essentials and linux headers wether it is Debian command line or graphical interface or even compiling a driver,I am in such deep water here and I am seriously floundering.Simple tasks like windows explorer just doesnt seem simple any more when I right click and it says copy I assume that is to copy to clipboard for pasting but it doesnt seem to have a copy for copying files to somewhere else or is it one and the same.Heres hoping.

---

### Post by editrix on 2006-07-09
Okay, first off I'll assume you've read the Dialup modem HowTo
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

It's really easy to make a mistake typing, so what I always do when there are instructions on a web page is highlight the command with my mouse--this automatically copies it, then in my terminal, hit the middle mouse button or scroll wheel, and that will paste it. All Linux works this way--copy with mouse, hit middle button to paste.

You can save the HowTo as a file on the machine that has a working modem and copy it to the one that doesn't.

I have to tell you I never got mine working in Breezy, but I didn't spend a lot of time on it. I think it's something to do with those missing files you have to download separately. It was very simple in Dapper.

---

### Post by bobanshirl on 2006-07-09
Thanks for your reply.I have got Dapper on a CD but really dont know how to change as I have Breezee installed with Win XP dual boot.That little exercise took forever is there a simple straight forward answer to this one.Thanks

---

### Post by editrix on 2006-07-11
> **bobanshirl said:**
> I have got Dapper on a CD but really dont know how to change as I have Breezee installed with Win XP dual boot.That little exercise took forever is there a simple straight forward answer to this one.Thanks

Now I'm not sure which "this one" you mean. :-)

Installing Dapper over Breezy was quite simple. Use the alternate CD so you can better see what you're doing. You won't mess up your Win partition if you don't touch it.

Regarding the modem, all I can suggest is you try installing it again. It's possible the downloaded tgz got corrupted somehow, so you might want to redownload it, just to be sure.

You could also try googling stdin:not in gzip format.

I find that searching on exact error messages is usually the best way.

Sorry I can't be of more help.

---

