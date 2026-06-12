---
title: "Ubuntu vs. Debian for G3 iMac"
date: 2008-03-18
forum: Apple PPC Users
---

### Post by tjniels on 2008-03-18
I have an iMac G3/350 (PPC) which is currently running OS X 10.4.11.  The thing is, I am also running 10.4.11 on my iBook G4/800 which is much faster, has more RAM, and has a bigger HD.  In short, I don't need the iMac to be running OS X, I'd like to let it retire as a Linux-only machine.  My problem now is choosing a current distro for such an old machine.  I'd love to tell my geek friends, "Look, I've got Gutsy on an iMac G3," but I have had some initial troubles.  Here's what I've done, let me have some pointers.  I'm a n00b so be gentle, I did try to find related posts before I posted this one.

I downloaded the 7.10 live disk image for PPC, and burned it.  I used it to successfully boot my iBook G4 after a good deal of trial and error.  I attempted to boot my iMac G3 from the same disk, but the iMac spits out the CD and boots to OS X instead, even when I hold down "c" like Mac users do to boot from a CD.

The iMac has 320 MB of RAM and runs OS X 10.4.11 fairly competently, so I think it should handle Ubuntu at least as well.  I know some PPC support was dropped with 7.10, but if my PPC iBook boots fine I don't see why the iMac wouldn't.  The iBook has 640 MB of RAM, but supposedly you can still boot from the live PPC CD with just 320, exactly what the iMac has.  Even if that were an issue, I don't think it explains how the machine doesn't seem to recognize the disk.

The options I see are
1) Try the alternate install CD for 7.10,
2) Try the live CD for 7.04
3) Try the alternate install CD for 7.04,
or
4) Try some kind of Debian.

Speed is not a concern.  If it were, I would not have been running 10.4.11, I would have used Mac OS 9.2.2 or maybe 10.3.9.  What I need most is something current, that has current software, forum discussion, and support.  I'd like to give this machine another 2-3 years of life, even if it is a silly Linux toy.  If anyone has pointers, or has experience installing on this type of hardware, please help.

If you recommend Debian, can you help me find a download link?  It seems like it might be a good option, but as far as I've been able to navigate on their website is [http://www.debian.org/ports/powerpc/]("http://www.debian.org/ports/powerpc/"), and then I don't see any download links.

Thanks in advance for the help!

---

### Post by MedianMajik on 2008-03-18
*I have an iMac G3/350 (PPC) which is currently running OS X 10.4.11.   I'd like to let it retire as a Linux-only machine. My problem now is choosing a current distro for such an old machine. I'd love to tell my geek friends, "Look, I've got Gutsy on an iMac G3," but I have had some initial troubles. Here's what I've done, let me have some pointers. I'm a n00b so be gentle, I did try to find related posts before I posted this one.*

I also have an iMac G3/350 (PPC) with 192mb of ram.  Yesterday morning I installed Xubuntu 7.04 via the alternate cd using the "powerpc-install" command.  Installation was slow, but painless as everything worked right away.  I decided not to install 7.10 and the main 7.04 install cd wouldn't boot.

imho Your best bet is Ubuntu over Debian, especially if you are a noob like myself.  Debian is not newbie friendly for a linux os as I find myself on the command line a lot more than in Ubuntu.  My system is running great and will serve it's purpose as a printer/mp3 server/2nd desktop (I'm posting from it right now).

To guarantee the cd booted properly I found rather than hold down "C" I should click it repeatedly until the cd boots via orange screen flash since I'm using a generic usb keyboard and this method has worked every time for me.  After it boots up you can press "Tab" and type your installation command from the list that appears.  I used powerpc-install

If memory is a concern I would consider using Kubuntu (KDE is lighter than default Gnome) or Xubuntu (Xfce is light enough to run adequately on 128mb of ram).  Know that it is pretty easy to change your windows manager (Gnome, KDE, Xfce, etc.) without having to reinstall Ubuntu.

I hope this helps answer your questions.  I'm happy with my setup.

---

### Post by tjniels on 2008-03-18
> If memory is a concern I would consider using Kubuntu (KDE is lighter than default Gnome) or Xubuntu (Xfce is light enough to run adequately on 128mb of ram). Know that it is pretty easy to change your windows manager (Gnome, KDE, Xfce, etc.) without having to reinstall Ubuntu.

My only experience with a window manager is X11 or x.org?? under OS X.  I use it for Gimp, and used it for OpenOffice.org before I discovered NeoOffice.  I don't understand the basic function of a window manager, though.  :confused:  I should, but I haven't messed with that yet.  Could you explain the functions, features, and frills of a window manager?

> imho Your best bet is Ubuntu over Debian, especially if you are a noob like myself. Debian is not newbie friendly for a linux os as I find myself on the command line a lot more than in Ubuntu. My system is running great and will serve it's purpose as a printer/mp3 server/2nd desktop (I'm posting from it right now).

While I do enjoy messing with the Unix Terminal in OS X, and know several Unix tricks, I don't want to be forced to do things that way.  With that in mind, and based on your comment, I will stay away from Debian for now.

Finally, referring to the first quote, am I understanding correctly to think that the main difference between Kubuntu and Xubuntu is that Kubuntu would use the KDE windows manager, while Xubuntu would use Xfce?  And does standard Ubuntu uses Gnome?  If I start with Xubuntu, and later change my W.M. to Gnome, would I say I have Xubuntu or Ubuntu?  :-?

It looks like I will start with 7.04 *ubuntu, will I face any serious limitations compared to Gutsy or Hardy?  I know Hardy might not be viable on this old of a machine, but hypothetically...

Thanks for your advice, and more pointers are welcome!

---

### Post by oswaldkelso on 2008-03-18
"One Debian to rule them all, One Debian to find them, One Debian to bring them all and in the GNU/Linuxs world  bind them." 

Its true Debian can be a little harder to set up but once done it just works and works and works........It's as stable or up to date as you want.......... how to at the bottom of the page.......

---

### Post by kerry_s on 2008-03-18
go debian, don't believe the hype, it's not that hard. here's the xfce4 installer-> [http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso)

also, debian is faster and more stable. install it once and your done, no trying to keep up with releases.

---

### Post by stream303 on 2008-03-19
Just remember that when burning for an Imac, be sure to burn at a speed it can deal with.  If it is particularly old or dirty, I've heard of burning at ridiculous speeds like 2X.

I can't comment on the live-cd's, since I only run the "alternate" images, which require less ram and tend to provide better overall results, imho.

Anyone running the "alternate" installers will feel immediately at home with Debian's installer.  It is a myth that Debian is hard to install or for gurus only.  Give it a shot - I run both Ubuntu and Debian quite happily.

---

### Post by tjniels on 2008-03-19
> Just remember that when burning for an Imac, be sure to burn at a speed it can deal with. If it is particularly old or dirty, I've heard of burning at ridiculous speeds like 2X.

That's an interesting point, I hadn't thought of it that way.  I don't know (except in iTunes) how to adjust my burning speed, I do you know if that option in in Apple's disk utility?  If not, what burning tool would you recommend for OS X, as that's what I always run on my laptop, and my laptop is my only computer with a burner?

Thanks, I'll keep looking to figure out how to adjust the burning speed, but I don't know where I'd find it.

Both Xubuntu 7.04 and Debian 4.0 are both sounding practical at the moment, I bet I could handle either, and so could my machine, but I am still open to convincing.  Thanks for all posts so far!

---

### Post by stream303 on 2008-03-19
This Ubuntu burning howto is a great help:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Basically just drag your downloaded .iso image into the left hand pane of disk-utility.  Highlight it.  Then click burn.  You should see a speed option show up.  Early versions of disk-utility were reported to sometimes have a bug that it couldn't verify a burn, when in fact the burn was good.

Thanks to kerry_s!  After looking at his link above, I didn't really realize that Debian's disk 1 of the sets show up for basic gnome, Kde, or xfce.  Nice to know as I like the plain xfce for low-mem machines.

Try Debian or Ubuntu and see which one suits you better.  You can always upgrade, change your mind, etc later.  Ah, freedom!

---

### Post by tjniels on 2008-03-19
> Thanks to kerry_s! After looking at his link above, I didn't really realize that Debian's disk 1 of the sets show up for basic gnome, Kde, or xfce. Nice to know as I like the plain xfce for low-mem machines.

I downloaded Debian with Xfce, but I haven't burned it yet.  If Xubuntu can run on 128 MB of RAM, would the same be true for Debian with Xcfe?

I did manage to (somewhat) successfully boot my iMac G3/350 using the Gutsy live CD.  I kept popping the disk back in and restarting it, naive enough to expect different results, and after 7 or 8 tries it didn't spit it out, the screen flashed orange (a good sign!)

I typed "live-nosplash-powerpc" at the boot prompt, which has worked on all my other PowerPCs, and it proceeded as normal.  After running the usual checklist that says [OK] several times on the right-hand side, the machine went to a screen that said (initramfs).  It looked like a prompt, but I didn't want to spend the time figuring out what to type, as it was 3:00 in the morning!

