---
title: "Install windows with iso."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by LinuxLoserr on 2007-08-13
Ok well, being the idiot I always am, i need people to help idiots like me.
I have an iso of windows xp, and i don't know how to boot it so i can install it over ubuntu.
Keeping it short and simple.
Help me.

---

### Post by omegamike3 on 2007-08-13
burn to disc, boot from disc, install.

---

### Post by chriscando on 2007-08-13
Install it over ubuntu? Awww, why would you want to do that? :)

---

### Post by omegamike3 on 2007-08-13
> **chriscando said:**
> Install it over ubuntu? Awww, why would you want to do that? :)

because he's a 'LinuxLoserr' and wants to run back to billy ;) j/k

---

### Post by LinuxLoserr on 2007-08-14
haha, well
i have it on a cd, but when it asks me to press esc for boot menu, i don't see the cd in the list...
maybe theres a problem when its on a dvd-cd?

---

### Post by nothing4me on 2007-08-14
> **LinuxLoserr said:**
> haha, well
i have it on a cd, but when it asks me to press esc for boot menu, i don't see the cd in the list...
maybe theres a problem when its on a dvd-cd?Did you burn the CD? Or did you drag the ISO onto the CD? :p

And make sure it's bootable.

---

### Post by LinuxLoserr on 2007-08-14
definitely burned it.
maybe im on the wrong boot list? :P

---

### Post by nvteighen on 2007-08-14
Are you sure guys if Microsoft hasn't put any kind of restriction to XP CDs?

---

### Post by LinuxLoserr on 2007-08-14
I shure hope not :(

---

### Post by bjarneh on 2007-08-14
maybe you dont have hard-drive before disk-drive in our boot setup?

---

### Post by nvrpunk on 2007-08-14
is your bios set to boot off cd?  Assuming you made no changes and guessing that you can probably boot an Ubuntu Livecd.

You probably burned it wrong.

check if you can boot off the Ubuntu Livecd.  If so the problem is you.

-nvrpunk-

ps reburn it if that is the case.

---

### Post by nothing4me on 2007-08-14
> **LinuxLoserr said:**
> definitely burned it.
maybe im on the wrong boot list? :PIt should just say "Press any key to boot from CD".

Doesn't it say that?

And yea, it could be the DVD-CD. It was made for a CD, those 700 MB ones.
Unless... You're installing Vista?

---

### Post by WebSiteGuru on 2007-08-14
> **LinuxLoserr said:**
> definitely burned it.
maybe im on the wrong boot list? :P

Did you burned it as image or data?

---

### Post by nothing4me on 2007-08-14
> **WebSiteGuru said:**
> Did you burned it as image or data?It should be "Burn Image to disk".

---

### Post by LinuxLoserr on 2007-08-14
yeah i did alll of that.
it didnt  say press any key for boot disk...
but i went to the boot menu and it just shows me a whole bunch of ubuntu stuff.

---

### Post by nvteighen on 2007-08-14
Wait a bit. From where did you get that ISO?

---

### Post by nvteighen on 2007-08-14
> **LinuxLoserr said:**
> yeah i did alll of that.
it didnt  say press any key for boot disk...
but i went to the boot menu and it just shows me a whole bunch of ubuntu stuff.

No, you're looking to the wrong place. When you restart your computer, there surely says something like "Press (something) to enter boot/BIOS menu..."

---

### Post by LinuxLoserr on 2007-08-14
Does it matter?
I must have burnt the iso wrong on my cd, i'll try playing around, see what i did wrong.

---

### Post by LinuxLoserr on 2007-08-14
uhh.
when SHOULD it say that, when it shows the ubuntu sign?
or before that?

---

### Post by nvrpunk on 2007-08-14
Or the illegal ISO you got isnt bootable.  Which is fixable but I am not going to help you pirate anything :)

Boot order should work like this:

CD/DVD -->Grub (that screen you talk of) --> Whatever device you choose to boot

but the cd/dvd coming first depends on if it is set in the BIOS.  As I said, if you put the ubuntu livecd in and it boots off it before grub pops up, you burned it wrong.  Or your illegal copy isnt bootable.  

