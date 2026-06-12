---
title: "AMD or Nvidia Graphics Card for Linux?"
date: 2012-08-18
forum: Any Other OS
---

### Post by JonasDeMoor on 2012-08-18
Hi,


In the future (probably a few months), I am planning to build a PC myself. I have already chosen all hardware, but not the video card.

I am currently running Linux Mint Debian Edition 64-bit on a Acer laptop with ATI Radeon HD 3650 graphics and the proprietary drivers don't work well (lag when dragging windows/scrolling).


So here's my question: which brand of video card should I chose: Nvidia or AMD?

[I][U]Current System Specs
[/U][/I]
[LIST]
[*]CPU: Intel Core 2 Duo @ 2.00 GHz
[*]GPU: ATI Radeon Graphics 512 MB
[*]Model PC: Acer Aspire 8920G
[/LIST]
PC is now about 4-5 years old.
--------------------------------------------------------------------------------------------------------------------------------
_*Future System Specs*_

[LIST]
[*]CPU: Intel Core i5/ AMD "Bulldozer" (8 cores)
[*]GPU: ?
[/LIST]




Thank you in advance :)

---

### Post by TenPlus1 on 2012-08-18
I'd recommend Nvidia all the time with Ubuntu and linux in general, not only because they are faster, but because the binary driver doesn't cause as much trouble as the ati one...

---

### Post by QIII on 2012-08-18
Umm...

Take a look at the NVIDIA problems on the forum.  There are plenty.   There are plenty of posts about NVIDIA driver issues, just as there are plenty of posts about ATI driver problems.

Faster in what way?  NVIDIA and ATI trade spots on "fastest" each time one or the other comes out with a new product.  Running tests on a number of different tasks and games, ATI wins in some cases, NVIDIA in others.

The advantage of NVIDIA is a richer set of hardware acceleration under Linux, but ATI does have Linux hardware acceleration.   

They both produce good products and they both have their fair share of problems.  If you want anything other than brand loyalty flame wars, I would suggest picking out a few of each that look interesting and go to Phoronix or another impartial site for reviews and performance comparisons.  Find one that suits your needs in your price range and don't pay any attention to whether it's red or green.

As for the processor, the same goes.  Read up on each.  Read *impartial *reviews and technical explanations.  Are you going for pure performance?  Price/performace?  Single threading?  Multi threading?  Will the applications you are likely to use take advantage of one better than the other?  Gaming (in which case the GPU is probably more important)?  Surfing?  Word processing?

Everyone has opinions and they are entitled to them.  Opinions are legitimate.  But that is generally what you get on forums.  And the opinion of one person does not necessarily apply to your case.

AMD/ATI versus NVIDIA.  Intel versus AMD.  It all depends on what YOU need, not what someone else opines.

---

### Post by indianya on 2012-08-18
AMD based on my experience.

---

### Post by Perfect Storm on 2012-08-18
Moved to Other OS/Distro Talk.

---

### Post by darkapec on 2012-08-19
I have had better luck with AMD also, but any "older" card will work fine on ubuntu eg 9800gt or similar. 

I assume you are not trying to game? As there are not to many high performance games for ubuntu. If you are just looking for something to give you smooth video playback etc then I would go with a legacy type card (amd 4000 series) or (Nvidia 9000 series). Those generations of cards will have more then adequate support especially the Nvidia 9000 series. It will also handle most games and 1080p video.

---

### Post by walker195 on 2012-08-19
AMD is mostly better but my nvidia graphics work great and in high def perfectly

---

### Post by doorknob60 on 2012-08-19
Nvidia, I have both, and Nvidia has never given me any headaches. I still have some minor problems with AMD such as Wine not working very well, and they don't update their drivers as often so sometimes new kernels or Xorg versions can break the drivers, while Nvidia usually keeps up to date with those (but that's more a problem with rolling distros like Arch, it shouldn't be a problem with Ubuntu). As for open drivers, AMD has better ones, but for me Catalyst is still far better than the open drivers in my experiences, both in performance and heating/power saving. Overall, they both usually work pretty well, but I have nothing but good things to say about Nvidia's desktop GPUs.

---

### Post by drawkcab on 2012-08-19
If you're playing back x264 encoded .mkv files then I've found nvidia is better because you can enable vdpau.

Otherwise ati seems to work fine.

Research the current state of hybrid graphics cards before you buy one of those.  Last I heard they're not supported well but I could be wrong.

---

### Post by JonasDeMoor on 2012-08-19
thank you all for the fast replies. I will probably go for a Intel core i5 with nvidia geforce gtx 550ti.

I will certainly go to phoronix and look at some reviews :)

---

### Post by ratcheer on 2012-08-19
I have used both nVidia and ATI cards with Linux. I've had about the same number and pretty much the same types of problems with both. Right now, I'm using a fairly recent ATI card with very good results using the ATI proprietary driver.

My one big problem is that I cannot install the proprietary driver in Siduction Linux. All my other distros (Ubuntu, Arch Linux, and Sabayon Linux) install it just fine.