After all this, I realized I was booting on a machine that only has 192MB of RAM - I have 3 iMacs: a 233/160, a 350/192, and a 350/320.  The 350s look identical, and I used the wrong one!  Surprisingly enough, 7.10 booted all the way to the desktop on my 233MHz, 160MB original iMac - it just took ten or twelve minutes to get there!

So how much RAM does Debian with Xcfe require, and does anyone have pointers for what to try at the (initramfs) prompt?  I need all the help I can find!

---

### Post by kerry_s on 2008-03-19
with debian you just got to try it, i've seen it used on as low as 32mb ram.
if you want the pretty installer type> installgui
don't really need it though, just boot it up and hit enter is good enough.

---

### Post by tjniels on 2008-03-19
Fair enough, it sounds like Debian could work on any one of my old G3s.  Any guess at how long the installation process takes?  Will it ask for a lot of feedback and custom settings, or if I have the ful (~650MB?) image on CD can I just do a default installation?  What is the recommended HD size, as my 233 only has a 4GB HD, the 350/192 and 350/320 have 6 and 20GB, respectively.  I'm wondering if the CD decompresses, or if it installs a lot of extra files from the web, if so, would 4 or 6GB be enough?

I burned the Debian CD at 8x instead of 24x and have confirmed that it works on all of my PPCs, but I haven't had the guts to install it on any of them yet.  I'll remember that trick for the next time I burn an Ubuntu disk.

Depending on the length of the installation process, I may throw Debian on my 350/192 tonight and leave it for at least a few days to see if I like it.  Would it be a good idea to format the HD with Mac OS 9 or X to clear the data before the installation?

Thanks!

---

### Post by kerry_s on 2008-03-19
just go for it, get your feet wet, learn how to find your way around. when you get to know it a little, you can fine tune it by going custom using the net installer. [http://cdimage.debian.org/debian-cd/current/powerpc/iso-cd/debian-40r3-powerpc-businesscard.iso](http://cdimage.debian.org/debian-cd/current/powerpc/iso-cd/debian-40r3-powerpc-businesscard.iso)

i use a custom install of debian etch/lenny, i've got my whole install in less than 600mb, everything on mines set for speed, no frills, nothing fancy.
my systems 450mhz 256mb ram. 
i start my custom install ->
base install
then
apt-get install xorg synaptic jwm mc

then i exit from root
and startx

then i open synaptic and continue building up from there.

that's all i put to start, just enough to get me to a gui.

my start up memory use is only 22mb, mines so fine tuned i have to do alot to actually use swap.

it actually looks bare right now, i done away with all icons except for the 1's in rox-filer, i'm feeling really minimal this month. :)

---

### Post by thespottedelf on 2008-03-19
if you still want to try ubuntu [http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

that is the guide i used.... i have a 500 mhz g3.. with 320 mb ram it runs it beautifully (i use it as a torrent server... right now uploading hackintosh stuff ;))

---

### Post by daniel-linux on 2008-03-20
if i were you, i would stick to xubuntu 7.04 on the iMac

regardless of writing speed, you should check the md5 sum hashes for CD integrity

mac os x takes up too many resources for the GUI alone, so xfce would be my first choice

(hell, if i were you i would run linux on the ibook as well :D)

---

### Post by tjniels on 2008-03-20
It's Debian!  For now...

Thanks for the link to the Debian PPC installer, it worked beautifully.  Let me point out some difficulties with Debian 4.0r3 with Xcfe, they may be machine-specific, or noob-specific, I'm really not sure which.  If I can't solve at least a few of these problems, I see two options: head over to the Debian forums, or switch to *ubuntu as I had initially planned.  Don't take my criticism as too harsh, I've been babied for quite some time now by OS X.

1) The Xcfe menu on my lower menu bar or dock only stays open for a few seconds at a time.  I'm serious.  Whether I hold down the mouse button or use a single-click to open the menu, after about 4 seconds the menu disappears.  This might be OK, except that it sometimes takes me significantly longer than 4 seconds (in an unfamiliar OS) to find the menu item I need.  I tried to find a control panel or preference pane where I could change this, but no luck.  Either this is a problem with my machine, or, IMO, a very stupid default setting.  :mad:

2) My machine won't shut down.  Whether or not I have any applications open, when I click the "Quit" button, it gives me a window with a few options.  Among the options are "Suspend" and "Shut Down", but both options are shaded and don't respond to clicking.  Do I have to press a key to release them?  :confused:  I have resorted to logging out, then holding the power button until my iMac shuts down, but I really doubt that is good for my computer!

3) Network settings and upgrades were not easy for me to find.  I didn't have my ethernet connected when I installed, and I was surprised that it didn't detect it automatically when I hooked it up.  I even rebooted, hoping that it would initialize the network on startup, but no luck.  Right now I am re-installing the system with the ethernet connected, I think it's working because it seems to have detected package download mirrors in my area.

4) Finally, and I know this is a beginner problem, I'm a bit annoyed that CDs and USB drives don't seem to mount automatically, nor could I find a GUI way to mount them.  I bet there's an app that I could download to mount the drives/disks/devices automatically, I just haven't looked for it yet.  I have used the Unix command to mount/unmount disks before, but I don't remember what it is and didn't want to use the terminal for such a simple task.

I will say that I like the overall feel of Debian, and it could work for me.  However, if I can't resolve these basic problems within the next few days, I will give Ubuntu it's fair chance.  Please let me know if you have any more advice.  I have downloaded the Ubuntu 7.10 alternate installer, the live CD seems to have issues with my iMac.  7.10 is my next candidate, but there is no rush to make my decision at this point.

This has been a very useful thread for me and I appreciate all of your input.  Thanks!

---

### Post by tjniels on 2008-03-20
> (hell, if i were you i would run linux on the ibook as well :))

I have an external HD in the mail, 120GB, and I plan to make 20 or 30GB of it a linux partition.  The iBook runs 10.4.11 beautifully, and I am a big fan of OS X, so I don't plan to change any time soon, if ever.  We'll see.  When I do the external HD thing, I'll either look for a good thread or make my own so you can know how the iBook fares...

I'm gonna try 7.10 before 7.04 for the iMac, I don't mind trial and error on a machine this old...  I'm wondering if Ubuntu or Xubuntu will be better - it the only difference the window manager?  What exactly does Gnome do differently than Xcfe?  I might initially attempt 7.10 Ubuntu before Xubuntu, just to see if the machine can handle it.  Go big or go home, right?  If 7.04 fully supports the PPC architecture, aka is not a port, I might be convinced not to mess with 7.10.

Thanks for the help!

---

### Post by tjniels on 2008-03-20
I re-installed Debian while connected to the internet, it used Gnome instead of Xcfe without asking.  Grr...

Well, it looks nice and most of the problems I listed above are gone now, so I'll try it for a while.  I'm attaching my first linux screenshot, let me know what you think!  That's all Gnome stuff that came with the installation, but I managed to tweak it OK for my first try!

Oh yeah.  :guitar:

---

### Post by daniel-linux on 2008-03-20
> **tjniels said:**
> I have an external HD in the mail, 120GB, and I plan to make 20 or 30GB of it a linux partition.  The iBook runs 10.4.11 beautifully, and I am a big fan of OS X, so I don't plan to change any time soon, if ever.  We'll see.  When I do the external HD thing, I'll either look for a good thread or make my own so you can know how the iBook fares...

I'm gonna try 7.10 before 7.04 for the iMac, I don't mind trial and error on a machine this old...  I'm wondering if Ubuntu or Xubuntu will be better - it the only difference the window manager?  What exactly does Gnome do differently than Xcfe?  I might initially attempt 7.10 Ubuntu before Xubuntu, just to see if the machine can handle it.  Go big or go home, right?  If 7.04 fully supports the PPC architecture, aka is not a port, I might be convinced not to mess with 7.10.

Thanks for the help!

1. i was suggesting xubuntu rather than debian because it's easier to work with if you're a new comer in the gnu/linux community

2. i was suggesting 7.04, because i had - sort of - the same problem on an older iMac - that was ok, but mac os x was too much for it - and i managed to install it on it, not gutsy

3. gnome, kde and xfce are actually "desktop environments", the "windows manager" is smth slightly different, it can be metacity, compiz, beryl etc. and it can be used under the same DE (ie., Gnome with compiz or metacity etc.)

4. the difference between gnome, kde and xfce is not only theGUI (the way it looks), but also the applications - you will have a different file manager for each one (nautilus, konqueror, thunar) and the list goes on... i personally prefer gnome or xfce, precisely because of that - kde apps are crap, at least in my experience

i also like mac os, but you will never get the flexibility you have on gnu/linux, you simply cannot customize your desktop to fit your needs entirely. either way, it's up to you - thank god you're not using windows :)

---

### Post by tjniels on 2008-03-20
> i also like mac os, but you will never get the flexibility you have on gnu/linux, you simply cannot customize your desktop to fit your needs entirely. either way, it's up to you - thank god you're not using windows 

