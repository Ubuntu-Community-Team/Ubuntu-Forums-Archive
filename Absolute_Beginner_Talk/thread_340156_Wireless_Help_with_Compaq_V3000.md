---
title: "Wireless Help with Compaq V3000"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by den.saunders on 2007-01-16
Hey all,

Im new to Ubuntu, new to Linux, and am (as could be expected) having some beginners issues. 

I installed it about a month ago, and a week of trying got my resolution set. :)

Now...I am unable to get wireless internet. I've tryed to piece together all the info I've looked up so far, but it's hard going back and forth to Windows for internet, everytime an attempt fails.

So...I have a Compaq v3015nr with AMD Turion64 X2, and an integral Broadband Wireless card.

When I try to use: **sudo apt-get install ndiswrapper-utils**
it says it cannot find ndiswrapper, is it not included with ubuntu? How can I call it up?

And then what?!? Ahhhh! So confused!
Thanks in Advance

---

### Post by den.saunders on 2007-01-16
Update!

So for some reason one time (and one time only! I have no idea how to make it happen again) when I booted ubuntu, with the install cd in the drive, I got an option to add some things from the ubuntu cd. So I added ndiswrapper, and was able to install it.

Now I am trying to install my drivers. From the .exe avaliable from compaq, I extracted the two files.
bcmwl5.inf and bcmwl5.sys
Now I want to do

sudo ndiswrapper -i bcmwl5.inf

but after that when i check

sudo ndiswrapper -l

it prints **bcmwl5 invalid driver!**

ideas?!?
Thanks in Advance again
!

---

### Post by kolinab on 2007-01-17
Hey,

I'm no wireless troubleshooter, nor do I have a Compaq, but there was a thread recently with a guy having wireless problems with a VXXX system. Thread here:
[URL="http://www.ubuntuforums.org/showthread.php?t=331775"]
http://www.ubuntuforums.org/showthread.php?t=331775[/URL]

and I found a link to a wiki page for compaq Vxxx users:

[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A]("http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A")

Hopefully one of those threads will get you going in the right direction.

K

---

### Post by waggygee on 2007-11-05
Look at this [http://ubuntuforums.org/showthread.php?t=405990&highlight=firmware+broadcom+43xx+chipset+family](http://ubuntuforums.org/showthread.php?t=405990&highlight=firmware+broadcom+43xx+chipset+family)

---

