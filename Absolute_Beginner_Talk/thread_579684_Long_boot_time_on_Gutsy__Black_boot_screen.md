---
title: "Long boot time on Gutsy / Black boot screen"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Johan_SV on 2007-10-18
I just installed Gutsy and experienced a black boot screen when launching it, and it also took about 3 minutes to get to the login screen. With Feisty it only take about 40 seconds.

I have attached a bootchart. Could somebody please help me with this? Thanks.

---

### Post by steveneddy on 2007-10-18
Very odd - look at [this thread]("http://ubuntuforums.org/showthread.php?p=3560142#post3560142"). Same issue.

:popcorn:

---

### Post by dptxp on 2007-10-19
Same here on ACER 5101

---

### Post by dragonlor20 on 2007-10-26
Same problem with fresh Gutsy i386 install on a Compaq Presario V2000 with AMD Turion64. For the record, the 64bit Gutsy was also very hesitant to install on my system (and by hesitant I mean it would not install under the normal graphic interface at all).

On a sidenote, it seems that Ubuntu never tires of the irony of needing a hardwired internet connection to get the Broadcom 4318 series functioning. HOWEVER, this version at least made it easy once you were plugged in with the expanded restricted driver support. The 3D desktop I had under Dapper seems to never be coming back to my Radeon mobile though :-( I suppose it was nice while it lasted...

---

### Post by swisscow on 2007-10-26
Had the same problem - this solved it for me

- editing /etc/usplash.conf to 1024x768 (SET THIS TO YOUR SCREEN RESOLUTION DIMENSIONS)
- running ```
sudo update-initramfs -u -k `uname -r
````

---

### Post by afeasfaerw23231233 on 2007-10-26
how to get that bootchart?

---

### Post by dragonlor20 on 2007-10-26
> **swisscow said:**
> Had the same problem - this solved it for me

- editing /etc/usplash.conf to 1024x768 (SET THIS TO YOUR SCREEN RESOLUTION DIMENSIONS)
- running ```
sudo update-initramfs -u -k `uname -r
````

That solution did not work for me. What it did was allow my ubuntu logo to be displayed as the system was shutting down (and it seemed to speed up shutdown, so perhaps it was a half solution), but the boot up was still painfully long.

What did work was going to the menu.lst and changing "splash" to "nosplash." Granted this is a workaround, but I am not terribly in love with boot screen splashes anyhow... I do believe that I am going to go ahead and kick my resolution down to 800x600 and see if we get any better results with that though.

---

### Post by joop905 on 2007-10-26
To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

---

### Post by orange2k on 2007-10-26
I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

---

### Post by xAnarChisTx on 2007-11-01
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

I gotta say thank you very much!  Before doing this, the screen was blank and it took at least 10 minutes for it to load Ubuntu.  Now, 30 seconds.  Again, thank you!

---

### Post by dragonlor20 on 2007-11-01
> **swisscow said:**
> Had the same problem - this solved it for me

- editing /etc/usplash.conf to 1024x768 (SET THIS TO YOUR SCREEN RESOLUTION DIMENSIONS)
- running ```
sudo update-initramfs -u -k `uname -r
````

You forgot a ` that will give some people problems. The update code should look like the following:

```
sudo update-initramfs -u -k `uname -r`
```

---

### Post by jnhatch on 2007-11-01
I have the same problem, but I am having trouble following the instructions given, I need them to be a little more specific since I have never used linux before.  How do I go aout editing my screen resolution?

---

### Post by mcdan on 2007-11-01
orange2k's method worked great for me, cut boot time down from 3 minutes, to under 1 minute

---

### Post by dioxip on 2007-11-06
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

Thanks :D

---

### Post by skoal on 2007-11-06
orange2k,

We had a couple of Dallas city and Texas state bonds to vote on today, in value of over $135 billion. I was so enthused after finally getting my usplash to work, I penciled in a new ballot (on your behalf) as Proposition 34 - "The Constiutional Amendment for issuance of $500 million in general obligation bonds payable to orange2k on behalf of his ubuntuforums.org usplash solution." Just in case, I also penciled in a more affordable alternative as Proposition 35 - "The construction of a 60 foot bronze edifice of orange2k's likeness in front of the new Dallas Cowboys football stadium."

Good luck. And Thanks.

\\//_

---

### Post by darkstar01uk on 2007-11-09
Cheers orange2k your fix worked great for me. I have a Dell Inspiron 1501 and boot time was cut from an eternity - about 4 mins I think - to < 30sec.
Gutsy works well on this lappy, my Broadcom wireless and ATI graphics restricted drivers installed and worked straight away. Nice one, developers.

darkstar

---

### Post by ConfidentiaL on 2007-11-09
> **jnhatch said:**
> I have the same problem, but I am having trouble following the instructions given, I need them to be a little more specific since I have never used linux before.  How do I go aout editing my screen resolution?

Try [this]("http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html") guide

---

### Post by Jova on 2007-11-09
Nothing above works from me. I have an asus wd193 wide screen monitor 1440x990, so it can support 1280x1024 resolution. All works fine with may old nvidia 6600 video card. But problem occurred:( when I change it with an nvidia 8400. But with other distros fedora, opensuse I have not this problem. So for now i'm switch off splash screen so I can have interaction  if some booting problem appears.

---

### Post by iiviip3 on 2007-11-12
Orange2k's suggestion worked perfectly for me. Got me from 3 minutes down to about 35 seconds. The only difference is that the splash screen for shutting down is so dark and pixelated I can barely make it out. Any suggestions for a fix would be greatly appreciated. Thanks!

---

### Post by drdrez on 2007-11-12
not sure if issue is similar.

I have had fiesty installed on my dell xps 410 desktop for the last week.  it is using a 7800 (i believe) nvidia card.  Ubuntu is on a 20 gb partition that is dual booting with Vista.



It was working fine, then i tried installing KXmame (i'm a sucker for old school arcade games)

it was working last night,  i played around with it this morning, rebooted and now after the ubuntu loading screen, i get a black screen with the mouse cursor showing it is busy.  i can leave it on for 20 minutes and nothing.  

i tried both reinstalling/updating the nvidia driver as well as installing envy (did this through recovery mode) and still same result.





Thanks in advance

---

### Post by drawkcab on 2007-11-14
Same thing.  I'm running a laptop (amd64 + Radeon 9600).  Installation was easy.  Gutsy just hangs forever on boot with the aforementioned black screen.  And my broadcom wireless card no longer works, although the last update to feisty didn't work either.  :(

I guess I'll try opensuse and simplymepis.  Maybe I'll come back for the next release.

---

### Post by VCSkier on 2007-11-14
I've got an ATi Radeon Mobility 9000, and orange2k's fix brought my boot time from over 3 minutes of a blank screen to exactly 30 seconds with bootsplash.  Thank you so much!

Also, that StartupManager tool is great.  I've never seen it before, but its great for easily tweaking things.

---

### Post by GaryLittlemore on 2007-11-14
This has also fixed my HP NX9005, Thanks Orange2k

---

### Post by Anias1092 on 2007-11-20
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

this seems great and as though it would work but i am such a newb i have no idea how to edit those with the exception of the screen resolution.

If i try to edit them in terminal it eather day i don't have  permission and when i give my self permission it says:

"Error: no "edit" mailcap rules found for the type "application/*"

Can anyone tell me in a bit more detail how to do this, thanks

---

### Post by crjackson on 2007-11-20
Glad I found this.  The 1st method won't work on one of my machines.  I can't wait to try orange2k's fix this weekend.  I sure hope they FINALLY fix boot splash problems in the LTS version.

I can't help but say this.  The boot problem has been around since at least 7.04.  I feel like more people would adopt the big U, if they didn't have this problem right out of the gate.  A perm. fix for this needs to happen ASAP.

---

### Post by rtmhal on 2007-11-22
IBM ThinkPad R50 corrected long boot time by editing /etc/usplash.conf 
setting resolutionto 1024x768 and running sudo update-initramfs -u -k `uname -r

---

### Post by crjackson on 2007-11-22
Too bad for me...  None of the solutions posted helps my system.

---

### Post by john262 on 2007-11-22
> **crjackson said:**
> Too bad for me...  None of the solutions posted helps my system.
Me either. Does anyone know when this bug will finally be fixed, or will we have to live with it forever?

---

### Post by Bigbird999 on 2007-11-22
> IBM ThinkPad R50 corrected long boot time by editing /etc/usplash.conf
setting resolutionto 1024x768 and running sudo update-initramfs -u -k `uname -rYou are missing the last backtick ` after -r  It will not work without it.. I screwed around for 2 days before I found that was the problem.
 The proper code is 
[HTML]sudo update-initramfs -u -k `uname -r`[/HTML]
Note that the ` are backticks (on the top left of the keyboard on the ~ key) not an apostrophe ' (left of the enter key)

BB

---

### Post by piousp on 2007-11-25
Ok, i had the same black-boot screen problem in Kubuntu AND Ubuntu (prob Xubuntu too)
I have a dell I6400 with an ATI Radeon x1400.

This is what i did to solve the issue:

```
sudo gedit /etc/usplash.conf
```
Set the resolution you want, then
```
sudo dpkg-reconfigure usplash
```
And it worked. Hopefully works for you too.

---

### Post by walkere on 2007-11-25
I've been struggling with this problem for a few days...

One solution I found that worked was to completely disable the splash screen altogether.  After doing that, the boot time went from 3-4 minutes to ~30 seconds.

I initially checked the resolution setting for the splash and it seemed fine - it was supposed to load up at 1024 x 768.  After Ubuntu loads up, the screen displays at that resolution just fine.

However, I found that while the computer is booting up and powering down, the monitor switches to a much lower resolution.  When it was trying to load at 1024 x 768, it was loading at some weird resolution like 700 x 440 (I checked by hitting the settings button on the monitor).  At that point, no splash screen loaded, I got a blank black screen at start up, and booting was taking 3-4 minutes.

I tried implementing the changes that were suggested earlier in the thread, and they didn't seem to help.

I then downloaded Startup Manager and changed the splash settings to the lowest display settings - 640 x 480, 8-bit color.  Now it works fine.

Booting takes ~30 seconds and I get a splash screen.  If you're still having trouble, try setting the splash settings as low as possible - even if your computer should be able to display at a higher resolution.

- Walkere

PS:  This was on a Gateway Desktop, Pentium 4 1.8 Ghz, Intel Graphics Card, 17" Flat Panel Monitor, 256mb RAM

---

### Post by hcrusher on 2007-12-02
> **piousp said:**
> Ok, i had the same black-boot screen problem in Kubuntu AND Ubuntu (prob Xubuntu too)
I have a dell I6400 with an ATI Radeon x1400.

This is what i did to solve the issue:

```
sudo gedit /etc/usplash.conf
```
Set the resolution you want, then
```
sudo dpkg-reconfigure usplash
```
And it worked. Hopefully works for you too.

Yes this one works perfectly. The solution is often easier than we thought:)

---

### Post by exohuman on 2007-12-06
>  Originally Posted by orange2k  View Post
I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

That worked for me! Thanks.

---

### Post by Pgi947 on 2007-12-14
> **hcrusher said:**
> Yes this one works perfectly. The solution is often easier than we thought:)

Works perfectly for me too :-) just reset the default resolution from 1280x1024 (not supported on my laptop) to 1280x800 and it works fine, no more 10min boot times :-D

---

### Post by egraves7 on 2007-12-14
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u
Thanks! That worked for me too!

---

### Post by staticvoid on 2007-12-15
> **joop905 said:**
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

this is the cleanest way

---

### Post by brad1138 on 2007-12-15
Ideally how fast should it be? I seem to remember with Feisty it being almost instant (less than 5 secs anyway) Mine has been taking 10-20 sec which seems long to me. 

Brad

---

### Post by Gunner_Sr on 2007-12-22
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

Perfect! I have been looking for this. The only problem left is that it is not holding the set resolution.

Cheers,

Gunner_Sr

---

### Post by neotasic1 on 2007-12-22
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

This suggestion by orange2k works perfectly for me.  Some of the suggestions to prevent the slow bootup (removing splash and quiet entries from /boot/grub/menu.lst) work, but will disable the splash screen and generate text rolling across screen at bootup - not a problem but not as pretty.  If you leave the entries in and add vga=791 to this file (as I read suggested in several posts) you will get your splash screen, but will lose your terminals that are normally accessible using the CTL+ALT+F1 - F6 key combination - a function that I believe is important on a Linux box - more important than a pretty splash screen. (Incidentally, the vga=691 is only applicable to the resolution stated by orange2k in his post. You can set up a different resolution, and I did read a post earlier this month giving a matrix of various resolutions, but have lost the bookmark to that thread - perhaps the original poster can illuminate - this could be the solution for those who cannot set this resolution on their machines.)
Also an update this month appears to have written the vga=791back to the menu.lst file as I had explicitly removed it because of the black terminals problem, and it mysteriously reappeared after the update, along with the missing terminals.  The above solution seems to fix it all.  Thanks again orange2k.

---

### Post by philinux on 2007-12-22
See the link for known bugs. Also startupmanager from synaptic as already stated is a neat little app.

---

### Post by Sean K on 2007-12-22
orange2k's fix worked perfectly for me. Thanks!

When I boot up, I used to get a message after GRUB saying "Video Mode Not Supported" instead of the boot splash screen. Then, it would load the login screen and everything would be normal after that. With his fix I see the splash screen now, and no ugly error message about it not being able to support my video mode.

---

### Post by mikerduffy on 2007-12-27
I was able to fix my slow, blank boot by:

-Installing StartUp-Manager
-Using StartUp-Manager to set the boot resolution to 1024x768 with 16bit color depth.

My desktop resolution is 1280x800x24, and StartUp-Manager did not in any way affect my desktop.  My boot went from a black 3 minutes to a colorful 30 seconds.

---

### Post by madflyguy on 2008-01-11
Thanks swisscow
after I changed my resolution setting at /etc/usplash.conf (my res is set to 1440x900) I ran;
```
 sudo update-initramfs -u -k `uname -r`
```
and it worked.
**BTW** your code section ends before " **`** " at the end of the command argument, took a newb like myself a while to figure out why the command wasn't working lol  
:popcorn:

---

### Post by Nythain on 2008-01-16
so i dont use usplash at all... i prefer to watch everything scroll by so i know whats what, whats ok, what fails, and when it wants to fsck and all that jazz.

In previous releases (fiesty backwards) all i had to do was remove
quiet splash
and add
vga=79X
to change resolution to something more readable (big letters = less on screen = hard to catch errors before they scroll by)

now when i try it, it cuts to an out of range blackness or a video mode not supported error.

Im assuming that even though i dont use usplash this is the guide for me, since the problems are derrived from the same source.

So my questions, anyone think/know if this will fix my problem, and wich modules does ATI use, is it the radeon module or the vesa/vga module as explained here
[http://ubuntuforums.org/showthread.php?t=585454&highlight=gutsy+grub+resolution](http://ubuntuforums.org/showthread.php?t=585454&highlight=gutsy+grub+resolution)

not that any of this really matters anymore, as its now a headless server, but i do randomly kvm over to it for regular maintenance and random downtimes... thanks

---

### Post by Borbus on 2008-01-18
I don't use usplash either and I wanted to get the ttys at my monitor's native resolution. The only way I could get it to display something was without a framebuffer (vga=normal). I tried orange2k's post and it seemed to be working great, ttys were at the right resolution, but then when X started Gnome said it couldn't start the settings daemon so Gnome looked crap. I've set it back to how it was now because tbh I use Gnome more than I see the boot process...

---

### Post by ubuntu-freak on 2008-01-18
With Startup Manager you can have usplash with text underneath. I've forgotten the command to do it manually. SUP is worth having though.
 
If anyone still has problems and they have a windows partition, try my how-to
 
[http://ubuntuforums.org/showthread.php?t=663214](http://ubuntuforums.org/showthread.php?t=663214)
 
Nathan

---

### Post by Jeffva on 2008-01-18
> **swisscow said:**
> Had the same problem - this solved it for me

- editing /etc/usplash.conf to 1024x768 (SET THIS TO YOUR SCREEN RESOLUTION DIMENSIONS)
- running ```
sudo update-initramfs -u -k `uname -r
````

Thanks!  Worked liked a champ for me.

---

### Post by Borbus on 2008-01-22
Ok, I tried this again, I installed startupmanager. I set the splash screen to 1280x1024 at 16 bit. The splash screen worked fine, with text, but my other ttys did not display anything. I then followed orange2k's post again and now everything works fine, splash screen is there, ttys work at proper resolution, and gnome settings daemon started up fine (not sure what happened the first time I tried it, maybe because I didn't use startupmanager?).

---

### Post by ubuntu-freak on 2008-01-22
> **Borbus said:**
> Ok, I tried this again, I installed startupmanager. I set the splash screen to 1280x1024 at 16 bit. The splash screen worked fine, with text, but my other ttys did not display anything. I then followed orange2k's post again and now everything works fine, splash screen is there, ttys work at proper resolution, and gnome settings daemon started up fine (not sure what happened the first time I tried it, maybe because I didn't use startupmanager?).

 
SUP shouldn't do anything untoward. It just edits how you would manually. Having said that, does seem to make the boot super quiet, which is good, but your disk check (every 30 mounts) might end up just being a black screen with no text. Don't want you thinking it's a hard lock crash and switching off/restarting. 
 
Nathan

---

### Post by Philio on 2008-01-24
Finally got my splash screen working, after hours of searching forums for a solution!!!

My system is 680i, QX6700, 8800 GTX, 4Gb

I had to use a combination of solutions posted in this thread.

I installed Startup Manager and changed the resolution which added a vga=xxx and changed /etc/usplash.conf

At this point with still got black screen, no X, so disabled the splash screen. My system now went from grub to a black screen for 10 secs or so and into X.

I added the fix posted by Orange2k, rebooted and I got text (fb was working), re-enabled splash and it works perfectly!

---

### Post by dbqp on 2008-01-26
IBM T30 running 7.10 with a VERRRY slow startup.

Using Orang2K's solution worked like a charm and is down to about 30-45 sec on startup and sped up the shut down too!

MANY THANKS! It was so discouraging having to reboot or shutdown for the night.

---

### Post by chlee on 2008-02-01
hello hello
^- noob

im using a compaq presario v2000, amd turion 64, ati .. etc.. with ubuntu gutsy.

i have only been using ubuntu a few days and its much nicer than i expected! yay! 

BUT..

no splash/text (black blank) on boot, very long boot time and no controls for the touchpad (boo!)

anyway, using the synaptic package manager i installed startup-manager. after setting the resolution to 1024x768 (the same as my normal resolution), checking the box for 'show boot splash' and 'show text during boot'; aswell as 'use colors'..

now the boot is perfect.. i have splash with text and the boot time is much, much faster!

hope it helps!
:popcorn:

---

### Post by ubuntu-freak on 2008-02-01
> **chlee said:**
> hello hello
^- noob

im using a compaq presario v2000, amd turion 64, ati .. etc.. with ubuntu gutsy.

i have only been using ubuntu a few days and its much nicer than i expected! yay! 

BUT..

no splash/text (black blank) on boot, very long boot time and no controls for the touchpad (boo!)

anyway, using the synaptic package manager i installed startup-manager. after setting the resolution to 1024x768 (the same as my normal resolution), checking the box for 'show boot splash' and 'show text during boot'; aswell as 'use colors'..

now the boot is perfect.. i have splash with text and the boot time is much, much faster!

hope it helps!
:popcorn:

 
gksudo gedit /etc/X11/xorg.conf
 
Then copy the synaptics settings from this [thread](http://ubuntuforums.org/showthread.php?p=975421). Make sure you add "synaptics" to the modules section too. Don't forget to cut and paste all of it, including "End Section". 
 
Back it up first with (write these down)
 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
 
to restore the back up
 
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
 
To stop your cursor moving around when you type, go to System>Preferences>Sessions and add this to your start up

syndaemon -i 1 -d
 
Hope that helps.
 
Nathan

---

### Post by SIXAXIS on 2008-02-05
> **dragonlor20 said:**
> Same problem with fresh Gutsy i386 install on a Compaq Presario V2000 with AMD Turion64. For the record, the 64bit Gutsy was also very hesitant to install on my system (and by hesitant I mean it would not install under the normal graphic interface at all).

On a sidenote, it seems that Ubuntu never tires of the irony of needing a hardwired internet connection to get the Broadcom 4318 series functioning. HOWEVER, this version at least made it easy once you were plugged in with the expanded restricted driver support. The 3D desktop I had under Dapper seems to never be coming back to my Radeon mobile though :-( I suppose it was nice while it lasted...

I'm using the same laptop and the boot times are HORRIBLE. 3 minutes at least. It's slower than Windows. And with all the proper drivers installed, I still can't add any effects on the desktop.

---

### Post by ubuntu-freak on 2008-02-05
> **SIXAXIS said:**
> I'm using the same laptop and the boot times are HORRIBLE. 3 minutes at least. It's slower than Windows. And with all the proper drivers installed, I still can't add any effects on the desktop.

 
Do you have a windows partition mounted? If so, try my [how-to](http://ubuntuforums.org/showthread.php?t=663214).
 
And I posted some desktop effects info [here](http://ubuntuforums.org/showthread.php?t=686047).
 
Hope that helps.
 
Nathan

---

### Post by Ripfox on 2008-02-07
Orange2k...

Dude, you did it. This was drivin' me nuts. 

Cheers!

---

### Post by hobo on 2008-02-07
It appears this slow boot problem has been fixed in Gutsy with the latest patches. I just updated my test Gutsy on a IBM t42 and it now boots in less than a minute. I made no other changes other than the system updates. I did however, have to screw with the wireless connections to get them going. But other than that the Gutsy image is working great.   7.10 2.6.22-14

---

### Post by Ripfox on 2008-02-12
Not so much...it still does it, fresh install two days ago.

Orange2ks suggestion is the only fix I have seen work for me...

---

### Post by Tails9 on 2008-02-16
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

**step 1**: edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

**step 2**: edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

**step 3**: sudo update-initramfs -u

Sooo, how bad is it when you only complete steps 1 and 2?

(after loading the hardware drivers on boot, the whole screen fades, everything becomes unreadable, boot time increases tenfold because of a black screen until the GDM, resolution resets to 800x600 and the logs say things like: "*nvidia: module license 'NVIDIA' taints kernel*", "*NVRM: The NVIDIA probe routine was not called for 1 device(s)*", and "*No NVIDIA graphics adapter probed*")

---

### Post by xadder on 2008-02-17
I have been using another proposed method to cut-down boot times, removing the "ro quet splash" and "quiet" bits from /boot/grub/menu.lst. This works great, except that each kernel upgrade resets menu.lst back, and I have to do the change again.

The method suggested above seem to be more work than the menu.lst change, but are they more permanent? If so I'll give them a try.

---

### Post by L_V on 2008-02-24
Hope this ugly bug is solved in Hardy.... which is LTS !

---

### Post by tylerjames on 2008-03-11
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

Okay, just gotta say "thanks" for this one. It fixed my bootup time beautifully. I no longer get the black screen either.

There have been a couple interesting "blips" though. For instance, I use Gnome with Compiz Fusion and I've had no problems with it (besides occasionally losing my window borders) however now when I change the volume using my hardware buttons the Compiz volume control applet shows up and indicates that the volume is being changed **but the actual sound volume does not.** I have to use the Gnome Volume Applet to change the sound now.

Anyone have any idea what about the above command might have caused this?

Thanks ahead.

---

### Post by Stickee on 2008-03-11
> **ConfidentiaL said:**
> Try [this]("http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html") guide

Thanks, that did the trick. :)

---

### Post by GregA on 2008-03-11
I also have no normal boot splash on a Compaq Presario Laptop 2414.   I am new to Ubuntu, and have only installed about 2 weeks ago.  It was taking 3, 4, 5 minutes to get to the login prompt screen (which has normal graphics).

A very simple "half-fix" is, right after starting your pc (and after grub is loaded), just press the combo keys of ALT+F3.  You'll immediately lose the black screen and see some scrolling, unformated text, but the login screen will now appear in about 20-30 seconds vs the longer time as before.

---

### Post by martyway on 2008-03-12
Thank you orange2k. less than 40 sec on my old Dell C610

---

### Post by martyway on 2008-03-12
> **ConfidentiaL said:**
> Try [this]("http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html") guide
Thanks for the link, I'm a real noob. Those type of tutorials are heaven sent.

---

### Post by chelse on 2008-03-26
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u
Orange T

I am gobsmacked. Your solution works just fine here on a Toshiba A60 Laptop. Bootup used to take 5 minutes with no splash screen. With yoiur fix bootup - to login screen is complete in 90 seconds. However, during shutdown a sort of shadowy black/grey Qbuntu logo appears instread of the full colour one we are used to.

These difficulties were not present in Feisty Fawn - only with Gutsy.

How on earth does one find these strange fixups? What do:-

vga16fb
fbcon
vesafb

etc mean?

---

### Post by mrm48 on 2008-03-31
orange2k,

Thanks for the solution. It takes ubuntu 30 seconds to boot now, in contrast to 3 minutes before.

---

### Post by anarchy88 on 2008-04-16
Hey name is Geoff.  Just started using ubuntu and I thought the first thing  i would try to fix is the start up time.  I have been trying to use the startupmanager that seems to be working for most people, but i can not get it to install.  I went into the terminal and typed startupmanger.  It told me to type:

sudo apt-get install startupmanager

it also said i will have to enable a component called 'universe'
i could not figure out how to enable the universe component however i did type the
sudo apt-get install startupmanager  line and got this

reading package lists...done
building dependency tree
reading state information...done
E: couldn't find package startupmanager

Help on how to install this would be much appreciated i do not know if I am on the right track or not.  The simpler the better this is my 3rd day using ubuntu and I am really trying to understand it.
Thanks in advance
Geoff

---

### Post by joshrobinson on 2008-04-17
> **anarchy88 said:**
> Hey name is Geoff.  Just started using ubuntu and I thought the first thing  i would try to fix is the start up time.  I have been trying to use the startupmanager that seems to be working for most people, but i can not get it to install.  I went into the terminal and typed startupmanger.  It told me to type:

sudo apt-get install startupmanager

it also said i will have to enable a component called 'universe'
i could not figure out how to enable the universe component however i did type the
sudo apt-get install startupmanager  line and got this

reading package lists...done
building dependency tree
reading state information...done
E: couldn't find package startupmanager

Help on how to install this would be much appreciated i do not know if I am on the right track or not.  The simpler the better this is my 3rd day using ubuntu and I am really trying to understand it.
Thanks in advance
Geoff

hey Geoff, 
go to system > administration > synaptic package manager
now click settings > repositories 
on the first tab here, you will see a bunch of check boxes, read the lines before the boxes, and make sure they have checks in front of the following
main
universe
restricted
multiverse

when you have checks next to those lines, click close
hit the reload button, then click search, put in startupmanager
when it comes up, click the little box next to it and mark for installation
now click the apply checkmark, then the apply button

---

### Post by wilpolktx on 2008-04-17
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u
Thanks to orange2k!  This worked perfectly!

Wil

Presario M2000Z
AMD Turion64 ML-28
ATI Radeon Xpress 200M

---

### Post by anarchy88 on 2008-04-17
> **joshrobinson said:**
> hey Geoff, 
go to system > administration > synaptic package manager
now click settings > repositories 
on the first tab here, you will see a bunch of check boxes, read the lines before the boxes, and make sure they have checks in front of the following
main
universe
restricted
multiverse

when you have checks next to those lines, click close
hit the reload button, then click search, put in startupmanager
when it comes up, click the little box next to it and mark for installation
now click the apply checkmark, then the apply button

thank you very much

---

### Post by awilki01 on 2008-06-08
> **orange2k said:**
> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

Thanks!  This worked for me too!

---

