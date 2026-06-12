---
title: "questions on macbookpro 6,2: temp sensors, nvidia display, boot errors"
date: 2010-12-21
forum: Apple Hardware Users
---

### Post by Alejandro Castanaza on 2010-12-21
Hi.

I have recently installed Ubuntu Maverick 10.10 in my macbookpro 6,2 (15 inch i5). (OS X is ok, but I like Ubuntu very much, besides, being used to Ubuntu, I found some OS X peculiarities very annoying).

It works ok, I followed the instructions in the mactel support wiki for mbp 6,2 maverick.

But, there are some things I'm still in doubt:
1-When I installed the packages for the apple sensors from the mactel support team, the install asked if the hard drive temperature sensor should run as a daemon or not, it sugested: "in doubt, select no", so i selected the option to not run as a daemon. The wiki did not specify anything about this.  Should hddtemp be run as a daemon? what is the recommended setting?

2-The laptop becomes hotter than when using OS X, and macfanctld is installed as told in the wiki. Is there anything else that can be done about it?

3- I have the nvidia driver running as recommended, but the plymouth splash becomes very ugly (a known issue since lucid). There is a "fix" for this, also very known: install v86d, and add some settings in /etc/grub and other files. Is it ok to set this fix to the macbook pro? Or is it not recommended due to the integrated intel gpu?

4- When booting, the system outputs some error messages:
    could not load /lib/modules/2.6.35-23-generic/modules.dep: No such file or directory
    could not load /lib/modules/2.6.35-23-generic/modules.dep: No such file or directory
    intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
    intel ips 0000:00:1f.6: request irq failed, aborting

is there some way to fix this errors? should be ignored?

Thanks in advance

Alejandro

---

### Post by Alejandro Castanaza on 2010-12-22
to bump this thread, I will anwer my own question number 2. I found that the macfanctl has a manual page (man macfanctl) in which the author has put useful information for tweaking the settings of cooling.
This way, I changed some of the default settings, and the laptop now runs cooler.
The other three questions, I kindly ask if someone can help me.
Thank you.

Alejandro

---

### Post by alexmurray on 2010-12-22
> **Alejandro Castanaza said:**
> 
1-When I installed the packages for the apple sensors from the mactel support team, the install asked if the hard drive temperature sensor should run as a daemon or not, it sugested: "in doubt, select no", so i selected the option to not run as a daemon. The wiki did not specify anything about this.  Should hddtemp be run as a daemon? what is the recommended setting?

If not running in daemon mode, programs like sensors-applet will not be able to use hddtemp to query the hdd temperature - however sensors-applet now has support for using udisks so you can probably safely leave this as 'No' - saying 'Yes' simply means hddtemp will run in the background and allow you to query it for temperatures over a local network socket (which is what say sensors-applet does). If you want to enable it in daemon mode, you should be able to run the following:
```
sudo dpkg-reconfigure hddtemp
```

> **Alejandro Castanaza said:**
> 
2-The laptop becomes hotter than when using OS X, and macfanctld is installed as told in the wiki. Is there anything else that can be done about it?

Sounds like you solved this already.

> **Alejandro Castanaza said:**
> 
3- I have the nvidia driver running as recommended, but the plymouth splash becomes very ugly (a known issue since lucid). There is a "fix" for this, also very known: install v86d, and add some settings in /etc/grub and other files. Is it ok to set this fix to the macbook pro? Or is it not recommended due to the integrated intel gpu?

Yes this should be fine to use this fix on the MacBook Pro - I use it on my mine (although mine is a 5,1 not 6,2).

> **Alejandro Castanaza said:**
> 
4- When booting, the system outputs some error messages:
    could not load /lib/modules/2.6.35-23-generic/modules.dep: No such file or directory
    could not load /lib/modules/2.6.35-23-generic/modules.dep: No such file or directory
    intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
    intel ips 0000:00:1f.6: request irq failed, aborting
is there some way to fix this errors? should be ignored?

The first two should be fine to ignore. The second two appear to be that the integrated intel GPU is not initializing, which is to be expected since the discrete NVIDIA GPU is the only one enabled as far as I know when booting Ubuntu so this can also safely be ignored.

