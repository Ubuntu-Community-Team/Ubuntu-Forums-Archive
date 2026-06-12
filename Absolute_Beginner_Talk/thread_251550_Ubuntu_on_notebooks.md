---
title: "Ubuntu on notebooks"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-09-05
Are there any laptops that are highly compatible with Ubuntu?

---

### Post by bluefrog on 2006-09-05
google for laptop linux.
you should find a page where ppl put their review (more or less accurate) of their experience.

james

---

### Post by annda on 2006-09-05
probably a zillion posts with laptop etc. - here's the only one i can find really quickly:

[http://www.ubuntuforums.org/showthread.php?t=228641](http://www.ubuntuforums.org/showthread.php?t=228641)

---

### Post by aysiu on 2006-09-05
[http://www.system76.com](http://www.system76.com)

---

### Post by davebgimp on 2006-09-05
Here's a list of makes and models tested with Ubuntu (there's probably more out there to be found via Google) letting you know the issues if any. 

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

For what it's worth, I have a Lenovo 3000 N100 running Kubuntu and I absolutely love it.:)

---

### Post by arijarot on 2006-09-05
> **bluefrog said:**
> google for laptop linux.
you should find a page where ppl put their review (more or less accurate) of their experience.

james

are you refering to [http://tuxmobil.org/](http://tuxmobil.org/) or [http://www.linux-laptop.net/](http://www.linux-laptop.net/) or just "googling" in genereal?

---

### Post by arijarot on 2006-09-05
> **annda said:**
> probably a zillion posts with laptop etc. - here's the only one i can find really quickly:

[http://www.ubuntuforums.org/showthread.php?t=228641](http://www.ubuntuforums.org/showthread.php?t=228641)

thank, annda, i've already came across this.

---

### Post by arijarot on 2006-09-05
> **davebgimp said:**
> Here's a list of makes and models tested with Ubuntu (there's probably more out there to be found via Google) letting you know the issues if any. 

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

For what it's worth, I have a Lenovo 3000 N100 running Kubuntu and I absolutely love it.:)

Thanks, davebgimp, i hand't come across this link yet. I have been looking at  your computer...but the sound issues are a deterent.

---

### Post by arijarot on 2006-09-05
What i'm looking for is a notebook that is known to be compatible with Dapper  (e.g., hibernate, sleep works, wifi works...) ... i don't have a model in mind and that is why the links to see if a particular model works is not helpful yet... and it would take a long time to go through all...

---

### Post by bobmorris on 2006-09-05
System76.com is an Ubuntu affliate and sells laptops with Ubuntu installed. Their prices are quite reasonable.

---

### Post by aysiu on 2006-09-05
Please look at post #4 of this thread. Those laptops are preloaded with Ubuntu and guaranteed to work.

---

### Post by arijarot on 2006-09-05
> **aysiu said:**
> Please look at post #4 of this thread. Those laptops are preloaded with Ubuntu and guaranteed to work.

Does anyone have a system76 laptop?

What about Dapper on any other notebook?

---

### Post by Paul133 on 2006-09-05
Well, I've got a cheapo Dell (an Inspiron 1200). It's about a year old and it's bottom-of-the-line. 1.4 Ghz processor, 256 MB shared RAM (Intel integrated graphics), and it has a Dell 1350 PCMCIA card (Broadcom 4306 chipset). I was a complete newb to Linux, though somewhat of a Windows power user. The LiveCD didn't work because my computer was so slow. Neither did the text install (it kept hanging after the partitioning). However, once I did a server install and apt-get install ubuntu-desktop things worked perfectly. It didn't recognize my wireless card, but I used an ndiswrapper tutorial with network-manager and now it works perfectly unless there's a power outage and my router loses power but otherwise the wireless works fine, even with WEP.

---

### Post by arijarot on 2006-09-05
Is there a specific model or something which is popular or reputed to work well with Dapper (e.g., an IBM, Dell, Toshiba,...)?

---

### Post by disciple on 2006-09-05
thinkpads are reputedly pretty popular with developers;as such they are very well supported  ( as evidenced by the Thinkpad power module in kde and  thinkwiki, the linux on thinkpad wiki)

personally, i like the T series..


at this point in linux, the majority of notebooks work well, in my opinion..  sure there are some quirks sometimes.. but i;ve found it helpful to just look at two things.. 

wireless  and graphics

nvidia writes much better drivers for linux, so i'd look at something with an nvidia card, and intel's wireless drivers are open sourced, so it's recognized out of the box by dapper.  (though my current notebook uses a broadcom chipset via ndiswrapper)

there isn't one specific model that someone can recommend off the bat.
if you want a machine that you don't have to configure, as others said, try system 76, for a preconfigured machine

else,
identify a notebook you like, check here on the forums for any instance of the model , or perhaps its main components ( card reader, wireless or graphics)

acpi is a bit tricky however...case in point, hibernate with dapper on my presario v2000 didnt work, but works like a charm on SuSE 10.1

---

### Post by arijarot on 2006-09-05
yeah, I noticed that the thinkpads are popular... this is going to be a noob question... but is there a reason why so many thinkpads still have the m chip? why do people use the m chips on thinkpads to compare to other computers that have core duo's (with the same ghz)? 

is suse better than ubuntu for laptops?

---

### Post by Frank Golden on 2006-09-05
> **arijarot said:**
> Is there a specific model or something which is popular or reputed to work well with Dapper (e.g., an IBM, Dell, Toshiba,...)?
Hello Arijarot,
  I have Ubuntu 6.06 LTS installed on an Acer Aspire 5672WLMi
and almost everything works out of box with Ubuntu.
I did have to change to the 686smp kernel after install using
Synaptic installer to get the most out of my Core Duo processor. 
My computer uses the ATi radeon mobility x1400 video processor,
the ATi drivers for it are proprietary (closed source) so they
can't be included on the install CD. I had to manually install
them after I got Ubuntu up and running. The ATi Linux wiki makes this fairly easy. Without the ATi drivers get a reduced resolution experience and no hardware 3-D acceleration. But it is usable.
As far as I can see everything else but the built in Texas
Instruments 5 in 1 card reader and the builtin Logitech web cam
works on this machine right out of the box so to speak. Excelent machine, can be had for around 
$1000.00 US today.
I have a HP printer which I set up in less than a minute and Ubuntu detected my Creative USB external sound card.
Read this thread from UbuntuForums-LaptopSupport section about the 5672. It starts near the first of the year when his machine
first appeared on the scene. 
[http://ubuntuforums.org/showthread.php?t=121125](http://ubuntuforums.org/showthread.php?t=121125)
Back then Ubuntu Dapper was far from ready for prime time.
If you read through the thread it seems almost as if 
Dapper was developed for this machine. They seem to be made 
for one another. My experience started with the fourth or
fifth beta version of Dapper eventually leading to what I have now.

You will still have to add the usual restricted codecs
and stuff to play DVD movies and stuff. You would anyway 
regardless of you notebook. Again to include them on the install
cd would probably violate the GPL agreement. Or be against some law or something.

---

### Post by arijarot on 2006-09-05
Frank, does your hibernate/sleep work?

---

### Post by aysiu on 2006-09-05
> **arijarot said:**
> Does anyone have a system76 laptop? Actually, a few people do. [Fuscia started a thread about his](http://ubuntuforums.org/showthread.php?t=191984). [New Linux has one, too](http://ubuntuforums.org/showthread.php?t=215690).
Also, [a random review from someone's blog](http://demian0311.blogspot.com/2006/04/review-of-system76.html).

System76 even has [its own support subforum on the Ubuntu Forums](http://ubuntuforums.org/forumdisplay.php?f=158)

And the guy who runs System76 (Carl Richell) is a member here: username *crichell*.

---

### Post by arijarot on 2006-09-05
Cool, thanks for the info, aysiu :)

---

### Post by jimrz on 2006-09-05
> **arijarot said:**
> yeah, I noticed that the thinkpads are popular... this is going to be a noob question... but is there a reason why so many thinkpads still have the m chip? why do people use the m chips on thinkpads to compare to other computers that have core duo's (with the same ghz)? 

is suse better than ubuntu for laptops?

My T42 works great with Ubuntu. It does has an m chip, but it is several years old. Levovo have just begun selling the T60p ( core duo) with SLED10 preinstalled and supported, so I would think that that model should work pretty well too. If you do not need dual boot. System 76 appear to have very nice equipment at reasonable prices + all comments I have seen about them here have been positive.

---

### Post by arijarot on 2006-09-05
after mention of the thinkpad, i was wondering, which works better with ubuntu the t43 or t60 ? does anyone have any experiences with theese that they would like to share?

---

### Post by aysiu on 2006-09-05
> **arijarot said:**
> Cool, thanks for the info, aysiu :)
No problem. Forgot to mention that [Ubuntu Forum members get a $25 discount off System76 laptops.](http://ubuntuforums.org/showthread.php?t=231459) Doesn't sound like much, but it's something.

---

### Post by arijarot on 2006-09-05
> **jimrz said:**
> My T42 works great with Ubuntu. It does has an m chip, but it is several years old. Levovo have just begun selling the T60p ( core duo) with SLED10 preinstalled and supported, so I would think that that model should work pretty well too. If you do not need dual boot. System 76 appear to have very nice equipment at reasonable prices + all comments I have seen about them here have been positive.

Cool,jimrz,thanks.
 specifically, does your system resume from sleep/hibernate? have good wireless connectivity? have you had any speaker issues?

---

### Post by arijarot on 2006-09-05
> **aysiu said:**
> No problem. Forgot to mention that [Ubuntu Forum members get a $25 discount off System76 laptops.](http://ubuntuforums.org/showthread.php?t=231459) Doesn't sound like much, but it's something.

lol :)  i'm a student, so it sounds like a lot to me!

---

### Post by Frank Golden on 2006-09-05
> **arijarot said:**
> Frank, does your hibernate/sleep work?
I don't know. I don't use these features/bugs.

Update: Just enabled both hibernate and suspend.
Suspend appears to work hibernate doesn't. As I said earlier I consider
these features to be thinly disguised bugs. I have no use for them. If their not working is a deal killer, Oh well.:D

---

### Post by davebgimp on 2006-09-06
> **arijarot said:**
> Thanks, davebgimp, i hand't come across this link yet. I have been looking at  your computer...but the sound issues are a deterent.

Perhaps that page is not updated. My Lenovo has great sound. I have zero issues (that I know of).

---

### Post by GreenHawkIA on 2006-09-06
I have a Dell Latitude D505 and it works great.  All the hotkeys and the Intel Pro Wireless 2200 b/g worked out of the box (even the WPA2 PEAP authentication my university uses with Network Manager installed).  Suspend and resume both work - but there is one bug - the wireless card is not recognized when returning from suspend/resume.  I have heard this is pretty common, though.  But people get jealous of my laptop all the time, especially my girlfriend, because it just works with the university's wireless.

---

### Post by arijarot on 2006-09-06
> **davebgimp said:**
> Perhaps that page is not updated. My Lenovo has great sound. I have zero issues (that I know of).

Thanks for sharing, Dave...what are the specs on your machine?

---

### Post by arijarot on 2006-09-06
> **GreenHawkIA said:**
> I have a Dell Latitude D505 and it works great.  All the hotkeys and the Intel Pro Wireless 2200 b/g worked out of the box (even the WPA2 PEAP authentication my university uses with Network Manager installed).  Suspend and resume both work - but there is one bug - the wireless card is not recognized when returning from suspend/resume.  I have heard this is pretty common, though.  But people get jealous of my laptop all the time, especially my girlfriend, because it just works with the university's wireless.

That sounds great, GreenHawkIA. so you haven't had any issues with ubuntu corrupting the bios...some ppl on the forum reported this and said that it was a confirmed bug with dells...

---

### Post by davebgimp on 2006-09-06
> **arijarot said:**
> Thanks for sharing, Dave...what are the specs on your machine?

Intel Duo Core Processor T2500 (2GHz)
1 gig ram
128MB NVIDIA GeForce Go 7300
15.4" screen 1680x1050
Intel PRO/Wireless 3945ABG, Bluetooth
100 gig drive
DVD R/W
Fingerprint reader (it's usable with a little work, but I've no need of it)

When I first got it, the screen was defective, but Lenovo fixed it right away and since then it's been great. Originally, yes, there was a problem with sound, but that was a good while ago. The sound is great on the machine. The only thing is that the speakers do not automatically mute for headphones, but that's easily done manually from the KDE or Gnome GUI and I expect it will be fixed eventually.

---

### Post by arijarot on 2006-09-06
so you mute the internal speaker manually and the headphones work without the internal speakers being on too?

---

### Post by davebgimp on 2006-09-06
> **arijarot said:**
> so you mute the internal speaker manually and the headphones work without the internal speakers being on too?

Yup, exactly. Not really a big deal.

---

### Post by arijarot on 2006-09-06
i'm interested in the dell 6400 / e1505 VS lenovo 3000 n100

i'm also interested in the ibm thinkpad t60 or t43 VS the dell 640m / e1405

does anyone have any opinions, comments, suggestions, experiences...?

---

### Post by arijarot on 2006-09-06
> **davebgimp said:**
> Yup, exactly. Not really a big deal.

cool...and you don't find the sound to be bad like some report then?

---

### Post by davebgimp on 2006-09-06
> **arijarot said:**
> cool...and you don't find the sound to be bad like some report then?

Well, I never really use the internal speakers for anything. The sound out of them isn't stellar, but it's laptop speakers so I don't expect much. It sounds okay to me though. I'm usually always using headphones or external speakers to blast stuff anyway.

---

### Post by arijarot on 2006-09-06
> **davebgimp said:**
> Well, I never really use the internal speakers for anything. The sound out of them isn't stellar, but it's laptop speakers so I don't expect much. It sounds okay to me though. I'm usually always using headphones or external speakers to blast stuff anyway.

that's what i was wondering about, since i want to hook up my speakers/headphones...great! thanks, dave :)

---

### Post by caricc on 2006-09-06
I have a compaq presario v2000 laptop with the broadcom 4306 wireless chipset. At first I loaded with Breezy then upgraded to 6.06. When I upgraded I actually had to go and get the version 4 of the Broadcom drivers to get my wireless to work. Now it works GREAT.

---

### Post by disciple on 2006-09-07
i'd go with the t60 or t43..
(leaning more to the t60)

thinkpads are generally well made; as opposed to the flimsy construction i've seen in almost every other manufacturer..

but this comes at a premium price ..


for a bargain notebook, i like the presario v2000 series ( okay, perhaps becuase i've got one)
it's fairly well supported, and has a basic, though attractive design, imho..
if you do purchase it, however, look into gettin the larger battery; protrudes slightly from the bottom, but the extra juice brings it to 5 hrs, i think..

---

### Post by elemental666 on 2006-09-07
[Sager Notebooks]("http://sagernotebooks.com") available at discounted prices from [PC Torque]("http://pctorque.com").  You might not have heard of them but that doesn't mean that don't rock! Best bang for the buck I've found... for years.

---

### Post by Leeghoofd on 2006-09-07
I've had Ubuntu running on two company laptops for several months.

We use Dell latitude laptops. I've had Ubuntu running without any problems on the ( old ) c610 series and and the ( somewhat newer ) D610. So no hardware problems were encountered.

:)

---

### Post by Corvillus on 2006-09-07
Gateway MX3558 here. Wireless, video and suspend/hibernate work out of the box. Compiz/AIGLX runs well on here as well.

---

