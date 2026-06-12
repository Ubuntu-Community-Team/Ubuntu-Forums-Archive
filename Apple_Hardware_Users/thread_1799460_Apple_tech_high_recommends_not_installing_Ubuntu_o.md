---
title: "Apple tech high recommends not installing Ubuntu on MBA"
date: 2011-07-07
forum: Apple Hardware Users
---

### Post by hotwax on 2011-07-07
Can a forum mod fix my title. "Apple tech highly recommends NOT installing Ubuntu on MBA"

I went into freenode and joined #mac and asked anyone if they knew how to make a bootable usb so i could install ubuntu on a MBA. this is what a apple employee has said in the chat.  I want to know what other MBA owners expierenced? have you expierenced cpu failures and had to return your MBA or does it run fine? I would ideally like to run Ubuntu 10.10 but now that i had this conversation with this apple rep, i am a  bit hesitant. I'm Riberty and the apple representative is Branes.


versatiletech> Riberty: have you considered something like Parallels?
<Riberty> no im not interested in virtual machine
versatiletech> so you just want to be able to boot up in Linux?
Riberty> yeah i just want to dual boot linux and osx. i found the directions on how to make a usb bootable drive but i cant seem to replicate the outcome that is on the instructions
versatiletech> [http://www.helium.com/items/421906-how-to-install-linux-on-an-intel-mac-with-boot-camp](http://www.helium.com/items/421906-how-to-install-linux-on-an-intel-mac-with-boot-camp)

versatiletech> Riberty: you might want to use boot camp

<Riberty> i tried that, it doesnt recognize the linux usb drive
<Riberty> oh wait... i mean i cant figure out how to make a bootable usb drive


<Branes> Riberty: If you value the life of your machine, do *not* try and run linux directly.

Riberty> virtual machines generate more heat 

<Branes> Riberty: I'm not shitting you mate. Apple use a custom power management chip, and no *nix distro can control it, leaving the CPU in an overvolted state.

<Branes> Fusion doesn't.
<Branes> Fusion is *brilliant*. Resource cost is approximately 0.2%
<Branes> Fusion and OSX is a marriage made in heaven -- VMware says that OSX is the best host OS for virtualisation ever.

versatiletech> Riberty: I have a virtual machine running all the time. It doesn't hog the CPU if it's on idle. It only uses as much of the CPU as you use. I don't have any experience with VMWare Fushion, but I love Parallels.
<Dmole> Riberty: macs don't boot off usb you need a boot disk

<Branes> A Mac will boot off USB if a) the external volume is OSX, with a GUID partition map, or b) the Mac has had Boot Camp installed correctly, then you can boot any volume with a GPT or MBR.
<Branes> What you can't do is boot Windows via USB.
Dmole> Riberty: never had an air flow problem on my macbook but it's an older aluminum version with big fans
<versatiletech> Dmole: depends on what virtualization software you use. Parallels allows you to the smart CPU sharing so only if you focus on a virtual machine it'll use more the CPU

**<Branes> Oh, gods ... dude, I've replaced the logicboard on twenty six Airs in the last month, because some idiot linux tweaker in a position of power made his company buy sixty Air 13's, then wiped OSX completely and installed linux. So far, a machine in their hands lasts about six weeks before catastrophic CPU failure.**

