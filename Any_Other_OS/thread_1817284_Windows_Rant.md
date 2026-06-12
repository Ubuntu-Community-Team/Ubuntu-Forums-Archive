---
title: "Windows Rant"
date: 2011-08-03
forum: Any Other OS
---

### Post by ki4jgt on 2011-08-03
> Is there somewhere I can let out all my screams about Windows? OK, they saw security holes, they saw that unix/mac fixed those holes with file ownership. Yay! :-) Now, they decide to implement file ownership, but instead of doing it like mac and Linux, they decide they're going to come up with their own funky system. . . :confused::confused::confused: I mean, COME ON! I need to burn an ISO I found online. Everywhere I look online, no body knows how to take file ownership, then, when the computer magically decides to allow you to have ownership, it erases it, b/c it's a threat to your computer. Even though, you own it! and you're making all the decisions about it :-( It shouldn't matter if it's Kon-Boot. It shouldn't matter if it's a virus. If I want to open it, I want to open it, not have it erased because someone at corporate headquaters doesn't think I should have access to it! You're file and wifi security are about to drive me up the wall.

All in all, does anyone know of a program which will take absolute ownership in win 7 and keep the OS from deleting what it thinks is a threat? (I completely disabled the antivirus, so that's not it) Every time I try to burn the kon-boot iso in win7 it says I don't have permissions to access the file because I don't own it. After I do what's written on Microsoft's site, it says I still don't own it. I consulted google, about this, apparently, when you first do it, it takes the system a little time to recognize it. Then when it does, the in built security blasts it to smitherines. Please, no suggestions like "Just install Ubuntu" It's my brother's laptop :-( if it were up to me, it would've happened a long time ago.

---

### Post by el_koraco on 2011-08-03
stupid question - are you trying to run the software via a regular user account with no admin privileges?

---

### Post by ki4jgt on 2011-08-03
> **el_koraco said:**
> stupid question - are you trying to run the software via a regular user account with no admin privileges?

I've tried both. I've even given file ownership to both, but once the system realizes that someone local owns it, before I even have the ability to do anything with it, the system deletes it :-(

It's an ISO. The program to burn the ISO, I've even ran from both accounts.

---

### Post by el_koraco on 2011-08-03
This is probably the blind leading the blind, since I have almost no knowledge of Win7, but can you try to download an iso burning program like Unetbootin and try it from there?

---

### Post by ki4jgt on 2011-08-03
> **el_koraco said:**
> This is probably the blind leading the blind, since I have almost no knowledge of Win7, but can you try to download an iso burning program like Unetbootin and try it from there?

The burning program's not the problem. I've used the program before. Every time the computer comes in contact with the ISO, it deletes it. When extract kon-boot from it's archive (zip) file, the computer shows a warning. (This file is untrusted) with my antivirus fully disabled, I click cancel on the system warning. I then proceed to change ownership as per Microsoft's instructions. Afterwards, I wait as per Microsoft's instruction, so the system can catch up. After I wait, the system then deletes it, when it knows I own the file.

---

### Post by zero244 on 2011-08-03
Why don't you just burn it with a Ubuntu Live CD.
Or better yet throw Windows in the trash and just use Linux.

If I remember.....a few years ago when Microsoft was the only kid on the block they used to play
"I Do It My Way" by Frank Sinatra at there big events.
That pretty much sums it up.

---

### Post by Frubli on 2011-08-04
I Google'd for kon-boot and found it at [http://www.piotrbania.com/all/kon-boot/](http://www.piotrbania.com/all/kon-boot/) , downloaded it and looked around.

1) I'm using Windows 7 and it did not change ownership, or lock me out of the file.

2) When I mounted the ISO in VirtualClone Drive, Kaspersky anti-virus accused it of having a boot sector virus.


I suggest you didn't completely disable the antivirus.

---

### Post by zero244 on 2011-08-04
Wow very interesting, and shows you have to be very careful what you download and run on your computer.

---

### Post by Frubli on 2011-08-04
The page warns that it might be detected as a virus but it isn't.

I know that it is supposed to intercept a booting OS and get you in around any passwords, so maybe it does something which viruses also do and is close enough to trigger AV software.

Or maybe the page is lying and it has a virus, who knows! :P

---

### Post by ki4jgt on 2011-08-04
> **zero244 said:**
> Why don't you just burn it with a Ubuntu Live CD.
Or better yet throw Windows in the trash and just use Linux.

If I remember.....a few years ago when Microsoft was the only kid on the block they used to play
"I Do It My Way" by Frank Sinatra at there big events.
That pretty much sums it up.

Brother's computer. Only one CD drive :-(

> **Frubli said:**
> I Google'd for kon-boot and found it at [http://www.piotrbania.com/all/kon-boot/](http://www.piotrbania.com/all/kon-boot/) , downloaded it and looked around.

1) I'm using Windows 7 and it did not change ownership, or lock me out of the file.

2) When I mounted the ISO in VirtualClone Drive, Kaspersky anti-virus accused it of having a boot sector virus.


I suggest you didn't completely disable the antivirus.

I can download the ISO just fine also, the problem arises when I attempt to use it.

The problem is, I'm using InfraRecorder to actually burn the ISO. It doesn't change ownership until you tell it to. On my brother's system it's owned by system. InfraRecorder won't burn or touch the iso b/c system owns it.
He has AVG. I go into AVG and disable it for 15 minutes. AVG is completely disabled. I then proceed to switch owners to my brother's account. After a few moments, the iso is gone. I know AVG didn't do it, b/c I've used and disabled AVG many times before on projects like this.

---

