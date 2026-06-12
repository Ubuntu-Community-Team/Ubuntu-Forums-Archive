---
title: "HP Pavilion 533w &amp; e-Ge-Force 6200 not doing anything"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Teddy_P on 2007-10-02
I am not getting anything if this card is plugged in. Its a pci card and I have tried every thing that I can find on these boards. I have it in a HP a1100y and its the same thing. I can't even get the the bois.



Teddy

---

### Post by nowshining on 2007-10-02
if you can't even see the bios then it's probably a problem with the card, or  unplug the card, plug it into an internal one if you have one, reboot - get into the bios - change settings, save, turn off computer - re-input the card - plug monitor cord into the video card, turn on computer and now see if it works.

---

### Post by Teddy_P on 2007-10-02
Can you tell me what to look for in the bios or what I should change. I have seen some threads here talk about auto detect.
Just any basic stuff I should look for?



Teddy

---

### Post by nowshining on 2007-10-02
check the manul and as for My own computer Auto detects the other card however will not work if I plug  the cord into the internal video and have to remove it so that was just a reference saying I don't know how HP does it in their bios..

[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=us&dlc=en&tool=softwareCategory&product=90862&sw_lang=8&dest_page=softwareCategory&](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=us&dlc=en&tool=softwareCategory&product=90862&sw_lang=8&dest_page=softwareCategory&)

---

### Post by Teddy_P on 2007-10-02
Well now I get a message that says

Failed to start the X server (your graphical interface) .....
Would you like to view the X server output to diagnose the problem?

I picked "yes"

(==) Log file: "/var/log/Xorg.0.log" , Time: Tue Oct  2 22:32:09 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) I810(0): Cannot read V_BIOS
(EE) I810 (0): VBE initialization failed.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

There is a detailed log also but there is no way my wife is typing all that for me.


Thanks
Teddy

---

### Post by Teddy_P on 2007-10-02
Now I have a command line.
So its getting better.



Teddy

---

### Post by nowshining on 2007-10-02
okay we got past the BIOS which then the first problem is cured.

Do the following  press okay if can or press ctrl + alt + f1 now type out ur username  and now your password, note that while you type out the password it will not show and this is normal, type it out as you normally do then hit enter...

then do the following

```

sudo /etc/init.d/gdm stop
c/code]

press enter and enter your password when asked to

then enter the following

[code]
sudo dpkg-reconfigure -phigh xserver-xorg

```

enter ur password when asked to, follow the instructions and select vesa as the video driver, then once out of there at the CLI as I think it will boot you back into the CLI..

```

sudo /etc/init.d/gdm start

```

if that doesn't work then do a reboot by pressing ctrl + alt + delete key on ur keyboard and if that doesn't work please let me know.

---

### Post by nowshining on 2007-10-02
lolz ur were too quick for me.. :) well instruction one solved.

---

### Post by Teddy_P on 2007-10-02
The gdm stop comand did do something then said      [OK]

In the "configuring xserver-xorg
It asked for resolutions
I just skiped and selected OK at the bottom.

then its says at the CL xserver-xorg postinst warning: overwriting posibly-customised configuration filr ; backup in /etc/X11/xorg.conf.20071002230231
teddy@kids1:~$


Teddy

---

### Post by Teddy_P on 2007-10-02
What if I did it with out the -phigh?

Teddy

---

### Post by Teddy_P on 2007-10-02
Thanks for your help.
I have to go to bed.
I will read up more on the mobo and the bois tomorrow.



Thanks again
Teddy

---

### Post by nowshining on 2007-10-02
GDM is what you see when you login thru the GUI graphically :) yes the password box is part of GDM and is GDM,

if you start it the GDM / logon screen will start up asking for your password to log in.

"
"then its says at the CL xserver-xorg postinst warning: overwriting posibly-customised configuration filr ; backup in /etc/X11/xorg.conf.20071002230231"

that is just a standard warning - just a SO U KNOW thing, it measn that ur xorg.conf you last had is in that folder - same folder as the xorg.conf goes in that folder and "xorg.conf.20071002230231" is just the new backuped name. :)


yes leave out the phigh part, I just did a quick lookup 'cuase I did forget the exact command of doing so, that should work, if the other didn't work, again do the same but leave out the phigh part and follow all the directions and selecting vesa unless your video card driver is there or something similiear is there you might like to try, but that's at ur own risk, which shouldn't cause any damage and should just throw up an error.

---

### Post by nowshining on 2007-10-02
good night, do u live in a PST timezone state like me... :P I stay up all night. I'll be asleep in the day time. if I do fall asleep maybe someone else may be of help to u.

---

### Post by Teddy_P on 2007-10-03
If I start GDM I never get to the log in screen. I was logging in at the CL.

I am at work now I am on EST. I tried it with the out the -phigh. And selected versa the same thing happened but some of the errors said Versa instead of I810.

