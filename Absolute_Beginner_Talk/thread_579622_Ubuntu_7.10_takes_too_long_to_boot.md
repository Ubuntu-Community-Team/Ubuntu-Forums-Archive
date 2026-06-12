---
title: "Ubuntu 7.10 takes too long to boot"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by yabune on 2007-10-18
I've just installed Ubuntu 7.10 but it takes too long to get the login screen..

When I choose the Ubuntu from the boot menu, the screen gets blanks and it takes some time until the login screen shows up.

Any guesses?

thanks!

---

### Post by orange2k on 2007-10-18
I don`t have that problem. Since I upgraded to Gutsy a couple of days ago, it boots even faster...

Edit: what are your system specs?

---

### Post by yabune on 2007-10-18
Laptop Toshiba Tecra A5
Intel Pentium M 750 1.86Ghz
1Gb DDR RAM
ATI Mobility Radeon X600SE 128Mb

---

### Post by rgraves22 on 2007-10-18
Ive been running gusty RC for a week today.. and it works great, boots fast... grub issue maybe?

---

### Post by steveneddy on 2007-10-18
You should install bootchart and look at your logs in /var/log/bootchart

It gives a graphical representation as to what may be taking so long to load.

I used it recently to find a problem when I went from 32 to 64 bit Feisty.

I am on Gutsy 64 bit now and the boot time is literally a third of the time. Almost 12 seconds from cold to login prompt.

:popcorn:

---

### Post by jackflap on 2007-10-18
I take it the splash-screen isn't coming up. Meaning you just get a blank screen and then you get your log-in window. 

I've found this to happen on a couple of computers, and the fact that it's a blank screen sometimes makes it SEEM like it's taking longer than it actually is since you can't see what it's doing, so you're waiting and it seems like it's not making any progress.

The following howto is an in-depth explanation and solution to this problem:

[http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash](http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash)

Regarding the long boot-times, I'm unsure, press alt+f2 or alt+f1 (cant remember now) to watch what linux is doing while it's booting up. If you see it running fsck and checking the disks, then that could be a reason, it only checks the disks every so often, so I wouldnt worry about it. Maybe if your bios battery is dead, it's checking the disks on every boot though. Could be a number of other things, let us know what you find.

Alex

---

### Post by orange2k on 2007-10-18
Im not sure. Have you installed the restricted drivers for your graphic card?

On the other hand, there is a known bug with the missing splash/boot screen if I understand correctly. Sorry I couldnt help...:confused:

---

### Post by insane_alien on 2007-10-18
go for boot chart. we will be able to see whats holding your booting up. could be a networking issue(random but it has happened before)

---

### Post by compiledkernel on 2007-10-18
orange2k. 

sudo cat /var/log/dmegs > ~/dmesg.txt
sudo cat /var/log/messages > ~/messages.txt

Those two commands should dump the two txt files into your home directory , just copy and paste their results in this thread.

---

### Post by phr0ze on 2007-10-18
> **jackflap said:**
> I take it the splash-screen isn't coming up. Meaning you just get a blank screen and then you get your log-in window. 

I've found this to happen on a couple of computers, and the fact that it's a blank screen sometimes makes it SEEM like it's taking longer than it actually is since you can't see what it's doing, so you're waiting and it seems like it's not making any progress.

The following howto is an in-depth explanation and solution to this problem:

[http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash](http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash)

Regarding the long boot-times, I'm unsure, press alt+f2 or alt+f1 (cant remember now) to watch what linux is doing while it's booting up. If you see it running fsck and checking the disks, then that could be a reason, it only checks the disks every so often, so I wouldnt worry about it. Maybe if your bios battery is dead, it's checking the disks on every boot though. Could be a number of other things, let us know what you find.

Alex

This is probably my problem. What I don't get is why this is happening. The boot splash worked in Feisty and it worked on the Gutsy Live CD. Now you say grub is suddenly behaving different? I just tried setting it to 1024x768 (vga=791) and it didn't work. I can keep taking guesses but can't I just see what the CD used?

---

### Post by yabune on 2007-10-18
thank you for the fast support :)

how do I use boot chart?

I've installed it from Synaptic Packet Manager but I can't find it in Applications menu...

---

### Post by jackflap on 2007-10-18
I would definitely try 800x600 before making any conclusions.

To be honest, I've never really bothered figuring this out, whenever this happens to me, I just go into my menu.lst and add nosplash to the kernel line, and just watch Linux init it's stuff instead. Better than a blank screen, but yeah, it's dumb how it works on the live cd, but not on the install.

---

### Post by Paul820 on 2007-10-18
You need to reboot your computer, then go to places->computer->filesystem->var->log->bootchart. It will be a .png image.

---

### Post by yabune on 2007-10-18
here it is bootchart result...

---

### Post by Johan_SV on 2007-10-18
I think you can fix the black boot screen by entering the correct resolution in the /etc/usplash.conf file.

---

### Post by ebichete on 2007-10-18
Turn off the splash screen by using the "nosplash" instructions previously posted. That should get you booting in reasonable time.

Then go file a bug in launchpad (against usplash) about usplash slowing your login by wastefully burning CPU. Include all the info you gave in this thread (bootchart etc...).

---

### Post by steveneddy on 2007-10-18
> **ebichete said:**
> Turn off the splash screen by using the "nosplash" instructions previously posted. That should get you booting in reasonable time.

Then go file a bug in launchpad (against usplash) about usplash slowing your login by wastefully burning CPU. Include all the info you gave in this thread (bootchart etc...).

I agree - usplash is the culprit.

Follow ebichete's advice by disabling the usplash and filing a bug report.

---

### Post by yabune on 2007-10-18
sorry, I didn't get how to disable usplash...

where do I change that?

---

### Post by rogerdean on 2007-10-18
hi yabune

i had exactly the same problem as you, and this thread has solved it with the usplash trick. thanks for that!

to disable, go to the terminal and type -

sudo gedit /boot/grub/menu.lst
...and enter your password

a big text file will open - you need to scroll right down to where it says ...


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash


...or similar. just change 'splash' to 'nosplash' and save. reboot and celebrate!
cheers
roger

---

### Post by yabune on 2007-10-19
> **rogerdean said:**
> hi yabune

i had exactly the same problem as you, and this thread has solved it with the usplash trick. thanks for that!

to disable, go to the terminal and type -

sudo gedit /boot/grub/menu.lst
...and enter your password

a big text file will open - you need to scroll right down to where it says ...


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash


...or similar. just change 'splash' to 'nosplash' and save. reboot and celebrate!
cheers
roger

Problem solved! Thanks!!!

---

### Post by mossop on 2007-10-19
Thanks rogerdean (+ yabune) I've had the same problem and this solution worked for me too.

Can I still ask someone though, if i have a widescreen on my lappy (1280x800), what res should I use? 800x600?

Johan_SV Re: Ubuntu 7.10 takes too long to boot

--------------------------------------------------------------------------------
I think you can fix the black boot screen by entering the correct resolution in the /etc/usplash.conf file

---

### Post by ecrissman on 2007-10-19
Thanks.  But same question as last post.  With a 1280x800 monitor could I change the usplash resolution to 800x600 if I still want it?

---

### Post by monstar on 2007-10-19
I removed all signs of QUIET/SPLASH and my boot times went from 5 minutes to under 1 minute.

Now if only I could get my damn Broadcom AF1 to work.. =[

---

### Post by YoungPastor on 2007-12-13
Bingo! I had just been dealing with the long boot because everything else worked so well. Thanks for the help, this easy fix solved my long boot problem on a Presario US2100 laptop.

---

### Post by Dngrsone on 2007-12-31
Anyone know if there is  fix on the way for this?

The nosplash trick worked for me on my Dell Latitude C610, but it feels like a hack and not a real solution.

---

### Post by philinux on 2007-12-31
Take a look at the link for know bugs workarounds.

Also installing and running startupmanager has worked for a few people.

---

### Post by ityro on 2008-02-05
Thank You rogerdean.

---

### Post by xpod on 2008-02-05
Having been a happy Ubuntu(gnome) users since the day i first stumbled across Ubuntu(6.06)back in July 06 i was always happy enough with the boot times. etc.......especially on the old/er pc`s in question i`d been using along the way.
I`d tried the Xubuntu(XFCE) & Kubuntu(KDE) offerings,both by separate HD installs and by installing the two desktops within my current Ubuntu(Gnome) machine of the time.
I`ve also tried  numerous lightweight distro and base installs.
My 7Yr old daughter still insists on keeping her Puppy installation on her own pc in fact.....who am i to argue:)

Ubuntu(gnome) though just seemed the easier one to navigate,it seemingly had more handy utilities and was overall a more friendly seeming approach...imho.
Thats without mentioning the fact that Ubuntu(Gnome) was the first ever "Linux"i  stumbled across,the first one i downloaded and indeed the first one i installed & got to know......the little i do know anyway.
My first love as it were.....Linux Love that is8-[

I`d done all the usual tweaks to speed things up but it was`nt until a discussion i had elsewhere about the speed of Gnome that i went and downloaded the Xubuntu cd just to have a wee look see.
It had been well over a year since i`d last had a look a it after all.

