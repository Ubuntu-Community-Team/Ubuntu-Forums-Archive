---
title: "SOS!!! Ubuntu crashes right after i choose it from my OS selection menu on startup"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Toxic-Waste on 2007-03-10
Hi!
I am a **Linux noob **and I only got into Ubuntu 3 days ago.  I am enjoying the transition from Win to Linux and I am spending more and more time learning all about Ubuntu Linux. This morning though, something dreadful happened…
**Ubuntu just WONT start!!!** It crashes! It freezes where Ubuntu presents its logo and the loading bar fills up in the bottom. I have to press Ctrl+Alr+Del to see disc movement and it only just restarts the PC. I am so pissed because I haven’t the knowledge to overcome this issue but at the same time feel so LUCKY that I didn’t do a clean install and get rid of my WinXP. At least WinXP boots!
Could somebody out there please help me out! I only just fixed my desktop and the freaking screen analysis in Ubuntu, a process that took me for ever, but I enjoyed it a lot!
I have looked through the forums and Google, but can’t seem to find someone that has dealt with a similar problem… I also have a PCLinuxOS disc and I am just dying to kill Ubuntu just to get into the Linux environment again…
Please help guys!
Thanks in advance.

P.S. Excuse my attitude, I am a pleasant person, but I so am pissed off because I REALLY LIKE UBUNTU and have already not slept before 4 am for 3 days just playing around on it plus I have printed out miles of tutorials and articles that I have been reading!!! Now that I can’t get it to work it is just making me feel so angry

---

### Post by xopher on 2007-03-10
Great to see that linux makes you angry! Every emotion it creates is one towards perfect unity ;) haha, well, let's see what could be causing your problem.

Did you alter anything (at all) in the session before you (re)booted? Eg. installed some applications, altered some configuration files, kernel?

Have you tried to do a safe boot? And when in GRUB, press e when the kernel your booting from is selected, then remove quiet from the boot line, and press b when done editing, this will boot the kernel in verbose mode, and you'll see what's going on -- and where it dies. Gets us a lot closer to what's causing your problem.

---

### Post by easyease on 2007-03-10
yep dont give up on ubuntu just yet, im sure we can get things right.

---

### Post by Toxic-Waste on 2007-03-10
Thanks guys for the fast reply! I fill more confident that the problem can be fixed now that you are backing me up. I am about to restart my system and do as Xopher said. 

 > **xopher said:**
> And when in GRUB, press e when the kernel your booting from is selected, then remove quiet from the boot line, and press b when done editing, this will boot the kernel in verbose mode, and you'll see what's going on -- and where it dies. Gets us a lot closer to what's causing your problem.

When done, I will get back to you with results!

Oh as for the question you asked Xopher, I did alter some things :) . Well... 

[INDENT]1. I modified the xorg.conf to get my ATI drivers to play and to have the resolution that I needed so bad. I followed instructions on this page [_http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide_]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") I am doing everything on a 15.4" laptop and I needed 1280x800 resolution. 
2. The other thing I did was that I followed a HOW TO to install Compiz... Yeah, look at me, the noob wants to do everything in one go! No wonder I messed things up... Anyway, I modified the xorg.conf again doing everything specified on this page [_http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/_]("http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/"). 
That is about it, well that and that 
3. I installed many things with Synaptic, things like Desklets, Download managers, Torrent downloaders, ect.[/INDENT]

**Important note:**The funny thing though, is that I had rebooted a couple of times since then before I turned of... I did have a similar problem, It would do the same thing, freeze at startup like now, but when I pressed Ctrl+Alt+Del, the screen would go all funny and Ubuntu would boot. The main thing is that it booted. After I shut down, went to bed, then is when this happened.

Well, off to do what you suggested. Be back soon with more info!
Thanks a million!

---

### Post by Toxic-Waste on 2007-03-10
Ok, I followed the instructions (I hope I followed them correct) and this is what happened. I have taken shots with my mobile phone so you can have a better view of things.

So this is what I did:

[INDENT]1. I have chosen the Ubuntu kernel to boot and before booting I have pressed **e** to get into the menu.

[IMG]http://www.papaspyropoulos.com/img/ubuntu/DSC00722.jpg[/IMG]

After removing the** quiet** I pressed **b** to boot

2. This is when the Boot screen freezes. It freezes at the exact same time and my hard disk just stops working at this point.

[IMG]http://www.papaspyropoulos.com/img/ubuntu/DSC00723.jpg[/IMG]

3. After waiting 5 - 10 mins, I press **Ctrl+Alt+Del** and the Hard Drive starts working again and the loading bar starts moving on! Yeah! (or so I thought...). Then the screen gets all messed up .... :mad: like in the screenshot.

[IMG]http://www.papaspyropoulos.com/img/ubuntu/DSC00724.jpg[/IMG][/INDENT]

