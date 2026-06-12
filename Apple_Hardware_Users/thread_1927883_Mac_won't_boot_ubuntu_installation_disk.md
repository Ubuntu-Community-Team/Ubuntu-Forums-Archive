---
title: "Mac won't boot ubuntu installation disk"
date: 2012-02-18
forum: Apple Hardware Users
---

### Post by fysicsandpholds on 2012-02-18
Hey Guys,
Okay so I'm having a very strange problem.
I have a 2007 21 inch Intel Mac and I am trying to install Ubuntu 11.10 alongside my mac os. I have sucessfully done this on this same exact machine before with the same installation disk but for various reasons I removed the installation I had.
When I turn on my machine with the installation disk in it, rEFIt recognizes the linux disk but when I try to load it, it freezes on the linux icon and remains there indefinitely.
To try to fix the problem I burned another copy of the installation disk and even wiped my entire hard drive and reinstalled mac but I am still having the same problem. 

It seems very mysterious to me because I have definitely gotten this to work before and even after wiping my hard drive it still won't work. Any help you can give would be amazing.

-Sam

---

### Post by fysicsandpholds on 2012-02-19
I'm not even looking for a definitive answer. If anyone has any ideas about where the problem is (Boot partition, EFI, something I'm totally unaware of, etc), that would be helpful. I'm just completely at a loss because I see no reason for the inconsistant behavior

---

### Post by entangled on 2012-02-22
You could try precise (ubuntu 12.04). I found that the standard 12.04 installer disk booted fine and installed on my iMac (mid 2010) whereas the standard 11.10 disk didn't even boot.
For 11.10 I had to download the special amd build for mac before I could get it to boot off the install disk.
12.04 is behaving very well, despite being a beta. However I prefer using archlinux (kde desktop) in a virtualbox guest image hosted on OSX. It gives great flexibility and no detectable loss of performance.

---

### Post by fysicsandpholds on 2012-02-22
Thanks entangled I will try that.

Update: 

The problem mysteriously fixed itself. However I ran into boot loading trouble and now I need to reinstall it, and then it stopped working again!

---

### Post by Haventfoundme on 2012-02-26
So you are you still using refit or are you holding the "C" key to boot from the disc? If you are using refit then that seems like the problem. If you *have* wiped the drive then the only thing I can suggest is try to run the install disc from an external DVD drive. I can only suspect that the DVD drive is the issue or some other hardware is hanging up the machine.

---

### Post by plussr on 2012-02-27
Was having the same problem, a person in this thread managed to install 11.10 with a usb (look at last few posts), there's a particular order that worked for them

[http://forums.macrumors.com/showthread.php?t=1329407](http://forums.macrumors.com/showthread.php?t=1329407)

---

### Post by fysicsandpholds on 2012-04-17
I've tried all of this with no success.

To clarify: It's not that refit doesn't recognize the linux installation disk, it's that once I chose the linux installation icon it just hangs there indefinitely.

I have tried to install Arch, Ubuntu 10.10, 11.04, 11.10, 12.04, and XUbuntu 11.10 in this manner, none of them worked.

The USB thing seemed like it was going to work but then a black screen showed up (I think it was part of refit) with a message saying that booting to external drives is not well supported on mac machines.

To re-iterate, I have successfully been able to install linux via disk on this machine before. Prior to all these troubles I never tried to install via USB so I have no comparison.

I just am curious whether this is a hardware or software problem and if there are any workarounds?
-Sam

---