My problem with the FOSS driver is that it makes my video card run too hot, about 15-20 C hotter than fglrx.

So, I have no bottom line answer. The two brands are about as good and about as bad as each other.

Tim

---

### Post by buzzingrobot on 2012-08-19
I had a nice AMD card but moved to an Nvidia card, primarily because it was much quieter. Linux code often does not offer the same fine-tuned fan control that proprietary drivers do.

If you are not a gamer, it's likely that nothing you do will ever challenge any contemporary video card.

Buy something that's about two years old and you should be fine with any Linux flavor.

---

### Post by kurt18947 on 2012-08-19
I abide by a rule to never install bleeding edge hardware for Linux, regardless of brand.  A model that's been in circulation for a year or so is less likely to cause grief.  And if it does cause problems, there is likely a proven solution available.  I'm not a gamer but have 2 Nvidia cards, 8400GS w/ 512 RAM and GeForce 210 w/ 1 gig. RAM.  Both Nvidia cards are on AMD/Gigabyte Motherboards.   Smooth sailing with both.

---

### Post by JonasDeMoor on 2012-08-20
> **ratcheer said:**
> I have used both nVidia and ATI cards with Linux. I've had about the same number and pretty much the same types of problems with both. Right now, I'm using a fairly recent ATI card with very good results using the ATI proprietary driver.

My one big problem is that I cannot install the proprietary driver in Siduction Linux. All my other distros (Ubuntu, Arch Linux, and Sabayon Linux) install it just fine.

My problem with the FOSS driver is that it makes my video card run too hot, about 15-20 C hotter than fglrx.

So, I have no bottom line answer. The two brands are about as good and about as bad as each other.

Tim

That's also the reason why I try to use the proprietary drivers: my laptop becomes too hot.

---

### Post by ratcheer on 2012-08-20
> **JonasDeMoor said:**
> That's also the reason why I try to use the proprietary drivers: my laptop becomes too hot.

My Arch Linux installation is up to Catalyst version 12.8. It is running even cooler than 12.6 and earlier.

Tim

---

### Post by ClementL on 2012-11-08
Maybe this is a bit late, but I wanna add this for everyone that stumbles on this thread though a search machine.


I´m using an ATI XFX 4770. This card is about 3.5 years old by now. Currently using Linux Mint Maya x86_64, but I´ve used Ubuntu 12.04 and Arch Linux too. And let me tell you something: the main reason I´m not yet fully switching to Linux is because of the horrible video drivers.

Not matter what I do, there are graphical glitches everywhere. The only time I was able to enable OpenGL acceleration for a DE was on Arch with KDE. And it worked awful, breaking half the desktop. Now I´m using Mint my CPU usage skyrockets from just moving a window.

So my experience with AMD Linux drivers isn´t exactly positive.

---

### Post by dannyboy79 on 2012-11-08
i always go Nvidia. Especially since they just released the newest version which supposedly doubles performance for gaming on the most recent cards out there.
[http://www.geek.com/articles/games/torvalds-rant-against-nvidia-works-new-linux-drivers-double-gaming-performance-2012117/](http://www.geek.com/articles/games/torvalds-rant-against-nvidia-works-new-linux-drivers-double-gaming-performance-2012117/)

---

### Post by JonasDeMoor on 2012-11-09
> **ClementL said:**
> Maybe this is a bit late, but I wanna add this for everyone that stumbles on this thread though a search machine.


I´m using an ATI XFX 4770. This card is about 3.5 years old by now. Currently using Linux Mint Maya x86_64, but I´ve used Ubuntu 12.04 and Arch Linux too. And let me tell you something: the main reason I´m not yet fully switching to Linux is because of the horrible video drivers.

Not matter what I do, there are graphical glitches everywhere. The only time I was able to enable OpenGL acceleration for a DE was on Arch with KDE. And it worked awful, breaking half the desktop. Now I´m using Mint my CPU usage skyrockets from just moving a window.

So my experience with AMD Linux drivers isn´t exactly positive.

Hi,

Thanks for the reply. I'm now using the open-source driver ('radeon') with Linux Mint Maya  (13) XFCE 64-bits with my HD 3650 and it's running great, except that the laptop becomes warm sometimes. 

Off-topic: Aren't you Clement Lefebvre from Linux Mint, by any chance? :-)

---

### Post by JonasDeMoor on 2012-11-09
> **dannyboy79 said:**
> i always go Nvidia. Especially since they just released the newest version which supposedly doubles performance for gaming on the most recent cards out there.
[http://www.geek.com/articles/games/torvalds-rant-against-nvidia-works-new-linux-drivers-double-gaming-performance-2012117/](http://www.geek.com/articles/games/torvalds-rant-against-nvidia-works-new-linux-drivers-double-gaming-performance-2012117/)

Yes, I've just read this too on OMG! Ubuntu: this means a huge step forward for gaming AND Linux :)

---