Agreed, but OS X is more customizable than most people realize.  I'll include a screenshot that shows a bit of tweaking according to my specifications.  :)

I tried using Windows for one full semester, and I felt like pulling all of my hair out!  :mad:  I believe in giving people their fair chance, and Mr. Gates had his!  I don't own a single Microsoft product right now.

> 1. i was suggesting xubuntu rather than debian because it's easier to work with if you're a new comer in the gnu/linux community


When I tried the Debian/Xfce, I was a bit underwhelmed with the DE - does Xfce typically come with OpenOffice and Gimp?  The basic install didn't include them, I guess that really surprised me.  The Gnome install had them, and everything else I wanted, and runs at a respectable speed despite my RAM limitations, so I'm wondering if I should stick with Ubuntu over Xubuntu when I get around to that.

I will continue to stick with Debian for a few more days, but if it becomes a headache, Ubuntu here I come!

Now for that OS X screenshot.  Notice 1) the color of the menubar, 2) the desktop trashcan I scripted, 3) the hiding dock, and 4) the name of my iTunes, as well as iTunes controls, in the menubar!  Most of that tweaking is accomplished through 3rd party apps, I agree that linux is more customizable, but OS X is still respectable, unlike another OS I see so many people using.

Thanks for the pointers!

---

### Post by daniel-linux on 2008-03-20
i guess you forgot to upload the screenshot :)

to me it's somewhat like this:

- windows is easy to use, but it's all crap under the hood

- mac os x is good stuff (based on unix/bsd), and still easy to use

(for which reason a lot of the settings are automated, which i don't like, since i like to configure it the way i want, whether we talk about web server, firewall settings, networking or graphic interface :D)

- gnu/linux requires some expertize, but it's by far the most customizable in any way you want, whatever the needs

you should also notice that OS-s like windows, mac os or bsd can only be installed on primary partitions etc., whereas linux can run on anything, from internal/external harddrive, primary/logical partition to liveCD or usb stick :)

not to mention the reachness of platforms/architectures supported by gnu/linux - you can install xubuntu for instance on a PPC iMac or on an i386 PC, just to give an example, whereas windows or mac would only run on either one of those

in any case, to each his own ;) freedom of choice, that's what FSF is all about

---

### Post by tjniels on 2008-03-20
I couldn't get the screenshots to load & I don't want to mess with it.  So much for making my point.  :rolleyes:

---

### Post by tjniels on 2008-03-20
Here are the screen shots I promised...  Enjoy!

---

### Post by daniel-linux on 2008-03-20
not bad ;)

this is my desktop with compiz fusion:

[http://stuparu-gnu-linux.blogspot.com/2008/03/compiz-emerald-in-ubuntu.html](http://stuparu-gnu-linux.blogspot.com/2008/03/compiz-emerald-in-ubuntu.html)

mind you, i have posted another reply before you managed to upload the screenshots

---

### Post by Cows on 2008-03-20
When your going to boot type the following :

linux-nosplash-powerpc video=ofonly break=top

then when the initramfs busybox shell comes out, type the following :

modprobe ide-core
exit

and thats it

---

### Post by tjniels on 2008-03-20
> not bad 

this is my desktop with compiz fusion:

Thanks!  I'm actually pretty proud of that desktop photo I took, but I don't get to show it to may people.  I like your setup too, it's real sleek.

---

### Post by tjniels on 2008-03-20
> **Cows said:**
> When your going to boot type the following :

linux-nosplash-powerpc video=ofonly break=top

then when the initramfs busybox shell comes out, type the following :

modprobe ide-core
exit

and thats it

Is this for using a *buntu live CD?  I missed the context for you comment, sorry.

Right now, I'm working on a Gutsy install, Debian was starting to get on my nerves.  I got it to look nice, and run smoothly, but every time I told it to shut down it would just reboot.  On top of that, every time I turned the machine on for the first time, it would boot to Debian, I would log in, and it would give me 8 to 15 error dialogs.  I found that by resetting the system clock, then logging out and back in, it would work with no problem, but that's a major pain to have to do every time I turn the computer on.  I'd leave it on, but I don't want to waste energy or money!

Debian seems viable, but I don't have the time to get it properly configured.  Check out my Debina screenshot a few posts ago if you don't believe I tried.  For now, my focus will be getting a working install of Ubunutu on the machine for comparison purposes.

Thanks all for your continued input!

---

### Post by Cows on 2008-03-20
Same over here. That's why I'm trying so hard to get Hardy 8.04 to work. I opened up a topic which you can find here :  [http://ubuntuforums.org/showthread.php?p=4529497#post4529497](http://ubuntuforums.org/showthread.php?p=4529497#post4529497)

That is for Ubuntu 7.10. For me Ubuntu Gutsy gave me a lot of errors. When I booted up and it started displaying the start up processes, all the status of the process were [fail].

---

### Post by tjniels on 2008-03-20
> That is for Ubuntu 7.10. For me Ubuntu Gutsy gave me a lot of errors. When I booted up and it started displaying the start up processes, all the status of the process were [fail].


I'll see how it goes on my G3... I'm using the alternate install CD and I'm just waiting for it to finish.  I'm surprised at how long the install is taking compared to Debian, but I guess it's only been going and hour or so now.  If I have errors, I'll downgrade to 7.04 for now.  Is 7.04 supposed to have full PPC support?  At this point, I'll be happy to just get *anything* to work.  If 7.10 and 7.04 give me the same problems as Debian did, I may just end up with a very fast Mac OS 9 machine.  We shall see.

---

### Post by Cows on 2008-03-20
Haha I remembered using Mac OS 9 in 3rd Grade. G3 iMac , aahh those were the days.

Yea Ubuntu Distros take forever to install compared to Debian. I'm installing Gutsy as well using :

cli-powerpc break=top;

I also opened up a Virtual Terminal and typed :

modprobe ide-core
exit

Just in case !

---

### Post by Cows on 2008-03-20
I'm surprised. 7.10 Installed successfully. ATM I'm updating everything.

---

### Post by tjniels on 2008-03-20
> I'm surprised. 7.10 Installed successfully. ATM I'm updating everything.


Was that comment to me?

It's sitting at 97% at the moment, it says it's "cleaning up", so if successfully means the installer runs OK, then it's been successful.  I'll let you know after I've booted it a few times and messed around if it really was successful.

If I have issues, I plan to try 7.04, and then perhaps resort to Mac OS 9.2.2.  I hope I can get linux to work, though, I've been in adventurous mood the last few days.  :)

More updates to come.

---

### Post by Cows on 2008-03-20
Lol.. yea it was for you.
 

Something is weird. Ubuntu 7.10 Installed successfully but for some reason I only have a GUI. I'm downloading latest xorg xserver-xorg-dev ubuntu-desktop

OOOhh I know why I only have CLI lol !! It's because I said "cli-powerpc" in the beginning. At least I'm not getting errors, everything is working perfectly. All I need to do after this is tweak the /etc/X11/xorg.conf and get my wireless card working ( Original Airport ).

EDIT: If you have problems with normal installation after you install ( like my previous problem where stuff fails ), Just reinstall with "cli-powerpc" , I can almost guarantee that everything will work.

---

### Post by Cows on 2008-03-20
Wow man, Gutsy 7.10 is really slow on my G3. Doesn't even open X now lol. Probably was cause I became impatient after hours of getting X to work. Oh well.. My ram is coming in tomorrow and hopefully that will fix all my Linux troubles involving installation and speed :). 640 MB RAM FTW !! lol ; )

---

### Post by tjniels on 2008-03-21
OK, 7.10 seems to have installed OK on my iMac 350/PPC with 192MB of RAM.  I used the alternate install CD, and it took about 3 hours, but it did finally install.  Here's the story:

I typed "install-powerpc" at the boot prompt.  This may only work on the alternate installer, I'm not sure.  I think everything installed automatically from there, it just had me answer a few questions.  Ubuntu 7.10 seems better than Debian 4.0r3 in at least one regard, it knows how to shut down my machine without rebooting it, lol!  Now, when I boot my machine, I get an orange flash, then a checklist that says [OK] a bunch of times on the right-hand side, then a beautiful black screen with a large Ubuntu logo and an orange progress bar.  Finally, after a minute or two, I get to the Ubuntu login screen that asks for my password.  Everything seems to work fine [I]up to that point.
[/I]

BUT...

I enter my name and password, I get another orange flash, and Ubuntu attempts to load.

I am greeted by a message telling me that my clock is set to 1903, and that I should fix it.

I click "Adjust Clock", and get a message telling me I do not have access to the clock settings.

I get another error dialog telling me that the Gnome preference manager has reset itself too many times, I click OK, and then all I have is an orange screen with a white Gnome-style cursor.  The system does not load beyond this point.

I had a similar experience using Debian, but in that case the system would load to a half-baked, Windows 3.1-like, semi-functional OS that would at least let me adjust the clock setting.  I would  log out and log in again, but this time the system would load correctly.  This led me to assume that several aspects of the system, as well as several included applications, simply will not operate when the system clock is set to an absurd date like 1903, or 1969 in the case of Debian.  I have heard of a date error or time error when using Debian on a G3 iMac, but I had not heard that Ubuntu had the same problem.

Since Ubuntu wouldn't let me access the settings, I tried a fix that resets the clock when I'm using Mac OS, I held command-option-p-r while the system booted, and held it until I heard the second chime.  This resets the PRAM, if I understand correctly, and forces the computer to access the date & time from a network if connected.  This trick did not work for Ubuntu, I'm guessing Ubuntu is not coded to check the date/time before it fully loads the system.  What a shame.

Does anyone know a fix for this?  Has anyone else encountered a similar problem?  I have a few ideas of how the problem could be fixed, but I don't have the experience to know where to start.  Here are my ideas:

1) There might be a way to manually set the clock from the command line before the system boots.  Can this be done?  If so, what should I type to set the clock manually?

2) There might be a way to force the OS to let me adjust the clock after I log in but before the system loads.  If I could log in as root, I might have more privileges, but Ubuntu did not ask me for a root password during the installation.