versatiletech> more of the CPU*
**<Branes> Do *NOT* try and run a linux on an Air.**
<Dmole> versatiletech: noe that I sad RAM and GPU not CPU
**<Branes> Keep it in a virtual machine, let OSX do its job of micromanaging the hardware correctly.**
<versatiletech> ah yes. Agreed.
Riberty> ok now you are more credible
<Dmole> Branes: are there known problems with linux on macbooks(not air)?
[B]<Branes> Riberty: Apple do not use a compliant SMbus device, their custom chip *forces* the host OS to micromanage everything, especially CPU voltages. No other OS can do it, and Apple refuse to divulge the SMC's protocols.
<Branes> Dmole: Yes, the chances of premature CPU failure rises by several hundred percent.
<Branes> Apple do not support linux.[/B]
<Riberty> what a shame
<CPng|N> well of course. Why would they help the enemy any more than necessary to get their interest and switch them over
<Branes> Don't fall for the fallacy that Intel CPU = generic class PC. It ain't so, Apple's stuff is slightly but annoyingly custom.
<blkcat> somehow that doesn't surprise me :\
<Branes> That's why you need *their* Boot Camp stuff to boot anything other than OSX.
<CPng|N> I don't think a bare OS X install with VMware maximized would be too much different. a little memory loss for OS X necessary usage
<Branes> blkcat: Apple have been changing hardware to suit their software for thirty years. It's not  habit they're going to break any time soon.
<blkcat> indeed.
<Branes> **Fusion handles linux beautifully.**
<Branes> **Go full screen, you'd never know OSX was sitting behind **the scenes looking after things.
<CPng|N> linux was the original VM target
<CPng|N> no surprise they've mastered that
<Branes> **Riberty: I've been a certified Apple technician since 1981. And the fault I describe has been confirmed by Apple engineers.**
<Riberty> ill give vm a try and see if i get heat issues
<Branes> It's not heat issues.
<Branes> It's voltage.
<Riberty> voltage = heat output
<Riberty> more voltage = more heat
<Branes> linux cannot control the voltage of *any* Core-class CPU in an Apple product.
<Branes> No.
<Branes> Think backwards.
<Riberty> dude its basic physics
<Branes> Nuh-uh.
<Riberty> lol
<Branes> It is not heat that causes the damage.
<Dmole> I thought Boot Camp was a boot manager not a VM, or dose it make a lightweight VM to run the other OSs in?
<blkcat> overvoltage kills circuits even without the heat entering into the equation
<Riberty> correct Dmole
<Branes> **What normally happens, is as the Core's delta-T approaches zero, the Vcore is *reduced* in minute increments to maintain potential against resistance.**
<Branes> **Dmole: Boot Camp is a driver suite, partition manager, boot loader, and most importantly, a BIOS emulation system.**
<Dmole> So running linux or any other OS in that way is fine than, and overhead should be neg right?
<Branes> **On a normal machine, the SMbus is reactive, adjusting the voltage after the temperature changes. OSX is pre-emptive, as the kernel monitors and controls the CPU voltage *directly*, when it recieves a request for increased load, it lowers the voltage *first*, *then* applies the load.**
Branes> **Any chip designer will tell you that maintaining equilibrium between active voltage, the electrical noise floor, and resistance, is crucial.**
<CPng|N> more and more so as chips shrink and speeds increase
<CPng|N> and # of transistors multiplies
<Branes> Apple has always favoured a software-hands-on approach to its hardware, and frankly don't trust one chip to look after another
Branes> **Localised heat should be able to disperse cleanly, and Intel do a reasonable good job of optimising the die to deal with that. AMD are much better at it, though. The real problem with the Air is that it uses a custom-for-Apple die carrier that's 38% smaller and 50% less mass than a standard Core CPU.**
<CPng|N> didn't realize that
<Branes> **heh, *everything* in the Air is custom-by-Apple or custom-for-Apple, except the mSATA connector :)**
<Branes> Even the SMD RAM chips are 85% the size of normal.
<Dmole> Riberty: basic physics is limited and simply dose not apply to some things like quantum chemistry(really small) or biology(really big); "basic physics" works best when the subject can be approximated by a perfect sphere.
Branes> **Riberty: In short, if the Vcore is not lowered properly, potential in the traces increases, causing excessively energetic electrons that can actually jump a trace on the silicon.**

<Branes> Riberty: If the electrons get too jumpy, they can make a permanent bridge between traces or gates where there's not meant to be any. The process is called electromigration, but you might know it better as "overclocker's cancer"

<Riberty> Branes: thanks for the info, guess i wont be dual booting linux  :(    what about dual booting with w7?

<Branes> As long as you've installed the Boot Camp driver pack, and let it download the latest, appropriate ones for your mardware, it'll work very well.
<Branes> ... you just won't get anywhere near the same battery life as you do with OSX.
<Branes> Seriously, if you love your linux, buy Fusion. It really really is that good, when paired with OSX.
<Branes> O'course, getting Win7 onto an Air is something of an ordeal if you don't have an optical drive handy :)
<Riberty> Branes: when you took care of those 6 macbook air with linux installed on it, did the person who installed linux also put the macbook air dirvers that was created for it or did the person install linux and let it run withoout any drivers?
<Branes> Riberty: They tried to use one of the smckexts that are available.
<Branes> **And it was twenty six, not six.**
<Riberty> Branes: im not sure what smckexts is but was it this... [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)
<Branes> Two of the Airs I've seen twice. Apple don't see it as a mistake. To Apple, linux does not exist.
<Branes> I wouldn't know Riberty, but it was the latest Ubuntu that was on all the Airs.
<Branes> I've got a nifty mSATA adaptor that lets me snap out the Air's SSD module and hook it up as an external USB drive on any other computer. That's how I can tell what they were doing :)
<Branes> Riberty: It would be worse.
<Branes> **The problem first manifest itself with Ubuntu 8.**
<Branes> Of the three SMC drivers (kexts) for *nix I know of, *none* of them can control Vcore.
<Branes> Yes.
<Branes> Any Mac with a Core-class CPU.
<Branes> And the newer the CPU, the higher the risk of premature CPU failure. The Air is just the most sensitive.
Branes> I've had MacBooks and MBPs with DBU logicboards too.
<Branes> An iMac, too.
<Branes> The Mac Pro is immune, the Xeons don't hand off VID control, they do it all on-chip.

