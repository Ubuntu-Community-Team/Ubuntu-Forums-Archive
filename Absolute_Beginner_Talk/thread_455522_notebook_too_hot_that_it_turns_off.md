---
title: "notebook too hot that it turns off"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-26
okay it started off with gnome restarting automatically.. i thought its bug within ubuntu.. i was frustrated and uninstalled ubuntu but it didnt help.. now im back using feisty.. and the restart problem didnt occur until this morning. when my notebook got too hot and it completely shutdown.. now i know its not problem caused by ubuntu.. its the fan or soemthing else that causes it.. is there anyway i can solve this problem ? as usual help is appreciated.. thanks guys

---

### Post by oilchangeguy on 2007-05-26
> **HunkieChan said:**
> okay it started off with gnome restarting automatically.. i thought its bug within ubuntu.. i was frustrated and uninstalled ubuntu but it didnt help.. now im back using feisty.. and the restart problem didnt occur until this morning. when my notebook got too hot and it completely shutdown.. now i know its not problem caused by ubuntu.. its the fan or soemthing else that causes it.. is there anyway i can solve this problem ? as usual help is appreciated.. thanks guys

sounds like you've got a dead fan. the only way to solve it is to take the computer to a shop that will work on laptops. unless of course you want to punish yourself by trying to take apart your laptop.

---

### Post by arvevans on 2007-05-26
Toshiba, and probably other, laptops use a software routine to sense the temperature and control the fan.  Your "Systems Drivers CD" that came with the laptop contains the necessary Fan Driver software.  Unfortunately, this software is usually designed to run under MS-Windoze.  As a result, when you install certain Linux, BSD, Minix, etc. operating systems you may not have the necessary software to run the fan...and things get [COLOR="Red"]**HOT**[/COLOR]!

However, there are software patches specifically for running the Toshiba laptop with a Linux OS.  Most present day distributions include the necessary "drivers", but older distro's may not.  It is also possible that you may have missed installing the necessary driver, even if it was included in the distro.

I have disposed of my last laptop (it was a personal thing relating to portability versus reliability) so cannot give specific software module names, but this information may provide some indication of what the problem might be, and what to look for to find a solution.

Arv
_._

---

### Post by oilchangeguy on 2007-05-26
> **arvevans@earthlink.net said:**
> Toshiba, and probably other, laptops use a software routine to sense the temperature and control the fan.  Your "Systems Drivers CD" that came with the laptop contains the necessary Fan Driver software.  Unfortunately, this software is usually designed to run under MS-Windoze.  As a result, when you install certain Linux, BSD, Minix, etc. operating systems you may not have the necessary software to run the fan...and things get [COLOR="Red"]**HOT**[/COLOR]!

However, there are software patches specifically for running the Toshiba laptop with a Linux OS.  Most present day distributions include the necessary "drivers", but older distro's may not.  It is also possible that you may have missed installing the necessary driver, even if it was included in the distro.

I have disposed of my last laptop (it was a personal thing relating to portability versus reliability) so cannot give specific software module names, but this information may provide some indication of what the problem might be, and what to look for to find a solution.

Arv
_._


the bios controls these functions. not a software program. also unless you enjoy spam, change your user id to something other than your email address.

---

### Post by nonewmsgs on 2007-05-26
maybe it's the email of someone he doesn't like.

yeah normally the fans turn on when the computer gets sufficently warm, however, you can solder a short to make it always on.

---

### Post by HunkieChan on 2007-05-26
well.. guys i dont know.. whats going on.. i talked to a friend and he asked me to get an external fan.. i dont know how that works.. but ill try that out..he is a comp eng..

---

### Post by bapoumba on 2007-05-26
My laptop died (well went to repairs) due to overheating. Run **acpi -V** to know the current temps (gnome has some temp applets). I got an external device, with 3 fans that pulls out warm air from under. It runs on usb (with 4 extra usb ports on a hub). It lowers the temp by 20°C ^^

---

### Post by HunkieChan on 2007-05-26
Battery 1: charged, 27%
     Thermal 1: ok, 64.0 degrees C
     Thermal 2: ok, 66.0 degrees C
  AC Adapter 1: on-line

---