3) There might be a command to force Ubuntu to access the time from my internet connection before the system loads.

I don't know which if any of the methods above would work, nor do I know how to implement them.  I am now downloading the alternate installer for Xubuntu 7.04, but if I can fix this problem before tomorrow evening, I'll keep 7.10.  I think 7.10 would be ideal, so please offer any help you can.

Thanks again!

---

### Post by stream303 on 2008-03-21
You may definitely want to look at these two faqs if you haven't already.  They cover many of the issues you are having and should help make that transition much smoother.

I'm looking forward to seeing how that new ram works!

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by tjniels on 2008-03-21
GUESS WHAT!  GUTSY WORKS ON MY IMAC G3!!!

And it works beautifully, at that!  I fixed the date bug using the thread above, and I booted the computer successfully twice since then!  I feel vindicated that I have the OS running.  If the date bug comes up again, I'll just replace my PRAM battery - I've got one lying around somewhere.

I must note that Ubuntu runs pretty slowly on my machine, but I see it as a miracle that it runs at all with only 192MB of RAM!

The only problems that remain are 1) that the iMac still sometimes reboots instead of shutting down, 2) every time I log in I get a message the the Gnome Settings Daemon has failed and will try again next time I log in, and 3) I can't seem to get an internet connection!  The live CD detected my ethernet automatically when I tried it automatically, but no such luck on the iMac.  I tried changing the settings in the network panel, but to no avail.  I will scour the FAQs to se if I can't solve these problems, but Gutsy has not worn out its welcome yet.

As soon as I can get the iMac on the internet, I will upload some more screenshots to document my progress and prove that I got it working.  Does anyone have ideas, pointers, or links to help me solve the problems in the paragraph above?  My main concern right now is that I get the internet working, otherwise that computer will be pretty pointless.  If I stick with Ubuntu, I will definitely upgrade the RAM to see if that helps the operating speed.

I've got another thread that might like to hear about this success, it's [http://ubuntuforums.org/showthread.php?t=719048&goto=newpost]("http://ubuntuforums.org/showthread.php?t=719048&goto=newpost")

I'll jet over there right now!  Thanks for the help so far.

---

### Post by stream303 on 2008-03-21
Congrats on getting that to work!  Yes!

> **tjniels said:**
> If the date bug comes up again, I'll just replace my PRAM battery - I've got one lying around somewhere.

I'd have to double-check, but I think it is a Tadiran 3.6v lithium.  I've seen them at Radio Shack part #23-037 if that helps.

> I must note that Ubuntu runs pretty slowly on my machine, but I see it as a miracle that it runs at all with only 192MB of RAM!

Be sure to give Xubuntu a try - it has lower memory requirements.  It might be enough to put it into the very usable category...

> but Gutsy has not worn out its welcome yet.

I sure wish I could find a solution to that.  I'd just stick with either 7.04 or the LTS 6.06x and see if Hardy will work when it is final...  Unless of course you want to go alpha ...

> My main concern right now is that I get the internet working, otherwise that computer will be pretty pointless.

What's your setup?  Are you behind a router?  Did you install with the ethernet connected?  Have you doublechecked the repositories in the Software Sources tab?  Does the browser just time-out, yet you are able to ping sites?

Again, congrats on the install!

---

### Post by tjniels on 2008-03-21
So I'm not the only one who stays up this late!

> I'd have to double-check, but I think it is a Tadiran 3.6v lithium. I've seen them at Radio Shack part #23-037 if that helps.

Yes, I do have the exact battery lying around for no apparent reason, it's a long story.

> Be sure to give Xubuntu a try - it has lower memory requirements. It might be enough to put it into the very usable category...


Yes, I've downloaded Xubuntu 7.04 and will probably install it within the next two days, unless Ubuntu 7.10 speeds up for no apparent reason.  :)

> What's your setup? Are you behind a router? Did you install with the ethernet connected? Have you doublechecked the repositories in the Software Sources tab? Does the browser just time-out, yet you are able to ping sites?

I go through Comcast with a cable modem, I've got a wireless router for my two iBooks, my three iMacs come off the back of the router via ethernet.  That's not counting any of the computers my roommates have!  But we have plenty of bandwidth.  So yes, I am behind a router, yes I installed with the ethernet connected, I don't know if I can ping sites, but I do know that every site I attempt to visit on the browser returns something like "Firefox is unable to access the server", and "bla bla bla check your firewall and proxy settings to be sure Firefox is allowed to acces the web."   Well, I didn't see anything in my proxy settings that would limit Firefox, I really think the computer just isn't seeing the ethernet at the moment.  I went into some settings and manually entered my IP address, but that didn't help either.  I will look for the Software Sources tab, I don't know where it is.

Thanks, I'll wait at least a few minutes to see if you get this, but it's 4:00 AM and I'll want to hit the sack soon.

---

### Post by hikujk123 on 2008-03-21
In linux, I believe swap replaces RAM.  If I am wrong, please correct me because I too am new.

---

### Post by Cows on 2008-03-21
Yea but I think that RAM is faster then SWAP. I just received my 512 RAM for my iBook G3. Now I have 640 MB RAM which is the max. Everything seems to be going much faster.

---

### Post by tjniels on 2008-03-21
> In linux, I believe swap replaces RAM. If I am wrong, please correct me because I too am new.

> Yea but I think that RAM is faster then SWAP. I just received my 512 RAM for my iBook G3. Now I have 640 MB RAM which is the max. Everything seems to be going much faster.


Swap space is identical to what would have been called "Virtual Memory" under the old (pre-X) versions of Mac OS - a designated amount of hard drive space that can be treated as RAM.  The only difference I can see is that in Linux, swap space gets its own partition when you do the installation.

Mac OS X uses swap space as well, but on a different level.  It dynamically chooses how much swap space you need, then only uses it as you need it.  If you have something in RAM that hasn't been used in a while, it moves that thing to swap space so you can maintain a respectable speed on everything else.  Swap is much slower than RAM, but gives you a nice buffer so you can keep running applications when you run out of RAM.  The reason it is slower is that it is based on the physical constraints of writing data to a hard drive, whereas RAM just stores that same data electronically.  When I run Ubuntu on 192 MB of RAM, the RAM is mostly full to start with, and I end up dipping into swap space frequently, I've watched the system performance monitor to see when it does it, and I think that's part of why my computer runs so slowly - not enough RAM!

Hope that clarifies things a bit for you.

---

### Post by stream303 on 2008-03-21
Remember that if  you let Ubuntu automatically calculate the swap partition size during installation, it may be too small now that you've added additional ram, unless you manually repartition it.  Swap is typically 1, 1.5, or 2 times the installed ram.

You may want to just reinstall at this stage if you want to let it recalculate the swap size and do it for you automatically.

If you do, and want to blow away the entire old installation, this time be sure to let the installer "use the whole disk" when it comes time for guided partitioning.

---

### Post by Cows on 2008-03-21
I'm going to forget about Ubuntu on PPC. It has way too many problems. I have tried 8.04 Alpha 6 , a updated version of Alpha 6 , Alpha 6 net install , 7.10 , 7.04 , and none of them have installed correctly. I managed to hack my way to the desktop but with problems. The Ubuntu set up was going so slow that I went to sleep and when I woke up it still was installing. 

Debian on the other hand installs seemlessly even under 256 mb ram. I have 640 mb ram now so it should be a speed demon.

Also I don't know if I can enable WPA on my Airport card in Debian Etch 4.0r3 :(.

---

### Post by tjniels on 2008-03-21
> I'm going to forget about Ubuntu on PPC. It has way too many problems. I have tried 8.04 Alpha 6 , a updated version of Alpha 6 , Alpha 6 net install , 7.10 , 7.04 , and none of them have installed correctly. I managed to hack my way to the desktop but with problems. The Ubuntu set up was going so slow that I went to sleep and when I woke up it still was installing.

Did you use the live CD or the alternate installer?  I installed 7.10 with the alternate CD, it took about 3 hours, but that was with insanely low ram for such an installation (192MB for full-on Gutsy 7.10.  Yikes.)

I can get to the desktop with no problems, it just tells me the Gnome Settings Daemon was reset, but it doesn't seem to make a difference???  I'm trying Xubuntu 7.04 next, I'll give you an update when it's done.  If that's a no-go, I'll give it one last hack at Debian 4.0r3, now that I know how to manually reset the date and fix the date bug.  If I can't get a bug-free linux on the iMac within the next two weeks or so, I'll resort to MacOS 9.2.2.  :|

I think on my next install, I'll force the installer to use a larger swap space - in case I upgrade the RAM.  As long as the swap space exceeds the RAM, it should be OK, right?

---

### Post by Cows on 2008-03-21
All of the installers were alternative. I'm downloading the GUI now and I'm going to try it. I'll let you know how it goes.

---

### Post by tjniels on 2008-03-21
> All of the installers were alternative. I'm downloading the GUI now and I'm going to try it. I'll let you know how it goes.

Is that for your iBook G3?  What *buntu version?  I'm curious to know if it works.  I used the live CD not for installing, but for testing, and it worked fine on my iBook G4.  Good luck, and I'll wait for your update.

---

### Post by Cows on 2008-03-21
The GUI installer worked great. I updated my main topic and added the solution to the first and last post.

[http://ubuntuforums.org/showthread.php?p=4529497#post4529497](http://ubuntuforums.org/showthread.php?p=4529497#post4529497)

Enjoy !

---

### Post by tjniels on 2008-03-21
> The GUI installer worked great. I updated my main topic and added the solution to the first and last post.


You're serious?!  You've got Hardy Heron alpha running on an iBook G3 with no problems???  I may have to dig out my iBook G3, or try that install on my iMac after I upgrade the RAM!

I have a checklist for you, I'd just like to see for sure that I'm hearing what I think I'm hearing.  Are you telling me that

1) The Hardy GUI installer *just works?*
2) Your machine will power down properly when you tell it to?
3) You machine will sleep when you close the lid, or at least when you tell it to suspend?
4) You don't get any date error, e.g. the computer remembers the date from the previous session, and doesn't reset to 1970 or 1904?
5) The Gnome Settings Daemon doesn't give you a warning when you start up that it has reset too many times?

