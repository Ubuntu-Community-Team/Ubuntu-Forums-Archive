---
title: "Why wont it work!"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-28
Ive been trying to get sound for the past 4 days taking instructions and stuff. BUT IT JUST DOESN'T WORK!

This is the message I get : Te Volume control did not find any elements and.or devices to control. That means either that you do not have the right Gstreamer plugins installed , or that you do not have a sound card configured

I have installed all Gstream plug-ins. It wont work. I restarted to computer to see maybe it takes effect. It wont work. Im frustrated now. Now if my sound card is not configured then wtf do i do? im pretty sure its detected.

I NEED URGENT HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!.

---

### Post by Vague on 2007-07-28
Well, open up the terminal, enter ```
lspci
``` and paste the output here.  That's probably a good place to start.

---

### Post by 4Real on 2007-07-28
00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:0f.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 03)

---

### Post by Vague on 2007-07-28
Huh.  I don't see a sound card there.  What kind of sound card are you using?

---

### Post by 4Real on 2007-07-28
Im not sure :( im only 13... so i&#314;l open up my computer and check it out... i added you to buddy list i&#314;l pm u later... but even if i find out what sound card im using then what do i do

---

### Post by Vague on 2007-07-28
It's probably as simple as loading a module.  My suspicion, though, based on your chipset and the fact that no sound card is showing up in lspci, is that you're using an ISA sound card.  There are various drivers for various chipsets, so knowing which one you have makes finding the right module a lot easier.

---

### Post by 4Real on 2007-07-28
any help? :confused::(

---

### Post by 4Real on 2007-07-28
> **Vague said:**
> It's probably as simple as loading a module.  My suspicion, though, based on your chipset and the fact that no sound card is showing up in lspci, is that you're using an ISA sound card.  There are various drivers for various chipsets, so knowing which one you have makes finding the right module a lot easier.

ok i&#314;l pm you details. and i need to edit Screen resoultion. theres no potion for 1084x867 (i forget whats the correct one)

---

### Post by Vague on 2007-07-28
> **4Real said:**
> ok i&#314;l pm you details. and i need to edit Screen resoultion. theres no potion for 1084x867 (i forget whats the correct one)

Try ```
sudo dpkg-reconfigure xserver-xorg
``` and select that resolution (I assume you meant 1024x768.  You probably won't find a 1084x867, although for a while mine liked to default to the thoroughly bizarre 960x720).  Assuming, of course, that your graphics card and monitor are comfortable running that resolution at whatever refresh rate you choose.

---

### Post by 4Real on 2007-07-28
i found out what it is.

Creative Tech 96

CT1745A-TBP9730

---

### Post by 4Real on 2007-07-28
or

Creative - Model # CT4500

---

### Post by 4Real on 2007-07-28
any help?

---

### Post by Vague on 2007-07-28
Ah, beautiful, a Sound Blaster card.  Alright, go to the terminal and enter ```
sudo modprobe snd-card-sb16
``` (you also might want to try "snd-sbawe" and "sb" in place of "snd-card-sb16"), then enter ```
alsamixer
``` and see if it recognizes the card.

---

### Post by 4Real on 2007-07-28
no help??? aww man... :(

---

### Post by 4Real on 2007-07-28
> **Vague said:**
> Ah, beautiful, a Sound Blaster card.  Alright, go to the terminal and enter ```
sudo modprobe sb
```, then enter ```
alsamixer
``` and see what if it recognizes the card.


THANKS i will tell you if it works or not but just to tell you the card is for 95/98 :(

---

### Post by 4Real on 2007-07-28
so my question is will Ubuntu pick it up if its a Windows 95/98 card?

---

### Post by Vague on 2007-07-28
> **4Real said:**
> so my question is will Ubuntu pick it up if its a Windows 95/98 card?

Shouldn't matter.  As long as the driver supports the card, you'll be fine.  Also, note the edit I made to my previous post.  Upon further research, I think you may have more luck with the first two modules, but let me know what happens.

---

### Post by 4Real on 2007-07-28
ok but you said as long as the driver supports the card... i dont have the driver. which is the cd right? i dont have it :(

---

### Post by Vague on 2007-07-28
> **4Real said:**
> ok but you said as long as the driver supports the card... i dont have the driver. which is the cd right? i dont have it :(

No.  You don't need the CD at all.  All you need to do is load the driver included in Ubuntu using modprobe.  When you find one that works with your card, you can make it load automatically every time you start up Ubuntu.  But don't worry about that card being "for Windows 95/98."  It'll be fine.

---

### Post by DBStevens on 2007-07-28
No the drivers that Vague is having you try are part of the linux kernel.

---

### Post by kostkon on 2007-07-28
> **4Real said:**
> ok but you said as long as the driver supports the card... i dont have the driver. which is the cd right? i dont have it :(

Ubuntu has already the driver, the only thing you need to do is activate it.

---

### Post by 4Real on 2007-07-28
no it didn't work :(

arrrrrghhhhhhHHH!

---

### Post by Vague on 2007-07-28
> **4Real said:**
> no it didn't work :(

arrrrrghhhhhhHHH!

None of those three worked?  Did you get any errors at all?  If so, could you post them, please?

---

### Post by 4Real on 2007-07-28
I have another sound card... Compaq X071
Can some get me module for that?

---

### Post by 4Real on 2007-07-28
> **Vague said:**
> None of those three worked?  Did you get any errors at all?  If so, could you post them, please?

FATAL: Module snd_card_sb16 not found.
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by 4Real on 2007-07-28
oh also

FATAL: Error inserting snd_sbawe (/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sbawe.ko): No such device

---

### Post by Vague on 2007-07-28
> **4Real said:**
> FATAL: Module snd_card_sb16 not found.
alsamixer: function snd_ctl_open failed for default: No such device

Woops.  My fault.  Try replacing that with ```
snd-sb16
```

---

### Post by 4Real on 2007-07-28
sorry for 4 posts in a row but also this -> FATAL: Error inserting snd_sbawe (/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sbawe.ko): No such device
bash: syntax error near unexpected token `('

---

### Post by 4Real on 2007-07-28
> **Vague said:**
> Woops.  My fault.  Try replacing that with ```
snd-sb16
```

FATAL: Error inserting snd_sb16 (/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb16.ko): No such device

:(

---

### Post by Vague on 2007-07-28
Hmmmm, try the other two, as well.  Also, in case you still want to know, the module for your Compaq card should be ```
snd-es18xx
```, I think.

Edit:  Well, looks like you might have to do a bit of tinkering with your BIOS.  [This](http://ubuntuforums.org/showthread.php?t=103180) thread has a link that might be useful.  Here it is:  [http://forums.fedoraforum.org/showthread.php?t=44691](http://forums.fedoraforum.org/showthread.php?t=44691)  Read post #9.  That fix has apparently worked for a lot of people.

---

### Post by 4Real on 2007-07-28
ok is there any other modules because its takes a while for me to to change sound card. is there any other modules for my Sound Blaster ? :(

---

### Post by Vague on 2007-07-28
> **4Real said:**
> ok is there any other modules because its takes a while for me to to change sound card. is there any other modules for my Sound Blaster ? :(

Basically just sb, snd-sbawe and snd-sb16.  Check out my last edit, though.  I think that might be your solution.

---

### Post by DBStevens on 2007-07-28
Well I'd expect a 4700 which is a PCI card aka ENS-1370 from what I'm finding on the net using Google to:

1: Show in the lspci output

and 

2: Respond to a proper setup using the information on this page:
 [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+PCI128+(earlier+model+CT4700).&chip=ES1370&module=ens1370](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+PCI128+(earlier+model+CT4700).&chip=ES1370&module=ens1370)

which for a quick test would mean:

sudo modprobe snd-ens1370

followed by showing up in 

alsamixer


If it is a 4500 then Vague probably has most of the bases covered  some Creative Cards were around for a very short time and more than one electronics package was called the same thing at least once.  I have two Sound Blasters only one of which I can still use.

---

### Post by Vague on 2007-07-28
> **DBStevens said:**
> Well I'd expect a 4700 which is a PCI card aka ENS-1370

Which card are you referring to?  He mentioned that his SB is a 4500, which is an SB AWE64 ISA, and as far as I can tell from Googling, his X071 is an ISA card using the ES1868 or 1869 chipset.

---

### Post by kostkon on 2007-07-28
Here in this [wiki page]("https://help.ubuntu.com/community/HowToSetupSoundCards") you will find a list of all the available drivers for ISA soundcards, and help on how to check which chipset you have and how to make the driver load every time you boot your system.

---

### Post by DBStevens on 2007-07-28
Vague like I said in my edit you had the ground covered if it was a 4500.

---

### Post by kostkon on 2007-07-28
Oh, seeing the list from the wiki, I recommend you to also check the *snd-sb8* driver for your old soundblaster card, assuming that is an ISA one. I hope it'll work.

---

### Post by Vague on 2007-07-28
> **DBStevens said:**
> Vague like I said in my edit you had the ground covered if it was a 4500.

Haha, sorry.  I posted before I saw the edit.

---

### Post by 4Real on 2007-07-28
I got the soundcard working!!!!!!!! It WAS an IRQ problem in the BIOS. For some reason, Kernel 2.6.9 played well with the pnp settings in the BIOS, but 2.6.10 did not. I went in and manually set the IRQ 5 and IRQ 11 to the Legacy ISA setting and it seems to have worked. The soundcard detection program still says nothing is installed, but the volume control works, the CD player makes music, and I can play MP3 files, so I am happy. Much thanks to everyone who helped me out, especially rega451 for mentioning the IRQ problems.

For future reference, here is a list of my hardware in case anyone ever runs across this thread again with the same problem:

FIC FB11 Rev 1.3 Socket 370 Mainboard with Intel 440BX chipset
Intel Pentium III CPU 933 MHz with 256 L2 cache, and 133 MHz FSB
384 MB various brands PC133 SDRAM
nVidia branded (Don't ask how I pulled that off) GeForce256 Video card with 32 MB SDRAM
D-Link DFE-530TX 10/100 NIC
Creative Sound Blaster AWE64 ISA soundcard
Promise Ultra 100TX2 ATA controller
Sony CRX160E 12x8x32 CD-RW drive
Maxtor DiamondMax D540X-4K 20 GB 5400 RPM hard disk (Really NOISY)
Epson Stylus Color 850 Printer
______________________________________________________________________________________--

How is that going to fix my problem??? it doesnt tell how to get to IRQ...

---

### Post by Vague on 2007-07-28
> **4Real said:**
> How is that going to fix my problem??? it doesnt tell how to get to IRQ...

Right, you'll have to go into your BIOS and manually change it.  I'm not sure what BIOS exactly your board is using, so I can't help you all that explicitly (although someone else here might be able to) but I'll see if I can find some sort of walk-through for you.  Just as a warning, I'm going to be gone for at least the next hour or so, so if I don't post anything immediately, it's not because I'm ignoring you.

---

### Post by DBStevens on 2007-07-28
It is a BIOS setting on your computer that should be looked at, that could prevent the sound card from being recognized by the current Linux kernels.

In short changing a BIOS setting may allow your card to work.   When those ISA cards were originally made plug and play was known as plug and pray.  You plugged the cards in and maybe they played.

---

### Post by 4Real on 2007-07-28
> **kostkon said:**
> Oh, seeing the list from the wiki, I recommend you to also check the *snd-sb8* driver for your old soundblaster card, assuming that is an ISA one. I hope it'll work.

this is what i get : FATAL: Error inserting snd_sb8 (/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb8.ko): No such device

---

### Post by 4Real on 2007-07-28
> **DBStevens said:**
> It is a BIOS setting on your computer that should be looked at, that could prevent the sound card from being recognized by the current Linux kernels.

In short changing a BIOS setting may allow your card to work.   When those ISA cards were originally made plug and play was known as plug and pray.  You plugged the cards in and maybe they played.

So does any one know how to change BIOS setting???

---

### Post by 4Real on 2007-07-28
i&#314;l be back in half an hour guys... so if you find any solutions plz post it here :)

---

### Post by 4Real on 2007-07-29
so hey all i want to change my BIOS setting so i can get the sound card working. anyone know how to do that. help is appreciated :D

---

### Post by 4Real on 2007-07-29
hey any help with setting the BIOS to ISA or something... :confused:

---

### Post by Vague on 2007-07-29
Alright, well, it looks like your motherboard probably uses an Award BIOS, judging from the Googling I've done.  Basically, you're going to want to restart and hit "Del" or "F1" or whatever you have to press to enter your BIOS setup menu.  From there, go to PnP/PCI Configurations and edit IRQ Resources.  You'll need to change IRQs 5 and 11 to Legacy ISA.  Here's a guide I found on Google for Award BIOSes, to give you a visual idea of what you're going to looking for: [http://www.buildeasypc.com/sw/bios_setup.htm](http://www.buildeasypc.com/sw/bios_setup.htm)

---

### Post by 4Real on 2007-07-29
> **Vague said:**
> Alright, well, it looks like your motherboard probably uses an Award BIOS, judging from the Googling I've done.  Basically, you're going to want to restart and hit "Del" or "F1" or whatever you have to press to enter your BIOS setup menu.  From there, go to PnP/PCI Configurations and edit IRQ Resources.  You'll need to change IRQs 5 and 11 to Legacy ISA.  Here's a guide I found on Google for Award BIOSes, to give you a visual idea of what you're going to looking for: [http://www.buildeasypc.com/sw/bios_setup.htm](http://www.buildeasypc.com/sw/bios_setup.htm)

alright it fixed :)

if i have problems in the future i&#314;l pm u... but right now see my latest thread.

---

### Post by Vague on 2007-07-29
> **4Real said:**
> alright it fixed :)

if i have problems in the future i&#314;l pm u... but right now see my latest thread.

Fantastic.  Congratulations on getting that working.

---

### Post by 4Real on 2007-07-29
ok thanks :)

also i fixed GRUB problem :P i changed the time to 1 second so barely see it :lolflag:

---

### Post by dragonwings on 2007-07-29
sudo asoundconf list
to get a list of soundcards you have ,take note of them

now
sudo asoundconf set-default-card (here is where you put your sound card name)


eg" for mine i put
sudo asoundconf set-default-card Audigy2

---

### Post by 4Real on 2007-07-29
> **Vague said:**
> Alright, well, it looks like your motherboard probably uses an Award BIOS, judging from the Googling I've done.  Basically, you're going to want to restart and hit "Del" or "F1" or whatever you have to press to enter your BIOS setup menu.  From there, go to PnP/PCI Configurations and edit IRQ Resources.  You'll need to change IRQs 5 and 11 to Legacy ISA.  Here's a guide I found on Google for Award BIOSes, to give you a visual idea of what you're going to looking for: [http://www.buildeasypc.com/sw/bios_setup.htm](http://www.buildeasypc.com/sw/bios_setup.htm)

The problem came back again :(

So i tried to do your solution and when do i hit F1 and Del? Because i hit the keys when Ubuntu was loading but it didn't do anything? Help Please :confused:

---

### Post by 4Real on 2007-07-29
any help :confused:

---

### Post by 4Real on 2007-07-29
come on i need help with changing BIOS setting IRQ5 and IRQ11 to Legacy ISA

---

### Post by 4Real on 2007-07-29
COME ON ANY HELP??? :confused::confused::confused::confused::confused:

---

### Post by Vague on 2007-07-29
> **4Real said:**
> The problem came back again :(

So i tried to do your solution and when do i hit F1 and Del? Because i hit the keys when Ubuntu was loading but it didn't do anything? Help Please :confused:

Just out of curiosity, what did you do to fix it before?  Anyway, you may have to hit either Del or F1, but you'll have to do it before Ubuntu loads, during the POST screen that you get right as the computer starts.

---

### Post by 4Real on 2007-07-29
> **Vague said:**
> Just out of curiosity, what did you do to fix it before?  Anyway, you may have to hit either Del or F1, but you'll have to do it before Ubuntu loads, during the POST screen that you get right as the computer starts.

You have me module for My Compaq sound card and i think it identify. and it played music cd. the next day i was watching a video with no sound. so i pop cd in to see if it still works but no. I hit F1 and Del in the beginning but it doesn't get me any where.

---

### Post by 4Real on 2007-07-29
I have a newer computer and it has a sound card , maybe i should take a look at that?

---

### Post by 4Real on 2007-07-29
So I guess no one can help? Unless Vague is googling something.

---

### Post by 4Real on 2007-07-29
No Help yet??? :(

---

### Post by Vague on 2007-07-29
I was gone again for a while, sorry.  Basically, your POST screen should tell you what key you have to hit to get into the Setup menu.  Like I said, I think the two most common ones are Del and F1, but it could also be Esc, F2 or something else.  Make sure you're hitting the keys during POST, and not afterwards, when you actually start booting.  If the POST screen doesn't tell you anything, you can also use the time-tested method of flipping the keyboard upside down and pressing it against the ground once or twice during POST.

---

### Post by 4Real on 2007-07-29
> **Vague said:**
> I was gone again for a while, sorry.  Basically, your POST screen should tell you what key you have to hit to get into the Setup menu.  Like I said, I think the two most common ones are Del and F1, but it could also be Esc, F2 or something else.  Make sure you're hitting the keys during POST, and not afterwards, when you actually start booting.  If the POST screen doesn't tell you anything, you can also use the time-tested method of flipping the keyboard upside down and pressing it against the ground once or twice during POST.

Ok but i tried almost every key but it loads really fast up to GRUB. I will try again. My computer takes about 5 minutes to BOOT so hold on. And why are you the only trying to help? *sigh* sorry for wasting all ur time

---

### Post by 4Real on 2007-07-29
no it just wont get me their :( 
i tried all methods.

---

### Post by Vague on 2007-07-29
Hmmm. . . not really sure what to tell you here.  As long as you're doing everything at the right time, and you hit the right key, it should work.  You might try Googling for a list of the keys that each BIOS uses to get into setup; I'm sure one exists.  Before you do that, though, let me see if I understand what you did last night.

1) Pulled out your AWE64 and put in your Compaq card, 2) used modprobe to load drivers for that card, 3) it worked?  After that, it didn't work?  Did you restart in-between when it worked and when it didn't?

---

### Post by 4Real on 2007-07-29
> **Vague said:**
> Hmmm. . . not really sure what to tell you here.  As long as you're doing everything at the right time, and you hit the right key, it should work.  You might try Googling for a list of the keys that each BIOS uses to get into setup; I'm sure one exists.  Before you do that, though, let me see if I understand what you did last night.

1) Pulled out your AWE64 and put in your Compaq card, 2) used modprobe to load drivers for that card, 3) it worked?  After that, it didn't work?  Did you restart in-between when it worked and when it didn't?

ok i need to go so i answer questions : i pulled out AWE64 , put in compaq card , useed modprobe to load driver , then it worked , then i shut it down when i was going to bed. then it didnt work. The only time i can press the keys for BIOS set-up is when it shows the compaq loading screen. after it is loaded it goes to grub , to ubuntu. so i cant get to bios set-up... do you think buying a new soundcard will work??? tell me man , i gtg peace. be back in 30 minutes or more.

---

### Post by Vague on 2007-07-29
> **4Real said:**
>  then i shut it down when i was going to bed. then it didnt work.

OK, I think that's your problem.  Sorry I wasn't more specific about this last night.  modprobe loads the driver, but that's pretty much all it does.  So if you restart, the driver doesn't load again.  Now, if you tried ```
sudo modprobe snd-es18xx
``` again and that doesn't work, we have other problems.  If you didn't, though, you need to add a line to a file to let Ubuntu know that it needs to load that module each time it starts.  Open up and terminal window and enter ```
sudo nano /etc/modules
``` You can use whatever text editor you prefer, like gedit or something, but I like nano.  At the end of the modules listed there, add a line that says ```
snd-es18xx
```  Now save it and you're done.  That module should get loaded every time you start Ubuntu.

> The only time i can press the keys for BIOS set-up is when it shows the compaq loading screen.

Yes, that would be the correct time to go into the setup, assuming you still need to do so.

> do you think buying a new soundcard will work???

Yes, there are a lot of PCI sound cards out there that Ubuntu will auto-detect and you'll never have any trouble with.  I don't think it'll be necessary, though.  Since you had it working last night, I suspect that just adding that line to /etc/modules will do the trick.

---

### Post by 4Real on 2007-07-29
no nothing it doesn't work. ah well ill just end up buying a new sound card. When i type sudo modprobe snd-es18xx it doesnt do anything it just goes back to myname@computername:~$: 
when i hit F1 F2 ESC DEL and everyother one it doesnt get me to the BIOS. Maybe because Ubuntu is the only Operating System I have. I dont have any windows. Thanks for all the help bud. I dont think theres anything else i can do.

---

### Post by 4Real on 2007-07-29
wtf! i popped in my music cd and it played! lol also it still tells my the warning thing that i have no sound device or gstream plugins! ROFL!

---

### Post by Lord Illidan on 2007-07-29
> **4Real said:**
> no nothing it doesn't work. ah well ill just end up buying a new sound card. When i type sudo modprobe snd-es18xx it doesnt do anything it just goes back to myname@computername:~$: 
when i hit F1 F2 ESC DEL and everyother one it doesnt get me to the BIOS. Maybe because Ubuntu is the only Operating System I have. I dont have any windows. Thanks for all the help bud. I dont think theres anything else i can do.

It doesn't make a difference whether Ubuntu is the only OS you have, pressing DEL/F1/F2 whatever, should take effect whether or not you even have an OS installed on the computer!! You're pressing it wrong, probably.

Regarding an other soundcard..yep, a cheap pci soundcard might be the best way to go..if you want, give us the details of what you are going to buy and we can check if it is compatible.

---

### Post by 4Real on 2007-07-29
hmmm i swear ive done this before i had to get safe mode and stuff. it doesnt work :( but hey i think i got it working ... but yeah if i buy one i think ill need ur guys help. ill add u to buddy list if you dont mind.

---

### Post by 4Real on 2007-07-29
Yes It Work Vague It Worked!!!!!! Thank You So Much Man!!!!!!!!!!!!!!!!

---

### Post by Vague on 2007-07-29
> **4Real said:**
> Yes It Work Vague It Worked!!!!!! Thank You So Much Man!!!!!!!!!!!!!!!!

Anytime.  Which solution worked, if you don't mind me asking?

---

### Post by 4Real on 2007-07-29
Well i just have to type in sudo modprobe snd-es18xx every time i boot computer and sound is going good. because i don't know how to make it load the module every time. i know you gave me the code but i don't know how to save.

---

### Post by Vague on 2007-07-29
> **4Real said:**
> Well i just have to type in sudo modprobe snd-es18xx every time i boot computer and sound is going good. because i don't know how to make it load the module every time. i know you gave me the code but i don't know how to save.

Ah, ok.  If you're using nano, make the changes you want, and when you're done, hit Ctrl+x.  It'll ask if you want to save, hit y.  It'll then ask what you want to save it as.  Just hit enter, since you're overwriting the file you're editing.

---

### Post by 4Real on 2007-07-29
Aha it worked. Thanks again Vague you saved me some money :popcorn:

---

### Post by Vague on 2007-07-29
No problem.  Glad you got a sound card working in there.

---

