---
title: "64bit Gutsy install. RAM shows as 3.2 gig not 4 gig"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Mildredd on 2008-04-01
I've used Ubuntu for a day now and I'm a COMPLETE NOVICE with it.

I see this has been posted about on more than one occasion but, like the others, I still haven't found a definate solution. 

Can someone point me in the direction of a 'how to' on this site or copy paste something helpful to enable me to use the full RAM?

I have the 64bit Gutsy running, 4gig of RAM only showing 3.2.

Also, the nvidia restricted drivers aren't in the restricted drivers section. Any ideas?

Many Thanks

---

### Post by stefangr1 on 2008-04-01
I believe that this has to do with your IO-board. You can possibly change this in the bios, with an option that has something to do with "remapping".

For the NVIDIA video card: it is my opinion that downloading and installing the drivers from the NVIDIA site (you have to relogin in console mode to run the installer) is the least hard way to get it done.

---

### Post by ian dobson on 2008-04-01
Hi,

Just go into the bios and enable the memory remapping function. It could be called memory reallocation or something along these lines.

The reason this happens is that PCI cards need to sit somewhere in memory so that the CPU/OS can send/receive data to them. When the PCI bus was designed 4Gb was "more than enough" so they decided to allocate memory for the PCI bus in the upper memory (3-4Gb range).

What memory remapping does is move the memory "hidden" by the PCI cards to a higher address over 4Gb.

Note: This also holds true for PCI-e.

Regards
Ian Dobson

---

### Post by forrestcupp on 2008-04-01
And if you're absolutely sure that you have an nvidia card that is not too old to be supported, it's much easier to use [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to download and install the latest drivers for you.  I think Envy will even tell you if your card isn't supported.  Envy is a script that automatically does for you what stefangr1 suggested.

---

### Post by Mildredd on 2008-04-01
Thanks for the fast responses!

I've d/l envy and am running it as we speak.

Is the BIOS like windows when it boots? How do i get there if i'm dual booting vista and ubuntu?

---

### Post by stefangr1 on 2008-04-01
No, the bios is a menu runs from a small flash memory unit on the IO-board, you usually get in to it by pressing Esc, Delete, or F2 (which is shown a few seconds at boot).

When you're in the BIOS, watch out with changing anything! The wrong settings could make booting impossible, so make sure you know what you're doing. Maybe look what options are available, then quit without saving, google a bit,  and then turn back to the BIOS. Better not to experiment with different settings!

---

### Post by Mildredd on 2008-04-01
> **stefangr1 said:**
> Now, the bios is a menu runs from a small flash memory unit on the IO-board, you usually get in to it by pressing Esc, Delete, or F2 (which is shown a few seconds at boot).

Since you never heard of the BIOS, watch out with changing anything! The wrong settings could make booting impossible, so make sure you know what you're doing. Maybe look what options are available, then quit without saving, google a bit,  and then turn back to the BIOS. Better not to experiment with different settings!

Hey, i've heard of BIOS before and used it to find info but wasn't sure if this was the same one or something within Ubuntu. 

I've gone through the menus but can't find a Remap Memory option or anything similar. Does every BIOS have one?

---

### Post by stefangr1 on 2008-04-01
I'm sorry, a misunderstanding from my side. The BIOS is apart from the operating system, it's part of the hardware. No, I believe some do not have the option to utilize the full 4GiB, but maybe someone else can tell you more about which ones can and which ones can't.

Also: have you looked in the manual of your IO-board? Maybe it could be helpful on this subject.

---

### Post by Mildredd on 2008-04-01
> **stefangr1 said:**
> I'm sorry, a misunderstanding from my side. The BIOS is apart from the operating system, it's part of the hardware. No, I believe some do not have the option to utilize the full 4GiB, but maybe someone else can tell you more about which ones can and which ones can't.

Also: have you looked in the manual of your IO-board? Maybe it could be helpful on this subject.

It must've have the option :( thanks anyway. As you said, somone else may know of another way. 

Many thanks!

---

### Post by Mogurijin on 2008-04-01
You could always try to update your BIOS to a newer version ("flashing" the BIOS) if you haven't already. Also, some boards have "hidden" options. They require a combination of keys (like ctrl+f1 or something) to show the "advanced" options. However, I think this is mainly a Gigabyte thing, I could be wrong though.

---

### Post by Duck2006 on 2008-04-01
> I have the 64bit Gutsy running, 4gig of RAM only showing 3.2.

You need a tweak to be able to use the hole of the 4Gb of mem, round 4 weeks ago some one had the same problem and it was solved not sure what the thread was called, but may be if you do a search will help you solve it. Try this search engine.

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by Mildredd on 2008-04-02
> **Mogurijin said:**
> You could always try to update your BIOS to a newer version ("flashing" the BIOS) if you haven't already. Also, some boards have "hidden" options. They require a combination of keys (like ctrl+f1 or something) to show the "advanced" options. However, I think this is mainly a Gigabyte thing, I could be wrong though.

The latest BIOS firmware is from around the time I bought the Motherboard.

My board is a Gigabyte but in BIOS I can access 'advanced', it just doesn't show memory remap.

---