done helping.  

-nvrpunk-

btw rtfm

---

### Post by nvteighen on 2007-08-14
> **LinuxLoserr said:**
> uhh.
when SHOULD it say that, when it shows the ubuntu sign?
or before that?
Immediately after you have turned your computer on.

---

### Post by LinuxLoserr on 2007-08-14
I'm sorry but it just isn't pirated. I just don't have to tell you where its from :)

---

### Post by LinuxLoserr on 2007-08-14
well, i have a toshiba, and it says press f12 for boot menu, but i press it and nothing happens.

---

### Post by nvrpunk on 2007-08-14
pebkac

---

### Post by nothing4me on 2007-08-14
> **LinuxLoserr said:**
> well, i have a toshiba, and it says press f12 for boot menu, but i press it and nothing happens.Boot up into BIOS and check the settings.

---

### Post by nvteighen on 2007-08-14
> **LinuxLoserr said:**
> well, i have a toshiba, and it says press f12 for boot menu, but i press it and nothing happens.

OK, I have a Toshiba too. This simplifies everything a lot.

You say F12 doesn't work. Weird.

Press F2 instead. This will open your BIOS configuration panel... Yes, you'll see a lot of options. Press the Right Arrow key to reach the "Boot" section. Then, follow the instructions you'll see in a grey rectangle at your right to change your PC's boot order.

When you have finished, press Right Arrow again (to "Exit") and select "Exit Saving Changes". This will restart your computer with your changes applied. Try booting Ubuntu Live CD to see if it works.

---

### Post by Paulmd on 2007-08-14
> **nvteighen said:**
> Are you sure guys if Microsoft hasn't put any kind of restriction to XP CDs?

Definately not on XP.  It would screw with slipstreaming. They care more that you have a COA, then having a hologrammed disk.

---

### Post by Paulmd on 2007-08-14
> **LinuxLoserr said:**
> I'm sorry but it just isn't pirated. I just don't have to tell you where its from :)


You don't HAVE to. But it might help us help you.  If we knew the source, we MIGHT be able to tell you if you've got a non-bootable ISO. 

If your cd/dvd drive is external, it might not be bootable in your machine.

It could also be that you burned it to a DVD instead of a CD. Not sure why that would matter, but try using a CD.


Older toshibas have different methods of booting a cd and/ or entering the bios I've seen:

Press the C key during post (stolen from Apple :) )

press esc-f1, while the machine is off, and then power it on while holding down those keys. that may get you into Toshiba's bios.

As well as the methods mentioned by other posters.

---

### Post by sailor2001 on 2007-08-14
before you try booting into windows. that isn't a live disk and will try to install. when it does it will wipe out your ubuntu partition. is this what you wanted to do? Short of that  you could first install vmware server

---

### Post by LinuxLoserr on 2007-08-14
K guys, i ended up pressing f2 and everything worked out.
however, i remembered it was windows i was installing so i ended up installing ubuntu again.
Happy story :D

---

### Post by nvteighen on 2007-08-15
> **LinuxLoserr said:**
> K guys, i ended up pressing f2 and everything worked out.
however, i remembered it was windows i was installing so i ended up installing ubuntu again.
Happy story :D
So, you have decided to have a dual-boot? Congrats.

What it's still weird to me is that F12 hasn't work for you and you had to do the long-F2 way...

---

### Post by LinuxLoserr on 2007-08-15
Whatever, it wasnt that hard to do the long way.

---

### Post by R0B071CxN1NJ4 on 2007-08-15
You have to write to the disc from an .iso rather than just burning the .iso to the disc. This is because burning the .iso to the disc does not install the iso on the disc it only transfers the files whereas writing to it from an .iso does.

First i would recommend getting the program GnomeBaker its a cd creator you can find in the software installer that comes with ubuntu. Then look through the menus (sorry i cant give specifics i dont currently have the app) and see if you can find something that says write to disc from iso. It should be in the file menu.

Select your file and burn. Voila.

---