As I was going through the configuring xserver-xorg and still see the onboard card.

I installed a Gforce 6800 on a different machine and I installed the card then Envy and it worked fine. Do I need to install drivers first then install the card?



Teddy

---

### Post by Teddy_P on 2007-10-03
Well I can't find anything on the HP sites. Next is off to Nvidia and I am going to call EVGA when I get home.


Any other thoughts?



Teddy

---

### Post by Teddy_P on 2007-10-03
Well I just got off the phone with Evga. The guy I talked to was very nice but they do not support Linux so not helpful.
I only have alternative CD's so I am downloading a desktop CD for Gusty and I will see what a live CD will do.


Any other thoughts?




Teddy

---

### Post by Teddy_P on 2007-10-03
the "start in safe graphical mode" Did not do anything.


So now I am stumped.



Teddy

---

### Post by Teddy_P on 2007-10-03
I keep seeing error messages that lead me to the resolution.
after the UBUNTU and process bar then it goes to the part that askes if I want to see the errors this time I clicked no and it went to the CL.
it reads:
Starting up...
Loading, please wait...
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot....

Ubuntu 7.04 kids1 tty1


I don't know what other information I could share to help this either.

Teddy

---

### Post by nowshining on 2007-10-04
well i'm sorry but a lot of that is beyond me, i'm guessing u tried installing the drivers first if not let me know or go ahead an try it.  The Graphical mode - yeah it sucks  :P didn't work for me either when I just wanted to see what that was.

"kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...."

the above are normal it's just trying to check to see if you used hibernations, etc.. :) in other words I get those to and I def. know what they are.


as for

"usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768"

something must be wrong wtih the usplash or GDM i'm guessing, have a go with Gutsy and let's see what happens. edit: oh also do a complete format with Gutsy - yes it's beta, however it should work fine.

---

### Post by Teddy_P on 2007-10-04
I will try Gutsy tonight.
I have that on two computer and its great for me. I did not want to use it for this in case I had problems then I would here a lot of "well its only betta".

I will try to just leave the card in and load it first. 
If that don't work I was thinking of using the recovery disc's (11 of them) and load windows on something just to see if its the card or not.


Teddy

---

### Post by nowshining on 2007-10-04
Beta means you can report any bugs to bugs.launchpad.net and they should then if confirmed be fixed, compared to after the Beta and when it's officially released meaning that afterwards u'd have to wait until the next version to see if it's fixed. Hope Gutsy works. :)

---

### Post by Teddy_P on 2007-10-04
Gutsy did not do anything. I loaded Windows on a different machine and I will try the card in there. If its ok then I will try a live CD. Then ....Well I don't know yet.
I will keep you informed.


Teddy

---

### Post by Teddy_P on 2007-10-04
nowshining,
I want to thank you again for helping me. I loaded Windows on the other computer and it did not work. So I called EVGA and we talked about the bois and then he asked how big the power supply was. He said I need 300w. Well I have 250w in one computer and the one that we were working on is only 200w. So I think that may be the problem.
I am so sorry for wasting your time but I did not even think to look at stuff like that before I bought the card.

I will look at prices for new power supplies and then hope that this card will give me the desk top effects.


Teddy

---

### Post by nowshining on 2007-10-04
it's alright, you were not wasting my time at all. :) however I'm glad we figured out the problem, however the card shouldn't take 50 watts of power at all. I'd more than likely switch cards instead, but it's ur call and maybe tech was right I don't know myself, I think my dell 4600i (yes it's the 4600 series and others have bad power supplies, but not me :) i = internal video card) - has 250 watts, but i'm not sure tho. I have 2 hard drives, a old dvd - rom, CDRW, VIA pci usb card left over when I had les USB ports on one of the older computer I had, all hooked up and using the Power Supply.

---

### Post by nowshining on 2007-10-04
oh and of course the cheap Zotac Nvidia Fx5200 card - underclocked of course a bit. :)

---

### Post by Teddy_P on 2007-10-04
what do you think I should do?
Get a power supply or send the card back?

Like I said before I only want the Beryl or the desktop effects. After I get a power supply do you think this card will do that and more?


Teddy

---

### Post by nowshining on 2007-10-05
is the computer still under warranty, because if it wouldn't boot under windows either, then well that's a problem then - the card did come with the computer right?? or did you buy it sepearatly ??

---

### Post by Teddy_P on 2007-10-05
The computer is older. I just bought this card last week.


Teddy

---

### Post by nowshining on 2007-10-07
a day has passed what have u done, if the card doesn't work send it back for a new one or ur money back, it should work also in at LEAST XP. ;)

---

### Post by Teddy_P on 2007-10-10
I am going to order a power supply next week If I don't get a chance to pick one up soon.
The requirements is 300W and the biggest one I have is 250W.
I agree that that is not much difference but the +12V should be 18A and mine is 12A.

I will let you know what happens.


Thanks
Teddy

---