### Post by HunkieChan on 2007-05-26
> **bapoumba said:**
> My laptop died (well went to repairs) due to overheating. Run **acpi -V** to know the current temps (gnome has some temp applets). I got an external device, with 3 fans that pulls out warm air from under. It runs on usb (with 4 extra usb ports on a hub). It lowers the temp by 20°C ^^

okay bro..where can i get that whateever you just said. its get freaken hot.. im scared :"(

---

### Post by bapoumba on 2007-05-26
> **HunkieChan said:**
> okay bro..where can i get that whateever you just said. its get freaken hot.. im scared :"(
(make it sis' BTW ;))
I just went to a general computer store. It was under €25.

For my own laptop, they found a problem with the CPU. I do not know whether it was a cause or a consequence of the overheating. No one would explain it to me... And it was under warranty, so I did not open it for a cleaning.

When it "died", it was upon feisty fresh install. It hit 86°C ... And shut off in the middle of it. It had been happening for some time before, with anything that would require some resources.
I did another install, in text mode (that went through), so that the techs could run the tests with windows.
They were nice actually, they pulled out my DD to put on one of theirs to run the tests, so they did not wipe out anything.

Sorry I cannot help you more. Is it still under warranty ? If not, you could open it and see if anything is clogging the fans.

---

### Post by madmetal on 2007-05-26
maybe if its intel processor the powertop tool helps..
i installed it today on my laptop and its a little cooler.. (gutsy + powertop)

---

### Post by HunkieChan on 2007-05-26
> **madmetal said:**
> maybe if its intel processor the powertop tool helps..
i installed it today on my laptop and its a little cooler.. (gutsy + powertop)

mine is amd mobile.. you think it would work on that ?

---

### Post by HunkieChan on 2007-05-26
> **bapoumba said:**
> (make it sis' BTW ;))
I just went to a general computer store. It was under €25.

For my own laptop, they found a problem with the CPU. I do not know whether it was a cause or a consequence of the overheating. No one would explain it to me... And it was under warranty, so I did not open it for a cleaning.

When it "died", it was upon feisty fresh install. It hit 86°C ... And shut off in the middle of it. It had been happening for some time before, with anything that would require some resources.
I did another install, in text mode (that went through), so that the techs could run the tests with windows.
They were nice actually, they pulled out my DD to put on one of theirs to run the tests, so they did not wipe out anything.

Sorry I cannot help you more. Is it still under warranty ? If not, you could open it and see if anything is clogging the fans.

im not that good at that.. i mean i am but you know i own my laptop so i dont wana take any risk.. i will talk to couple of people and see what ic can do.. hope i can fix it.. uggh.. hate this things

---

### Post by irish_flu on 2007-05-26
My boss had this problem and bought himself a product called the "Targus Notebook Chill Mat".  It plugs into your USB port (to power the fans).

This solved his overheating problems.  If you're in the USA you can get this or something like it at any of the big office stores (Staples, Office Depot, etc).  Best Buy and Circuit City probably carry them too.  You can also get one from just about any website that sells laptop computers or accessories for them (Amazon.com, Newegg.com, etc).

---

### Post by arvevans on 2007-05-27
[INDENT][http://people.debian.org/~dz/i8k/00-README](http://people.debian.org/~dz/i8k/00-README)[/INDENT]

_._

---

### Post by HunkieChan on 2007-05-27
> **arvevans@earthlink.net said:**
> [INDENT][http://people.debian.org/~dz/i8k/00-README](http://people.debian.org/~dz/i8k/00-README)[/INDENT]

_._

what is that ?

---

### Post by chemtut on 2007-05-27
does the fan spin at all?
might be clogged with dust
I used a vacuum cleaner with narrow nozzle to clean mine
there are cans of compressed air whichh are used to clean computers-----you can only try!

---

### Post by meborc on 2007-05-27
or you could try to "force" bios to leave the fans always on... then boot your system and see if the fans are really broken and not working or they just didn't get the input needed to work... i used this method on old (like only floppy drive old) laptop (compaq)... i had external cd-rom and tried to install breezy on it... it died on half way... i solved it by installing the server version, which took less time... and constantly blowing air on the fans :D ... other people in the room were laughing their asses off... but as soon as the installation was done and i turned on (or off i really don't remember) the acpi (or something like this) the fans started to work :)

but i fear that probably you just have a dead fan and you need it replaced... go to the repair shop and let them test your fan with external power source... if dead, let them replace it... it is not that costly

---

### Post by nickpaton on 2007-05-27
I have anHP Compaq NX6125 laptop with the same problem, and found that when initially loading Ubuntu it shut down because it overheated before installation was complete.

To get round this I discovered that within the BIOS you could specify for the fans to be on all the time when running on AC.

Also to speed up installation I pressed F6 on the first menu choice and added *noapic nolapic* to the end of the command line.

Also I've come across notebooks where the underneath fans are completely clogged with dust etc and needed to be be stripped down to remove all the c**p from inside.

Also take care using a vacuum cleaner or air spray since if you cause the fan blades to spin there's a very good chance that you will make them run faster than they were designed to go and will damage the little bearings - always stick something in to stop the blades from spinning if possible.

Finally....using an air spray will blast dirt INTO the notebook rather than suck it out and will probably contribute to blocking the internal airways even further.

---

### Post by meborc on 2007-05-27
> **nickpaton said:**
> Also to speed up installation I pressed F6 on the first menu choice and added *noapic nolapic* to the end of the command line.

just remembered - that is what i did too :D ... ahh, my memory sucks

---

### Post by crimesaucer on 2007-05-27
> **HunkieChan said:**
> okay bro..where can i get that whateever you just said. its get freaken hot.. im scared :"(

I was having overheating issues too, this Laptop cooler made my temp go from 60-70 degree range that was to hot, to the 40-50 degree range: [http://www.coolerguys.com/llnc02.html](http://www.coolerguys.com/llnc02.html)

The fans have worked quietly, and can be made to either pull air out, or push cool air in, and the aluminum keeps everything cool. It also fits a larger 17 inch laptop.

---

### Post by HunkieChan on 2007-05-27
> **irish_flu said:**
> My boss had this problem and bought himself a product called the "Targus Notebook Chill Mat".  It plugs into your USB port (to power the fans).

This solved his overheating problems.  If you're in the USA you can get this or something like it at any of the big office stores (Staples, Office Depot, etc).  Best Buy and Circuit City probably carry them too.  You can also get one from just about any website that sells laptop computers or accessories for them (Amazon.com, Newegg.com, etc).

thanks a lot bro.. does it work ? how much improvement does it has on the temperature ?

---

### Post by HunkieChan on 2007-05-27
i tried to tear apart my laptop (not literally) but i didnt finish it cause there were so many parts and screws that i was afraid that i might do something wrong . but one thing i have found is my hard drive is exactly underneath the most heated part of my laptop.. is my hard drive causing the heat ? i dont know.. or if there is soemthing else beneath the hard drive, i dont know..  as some of you asked if my fan is on . i tried to go to bios and look for fan option but there wasnt any..

---

### Post by amok69 on 2007-05-27
please note that even though i've fixed quite a few of them, i'm not a certified pc repair man in any form, shape or shade. everything i write might be completely wrong so please proceed  carefully and look for more info if you need any.

99% of overheating crashes are caused by various cpu fan issues.

next time the lappy crashes restart to bios and check the cpu temp. that will give you an indication of just how hot things are there and if its the cpu +/- the fan or not . if you have windows dual boot try installing everest home edition (i don't yet know of a linux app that does this) and using the sensor tab you'll be able to see in real time the cpu temp and the fan's speed. get everest home from [here]("http://http://www.majorgeeks.com/download4181.html").

to try and analyze the problem you can listen to hear if your fan is on all of the time. if you hear it kicking in shortly before the machine crashes that will probably mean that either its clogged up and not working or that the thermal paste between the fan and the cpu has dried up. or both.

if your fan also makes a rattling or clicking noise (try imagining a failing hard disk noise here) that might mean there is a problem with the fan itself,  with the physical attachment of the fan to its bracket or the attachment of that bracket to the motherboard. a shop will probably tell you at this stage that something needs replacing. other than the fan itself this tends to be on the expensive side (think new motherboard...) but can be avoided if an external cooler works for you. if it doesn't work and the problem is with the motherboard screw sockets,  shop repair might be too expensive or not justifiable per your machine but there is still another option although it does require that you go mad max on your lappy. 

i would try all "soft" solutions first: check the bios to force spin the fan if that option is available, clean the fan and other airways with vacum or compressed air etc.

if all of the above fail, i would ask the shop for a quote on checking and replacing the hard disk, fan and thermal paste. it actually might cost you less than getting an external cooler and would be a better long term solution. however, most small shops are wary of doing internal lappy work and will either tell you so upfront or after a week the thing has been laying there (more on that later).

if you do have to open your lappy find info on that on ze webs, although most will open up quite easy with only 2 or 3 screws. the fan is usually just below the keyboard which is held in place by that plate with all the buttons nobody ever uses, which is held in place by 2-3 screws going in at the underside of the lappy.

WARNING: imho, below steps, while not too complicated, are not for the technical faint of heart.

after you free that plate move or disconnect the keyboard as needed and if you don't see the fan straight away look for a plate with 4 screws or screw sockets in it. CAUTION: if you move that  you'll need some thermal paste later in order to replace it. if you don't have it laying around you can get some at most pc hardware shops.

take the opportunity of opening the lappy to do some spring cleaning: fans and dust bunnies.

if the fan or its plate move / rattle around freely its more than probable that the screw sockets on the motherboard have broken. even if money is not a problem i personally wouldn't change the motherboard just for that and instead go mad max on it instead.

the best solution in this case would be to get some screws identical to the ones that hold the fan in place at the moment but longer and with appropriate nuts.

if the broken sockets on the motherboard have enough insulated anchorage on the motherboard you might just lift it as well and connect the screws thru the motherboard, placing the nuts on the opposite side. make sure everything is insulated and that the screws don't touch any component or shourt any circle. 

if the screws do touch any other board or the case, mark them for cutting, open, cut and recheck fit.

once the mother board fits into place and the screws are short enough not to touch anything else - open them up, apply the thermal paste and close them up again.  put all the guts back in properly and close the case.

should have taken you less time than to read this.

usually the mother board is the most bottom board which means you might not have to adjust the screws a lot and, if you're short on time, lazy and or just don't care (like me) just drill thru the case (the broken sockets on the motherboard should allow you to do this) and place the nuts on the OUTSIDE of the case. you run a smaller chance of ruining the board this way although it will be a bit wobbly. stick a spacer on the other side.

did this to a friend's laptop a while ago - the store kept it for a week just to say they were afraid to open the case. still friends. lappy still working. 

again, remember that i'm not a certified pc repair man - so measure twice before cutting once.

---

### Post by HunkieChan on 2007-05-27
thanks a lot bro but i guess ill get an external fan. thats the safest way to go..

---

### Post by arsenic23 on 2007-05-28
Just a heads up.  Extreme overheating can damage the thermal compounds on many notebooks/laptops.  One or more of these events can seriously retard your heatsink's ability to pump heat out of your PC.  In the long run this can seriously shorten CPU life.

The safest thing to do is have a shop or someone experienced that you trust take a look at the heatsink/fan and apply an appropriate thermal compound.

Also, in these cases, external cooling devices arn't so much of a fix as they sometimes appear to be.  Even if they are moving heat out of your laptop and keeping the laptop as a whole cooler it's still possible that the CPU has abnormally high localized heat.  In a lot of cases this is obvious when the laptop feels cool but the internal fan is sill pushing hard most of the time.  Of course if your fan or sensors are damaged this little bit of advise will do you no good.

---

### Post by HunkieChan on 2007-05-28
> **arsenic23 said:**
> Just a heads up.  Extreme overheating can damage the thermal compounds on many notebooks/laptops.  One or more of these events can seriously retard your heatsink's ability to pump heat out of your PC.  In the long run this can seriously shorten CPU life.

The safest thing to do is have a shop or someone experienced that you trust take a look at the heatsink/fan and apply an appropriate thermal compound.

Also, in these cases, external cooling devices arn't so much of a fix as they sometimes appear to be.  Even if they are moving heat out of your laptop and keeping the laptop as a whole cooler it's still possible that the CPU has abnormally high localized heat.  In a lot of cases this is obvious when the laptop feels cool but the internal fan is sill pushing hard most of the time.  Of course if your fan or sensors are damaged this little bit of advise will do you no good.

thanks alot bro

---

### Post by bone43 on 2007-05-28
> **HunkieChan said:**
> thanks alot bro


 Try gkrellm it will tell you all your temps and fan speeds in Ububtu im running 127F and 116F on a core duo under average load the fan speed 3400 rpm when running maxed out.

check here for more tips on heat and hardware...

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware)

---

### Post by HunkieChan on 2007-05-28
> **bone43 said:**
> Try gkrellm it will tell you all your temps and fan speeds in Ububtu im running 127F and 116F on a core duo under average load the fan speed 3400 rpm when running maxed out.

check here for more tips on heat and hardware...

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware)

thanks a lot , again !.. ill guss ill just buy an external fan but the thing is some dude said it might not make any diff.. now im a but heart broken

---

### Post by irish_flu on 2007-05-28
> **HunkieChan said:**
> thanks a lot bro.. does it work ? how much improvement does it has on the temperature ?

It helped, I'll say that much.  I'm not sure how much it actually changed the temperature (my boss lives 1000 miles away from me, hehe) but it doesn't reboot on him anymore.

---

### Post by arvevans on 2007-06-12
**One poster doubted that fan controls were included in the OS.  This data (from the URL provided) shows that fan control may be included in kernel compiles:**

Since version 2.4.14-pre8 of the kernel the i8k SMM driver is included in
the core kernel distribution. The driver source included in this package is
needed only if you want to compile the module for an older kernel version
or if you need a more recent version then the one in the Linux kernel.

The driver has been reported to work with the following hardware and BIOS:

    Inspiron 1100 (BIOS A06), one fan, no buttons
    Inspiron 2650 (BIOS A05)
    Inspiron 3700 (BIOS A15), no fan speed
    Inspiron 3800 (BIOS A14), no fan speed
    Inspiron 4000 (BIOS A10), no fan speed
    Inspiron 4100
    Inspiron 4150
    Inspiron 5100 (BIOS A06), one fan, no buttons
    Inspiron 5150 (BIOS A24), one fan, no buttons
    Inspiron 8000 (BIOS A17)
    Inspiron 8100 (BIOS A04)
    Inspiron 8200 (BIOS A06)
    Latitude C400 (BIOS A01)
    Latitude C510 (BIOS A07)
    Latitude C600 (BIOS A17)
    Latitude C610
    Latitude C800 (BIOS A17)
    Latitude C810 (BIOS A12)
    Latitude C840 (BIOS A10)
    Latitude CPiA (BIOS A14), no fan speed
    Latitude CPx J750GT (BIOS A13), no fan speed
    Latitude D600 (BIOS A05)
    Latitude D800 (BIOS A00)
    Latitude X200 (BIOS A07)

but will probably work on any recent Dell laptop. Note that on some models
or BIOS versions the fan speed is not available. On some BIOS also the BIOS
version is not available from SMM but the driver is able to obtain it using
another method.

[B]On my Toshiba 8100 it is possible to detect fan operation by holding a strip of paper close to the air outlet near the left rear corner.

The suggestion to check CMOS settings for fan control is a good one.[/B]

---

### Post by daller on 2007-06-19
Hi there,

I have a Dell Inspiron 8600 - And I can't set the fan to "always on" in the BIOS...

Somebody mentioned Gutsy + Powertop, is it buildin in Gutsy, or how do I get it? - And how does it work?

I had a severe crash! - The computer didn't boot (No HDD activity, no picture... Nothing)

It started with the GFX acting weird - vertical different colored stripes, and sometimes a garbled image... And the screen freezed...

I rebooted, say 30 times... Same **** every time... 

I opened the laptop, removed the GFX (including heatpipe, and stuff) - Cleaned it all up (damn, 4 years old... what a nasty mess...) And put it back together...

It's running all fine for now... But my fans aren't moving a bit... Not even putting the system into heavy load...

Thanks for any help!

---

### Post by sw1995 on 2007-06-20
Hello,

I had a problem with my Gateway laptop getting insanely hot and the sound of the fan running all the time just about drove me nuts; I bought a "chill mat" which connects via usb and sits underneath the laptop and it does an amazing job keeping the cpu running at a cooler temperature--it is kind of ugly but it does the job.

Here is an example:

[http://www.bestbuy.com/site/olspage.jsp?skuId=6211752&st=targus&type=product&id=1074788100200](http://www.bestbuy.com/site/olspage.jsp?skuId=6211752&st=targus&type=product&id=1074788100200)

Good luck!
-S

EDIT: Sorry, I am half asleep and did not notice that the chill mat was brought up earlier:)

---