If this is true, it sounds like PowerPC support for Hardy is better than Gutsy, and Hardy is still in alpha!  Oooh, this could be revolutionary for me,  :)

Please follow up on that checklist, I know this thread is about my G3 iMac, but you've basically got the same processor in your iBook.  If you had to fix any bugs, can you provide a link to how you did it?

Thank you so much, you just made my day!

---

### Post by slacka-vt on 2008-03-21
Am I missing something here ?
Dapper and Hardy are the ONLY ubuntu distros officially supported on PPC.
Says so on their website.
 All the others (i.e. Edgy, Feisty, Gutsy) are not officially supported.
It comes to absolutely no surprise to me that, less then 2 weeks before it's official release,
Hardy should be installing on PPC's with little hassle.

~s

---

### Post by tjniels on 2008-03-21
> Am I missing something here ?

No, I don't think you're missing anything.  There have been some very good *ports* of Feisty and Gutsy, I installed Gutsy on my iMac G3 with only minimal problems.  I have not followed Ubuntu closely until recently, when I had the hair-brained idea of turning my old iMac into a Linux toy.  I had heard that Ubuntu had dropped official PPC support after 6.x? but I've heard so many good things that I went looking for a port.  I can confirm that the ports are usable, but a bit of a pain as described above.

If Hardy is bringing back official PowerPC support, I will use it!  I just had not heard.  My reason for installing 7.10 is that it was the most current *non-alpha* version available.

So Hardy will be officially supported?  I apologize for my ignorance.  That is very cool.  Any idea when Hardy Xubuntu PPC will be available?

I'll just need some more RAM before I can put Hardy on that ancient machine.  Sorry, it won't go on the iBook G4 anytime soon, I don't want to give up my current setup in OS X.

---

### Post by Cows on 2008-03-21
Lol. 8.04 Alpha is already better then all the ports.

Checklist :

1) The Hardy GUI installer just works?

```
- Yes It just works ; )
```

2) Your machine will power down properly when you tell it to?

```
- Machine powers down and reboots fine.
```

3) You machine will sleep when you close the lid, or at least when you tell it to suspend?

```
- The Machine doesn't sleep when I close the lid but I do get a nice sound when I open it and close it meaning lid detection is working properly.
```

4) You don't get any date error, e.g. the computer remembers the date from the previous session, and doesn't reset to 1970 or 1904?

```
Nope no date bugs. I made sure to reset-nvram && reset-all before I installed.
```

5) The Gnome Settings Daemon doesn't give you a warning when you start up that it has reset too many times?

```
Nope no errors for Gnome Settings Daemon.
```

PowerPC is definitely good with Hardy. Only problem is that my Airport card doesn't support WPA because it has a Orinoco chipset. I'm compiling a new kernel so that it does.

---

### Post by tjniels on 2008-03-22
> Lol. 8.04 Alpha is already better then all the ports.

That is so good to hear!  I was about to give up on all things *ubuntu!

Right now, I'm working in OS X on my iBook, but I have the Xubuntu 8.04 desktop CD downloading in the background to use on my iMac.  I also am reinstalling Debian on the iMac, now that I know how to fix the date bug, so I can say that I gave it a fair chance.  My guess is that I will end up with Xubuntu 8.04 because of its low RAM requirements.  Besides, I kinda like Xfce.

If my Debian install works out, I'll inspect if for flawlessness, and when/if it fails my test, I try the Xubunt live CD.  If I like the look and feel, I'll let it install while I shower, eat breakfast, and run a few errands tomorrow morning.  This iMac install will be a great test of how far back the PowerPC support really goes!

BTW, I've been assuming all along that your iBook is one of the white ones, e.g. 500 MHz or more.  What is your clock speed?  Send some screenshots along when you can so I can see which features you've got working.

Thanks for the update, and for running through my checklist!

---

### Post by tjniels on 2008-03-22
> - Yes It just works ; )

I have not been so fortunate with the installer just yet, I'm trying to get Xubuntu Hardy on my iMac using the desktop (live) CD.  I first tried reinstalling Debian, but I majorly messed up the hard drive working with manual partitions.  I guess I know just enough to be dangerous!  I could have fixed it, but I figured oh well, I'll just boot off the live CD anyway and have no troubles.

Right.

The Xubuntu installer gets me to the boot prompt, and I have tried at least 20 combinations of "live", "live-powerpc", "live-nosplash-powerpc", "video=ofonly", and "break=top".  I even typed "modprobe ide-core" at the (initramfs) prompt, but regardless of my boot settings, the "modprobe ide-core" and "exit" only yielded an excuse that the computer couldn't find any home directory, or that the selected volume (my hard drive, I presume?  or the CD?) had no home directory.

I'm only vaguely aware of what the above paragraph means, but as a pure shot-in-the-dark I am reinstalling Debian as a means to an end: it will get a home directory on my messed-up hard drive (which I formatted incorrectly earlier) so that if I get the error again I will know that the message about no home directory being found refers to the CD, no the HD.  Why Debian?  It has the fastest installer.  :)

I followed all of the suggestions in the PowerPC FAQs, but I think most of them were referring to 7.10 rather than 8.04.  :confused:  Every other version of *ubuntu that I have used with a live disc has loaded properly with just the live-nosplash-powerpc command, or at least after the modprobe ide-core command at the (initramfs) prompt.

Wish me luck, I probably won't finish this tonight.  I just ordered some extra RAM for $5, just an extra 128MB stick.  It's not much, but if I pull the 64 stick I can up the iMac from 192 to 256MB, enough to run Xubuntu very nicely I suppose.  I wanted to get more, but I had two reasons not to:  1) I'm engaged and finances are tight, and 2) My swap space is only ~347MB, and I don't want to mess with the manual partitioner.  Besides, my HD is only 6.8GB before formatting, so I need to preserve as much space as I can.  If I ordered even a 256MB stick, I could go for 320MB like my other iMac, but that would mean wasting a perfectly good 128MB stick just to keep my ram lower than my swap space, as 320 < 347 < 384 if that makes sense.  Yes, I passed my third grade math class.

If anyone has run into problems installing any *ubuntu 8.04 on an older iMac like mine, especially if you know the solution to the problems I listed, please post to help.  I'd like this to be a valuable thread that will help many PPC users with installations in the future.

---

### Post by stream303 on 2008-03-22
Sounds like you are giving your partitioning a workout. :)

In either Ubuntu or Debian, the simplest way I know of is to let the guided partitioning "use the whole disk", rather than install to "free space".  That way it will set up the 4 partitions that are needed at a minimum, and you won't have to deal with it for average desktop use.

I'll have to fire up the partitioner again to see where I get to "use the whole disk".  When I do that, I don't even have to worry about existing partitions, it will take care of the whole thing for me and start fresh.  I blow away an install about once a week now with all this testing, and "use whole disk" has been my best friend. :)