That is it! I don't know what to do now. I am a Linux noob and I will keep the faith for as long as possible. Even if there is no way out of this, I will try another Linux distro. If I face similar problems with other distos I will have to switch back to WinXP or even Vista. I really don't like Windows, but if I can get my job done without any trouble....:( 

Anyway, thanks again!
Looking forward to any available help!

---

### Post by pveith on 2007-03-10
At the time Ubuntu stop booting, please try to press "<ctrl><alt><f1>" together to get to an terminal, login and here a some steps to get back to an working Xorg-Session.

```

sudo invoke-rc-d gdm stop
sudo dpkg-reconfigure xserver-xorg

```

This reconfigures your X-Server and after that do

```

sudo invoke-rc-d gdm start

```

And then you should have your X back. If you want to backup your previous X-config copy the file xorg.conf, before the reconfiguration command.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-org

```

Hope that helps...

---

### Post by Toxic-Waste on 2007-03-10
Ok thanks! Will go try it out now and get back to you... hopefully from my Firefox in Ubuntu!
Be back soon!

---

### Post by Toxic-Waste on 2007-03-10
> **pveith said:**
> At the time Ubuntu stop booting, please try to press "<ctrl><alt><f1>" together to get to an terminal, login and here a some steps to get back to an working Xorg-Session.

I tried this and nothing happened. Even after I pressed "<ctrl><alt><f1>" together, nothing happened.

Any other ideas?

---

### Post by pveith on 2007-03-10
Now we have to get a little bit dirty: Let's try to deactivate X and splash through grub to get a working terminal.

On boot press <esc> and <e> on the default boot option. Edit the vmlinuz line, changeing "splash" to "nosplash" and remove the quite option. Then boot this setting.

This should output lots of messages in a terminal window and -if my guess ist right- try to start Xorg and fail. But this should leave you with a working terminal and you can try the steps mentioned before.

Hope that helps.

(Sorry for the long response time, had to leave my computer for a while.)

---

### Post by Toxic-Waste on 2007-03-10
Hey Pveith, 
Don't worry about the response time man! Thanks for helping out in the 1st place! :) .
I will try this out now and get back as soon as possible.

Later!

---

### Post by Delvien on 2007-03-10
> **Toxic-Waste said:**
> Hey Pveith, 
Don't worry about the response time man! Thanks for helping out in the 1st place! :) .
I will try this out now and get back as soon as possible.

Later!

What kind of vid card are you running and what kind of driver are you using?

---

### Post by falcons7 on 2007-03-10
I've Had the Same problem installing ubuntu for my friends.... It is your xorg.conf


you might want to revert it.... if you used a script to install your drivers most likely you have a backup automatically created.

when you boot... select recovery mode and either try to navigate to the folder

cd /etc/X11/

then ls
see if you have any xorg.conf files that have a ~ at the end or named backup.....

if you cannot copy them using the command:    sudo cp xorg.conf~ xorg.conf

try modifying the files driver from ati to vesa located in the xorg.conf file

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

thats how mine looks just change where mine says nvidia to vesa

---

### Post by Toxic-Waste on 2007-03-10
Thanks,
Will give it another try...

I hate not having the proper knowledge for this...
Why do things have to be so complicated?

Oh, I am using the ATI X1600 Mobility and am using drivers found in Synaptic

---

### Post by Toxic-Waste on 2007-03-10
Hey Falcons7!!!
This is a reply from my UBUNTU FireFox Browser!!!
HURRAY!!!

If anybody else has the same problem don't go through the Thread, just look in the quotes below.

**THE SOLUTION IS IN THE QUOTES** :popcorn: 
> **falcons7 said:**
> I've Had the Same problem installing ubuntu for my friends.... It is your xorg.conf


you might want to revert it.... if you used a script to install your drivers most likely you have a backup automatically created.

when you boot... select recovery mode and either try to navigate to the folder

cd /etc/X11/

then ls
see if you have any xorg.conf files that have a ~ at the end or named backup.....

if you cannot copy them using the command:    sudo cp xorg.conf~ xorg.conf

try modifying the files driver from ati to vesa located in the xorg.conf file

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

thats how mine looks just change where mine says nvidia to vesa
:lolflag:

I would like to THANK, all you guys for your help!!!
THANKS!

P.S. I solved the problem by following the copy command. Just out of curiosity, how do I edit a file from command line?

---

### Post by falcons7 on 2007-03-11
sudo pico filename

---

### Post by Toxic-Waste on 2007-03-12
Thanks again!
:lolflag:

---

### Post by hyper_ch on 2007-03-12
Well, still you need to get the ati drivers running well... there are some howtos here in the forum that may help you... I have a nVidia card so I can't really help you there :)

Good luck :)

---

### Post by Toxic-Waste on 2007-03-12
Thanks Hyper_ch I will check them out

---

