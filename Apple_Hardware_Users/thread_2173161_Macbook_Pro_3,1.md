---
title: "Macbook Pro 3,1"
date: 2013-09-08
forum: Apple Hardware Users
---

### Post by tara2 on 2013-09-08
Hello I have tried my best searching the forums and still cant seem to  find the info I need. Perhaps someone can point me in the right  direction? I have an Macbook Pro 3,1 core 2 duo 2.3 ghz. I would like to  install to an external hard drive although I can use a usb stick for  now. I have downloaded the 13.04 desktop 64bit version and burned it to a  DVD. When the DVD was finished burning it was ejected and said it was  not useable. Upon trying to boot from the DVD I was presented with 3  options two for efi boot and one for windows. I tried all 3 and it just  hung at a black screen. I was however able to get a virtual box setup  running from the DVD that I burned. So I guess my question is what do I  need to do to get my macbook to boot from the dvd so I may install?  Thanks!

---

### Post by SilverOne on 2013-09-08
Hey tara2, 

I'm not exactly sure what is going on since i don't own a macbook 3.1, what exactly do you mean by black screen ? it just hangs there ? is there a flashing _ at the top left corner ?

Also may i suggest you use [refind]("http://www.rodsbooks.com/refind/") ? refind is a boot loader, and it is very easy to [install]("http://www.rodsbooks.com/refind/installing.html") and remove.

---

### Post by tara2 on 2013-09-08
Hi, I will try refind later tonight. What I am getting is if I hold the C key down at boot it will hit the grey screen and stay there same as when osx is booting sans the apple logo. It will stay there till I power down I even let it go for over 30 mins during one try. While its in the grey state I can hear the dvd drive going back and forth over and over in the EXACT same pattern. If I hold the option key during boot it shows my internal HD and for the unbuntu dvd it shows three separate dvd icons windows, efi and efi in that order. Choosing the far right efi gets it stuck in a black screen with nothing else. The other efi icon will start to boot for a second and I get the message "secure boot disabled". When choosing the windows icon I get a message that says something like choose cd/dvd drive but no keys work and it is just stuck there.
I also thought I read it was hard to boot from an external which is what I would prefer however whatever can work is fine for me. I have my internal backed up so I can use that if need be. I was looking for a single boot type deal not dual osx/unbuntu. Thanks!

---

### Post by SilverOne on 2013-09-08
Hello,

it seems to me you're having problems with EFI boot, and you're not even getting to grub which kinda sucks. However, i suspect that EFISTUB (bios compatibility mode) which is represented by the windows logo will work with refind. 

Fingers crossed.

---

### Post by tara2 on 2013-09-08
Thanks I will give it a shot and report back tonight.

---

### Post by tara2 on 2013-09-08
Well that got me to be able to "start" the boot process but not finish. I had 2 choices regular and fallback and got the same results with both. I did not choose install at first just the run without installation option the end result was that after much dvd reading the drive would just stop spinning screen black the entire time. After many re tries I chose the install option and here is what I got when it froze...

12.496334 kernel panic-not syncing: vfs: unable to mount root fs on unknown-block (1-0)

of note is that it was doing/loading something as shown by the ethernet light on my router turning on midway through the process

---

### Post by SilverOne on 2013-09-08
Hey, 

