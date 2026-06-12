---
title: "New would-be user, not very bright"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by SusieK on 2007-05-17
Hello

As the title says, I would like to become a Ubuntu user, but when it comes to computers, I'm not very bright; in fact, very dim, so please forgive me if my questions are really stupid. 

I have two notebook computers. A relatively new Acer Aspire 3610, and an older notebook, bought five years ago. It's made by AJP, a smaller UK company who make quite good computers.

What I wanted to do was install Ubuntu on the old machine first, to try it out. Then, if it works well for me, replace XP on my Acer with Ubuntu as well.

I've downloaded Ubuntu and made the CD, but when I've put it into the old notebook and asked it to run as a live CD, it comes up with a message about BIOS cut-off 1997. From what I have read, I understand that the BIOS is too old to work with Ubuntu. My question is: If the BIOS cannot be updated, does that mean Ubuntu is never going to run on that machine? Tomorrow I'm going to speak to AJP and find out if the BIOS is up-datable. 

If somebody could be kind enough to answer that question, probably I can save myself a lot of time and stress.  Many thanks. It's nearly mid-night here in France, so I'm off to bed in 10 minutes, but hope to find a reply in the morning. 

Bonne nuit.

---

### Post by annda on 2007-05-17
i suppose the old laptop can't even boot from the cd. you can try out ubuntu on the Acer - it is a live CD, so you can use the system and even "install" programs without changing anything on you hard disk. try it out. it will be much slower running from the CD but you can see if you like it and if it understands your hardware.

---

### Post by overdrank on 2007-05-17
> **SusieK said:**
> Hello

As the title says, I would like to become a Ubuntu user, but when it comes to computers, I'm not very bright; in fact, very dim, so please forgive me if my questions are really stupid. 

I have two notebook computers. A relatively new Acer Aspire 3610, and an older notebook, bought five years ago. It's made by AJP, a smaller UK company who make quite good computers.

What I wanted to do was install Ubuntu on the old machine first, to try it out. Then, if it works well for me, replace XP on my Acer with Ubuntu as well.

I've downloaded Ubuntu and made the CD, but when I've put it into the old notebook and asked it to run as a live CD, it comes up with a message about BIOS cut-off 1997. From what I have read, I understand that the BIOS is too old to work with Ubuntu. My question is: If the BIOS cannot be updated, does that mean Ubuntu is never going to run on that machine? Tomorrow I'm going to speak to AJP and find out if the BIOS is up-datable. 

If somebody could be kind enough to answer that question, probably I can save myself a lot of time and stress.  Many thanks. It's nearly mid-night here in France, so I'm off to bed in 10 minutes, but hope to find a reply in the morning. 

Bonne nuit.

Hi that is a good idea to use the old laptop. I might suggest that you look a the ram and see if you have enough because the minimum for is 256mb, You can try xubuntu or maybe update the ram and even try the alternate cd found at this link scroll down to the alternate cd
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
Hope this helps and good luck!:)

---