Shock,horror,stun ....it was just so damned fast(compared to Ubuntu ala Gnome) and any of those little bits i missed from Gnome are of course easily installable in Xubuntu.  By then it was already installed on the 2nd drive in the pc of the moment.
I have an xfce base install on a lappy somewhere and even *thats* a bit tardy in comparison.Far less oomph of course.

I just bought the makings of a shiney new box back in January,with an AMD64 dual core 2x 2.1Ghz cpu and 2 G of dual channel ram,
Few seconds to boot,shutdown and most apps open instantly.
Xubuntu does indeed run good on older hardwrae but it makes  new/er hardwrae run even faster.
"Vista Ready" machine of course but complete overkill for lil ole me:rolleyes:

Just an option to consider though.One of many in fact:)
Good luck either way.

---

### Post by Thug14 on 2008-02-20
thnx a lot m ate helped me a lot

---

### Post by mcdan on 2008-02-25
i used to have the same problem, the reply #9 by orange2k on this forum
[http://ubuntuforums.org/showthread.php?t=579684](http://ubuntuforums.org/showthread.php?t=579684)
solved my issues.  i think it has something to do with my widescreen monitor, but i'm not sure.  
i also found out that if i install fiesty, then upgrade to gutsy through the system update manager, this preserves the bootsplash screen from fiesty that worked fine with my system.  good luck

---

### Post by mcdan on 2008-02-25
u can change the boot splash resolution in StartUp-Manager

---

### Post by slimordium on 2008-02-26
This "fix" did not change anything for me. I have a Dell XPS 410, Core 2 Duo , Nvidia geforce 8300 gs, clean install of Gutsy, also tried Heron and had the same problem. System freezes after at a round wait icon.

---