I digged around the internet for a bit, this seems to be a common problem. 
[http://forum.acronis.com/forum/16521](http://forum.acronis.com/forum/16521)
```

i have followed the recommendations by Customer support to create a bootable rescue media on a "USB stick". after doing some brief testing i have not observed the "kernel panic" when booting from that type of media.
in other words:
 - booting from USB: PASS
 - booting from CD - AHCI: sporadic FAIL

```

I have never installed ubuntu from a cd or dvd either. 

so would you try doing this with a USB drive ? there are step by step instructions here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx")

also after you write the image to the pen drive, verify the md5 sig [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Mac_OS_X]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Mac_OS_X")
you can find the md5 sums here: [http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)  

you can also try the image made specially for macs! that might work too.

---

### Post by tara2 on 2013-09-08
Thanks much! I am pretty clueless with using the terminal so its gonna take me a bit to figure out those usb instructions but I will attempt. Thanks again!!

---

### Post by SilverOne on 2013-09-08
Hello, you are welcome. 

Do not be afraid of the terminal. We all were at some point. 
If you do not know where your ubuntu image is downloaded on your drive, you can always "drag" it to the terminal. that should input the path for you. 
you will still have to figure out the path to the usb drive, it should be something like /dev/disk2 or something.

---

### Post by tara2 on 2013-09-08
I have completely given up on terminal could not get it to work convert failed no such file or directory no matter how I do it going to try to get it working via the virtual box and the startup disk creator. ugh

---

### Post by tara2 on 2013-09-08
makes me wonder though why there is no downloadable .dmg version

---

### Post by SilverOne on 2013-09-08
Hello,

it's okay, working with the terminal is easy. here, i will show you.

So, first to make things simple, let's move the ubuntu download iso to the desktop. 

then we open a terminal, and write hdiutil convert -format UDRW -o ~/Desktop/ubuntu  

now, click on the ubuntu iso and drag to the terminal, wait a second, and then drop :

[http://d.pr/i/1PCj](http://d.pr/i/1PCj)

you are probably thinking... but HEY! on the tutorial we first insert the INPUT location, and then the OUTPUT... well...  this is probably why you were failing. Also, keep in mind the ~ means your home folder.

[http://d.pr/i/e79r](http://d.pr/i/e79r)

okay now we have an image, now what ? 

first we insert our little usb drive

then click on the little apple, on the top left, and about this mac. Depending on the mac os x version you are running, you will either open system report directly, or will have to click on System Report. Then click on usb. 

[http://d.pr/i/qk34](http://d.pr/i/qk34)

now, try to find your USB drive, and then click on it. 

you will see some information pop up below, we need the BSD NAME, which mine is disk2. with that out of the way we move on.

Now, open Disk Utility, select your pen drive on the left, and click UNMOUNT. 

[http://d.pr/i/M3hQ](http://d.pr/i/M3hQ)

mine shows mount because its formatted under ext4 which isn't readable on mac os x. make sure you dont click EJECT. 

all we have to do now is burn the dmg. 

[http://d.pr/i/FHpv](http://d.pr/i/FHpv)
on the terminal write clear and then press enter, this will clean up the terminal.

then write sudo dd bs=1m if= (drag ubuntu.dmg) of=/dev/(your disk) 

it'll ask oyu for your admin pass, you won't see ** pop out as you type in the chars, press enter. 

you will not get a percentage, or anything. you'll just see your usb drive led flash. 

when it is done, you will see this : 
[http://d.pr/i/oCQR](http://d.pr/i/oCQR)

good luck! i would first try the normal image, then the one made for macs.

---

### Post by tara2 on 2013-09-08
wow thanks for the step by step it is working well almost done just waiting I screwed up when reading the orig instuctions and typed target.img that was my mistake been a long day sorry!

---

### Post by tara2 on 2013-09-09
Ok that worked but only part way. I am getting the exact same results with the usb route although it gets to hang much faster reading from the usb than the dvd drive. The only change was that I did not get the unable to mount error I got before when trying the install route. I redid the usb a few times just to be sure. I am running out of ideas and patience I am thinking about trying the same with the 12.04 release just for giggles.

---

### Post by tara2 on 2013-09-09
Small update just for giggles i tried to skip the .iso to .dmg conversion it seemed to work just fine although the end result was the same. Could this be an unnecessary step?

---

### Post by tara2 on 2013-09-09
Ok tried the 12.04 version and got the same result:(

---

### Post by SilverOne on 2013-09-09
did you try the mac version ?

---

### Post by SilverOne on 2013-09-09
just to make sure , there is no other error about the drive mounting ?

just a black screen ? if this is so ,this may be solved by setting nomodeset in grub. take a look here : [http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)

if you have any issues let me know.

---

### Post by SilverOne on 2013-09-09
after googling for "macbook 3.1 ubuntu nomodeset" i found this: 

[http://ubuntuguide.net/how-to-install-ubuntu-on-macbook-air-3-1-via-usb-flash-drive](http://ubuntuguide.net/how-to-install-ubuntu-on-macbook-air-3-1-via-usb-flash-drive) 

this may indeed fix your issues.

---

### Post by tara2 on 2013-09-09
Hello again! The mac version? I guess I am not sure what you mean there were only two choices one was 64bit and the other 32bit or did you mean at startup? there is 3 options one for windows and 2 others I tried all 3 just in case as for the nomodset some links to tools specifiacaly mkisohybrid are not working but isnt that basically what I did in terminal? and the other post you linked to seems like it shows how to do it after install? Sorry but I am really getting lost here. And yes no drive errors nothing.

---

### Post by SilverOne on 2013-09-09
Hello, 

Let's try nomodeset first, follow the directions on this link: [http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997) 
scroll down to: 
How to enable kernel options on the livecd (before install) 


if it installs well, you'll have to enable that after installing too! the rest of that link explains how to do that. 


if nomodeset doesn't work, there is an iso image made just for macs : [http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)
if you scroll down you will find : 

ubuntu-13.04-desktop-amd64+mac.iso          24-Apr-2013 18:26  783M  Desktop image for 64-bit Mac (AM

you are currently using the :
ubuntu-13.04-desktop-amd64.iso              24-Apr-2013 18:25  785M  Desktop image for 64-bit PC (AM

---

### Post by tara2 on 2013-09-09
Ok thanks I will try the first step unfortunately I have only one computer so it takes a bit to log in and out etc. And thanks now I see what you mean by mac version i was getting my .iso files from the main ubuntu page not your link

---

### Post by tara2 on 2013-09-09
ok the nomodeset is not available the screen has no f6 option and pressing the key does nothing(if the mac image does not work I will go back and try to get a screen shot). I am download the mac specific image now and will give that a shot.

---

### Post by tara2 on 2013-09-09
ugh the link is dead [http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-amd64+mac.iso](http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-amd64+mac.iso) but the torrent file worked so I guess its time for a coffee!

---

### Post by SilverOne on 2013-09-09
Hello,

did you try EFI mode and EFISTUB ( the fall back ) mode ? 

what screen do you get ?

---

### Post by tara2 on 2013-09-09
Yes I tried both routes same result the screen I got was close to this[IMG]http://img827.imageshack.us/img827/3509/dgfdgrunningoraclevmvir.png[/IMG]but all text was on upper left hand corner and none of the f options listed but the mac version should be done loading in about 30mins ya slow dsl here and I will give that a shot

---

### Post by SilverOne on 2013-09-09
Hello, i would prefer you to use the regular image which will install it in efi mode. let me reboot and see which screen shows up

---

### Post by tara2 on 2013-09-09
I did however find a way to get into a screen close to this where I could possibly type in some boot options but was not sure what to type and where if the mac 

version does not work ill get some screen shots and go from there.
[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

---

### Post by tara2 on 2013-09-09
sorry just got that last message ill try the reg image

---

### Post by tara2 on 2013-09-09
gonna try to log into the forums on my iphone that may help a bit to free up the computer

---

### Post by SilverOne on 2013-09-09
Hey, 

great that's the screen i get too! that's the grub bootloader: 

[http://d.pr/i/vvCP](http://d.pr/i/vvCP) 

select install linux, and then don't click enter, click e instead.

[http://d.pr/i/nfd](http://d.pr/i/nfd) 

this screen will appear, go to the end of the biggest line and write nomodeset, i don't know if it needs to be before or after the -- so test around. 

after you write it, press f10 to launch.

also after you install linux you will have to do the same but the screen will be the one you posted, make sure you write nomodeset and not what the original author wrote, which is a typo. 
after you install there will be no refind menu, you can press ALT (the key next to cmd) to enter the "general" menu, and choose which os you want to boot. 

you'll have to reinstall refind later.

---

### Post by tara2 on 2013-09-09
Now we're getting somewhere! It's up and running thank you so much!! I have to do some hard drive rearrangement before I install though. Are there anymore steps?

---

### Post by SilverOne on 2013-09-09
Hello,

sure, if you want to keep MAC OS X, i recommend you shrink the partition using disk utility on the mac OS X side, this will give you a "free space" partition. 

Also, after you resize the partition if you need read/write you must disable journaling. To do this you can click on the mac os x partition, click alt, and then go to file and disable journaling. You need journaling on to resize thought.

if you have less than 2GB of ram i recommend you set up a 4GB scratch partition, you can also later make a scratch file. it should be easy to find tutorials to do a scratch file.

---

### Post by tara2 on 2013-09-09
Ok I was planning to use a empty internal drive for Ubuntu and use an external for osx. Gonna do some drive work gonna be a few hrs of moving files around drive space is at a premium here! Thanks again ill post when she's all up and running!

---

### Post by tara2 on 2013-09-09
Any suggestions on the best format style to put my drive in or will the installer figure that out for me? Again no dual boot just Ubuntu

---

### Post by SilverOne on 2013-09-09
in that case there's a replace mac os x with ubuntu no? that'll take care of things for you. 

keeping os x on a separate drive is a good idea because it's the only way to get firmware updates. i doubt there's anything important coming though.

remember after you install you will have to follow the grub guide from where you took the screenshots to make nomodeset permanent. otherwise it won't work again i think. but still, you could install drivers and test it. if it doesn't work, add nomodeset.

---

### Post by tara2 on 2013-09-09
Ya not sure about the replace option I'm back in osx cleaning up the drives. And yup thanks I remember about making the change perm. Thanks again you've been a huge help!!

---

### Post by tara2 on 2013-09-09
Well I got it to install but still having some issues. After the install and upon reboot I tried to get into the menu by holding shift that did not work but holding the esc key did. So i hit the e key to add "nomodeset" and low and behold it was already there so i tried to let it boot got the purple screen for a sec then right to some text asking for login i logged in and typed "startx" and got the following error 
Fatal server error:
no screens found

I tried to boot without the nomodeset command and also moved it place in line all with the same prob. Any thoughts? Sorry for the sideways pic.

---

### Post by SilverOne on 2013-09-09
Hello,

what pic ? and what gpu do you have

could you also post the output of : lspci | grep VGA  
take a pic if you can

---

### Post by SilverOne on 2013-09-09
Actually that's not needed you should have a 8600. 

I suspect this has to do with EFI booting, but i can't be sure. the only way around this, is to install using the mac image, which will use EFISTUB (bios compatibility) mode.

EDIT:

I have a macbook 8.2, in EFI mode i'm only able to access the integrated graphics. You don't have any. I usually boot into bios compatibility mode when i want to use my ATI card. There's ways of using discrete graphics but they're complicated, so i usually stay off that end just because they require maintenance. 

So, sorry but it seems you'll have to redo with the BIOS (mac ubuntu image).

---

### Post by tara2 on 2013-09-09
Hi sorry I could not get the pic to attach guess I need some sort of hosting service? and yes its an 8600. I have the mac image downloading again ill redo everything and repost thanks!

and just when you think your flying into homeplate.... hahaha

---

### Post by SilverOne on 2013-09-09
Hello, 

i was in your position once. there's a thread around here somewhere. 

i fiddled with it until it finally worked. these days i know exactly what to do so running linux is easy and doesn't require anything from me. 

good luck. oh and i updated the previous post

---

### Post by tara2 on 2013-09-09
Thanks ill get there soon enough I have had it with osx (still beats windoze) pretty determined to get this going! I did do a bunch of forum searching but nothing really seemed to fit. Hope the mac image does the trick.

---

### Post by SilverOne on 2013-09-09
I've had it with apple and windows too. Never looked back. Unfortunately no one makes hardware like apple does. 

Anyway, make sure you boot in fallback mode or whatever it's called. I don't think your image comes with an EFI boot but you never know.

---

### Post by tara2 on 2013-09-09
I guess I shouldn't knock osx that much I went with it after they went to osx from 9 (still have a ppc mac mini running as a music server) its been pretty good crash wise and I plan to keep it on another disk as I use final cut (the old one) and some music programs that are invaluable to me guitar rig, pro tools etc never had issues with them but honestly the final push to get something else was the video playback performance on you tube netflix etc even watching a 480 res vid that way has my processor pinned. I love vlc and it runs on ubuntu:)

---

### Post by SilverOne on 2013-09-09
Well my final push is seeing how closed apple is. And never knowing how far they can go. Sometimes, i look onto the future and see laptops without root access. 

But not only that, not only because of the bad things - Open source is really the way to go, it just brings so many benefits and linux is in a way the biggest community effort in the world. It's because knowledge is free and accessible to all that we've come this far as a society.

how's that download going ? 

try without nomodeset first btw

---

### Post by tara2 on 2013-09-09
finished the download a while ago put it on the usb stick and all I got for an option was the windows legacy choice did not work at all I skipped the convert to .dmg step so I just finished that and it is writing the .dmg to the usb right now wish me luck.

---

### Post by SilverOne on 2013-09-09
that's the mode you want. use legacy, if you boot into EFI you'll have the same problem.

Best of Luck

---

### Post by tara2 on 2013-09-09
Just tried again same issue when I choose legacy OS it pops right away to a black screen drives shut down and it hangs. I will try one last time for the heck of it. I do not have the other two EFI options using this mac image as I did before just the Legacy choice also the only way I can even get the mac to see the usb is by having my external with osx and refind on it hooked up. Holding the option key shows nothing at all although with the non mac image I had the two efi choices and the one legacy. Gonna pack it in for the night though before this things goes flying out the window! Ill take a fresh stab at it in the morn after a coffee. Thanks again for the help I know you have spent a ton of time trying to walk me through this. I cant possibly be the only one whos had these issues. Cheers!

---

### Post by SilverOne on 2013-09-09
Hello, 

i believe the bios mode will work with refind, if it doesn't though i don't know what to do next. Have you tried connecting the external drive and seeing if it boots straight into refind ?

the mac cd does not have efi boot , you will never see those. 

good luck for tomorow then

---

### Post by tara2 on 2013-09-09
No it wont go right to refind unless I hold the option key seems like it wants to go right to my internal that has ubuntu on it. Hmmm maybe wipe the internal clean then try with rebooting with just the usb in?

Still confused about needing to convert the .iso to .dmg seems to work the same both ways and yes I have tried each time going both routes.

---

### Post by SilverOne on 2013-09-09
Hold the key, open refind, and then try to launch the installer.

don't worry about the conversion it probably doesn't affect anything.

---

### Post by tara2 on 2013-09-09
Yup tried that it just goes to black right away. And I just figured I would try both ways anyhow just in case the conversion did matter. Didn't want to waste all this time due to being to lazy to do the convert!!

---

### Post by SilverOne on 2013-09-09
I downloaded and attempted to test the buntu mac iso but for some reason it doesnt even show up for me. 

I don't think there's much else you can do, did you try fallback mode on the regular iso ? that would be the last thing i would try.

i would try it now and either try another distro, or just burn the backup back into the macbook main drive overnight.

---

### Post by tara2 on 2013-09-09
Yes I tried the fallback on the regular iso as well as the 12.04 release. Oh well no ubuntu for me back to osx thanks for the help I really appreciate the time you have spent trying to help. Maybe the Macbook pro 3,1 should be put in an incompatible list somewhere. Thanks again Cheers!

---

### Post by SilverOne on 2013-09-09
No problem , i'm sorry i wasn't able to help you further.

good luck in the future though.

---