---

### Post by Alejandro Castanaza on 2010-12-23
thank you for taking the time to answer all the questions.
I'll try the plymouth fix and come back if something happens. The text plymouth is uglier than the low resolution ubuntu logo that appeared in lucid.  :)

---

### Post by Alejandro Castanaza on 2010-12-23
> **alexmurray said:**
> 

Yes this should be fine to use this fix on the MacBook Pro - I use it on my mine (although mine is a 5,1 not 6,2).


Does your Macbook pro 5,1 have integrated and discrete graphics as the 6,2 has?
(just to make sure ;) )

---

### Post by alexmurray on 2010-12-25
Yes (it has an integrated NVIDIA 9400M and a discrete NVIDIA 9600M GT - you know you could just google for the specs if you want.)

---

### Post by Alejandro Castanaza on 2010-12-25
yes, sorry. In fact, I did yesterday before I applied the fix for plymouth.
Anyway I tried and it works ok. Thank you. Also, I reconfigured the hddtemp to run as a daemon and now the sensors applet shows the hdd temp. Thank you again.
By the way, although the sound works, I have noticed that when turning the computer off with ubuntu, the speakers make a short noise, but when turning off with mac os x, it turns off silently.  Is it normal?

---

### Post by Alejandro Castanaza on 2011-01-09
...bump...

I have tried muting the speakers but the noise still is there.
That small instant where the system is physically powering off (not the linux shut down) where the speakers make a very very short noise that would not bother me if it where the same with mac os x.

---

### Post by apfejes on 2011-01-23
> **Alejandro Castanaza said:**
> to bump this thread, I will anwer my own question number 2. I found that the macfanctl has a manual page (man macfanctl) in which the author has put useful information for tweaking the settings of cooling.
This way, I changed some of the default settings, and the laptop now runs cooler.

Hi Alejandro,

I'm running the same setup as you, and really appreciate your comments.  Would you be willing to share what changes you've made to the macfanctl settings?  I'm not sure what changes are worth making, and it sounds like you've already done some optimization on this problem.

Thanks!

---