---

### Post by tjniels on 2008-03-22
> Sounds like you are giving your partitioning a workout. 

I know, isn't it great?  :rolleyes:

> In either Ubuntu or Debian, the simplest way I know of is to let the guided partitioning "use the whole disk", rather than install to "free space". That way it will set up the 4 partitions that are needed at a minimum, and you won't have to deal with it for average desktop use.

Yeah, that's what I've done before, and what I did this time.  I let Debian run it course with the partitioner set to "Guided, use the whole disk" and it set up the four partitions you described.  I was doing the same 4 partitions, but attempting to make a smaller ext3 and a larger swap space to accomodate a future RAM upgrade.  I kept getting a red error screen, saying either that "For an unknown reason, the computer is unable to adjust the ext3 partition on your hard drive," (almost verbatim, I promise!  I laughed about "For an unknown reason"!) or "Partition size is too large." when I chose anything above 347.4MB.  Why 347.4 and not 320, 384, 512 or something, I have no idea.  Probably based on the current amount of installed RAM, or just that the rest of the HD is taken up by other partitions.

I decided that it was futile to adjust the swap space, even when reformatting the whole drive it refused to allow my *attempted* action.  My solution?  I went ahead and ordered a the 128MB card instead of 256 or 512 for my upgrade.  It is my understanding that the swap space ought to exceed the amount of installed RAM, I'm guessing that when you suspend the computer it writes the contents of the RAM to the swap space.

*If* I manage to get Xubuntu Hardy working on my iMac PPC, *which should be supported*, upgrading the RAM just slightly from 192 to 256 (192 - 64 + 128, the iMac only has two RAM slots) should give Xcfe oodles of memory to play with.

For clarification, does anyone know what the command "modprobe ide-core" entered at the (initramfs) prompt actually means?  That's a new command to me, but I keep reading that I should use it when installing on a PPC.

The *BEST* scenario I can think of would be for someone with an identical machine to try the installation so we can sort out the bugs, but I don't know who else has an iMac G3/350 sitting around.  Volunteers?

Please rescue me from being forced to use Debian!!!  It's a nice OS and all, but until I have installed and tried Xubuntu Hardy I will feel too uninformed to make the decision between Debian and *ubuntu.  Mostly I am stoked at the fact that Ubuntu is bringing back PPC support, I don't think they should have ever dropped it.

All help is appreciated at this point.  I'd really just like to get the Xubuntu live CD to work so I can get a feel for it...  Not so sure I dare install if the live CD won't work first.

Thanks, all!

---

### Post by Cows on 2008-03-22
Wow, I have a lot of questions to answer so let's get started.

1. I have a iBook G3 12" 800 Mhz, 640 MB SD-RAM ( PC-133 ) , After upgrade of course.
Pictures are at my blog <a href ="http://fearedbliss.blogspot.com/2008/03/ibook-g3-review.html">here</a>.

2. The Home folder problem. Make sure that you burned the disk correctly. The way I burn a disk is I open up Terminal on my iMac and I type :

md5 <name of ubuntu disk>.iso
After that I burn at 8x and enable verify disk at end.

The above 2 steps will act as 2 layers of verification.

3. modprobe ide-core is basically saying to look for the module called ide-core in which ide-core will look for all plug and play devices. I am not 100% sure on this. You only need to use this in 7.10 because there was a bug there.

4. I only used the GUI installer because I exceeded the requirements. Even after I received and install my RAM , I tried the Alternative installer and it still gave me problems. So what I suggest doing is basically download and burn a new Xubuntu 8.04 Alpha 6 GUI Installer and use the above checks to do so. It will probably take a longer then what it took me to get my desktop booted up but at least you wont have to worry about failures.

5. Debian is good and everything and it's definitely fast, but the only reason it's fast is because it's not installing as much as Ubuntu is.

Don't give up. *buntu is definitely supported on G3's.

---

### Post by tjniels on 2008-03-22
> 3. modprobe ide-core is basically saying to look for the module called ide-core in which ide-core will look for all plug and play devices. I am not 100% sure on this. You only need to use this in 7.10 because there was a bug there.

What did you type at the boot prompt?  I've used live-nosplash-powerpc on other *ubuntu distros, I tried that and several other things on Hardy, but maybe I still should type something different, becuase it stops at the busybox (initramfs) prompt.

> 4. I only used the GUI installer because I exceeded the requirements. Even after I received and install my RAM , I tried the Alternative installer and it still gave me problems. So what I suggest doing is basically download and burn a new Xubuntu 8.04 Alpha 6 GUI Installer and use the above checks to do so. It will probably take a longer then what it took me to get my desktop booted up but at least you wont have to worry about failures.

Yeah, I exceed the requirements for the Xubuntu live CD, it says it will load with as little as 128MB of RAM!  So 192 or 256MB should be plenty.  If you don't have a suggestion for a boot prompt that I haven't tried, maybe I'll have to follow your instructions for burning a new disk.  Too bad I deleted the .iso already!  Oh well, I can download 600MB in about 30 minutes, so it's OK.  :)

Just for clarification, when I type "md5 <name of ubuntu disk>.iso" in the terminal, do I type the full name of the .iso that I downloaded, or can I type some random, shorter name if I prefer?  I'm really only familiar with terminal commands like rm, mv, cd, ls, and cp, so I need a little clarification on this step.

Thanks again, you've been very helpful!  I'll get this working, someday.

---

### Post by Cows on 2008-03-22
I didn't type anything at the prompt. I just used the default which is live.

You must type the exact image name.

---

### Post by tjniels on 2008-03-22
I tried doing it that way and it still hung at the busybox (initramfs) prompt.  I'm going to try the burning method you described right now, I'll let you know how it goes.  Thanks!

---

### Post by Cows on 2008-03-23
I was trying OpenBSD and FreeBSD. They are good OS's but the community sucks.

---

### Post by tjniels on 2008-03-24
Do you not like Ubuntu Hardy?

I've still been failing to get Xubuntu Hardy on my iMac - the live CD always ends up at the busybox prompt before the desktop loads.  The alternate CD loads the kernel and goes through the preliminary steps of the installation, but when it tries to detect my hardware it can't seem to detect the CD it just booted from.  :(  Kinda sad, it says "This probably means the CD is not in the drive."  I retried mounting the CD a few times, but no luck.

The Xubuntu live CD is crap on my iMac, it's a bit better on my iBook, it at least gets me to the pretty Xubuntu logo with a moving bar, but it still gets to the busybox prompt and won't go anywhere from there.  I think I used live-nosplash-powerpc? for booting, but I'll try again tonight

SO, considering I have successfully installed Debian 4.0r3 Xfce, Debian 4.0r3 Gnome, and Ubuntu 7.10 on the iMac, and considering that the Xubuntu CDs almost boot, I know I am burning them correctly.  I have also used the Ubuntu 7.10 live CD on my iBook, and it worked fine.  Has anyone else had issues installing on PPCs?   I heard about a guy with an iMac G5 who had the same problem of the CD not being detected, and it didn't sound like he had found any solution.

Well, I hope the PowerPC installer gets ironed out before the official release - I seriously want to try this new version.

---

### Post by Kasa on 2008-03-24
just to say, the only "support" PPC macs have are well this space of forum, and other community groups.
Offical support for the releses was scrapped when mac brought out intel.
If anything we are keeping the Ubuntu theme alive almost more so then Ubuntu it self, seeing they dont support there own work :?.
but anyway.
We as humans should strive to keep improving what we have, and keeping PPC alive in some form is a good thing.
we just need to improve on how we keep it alive :?.
I support the uses of ubuntu on PPC, but seeing they left us at 6.10, and we are just geting into 7.10 now, why think 8.04 is going to be any easier :?.
we just need to fix 7.10 first then think of fixing 8.04 xD.
:lolflag:

---

### Post by tjniels on 2008-03-24
> we just need to fix 7.10 first then think of fixing 8.04 xD.
I had heard a few reports of 8.04 installing with no problem on PPCs, and a few people suggesting that 8.04 was bringing back official PPC support.  That may be bogus, as I don't have any documentation.

*EDIT: Ah, I just noticed that 8.04 is in the ports section of the Ubuntu website.  Drat.  Unless I hear amazing success stories soon, I may have to stick with Debian for the moment.*

BTW, I had Ubuntu 7.10 installed on my old iMac G3, the only problem that I couldn't fix with half-hearted effort is a dialog box that popped up on login, stating that the Gnome Settings Daemon had reset and would try again on the next login.  I don't know what that meant, but the system seemed to run fine without it.

I'll go back to Ubuntu if anyone can tell me how to fix the Gnome Settings Daemon.  :)

---

### Post by Cows on 2008-03-24
I like Ubuntu 8.04. It has full hardware support for my iBook G3. The only problem is that it feels pretty slow compared to Debian's Gnome and on top of that the 8.04 PPC net and alternative installers are both screwed.

---

### Post by tjniels on 2008-03-25
Still no luck with either the iBook G4 or the iMac G3.  I'm going to check the Hardy Testing string at [http://ubuntuforums.org/showthread.php?t=705267]("http://ubuntuforums.org/showthread.php?t=705267") to see if anyone has addressed the problems I've encountered.  If anyone has the silver bullet for installing on PPCs like mine, please help!

Thanks so much!

---

### Post by ubuntubrian on 2008-04-12
I have successfully installed hardy on to my G3Powerbook, Lombard and everything works perfectly. I installed from the live CD which boooted up with only a "live video=ofonly" commandatthe boot prompt.
The same live cd ran fine on my TiBook except for sound so I've deferred in hopes that issue gets resolved ([http://ubuntuforums.org/showthread.php?p=4702420#post4702420](http://ubuntuforums.org/showthread.php?p=4702420#post4702420))
the latest live cd won't boot without the same command but then the mouse freezes, either trackpad or usb. Trying Xubuntu but that wouldn't boot at all last time.

---

### Post by stream303 on 2008-04-12
Now that Hardy is in feature-freeze, things look to be much more stable and it is working very well.  Just like in Debian, it now actually runs faster from an external firewire drive, than Gutsy does on my internal drive!  I can't wait to put it on the internal drive.

**Us - vs - Them**

I think the thread title is kind of misleading.  There is no reason not to use both.  Both have their good points and the experience can be rewarding by taking the tips and tricks you learn from one to the other.

A large influence is the community, and it all depends on where you go.  Both sides have the fantasy-world of:

```
$
```

"You figure it out.  Try apropos.  What do you think it means?"  as if we were living back in 1973.   Put on bell-bottoms or a pen-protector and pretend to be in a *nix university class. :)