---

### Post by tgalati4 on 2011-07-07
Interesting post.  I'm glad that I can undervolt my heavy, black, ugly thinkpad under linux.

---

### Post by snafu006 on 2011-07-07
That's BS about the part where Linux can't manage the voltage my old g3 has no fan inside and never overheats using Ubuntu. Now when it was running OSX it would over heat all the time so I say BS to guy and if you have the computer for a long time and the os changes overtime you don't have support anymore

---

### Post by conundrumx on 2011-07-08
If you want to run Linux as your primary OS don't buy a Mac.

Linux (and Windows, for what it's worth) can't manage the hardware of an Apple product the way OS X can, quite intentionally.  You're going to get lower battery life, more heat generation and probably less life out of the hardware.

---

### Post by linuxopjemac on 2011-07-08
I am running Linux on both Intel and PPC based Macs as only OS for many years without troubles...

---

### Post by handy on 2011-07-08
> **snafu006 said:**
> That's BS about the part where Linux can't manage the voltage my old g3 has no fan inside and never overheats using Ubuntu. Now when it was running OSX it would over heat all the time so I say BS to guy and if you have the computer for a long time and the os changes overtime you don't have support anymore

He wasn't talking about PPC CPUs.
________

I've been running a 2007 alu' 24" iMac on Arch since March 2008. I check on the temperature from time to time using LMsensors. It is always running quite cool.

Though the guy did say the problem is worse in the more recent Core class CPUs. The Air is so small as well. Apple have somewhat of a reputation for making hot notebooks. They made one that you could literally fry an egg on! lol

---

### Post by Blasphemist on 2011-07-08
I can't help as I have no relevant experience but, LOL, really loud. :D 

This has to be the funniest post I've read in a long time. I am so glad to have never been an apple guy, wait I have an iphone, jeez! I do recommend looking through these forums and doing some googling before you take the a heads in that chat at their word. They may be right or just smoking something bad.

---

### Post by pygo on 2011-07-08
Hah! I've heard similar things from apple techs that say not to use non-apple branded ram and to only get apple to do it and use theirs because 3rd party apple memory is only based on pc memory and is 1mm off in dimmenions and the voltages aren't right and the timings are all off.

This may be slightly against forum rules, but I'm just going to say it like it is. They're all brainwashed to believing apple is the only way. Much like most people with an MCSE - they hate anything that's different. There are some with more open minds though. It's easy to spot the loons, they tend to not have open minds.

Just do your research and you should be fine.

As far as getting a USB disk created, if you do have vmware fusion (free 30 day trial from their site), just install ubuntu and attach the usb stick in after. Then use the startup disk creator from a linux iso as if you where doing it normally. A bit of a shadier method is to buy any usb dvd drive from best-buy/future-shop/walmart, install linux and return it when done. I've used my samsung dvd drive many times. (It's actually worth keeping. Instead of buying some $30 DVD drive for each PC I've got, I just got one maine DVD burner for my main PC, and the USB drive for all the others, as well as for diagnosing and fixing friends computers.)

---

### Post by pauljwells on 2011-07-08
Yep, as a lifelong fanboi, I sold my last intel mac, bought a G5 to run natty (works beautifully) and replaced a long line of 'pro' class apple laptops with a Lenovo X220.

When I did have intel macs though, it was true that Fusion worked very well.

Never looked back!

---

### Post by DoubleClicker on 2011-07-09
The Apple Tech is at least partially right.  "Out of the box"  ubuntu will fry your MacBook Air.  

The Mactel Support Team has a PPA, that that has applesmc-dkms and other packages, that address hardware problems for MaBookPro, but i do not know if they work on MacBook Air.

[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by Grungekid on 2011-07-09
If this were a real issue wouldn't apple release a statement about this or mention it within there warranty? Surely due to the millions of people who use linux this would cost them a fair bit in repair costs should it be true? Especially if the issue occurs within 6-9 months as stated by Mr Branes?

---

### Post by alexmurray on 2011-07-10
> **DoubleClicker said:**
> The Apple Tech is at least partially right.  "Out of the box"  ubuntu will fry your MacBook Air.  

The Mactel Support Team has a PPA, that that has applesmc-dkms and other packages, that address hardware problems for MaBookPro, but i do not know if they work on MacBook Air.

[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)
That's bogus - as someone who has contributed code to the applesmc driver I can say the applesmc-dkms doesn't do anything to help 'cool' your machine - it simply provides access to read and control the fan / temp sensors etc - and the mainline version of the driver is the same in natty as the one in the ppa anyway as far as I recall so there should be no need to install it.

In general OSX does a better job of power management over Ubuntu (because it was purpose built to run on the hardware where as Ubuntu is built to run on an extremely large array of hardware) so OSX runs a bit cooler than Ubuntu but unless your SMC firmware is buggered ([http://support.apple.com/kb/ht3964](http://support.apple.com/kb/ht3964)) Ubuntu shouldnt run much more than about 5 degrees hotter than OSX and this is certainly not enough to 'fry' your machine. If Ubuntu does run much hotter than this I would suggest resetting your SMC as described in that link and then see how it is.

---

### Post by User4519 on 2011-07-22
This thread is scaring me. My MBA is now on a truck somewhere on its way to my home. No way in hell will it be running OS X. But how much of this is FUD and how much of it is real? Are the Mactel dudes further ahead than this supposed Apple tech dude knows? Is the new MBA different in any way (it IS a new processor, mind you - mayhap Intel didn't make any deviations from their standard blueprints this time around...) ?

---

### Post by cdEWoozy on 2011-07-23
> **DanielBuus said:**
> This thread is scaring me. My MBA is now on a truck somewhere on its way to my home. No way in hell will it be running OS X. But how much of this is FUD and how much of it is real?

There was a [discussion]("https://bbs.archlinux.org/viewtopic.php?id=92124") on the Arch Linux forums last year where [someone analyzed bootcamp]("https://bbs.archlinux.org/viewtopic.php?pid=748111#p748111") (which, according to Branes, [sets the vcore value to a safe state]("https://bbs.archlinux.org/viewtopic.php?pid=717314#p717314") before booting Windows) and didn't find any indication of it tinkering with the vcore values, so it looks like FUD.

---

### Post by User4519 on 2011-07-23
> **cdEWoozy said:**
> There was a [discussion]("https://bbs.archlinux.org/viewtopic.php?id=92124") on the Arch Linux forums last year where [someone analyzed bootcamp]("https://bbs.archlinux.org/viewtopic.php?pid=748111#p748111") (which, according to Branes, [sets the vcore value to a safe state]("https://bbs.archlinux.org/viewtopic.php?pid=717314#p717314") before booting Windows) and didn't find any indication of it tinkering with the vcore values, so it looks like FUD.

Thank you for that link! Now, even if we were to accept the premise here, then it's now clear that this Branes quote is **years** old. It actually predates the previous generation of MBAs. And then, even if true, it would apply to those systems which actually had an SMC - Mid-2010 and the new ones don't; and the CPU types used in the new MBAs are **not** specific Apple builds - for instance, the Samsung 9 series uses the same CPU as the new MBAs!

In my mind, I'm now pretty certain this is just complete FUD at present, even if two years ago it might have been true. I'm lucky I was too late to be able to cancel my shipment of the MBA yesterday :)

---

### Post by dentifrice on 2011-07-23
> **DanielBuus said:**
> I'm lucky I was too late to be able to cancel my shipment of the MBA yesterday :)

** @DanielBuus:** since you seem to be getting the latest MacBookAir that just came out, can you share your first impressions and progress in running Ubuntu on it in *[this dedicated thread]("http://ubuntuforums.org/showthread.php?t=1810275")*? That'd be great, thanks!

---

### Post by User4519 on 2011-07-23
> **dentifrice said:**
> ** @DanielBuus:** since you seem to be getting the latest MacBookAir that just came out, can you share your first impressions and progress in running Ubuntu on it in *[this dedicated thread]("http://ubuntuforums.org/showthread.php?t=1810275")*? That'd be great, thanks!

Will do! If I'm lucky I'll get it Friday, otherwise it should be here next Monday at the latest. :)

---