### Post by lluisanunez on 2007-05-17
If your BIOS can be upgraded, the right thing to do is to ask at the vendor's site. You should also check the RAM memory of your laptop --you'll need at least 250Mb to run Ubuntu (and then Xubuntu would be a better choice, it is lighter)
You could also try WUBI:
[http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
No CD is needed because Ubuntu gets installed from within Windows. As this is your second laptop you could try it without risks.

Good luck

---

### Post by Pollywoggy on 2007-05-17
Try the alternate install CD and if that does not work, you might want to try Debian.
I have gotten Debian to install on older laptops that would not install other Linuxes.

---

### Post by SusieK on 2007-05-18
Thank you all for your suggestions. I'll work my way through them.

I've started with Wubi which sounds the easiest, being the wuzzock that I am.  It is going to take nearly 8 hours to download and install the files - is that normal? We do have a broadband connection, but it's not very fast.

Also, after checking the RAM, I find that the person who was meant to be fixing a minor problem with the old notebook has helped themselves to the 512K it had, and now there is only 125K. Will Wubi work with that, or should I abort the download?

---

### Post by ugm6hr on 2007-05-18
Presumably it's 128MB RAM you're left with after the theft (sorry to hear about it).  In that case, I think you will struggle with any version of Ubuntu (Xubuntu included - which I use on my brand new Acer Aspire laptop).  I think it is possible to install it, but you have to do it with the "Alternate CD" via a text entry system (like a frsh Windows install).  The unfortunate issue with that is that there is no way to check for hardware issues (which are common with laptops).  In theory, the Xubuntu Live CD will run, but you won't be able to install it - so it will probably be quicker to just use the Alternate CD.

If you want to try:
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

If you want to an alternative Linux Live CD on an old laptop - I recommend PuppyLinux.  It's not quite as easy to use as Xubuntu, but runs better on hold hardware, and will definitely load and install from it's LiveCD.  It doesn't look that pretty (as standard), and it's not as easy as Windows to install, but compared to other Live CDs - it does come with easy setup for wireless networking and hardware setup, which is a major problem for lots of Linux versions.  Unfortunately, that won't help with trying Ubuntu/Xubuntu on the old laptop prior to installing on the new laptop.

---

### Post by SusieK on 2007-05-18
Oh dear, it sounds as if it is going to be too problematical to install onto the old laptop, so I'll wait until my projects are safely in the bag, and then see if I have more luck with the newer Acer laptop. Can't find any reference to my model (Aspire 3610) in any of the listed Acers.

Thank you to everybody for your advice, which is greatly appreciated.

---

### Post by Delkster on 2007-05-18
> **SusieK said:**
> Oh dear, it sounds as if it is going to be too problematical to install onto the old laptop, so I'll wait until my projects are safely in the bag, and then see if I have more luck with the newer Acer laptop.

The beauty of the Live CD is that you can try running the operating system directly from it without altering anything on your hard drive, and you should be able to see if it works with your hardware. Try booting from the Live CD on the Acer laptop -- it can't do any harm since it doesn't change anything in your hard disk. Try and see if you can get the network connection, sound and other such things working, and if everything hardware-related seems to work, you can go on with the installer if you like.

If you have enough disk space, you don't even need to get rid of Windows -- you can keep the two side-by-side and every time you start the computer you'll be able to choose which one you want to run ("dual-boot"). If you're at all uncomfortable with the thought, come back here and I'm sure someone can instruct you with making sure that your data (and the Windows system) remains safe.

---

### Post by SusieK on 2007-05-19
Having given up on the old laptop, now I'm trying to install Ubuntu onto my (relatively) new Acer laptop.

So far I've downloaded it twice, with the following results. (Each download takes 3 hours plus).

Both CDs will play the demo, but when I try to boot from them they bring up a string of errors. One of them, when I checked the contents, said there was something missing, so I binned it. The other said there were no errors, but still when I try to boot from it it stops, saying something is missing, probably due to the download stalling.

So then I downloaded WUBI. (Three hours plus). When I installed it, it went through the process of downloading Ubuntu (another three hours plus). When I tried to run it, it went just so far and then generated a whole load of error messages.

The first one said: "An error occurred and the network configuration process has been aborted. You may try it from the installation main menu."

Then came Debootstrap warning: 
file cdrom/pool/main/n/ncurses/libncurses5_5.5-5ubuntu2_i386 deb was corrupt.

There were a whole stream of other messages following on.

I'm quite frustrated, particularly as WUBI did promise that it was a very straightforward process. :confused:

---

### Post by seshomaru samma on 2007-05-19
> **SusieK said:**
> 

Both CDs will play the demo, but when I try to boot from them they bring up a string of errors. One of them, when I checked the contents, said there was something missing, so I binned it. The other said there were no errors, but still when I try to boot from it it stops, saying something is missing, probably due to the download stalling.

d:

it's important to know what was that something that was missing
when you burn a linux iso you should first check the md5sum - (detailed[ instructions here]("http://www.psychocats.net/ubuntu/iso"))
sometimes a liveCD wont boot because of a graphic card which is not supported 
which graphic card are you using? (in windows right click on 'my computer' choose 'properties' and look for the 'device manager' or whatever they call it...should have info about your hardware there)

---

### Post by xpod on 2007-05-19
Sorry to hear your having sooo many problems SusieK:(

I dont know about wubi but have you tried burning the *buntu iso`s at the slowest speed possible??
There should be a "check cd for defects" option on any live cd`s that actually  boot as far as the start screen.You can also check the md5sums before hand although this is something i`ve never done myself....or had to do come to that and i`ve downloaded more iso`s than i can even remember this last 8 months:)

You could also consider a much lighter distro for you 128mb laptop such as dsl or puppy linux.
I currently have puppy  on my slave drive and it would be great for your older machine me thinks.A bit different to the "Ubuntu way" but i doubt that would be an issue seeing as your new to it all full stop.

Good luck either way.

---

### Post by SusieK on 2007-05-19
Thanks to you both. 

As I have spent over 15 hours out of the last 36 downloading, :(, and ended up with three CDs which don't work, I have bitten the bullet and paid for one to be sent to me by an official dealer. Fingers crossed that I'll have more luck with that. I have noticed that when downloading, the speed becomes slower and slower and sometimes the download stops for several minutes, so maybe that is causing the CD's not to work?

I couldn't find which graphic card is in the computer. Found the list of devices, but I don't know where the graphic card would be. :redface::redface:

Now moving back to the old notebook, I have downloaded the puppy Linux and will have a go with that.

---

### Post by SusieK on 2007-05-19
When burning the iso image to CD, using InfraRecorder,  when the burn begins there is a warning message that says: Controller returns wrong page 3 for Ricoh Vendor Page (30). Then the burn continues.

Does anybody know what is the significance of that message, please?

---

### Post by SusieK on 2007-05-19
> **xpod said:**
> 
You could also consider a much lighter distro for you 128mb laptop such as dsl or puppy linux.
I currently have puppy  on my slave drive and it would be great for your older machine me thinks.
Good luck either way.

That's great - Puppy is now installed on the old machine, and up and runnng, although in a slightly hysterical way, as young puppies do. I can see that once I have set it up properly, it is going to help me to learn my way around Linux, so I'm very grateful for the advice. :)

---

### Post by hyper_ch on 2007-05-19
Well, glad to hear, that at least  something works now :) good luck with the rest...

---

### Post by SusieK on 2007-05-19
Thank you. To see that I can actually get something to work is very encouraging, and spurs me on to further achievements !:lolflag:

---

### Post by SusieK on 2007-05-23
Today I received the Ubuntu disk that I bought from a company in the UK. It is version 7.04.

I put it into the CD player, and rebooted. After selecting "Ubuntu", it brings up a couple of lines of text, then says "Error 17: file not found". I've tried twice, same result each time.

Is it likely to install, if I try that, or is there something inherently wrong with my machine? It's a Acer Aspire laptop just over a year old.

Grrrr.

---

### Post by Chadzero on 2007-05-23
sorry

---

### Post by lluisanunez on 2007-05-23
I once bought a copy of Fedora Core from a French company called linuxcd.org. The CD had errors, then I wrote to them and they sent me a new CD.
You are having bad luck, Susiek...! I have a spare (working) Canonical Ubuntu Feisty CD I could send to you, if you'd PM me your address

---

### Post by SusieK on 2007-05-23
Thank you, Lluisanunez

I have PM'd you.

---

### Post by lluisanunez on 2007-05-24
Hello,
I meant to write to you (but today was a frantic day at work), because later I googled the error message number and I found that "error 17" it's an error GRUB gives when not finding the disk. So, the CD is okay and the problem is related to the BIOS configuration of your disk. I'm not proficient enough on such matters so I hope this post will bump the problem up again for someone to help. There must be a solution for a laptop one year old.

Good luck,

---

### Post by Delkster on 2007-05-24
Either that, or a problem with the hard disk controller or something. Either way, sounds like a traditional hardware compatibility issue.

On the other hand, quick googling would seem to reveal that people actually use Linux on that laptop. I'll try to dig a bit deeper if I can get some time in the coming days -- right now I can't.

I'm sorry to hear about such problems. Unfortunately that sometimes happens, particularly with some very new hardware, or some devices whose manufacturers aren't interested in supporting Linux. I'm not sure if this is one of those two cases, or if it's just a slightly exotic bug you've happened to hit.

I'd suggest you take a couple of deep breaths and stop banging you head into the wall for a few days now unless you really feel like digging deeper into the matter. Keep checking back here because someone may find a solution to the problem but if I were you, until then, or until you happen to find something yourself by googling or something, for now I'd probably just use whatever you've been using (and of course getting familiar with the Puppy you just got working ;-)).

---

### Post by SusieK on 2007-05-25
Good news at last! Yesterday I tried once again to download and use the Wubi installer, after many previous attempts had failed. This time it worked, and Ubuntu is finally installed.

I had read up on "Error 17" and the recommended cures were beyond my very limited capabilities. So I thought that I'd just keep on trying Wubi until it worked the way it said it should. Maybe the previous failures had installed or changed something in the computer which was causing the difficulties, and it eventually sorted itself out.

The wireless connection doesn't seem to work yet, but I will have a go at that later.

Thank you all for your help. 

Susie

---

### Post by lluisanunez on 2007-05-25
Congrats!
And don't say again that your capabilities are limited! You should be proud of yourself :guitar:

PS. Edit your thread and add "Solved" to the subject

---

### Post by hyper_ch on 2007-05-25
actually having limited capabilities makes it simpler to start... you know, the more you know about windows the harder it is to adjust to something totally different... you keep asking "why isn't this done the same way like in windows" :)

Just don't give up and if you have problems then ask :)

---

### Post by SusieK on 2007-05-25
> **lluisanunez said:**
> Congrats!
And don't say again that your capabilities are limited! You should be proud of yourself :guitar:

PS. Edit your thread and add "Solved" to the subject

Thanks! 

Couldn't find out how to edit title of thread, though. :(

Have a nice weekend.

---