### Post by ArtificialMusik on 2011-01-23
Hello Alejandro,
I have the same Macbook pro you have, (6,2 15 ((i7)) and for some crazy reason I can't get the wifi to work. What is/was your solution?

---

### Post by ld9828 on 2011-02-05
hi,

also have ubuntu running on a Macbook pro 6,2 with i7. 
how is your battery live in average? I get 4h at max.

@Alejandro Castanaza and apfejes
how did you solve the problem with getting to hot? can you give me a short introduction? would be great!

---

### Post by Alejandro Castanaza on 2011-03-18
well, the macfanctld settings are to keep an average of 45 to 55 degrees, and the cpu and gpu temperature sensors in the range of 50 to 58 degrees.
Simply editing the macfanctld.conf file to lower those vales, for instance, 5 degrees less on each of the limits, makes the daemon to raise the fans higher to try to keep the macbook cooler.
Still, the mac os x posibly makes many more things to operate more efficiently, what makes the macbook not only to run cooler, but the battery to last more. It uses the intel integrated graphics if not using too much graphics power, and turns off the nvidia gpu, which consumes more power, and I think it maybe even turns off some other components, which makes it so efficient.
If that is true, in Linux I don't think there are, yet, those optimizations, and that is why at most, we get up to 4 hours battery life, and the fans run faster and louder than in the mac os x to run just as cool.

---

### Post by Alejandro Castanaza on 2011-03-20
Hi. Well, I did not have any problems with wifi. Just installed the propietary drivers as told in the ubuntu mactel documentation. You should check in the propietary drivers if the Broadcom drivers for the wifi card are installed.

---

### Post by beaufils on 2011-06-28
Did some of you try to upgrade to 11.04 (Natty) under MacBookPro6,2 ?

I upgraded and then, for independent reasons, I was force to reinstall from scratch and get a lot of trouble with heat control. My MacbookPro6,2 is going really hot since that reinstallation (can not let it on my laps).

For instance macfanctld is not available in the ppa repository for Natty (the one of maverick did not seem to be able to control fans unless you also install apple-smc-dkms from maverick ppa), the nvidia-bl-dkms package available does not control really the LCD backlight (I had to install the mbp-nvidia-bl-dkms from maverick to control it actually) ?

Did some of you make some modifications in the xorg.conf in order to cool the NVIDIA GPU ?

---

### Post by Alejandro Castanaza on 2011-08-24
Hi, I am asking the same question. Since the natty guide says our macbookpro 6,2 is partially compatible, I have not upgraded, but the guide only guides through clean install, it does not say anything about upgrading.
If someone with experience could update the guide so it also includes information about upgrading from the previous distribution, it would be very useful.
@beaufils:
for the nvidia gpu, I think the configuration recommended in the guide so that it stays in the lower powermizer level should help keep it cool, but its most the control of the fans.

---

### Post by darkvad0r on 2011-09-05
Hi all, I thought I'd chime in since I just installed natty (64 bits) on a macbookpro 6,2 and I can confirm that almost everything works exactly like it worked on maverick.

The only thing that's still bothering me is the display backlight : nothing seems to work, display is always at ~50% brightness no matter what I do. 

On maverick I could just put the computer to sleep then wake it up and the display would be at 100% brightness, but after applying the ssd fix described in the mactel wiki, sleep doesn't work anymore so now I'm stuck at 50% brightness.

There's one thread that suggests installing mbp-nvidia-bl-dkms so I thought I'd try that and that's when I realized what was going on: none of those packages (nvidia-bl-dkms nor mbp-nvidia-bl-dkms) were available for the 64 bits architecture, neither on maverick nor on natty.

**If you're on natty or maverick 64 bits, and can't set the display brightness, you should mark yourself as affected by the following bug:**
[https://bugs.launchpad.net/mactel-support/+bug/841611](https://bugs.launchpad.net/mactel-support/+bug/841611)

If you're on natty or maverick 64 bits and you can set the display brightness, please reply to this thread and let me know how you did it, I'll be eternally grateful :)

---

### Post by Alejandro Castanaza on 2011-09-27
Well, I have maverick 64 bits and display brightness works well, I only followed the instructions in the mactel wiki and nothing more.
As for natty, did you do a clean install or upgraded from maverick?
I have read natty may corrupt the macbookpro efi firmware. Is that bug solved?

thank you

---

### Post by Alejandro Castanaza on 2011-10-18
Bump

---

### Post by darkvad0r on 2011-10-19
Thanks for your feedback Alejandro.

As for me, I managed to figure it out: I ended up having to manually install the mbp-nvidia-bl package from maverick repositories because the nvidia-bl didn't work (the notifications showed when pressing buttons but brightness didn't really changed)

Also, no firmware corruption here (I installed natty from scratch).

Hope that helps

---

### Post by Alejandro Castanaza on 2011-10-19
Thank you darkvad0r,
I just want to be sure, if someone can tell me if upgrading from Maverick to Natty 64 bits wont corrupt firmware either, it seems like Oneiric is working better with this mbp 6,2 than Natty, right?

---

### Post by darkvad0r on 2011-10-20
well, I neverd heard about that FW corruption issue and I couldn't tell you about oneiric, sorry

---

### Post by Alejandro Castanaza on 2011-10-20
it is bug #774089 in launchpad, that when installing natty the first three boot attempts failed, and only the forth or fifth boot would be successful, every time you shut down or restart. It was because of a bug in the installer or grub2, i'm not sure, that corrupted the EFI firmware in the macbookpro.
This and the inability to connect to wireless N networks have made me not to upgrade, waiting for those problems to be solved.
But Oneiric is out now, and if I want to upgrade to it, I have to still upgrade to Natty, that is why I am asking.
The other option would be to clean install Oneiric, with all the work in reconfiguring and re copying personal data it involves.
I appreciate very much your feedback, but I would like to be very sure before proceeding, if there little chance that installing or upgrading to natty or oneiric will corrupt the firmware or give more problems than with Maverick, which works fine, but it is not up to date.

---