The other side is to try loading the installer, and then at the first sight of a problem, bashing the distro and going on the endless hunt for one that does everything 100% right.  You'll be burning a lot of cd's.

The smart money is on exposing yourself to many environments, and furthering each by participating in the community and making a difference, not only for yourself, but for others.  Leave the cheerleaders on the sidelines, and get in there and play.

So far, Ubuntu for PPC, even without "official" support, has been the most valuable to me.  Even if you decide that Ubuntu isn't for you, there is no reason not to take Ubuntu's spirit of community support and helpfullness with you.  As an example, there are many Debian users here who have provided me with great support for my Ubuntu setup, and that only makes me want to support Debian in return.  Elitism in any form is just a waste of time.

So give the latest Hardy Beta a try.  For that matter, give Debian Lenny-testing a try.  Try others.  If you find something that works, see if it works in the other environment.

Whew - rant over. :)

---

### Post by tjniels on 2008-04-12
Thanks for the info.  Hardy PPC is still in "alpha", right?  I think I tried alpha 6 several times on my iMac G3, and tried the Hardy live CD on my iBook G4 to no avail.  Is there a newer alpha out there?  If you got it going on your G3 Lombard (400 MHz?) than it really ought to work on my similar-age iMac G3/350.  Same story, no luck with Hardy Xubuntu, which is a shame–it would be a nice match for my iMac.  Even the alternate installer didn't work, but all of this was a few weeks ago, they could have fixed things by now.

Let me know if there's a newer alpha, also please if anyone else is having success please let me know.  I'd like to try again, but until I have a reason to believe it will work...  I'll hold my horses.

Thanks!

---

### Post by stream303 on 2008-04-12
It is no longer Alpha, but beta, and in feature-freeze to boot!  (no pun intended. :)

It is highly likely (but no guarantees) that what you see now is what you will get upon release.  Also be aware that Xubuntu has undergone a reorganization, and may be lagging just a little bit.  Afaik, they could be fully up to speed right now.

Why not try the latest Ubuntu "alternate":
[http://cdimage.ubuntu.com/ports/daily/](http://cdimage.ubuntu.com/ports/daily/)

or even the Live-CD desktop (although I'm a die-hard alternate installer)
[http://cdimage.ubuntu.com/ports/daily-live/](http://cdimage.ubuntu.com/ports/daily-live/)

I'm sure that Xubuntu will be getting right up to speed shortly, if not now.  You can always load Ubuntu, and then install the Xubuntu environment afterwards and choose it at the GDM login session prompt:
```

sudo apt-get install xubuntu-desktop
```

---

### Post by tjniels on 2008-04-12
I'll try what you said.  Right now I'm downloading Ubuntu 8.04 PPC, the desktop CD.  I like the alternate installer as well, but since I like my Debian setup on my iMac G3 I don't want to change it...  Ubuntu is probably too heavy for that iMac without a serious RAM upgrade anyway.  I'm going to test the live CD on my iBook G4, which is my work computer, and if it works I may install in a few weeks.  It's either that or Leopard, maybe even a dual-boot setup.  Does anyone know if the thermal controls, i.e. fan, etc, are working on Hardy?  Specifically for a G4?  I've heard that Gutsy never got the thermal controls for G4s and G5s, and I'd rather not have to compile my own kernel.

It looks like I'm not the only one downloading today, I can't keep my download rate above 300 KB/second.  Wow, cable internet has really spoiled me!

Thanks!

---

### Post by stream303 on 2008-04-12
Thermal control was more or less fixed in Feisty, so I don't see any problems there.  The only weird thing for me so far has been having to use cpudyn instead of powernowd for frequency scaling on my G5 iMac.  That may not be an issue on your machine.

Look forward to reading the results of your tests!

---

### Post by tjniels on 2008-04-12
> I think the thread title is kind of misleading. There is no reason not to use both. Both have their good points and the experience can be rewarding by taking the tips and tricks you learn from one to the other.

Oh, I agree completely.  I had a few reasons to name the thread what I did, and it has evolved since then.  Here are the reasons I had:

1) I was a total noob when I started this thread, and didn't know enough about either to make a fair judgment.  I wanted to see who in the community had done similar things, and get a feel for which distro would be a better match *for my iMac G3.*
2) I thought a comparison thread like this would both get a lot of attention, and help other noobs get a feel for which distribution has the features they would like.  Sure the live CD is a great option for trying Ubuntu, but I have not found any sort of "live CD" for Debian.  It seems to be more of a leap of faith, if you know what I mean.  :)

I was right that this thread would get a lot of attention, it comes up in Google results all the time!  If you search for the right topics, of course.  I think it is worth keeping this thread alive so that:
1) Die-hard Ubuntu users and noobs alike can share and/or read success/failure stories about various *ubuntu distros, and make informed decisions before downloading or installing, and
2) So that the would-be Ubuntu users who don't have as much luck installing on their PPCs don't entirely give up on Linux.  I love OS X, but sometimes running Tiger on an older machine can be like pulling teeth.  10.3 and 10.2 are only marginally faster, and lack features.  Enter: Debian and/or Ubuntu.

So while a few posts are off-topic, I think the general feel of the thread is that of a comparison thread and install log for older PPCs.  Thanks to all those who have posted so far, I've learned a lot!

I have just finished the Hardy download, I'll burn it and try booting my G4, then report back.

---

### Post by stream303 on 2008-04-12
> **Cows said:**
> I was trying OpenBSD and FreeBSD. They are good OS's but the community sucks.

Therefore it's time to show them how to do it with Ubuntu-spirit!  :)

I actually like all three bsd's for various reasons, although I have only run OpenBSD on an old-world mac.  It was quite a revalation to me that you could partition your disks with just a simple root and swap, instead of going for separate /usr /home /var /log etc, although that would make any bsd sys-admin gasp. :)

FreeBSD initially hooked me when I found that they included a very simple editor with the initial install, (The EE editor), when I quickly found out that I didn't have the vi-editor skills of Bill Joy. :)  It was that level of thoughtfullness, rather than any speed-hype, that made me want to look into it more.

Net and Open also appealed to me, so I ran those as well once I discovered some basics that were shared with FreeBSD.  FreeBSD has my interest again, now that they also offer ppc support, but I admit that I haven't tried it yet.

The main support still seems to be in the mailing lists and newsgroups, so I quickly got my favorite newsreader, SLRN up and running, although later got my gui on, and used a graphical newsreader from there on.

With OpenBSD you have to remember that the devs have created something for themselves, and have made it publicly available.  So if you dig it, go for it.  Once one wraps their head around this, it doesn't seem so hostile after all.

At any rate, people are just people, and ignore the cheerleaders.   Use and enjoy what works.  There is a bsd forum here, so that is a good start.

I can see it now on Slashdot --  "Ubuntu user praises BSD!"

It's time to blow away user-misconceptions about each other, that only serve to distract the average guy from using and enjoying something wonderful - from Linux to BSD.  They BOTH rock!

Man, what are you guys doing to me today?  What's with the soapbox? :)

---

### Post by tjniels on 2008-04-12
> It's time to blow away user-misconceptions about each other, that only serve to distract the average guy from using and enjoying something wonderful - from Linux to BSD. They BOTH rock!

Yeah dude, make love not war, right?

JK, lol.  8-)  I couldn't find a peace sign emoticon, too bad.

Interesting observation–I have always known that OS X is UNIX based, but when doing a custom install on an older machine two nights ago, I found an interesting option: a checkbox next to the words "Install BSD subsystem".  I assumed that was required for the system to function, so I left it checked.  However, in all my years using OS X I have never noticed anything referred to as BSD.  Now, without evoking any angst or calling down "fiery darts from the adversary", can I get an informed opinion on what this means?  The OS was 10.3.9.

OK, the Hardy Live CD is in my drive, I will now *try to* boot into 8.04 on my iBook G4.  Ready, set, GO!

---

### Post by stream303 on 2008-04-12
> **tjniels said:**
> Yeah dude, make love not war, right?
Oops. I looked down and saw that I still had my bell-bottoms on.  Guess I would have run the Berkeley bsd rather than ATT back in the day. :)

I guess in today's vernacular, I should have said "don't be a hater, player!"  Or something like that.

> I found an interesting option: a checkbox next to the words "Install BSD subsystem".

It's been awhile since I've done a custom install, but I think this refers to installing Apple's X11 environment, which I played with for awhile with the fink repositories.  I got some good retro-practice with the TWM window manager, lynx, Xeyes, Xcalc etc.  I know you need it for running things like OpenOffice compiled for X11.  Maybe a native aqua port is available these days.

The funny thing is when they state that OSX is based on FreeBSD for the userland, many forget the cross-pollination in the code between all three of the BSD's.  Plus the kernel is based on Mach, yada yada.  

Interesting to see the results of the Hardy install....

---

### Post by tjniels on 2008-04-12
> Oops. I looked down and saw that I still had my bell-bottoms on. Guess I would have run the Berkeley bsd rather than ATT back in the day. 


lol, I don't go back quite that far!  My first computer was an original 128k Mac, I would boot the OS from an 800k floppy disk.  The computers at my elementary school were of the Apple ][e variety, I'm sure you remember those!  All 30 or so computers would boot from like an 8MB network hard drive, then ran AppleDOS from memory.  Wow, what a riot.  We would all fight over the two computers that had four-color screens, the rest were green and black.  If the computer ever froze, the teacher would come over and slap the monitor as hard as she could.  Funny thing is, that always seemed to fix it!  Ah, those were the days.

*sigh*

So no, I don't have bell bottoms on, but I can still be a sentimental sap!  I guess I'm wearing my neon pump-sneakers and a striped sweatshirt with silver-tab levis, or something like that.

Here's the report on my attempts so far with the Hardy Live CD, I'll just write first what I typed at the boot prompt :
1) "live".  No luck.  It acted normal for about a minute, then hung on a black screen.  The CD stopped spinning for over a minute and I rebooted.
2) "live video=ofonly".  No luck.  It acted normal for about a minute, then hung on the same black screen.  The CD stopped spinning again and I rebooted.
3) "live-nosplash-powerpc".  Ah, a glimmer of hope!  It acted normal and even ran through the checklist with a bunch of [OK]s on the right side of the screen.  The only error was bluetooth, probably because this isn't a blue-tooth laptop.  It got to the orange screen, then the desktop appeared with a new background (about time for that, IMO).  It was a strange-looking bird with swirly feathers, presumably a "Hardy Heron".  The top and bottom panels looked familiar.  HOWEVER, the cursor would not move.  I tried both the trackpad and a USB mouse, to no avail.  Nice desktop, though.
4) "live-nosplash-powerpc video=ofonly".  Same story as #3.

Any other guesses for what to type at the boot prompt?  I won't attempt any install until I've seen it work live, this computer is too important to risk at the moment.

You know, if Hardy Heron gets a picture of a Heron for it's desktop background, I have a recommendation for Gutsy Gibbion background, see below:

---

### Post by tjniels on 2008-04-12
> It's been awhile since I've done a custom install, but I think this refers to installing Apple's X11 environment, which I played with for awhile with the fink repositories. I got some good retro-practice with the TWM window manager, lynx, Xeyes, Xcalc etc. I know you need it for running things like OpenOffice compiled for X11. Maybe a native aqua port is available these days.


X11 had its own checkbox, so I don't think it's that.  I always install X11 so I can use GIMP.  I used to use OpenOffice, but there is an Aqua port–called NeoOffice, it's actually pretty nice.  That's what I'm using for now.  OpenOffice for Linux, NeoOffice for Mac.

> "You figure it out. Try apropos. What do you think it means?" as if we were living back in 1973. Put on bell-bottoms or a pen-protector and pretend to be in a *nix university class. 


I know the feeling, I don't know if using GUI-based OSes has dumbed us down or made us more efficient (or both) since then.  One think I appreciate about OS X is that I have only been "forced" to the command line a handful of times, and only after having seriously tweaked things I knew I shouldn't have.  ;)

---

### Post by oswaldkelso on 2008-04-12
> **tjniels said:**
>  but I have not found any sort of "live CD" for Debian.  It seems to be more of a leap of faith, if you know what I mean.  :)


I have a live debian etch cd but cant remember where i got it. By default, there is not any root password. I remember I got stuck here and someone told me to You can switch to root with sudo -i or set a password for root with sudo passwd I cant remember exactly!!! sorry.It may have been here but I'm not positive its the same image. 

[http://live.debian.net/cdimage/release/4.0_r0-rc1/powerpc/iso-cd/](http://live.debian.net/cdimage/release/4.0_r0-rc1/powerpc/iso-cd/)

not ppc but good info on how to build you own cd
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

And you may like to try the ppc image built for ps3
[http://www.keshi.org/moin/PS3/Debian/Live](http://www.keshi.org/moin/PS3/Debian/Live)


the other live ppc cd I use is finux


[http://www.finnix.org/](http://www.finnix.org/)

[http://distrowatch.com/table.php?distribution=finnix](http://distrowatch.com/table.php?distribution=finnix)

---

### Post by tjniels on 2008-04-12
Thanks for the info.  I really don't need a live Debian CD, I already installed on my iMac and it works better than anything else I've found, including OS X!  It make the machine feel fairly useable.  But the links you shared may at least be valuable to those who haven't tried Debian.

I was just commenting on my experience, when I installed Debian I couldn't find a Live CD and thus it was a leap of faith.  Since Debian maintains official PPC support, for now at least, and I determined that it works properly on one PPC machine, I will rely on flawed induction to assume that Debian will work on *all* PPC machines.  Some time this summer I'll give Debian its fair chance on the G4 iBook, I imagine it'll run like a dream.  ;)

Thanks again for the links!

---

### Post by stream303 on 2008-04-12
> **tjniels said:**
> HOWEVER, the cursor would not move.  I tried both the trackpad and a USB mouse, to no avail.  Nice desktop, though.

Arggh! :)  Ubuntubrian had the same problem - I guess the major thread is in the Hardy Development forum:

[http://ubuntuforums.org/showthread.php?t=705267&page=7](http://ubuntuforums.org/showthread.php?t=705267&page=7)

I'm hoping that *somebody* in the devs read it, although we know forums aren't supposed to be where it's at for feedback.  Well, I guess that even though we are in feature-freeze, they've still got some work to do on Beta.. :(

---

### Post by tjniels on 2008-04-12
> Ubuntubrian had the same problem - I guess the major thread is in the Hardy Development forum:

[http://ubuntuforums.org/showthread.php?t=705267&page=7](http://ubuntuforums.org/showthread.php?t=705267&page=7)

Thanks, I just posted about it over there to try and draw some attention to the problem.  I don't know if they'll be able to replicate it, but I sure hope it gets fixed.

---

### Post by oswaldkelso on 2008-04-12
That 's cool I just thought it good to point out they do exsist :)  They're just not so easy to find

---

### Post by tjniels on 2008-04-12
> That 's cool I just thought it good to point out they do exsist  They're just not so easy to find.


Thanks for the contribution!

---

### Post by themailman05 on 2008-04-12
Ok...

This is my first post, although I have been using Ubuntu for a while.
Well technically not Ubuntu, Xubuntu. I am running a slot load Imac G3 350 with Xu 7.04, and it integrates almost seamlessly with the other windows PCs in my house. In fact, switching from OSX 10.3 to Xubuntu had to have at least quadrupled my total speed, every way around. I would _NOT_ use any form of 7.10 on a PowerPC type of mac in any way shape or form. The mac will appear to have been installed correctly, but the problem is, the kernel stops booting about 1 bar into that funny splash screen. Trying to upgrade from Fiesty to gutsy lost me all of my personal files. I had to change hard drives so I could actually reinstall. All ubuntu forms have some problems, but there is so much code out on the forums to solve them. Fiesty has a very active community, and almost any problem is easily solved by a quick trip to the forums. Debian is O.K., but I have to admit, Xubuntu has been nothing but great to me through any of this long, winding road.



XUBUNTU 7.04 ALL THE WAY!!!!!!!

---

### Post by tjniels on 2008-04-13
> XUBUNTU 7.04 ALL THE WAY!!!!!!!

I haven't tried Xubuntu 7.04 yet, I think I may have had problems with the installer.  Here are my current setups (below).

---

