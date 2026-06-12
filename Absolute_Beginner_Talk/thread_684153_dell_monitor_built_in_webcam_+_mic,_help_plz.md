---
title: "dell monitor built in webcam + mic, help plz"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Miroku on 2008-01-31
hello

i got this [dell monitor]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&cs=19&l=en&s=dhs&sku=320-6252&redirect=1") that has both a webcam and mic built in. none of them work in linux.
i am running gutsy amd64.

here is lsusb before i plug it in:

```
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

and after i plug it in:

```
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 022: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 021: ID 05a9:2643 OmniVision Technologies, Inc. 
Bus 001 Device 020: ID 0424:2512 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000  

```

i believe its a creative webcam. let me kno if i should post any other info. thx.

i did try easycam but it wont install i think because i am running amd64.

---

### Post by Miroku on 2008-01-31
i found [this website]("http://translate.google.com/translate?hl=en&sl=it&u=http://marco.boneff.ch/blog/%3Fp%3D482&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dlive!cam%2BOmniVision%2BTechnologies,%2BInc.%2Blinux%2B05a9:2643%26hl%3Den%26sa%3DG")

i was just wondering if easycam would do all of that automatically? because if it will, i will just wait until im back in 32bit ubuntu when hardy comes out. tia.

---

### Post by Miroku on 2008-02-09
so anyone got any ideas?

---

### Post by linuxwizard on 2008-02-09
Hello Miroku
This is your webcam > Bus 001 Device 021: ID 05a9:2643 OmniVision Technologies, Inc. > I am searching to find which driver you need but no luck yet. Will let you know if I find something

---

### Post by Miroku on 2008-02-09
> **linuxwizard said:**
> Hello Miroku
This is your webcam > Bus 001 Device 021: ID 05a9:2643 OmniVision Technologies, Inc. > I am searching to find which driver you need but no luck yet. Will let you know if I find something

thanks alot.

i think that italian website i mentioned in my previous post may have the drivers but i am not sure, so you may want to check that out.

thanks again for your effort.

---

### Post by linuxwizard on 2008-02-09
Have you tried using your webcam with Ekiga ? Or any other apps. ? If so did you get any errors messages ?

---

### Post by Miroku on 2008-02-09
in ekiga, under webcam, it just shows 'standby', other cam software does not detect it at all. i cant use easycam because i am running amd64.

---

### Post by linuxwizard on 2008-02-09
You might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there

---

### Post by Miroku on 2008-02-09
i tried with ekiga, it does not recognize that i have plugged it in

---

### Post by linuxwizard on 2008-02-10
Not sure what else to say. I thought maybe working with the setting in Ekiga might get the cam working. I have searched looking for a driver but don't see anything on yours. Found other OmniVision Technologies, Inc but not your ID #. Wished I had more to offer you.

---

### Post by Miroku on 2008-02-10
> **linuxwizard said:**
> Not sure what else to say. I thought maybe working with the setting in Ekiga might get the cam working. I have searched looking for a driver but don't see anything on yours. Found other OmniVision Technologies, Inc but not your ID #. Wished I had more to offer you.

well im hoping that when i switch back to 32bit, easycam will do the trick. the software that is installed for it on winxp is saying it is 'creative livecam' which i think is popular so easycam should do it.

thx again for the effort. :)

---

### Post by Miroku on 2008-02-10
well this may help someone in the future, i tried the instructions that i found on that italian website i previously mentioned. they did not work.

i may have done it incorrectly, but i tried following the instructions to no avail.

---

### Post by kriok on 2008-02-11
> **Miroku said:**
> i found [this website]("http://translate.google.com/translate?hl=en&sl=it&u=http://marco.boneff.ch/blog/%3Fp%3D482&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dlive!cam%2BOmniVision%2BTechnologies,%2BInc.%2Blinux%2B05a9:2643%26hl%3Den%26sa%3DG")

i was just wondering if easycam would do all of that automatically? because if it will, i will just wait until im back in 32bit ubuntu when hardy comes out. tia.

Hi,
I am a very new Ubuntu/Linux user. Currently running Ubuntu 7.10 **amd64** version.
On the italian web page u linked, there is a link to [[COLOR="Blue"]http://www.rastageeks.org/downloads/ov51x-jpeg/[/COLOR]]("http://www.rastageeks.org/downloads/ov51x-jpeg/"). That driver worked for my  Hercules Deluxe Webcam with inbuilt mic (05a9:4519 OmniVision Technologies, Inc.). The list of working webcams is listed [[COLOR="Blue"]here[/COLOR]]("http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams") - yours is not listed there but the guy from the italian page used driver from there so it might work for you as well. It did work for me being on a 64bit platform. I have to add that Camorama doesn't display the image correctly for me (black and white and some weird distortions), however "Cheese" which I installed from repositories works quite well (I get better image in WinXP-32bit).

I want to confirm that this driver works for me (somehow - see above) in Ubuntu 7.10 amd64. Can't compare it to any 32bit Linux distro since this is my first linux experience. I dont want to post any code how i got it working because my system must be a mess. Usually solving my problems with trial and error :( having only a very vague idea what I might be doing to my system :(

For possible solutions try: [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/Ov51x"), [[COLOR="Blue"]rastageeks-driver page[/COLOR]]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall")

If you intend to use your webcam in Skype 2.0 beta. I suggest have a look [[COLOR="Blue"]here[/COLOR]]("http://forum.skype.com/index.php?showtopic=100897&st=40&p=465545&#entry465545"),
[[COLOR="Blue"]Hercules Deluxe (still, might work for you as well)[/COLOR]]("http://forum.skype.com/index.php?showtopic=100897&st=100"). 
The 1.5.6 version of the driver should have included the workaround they are talking about in those posts. Still I had to add to **/etc/modprobe.d/options** the following line:
```

options ov51x-jpeg forceblock=1

```

As you can see i tried a lot of things and i am not complete sure which one worked...

Hope some of this will help you

---

### Post by Miroku on 2008-02-25
well some strange thing happened to my gutsy today. i started up my computer and chose gutsy from my GRUB menu and it didnt start up. then i was thinking it may be a fluke, so i hard reset and chose gutsy again from GRUB. still blank screen and no hdd activity. then i restarted and picked the recovery gutsy from GRUB and the text startup began. it was going until it reached to look for devices i believe and then kept getting errors one after another. some of them had to do with USB devices, SATA, and then switching something to ATA/100. alot of stuff i did not recognize and then it ended with command line at 'initfrms' or something like that.

very strange.

i then proceeded to log into my xp partition which worked like normal (i was suspecting hdd failure). i then remembered that i unplugged my usb camera + mic that i have tried various ways to fix so i plugged it back in and restarted ubuntu, and guess what? -- started up without a hitch ( i chose my normal gutsy, not recovery).

i am wondering what is going on. is there any way for me to get the log of the startups that failed?

its funny how when something goes wrong in windows, i blame xp but if something goes wrong in linux, i blame myself -- DOUBLE STANDARD but anything to help me from migrate from windows foreverr.

---

### Post by gotsomeideas on 2008-03-14
I have the same monitor as you (the Dell SP2208WFP), and in case you hadn't figured it out yet, the package you need to get the webcam working will be available in Hardy (I installed Hardy alpha 6 and the webcam worked out of the box). It needs [the luvcview package]("http://packages.ubuntu.com/hardy/luvcview").

I still haven't figured out the built-in mic though, if you ever figure it out you should PM me or something.

---

### Post by Miroku on 2008-03-18
> **gotsomeideas said:**
> I have the same monitor as you (the Dell SP2208WFP), and in case you hadn't figured it out yet, the package you need to get the webcam working will be available in Hardy (I installed Hardy alpha 6 and the webcam worked out of the box). It needs [the luvcview package]("http://packages.ubuntu.com/hardy/luvcview").

I still haven't figured out the built-in mic though, if you ever figure it out you should PM me or something.

really? that is awesome. i have a question tho, is it supported in both 32/64 bit or exclusively in one? i was thinking of switching back to 32 bit just so i could use the easycam software which may enable it. and also another question, since my gutsy doesnt recognize it yet, whenever i put my monitor on the cam blinks blue. i was wondering if that happens after you have actually installed it and get it to work? thx for the info.

---

### Post by linuxwizard on 2008-03-19
Hello Miroku
You remember that we could not find a listing of your cam before > Bus 001 Device 021: ID 05a9:2643 OmniVision Technologies, Inc. Found other OmniVisions but not your. I just saw the post by gotsomeideas. So I went and checked again on your webcam and now it is listed here > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) > that is the driver you need. I know that is was not there before, so they must have just add support to it. Will it work on 64 bit you can search on that, 32bit no problem.

---

### Post by nikkkko on 2008-04-28
Hi, I have recently acquired this monitor, (SP2208WFP), and have upgraded successfully to Hardy over the weekend. Reading through these posts it's not clear to me how to get the webcam working.  I installed Lucview to no effect and am hesitating over the Linux UVC driver because I don't really know what I'm doing and don't want to screw up my perfectly working system.

Is Linux UVC the only way to get the webcam going, and if so, do I have to download, compile and install from source?

Thanks

---

### Post by linuxwizard on 2008-04-28
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.
Video Plugin if it shows V4L change to V4L2 or if it shows V4L2 change to V4L. 

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by nikkkko on 2008-04-28
Thanks for the quick reply.  Fiddled with the Ekiga settings but no joy. What I didn't mention in my previous post was that I uninstalled Lucview. Is Lucview a red herring or do I need it?

---

### Post by linuxwizard on 2008-04-28
No you don't need Lucview to get your webcam working. But you are going to need to install the Linux UVC driver to get your cam working.

---

### Post by gotsomeideas on 2008-04-29
> **nikkkko said:**
> Hi, I have recently acquired this monitor, (SP2208WFP), and have upgraded successfully to Hardy over the weekend. Reading through these posts it's not clear to me how to get the webcam working.  I installed Lucview to no effect and am hesitating over the Linux UVC driver because I don't really know what I'm doing and don't want to screw up my perfectly working system.

Is Linux UVC the only way to get the webcam going, and if so, do I have to download, compile and install from source?

Thanks

In case linuxwizard's post didn't convince you, luvcview is very easy to install, no compilation necessary... it won't screw up your system! It's just a small package, nothing to worry about. Just type:

```
sudo apt-get install luvcview
```

into a terminal or just search for the package in Synaptic. If for whatever reason you decide you don't want the package or it doesn't work (it really should though), you can just open a terminal and type:

```
sudo apt-get remove luvcview
```

and it's gone. Nothing to worry about. Are you planning on using Cheese? That's mostly what I was using it for and had a lot of fun messing around with the effects and everything. :) Cheese is also a really simple way to check that your webcam is working. Simpler than trying Ekiga, IMHO.

---

### Post by nikkkko on 2008-04-29
> In case linuxwizard's post didn't convince you, luvcview is very easy to install, no compilation necessary... it won't screw up your system! It's just a small package, nothing to worry about.
I did try luvcview, but it didn't work for me. In fact I tried it first because I prefer to install everything from the repositories, this being my work machine.

I have subsequently downloaded, compiled and installed the Linux UVC driver, (installation going without a hitch), but still don't have the webcam going. I think I'm missing a step.

---

### Post by pravina on 2008-04-29
The best site ever i seen

Is [www.baajaa.com](www.baajaa.com)

where you can get all the things like


jobs, dating, property, motors,sale or purchase items, showbiz section

in showbiz you can post FREE  ad  to Balaji Telefilms, even you can post your Audition Videos.


New Feature Added in baajaa.com is Yellow Pages.
You can have your free simple posting in Yellow Pages.
Even you can Create Your Own Website on baajaa.com in less price than any other site.

---

### Post by linuxwizard on 2008-04-29
nikkkko
After installing the driver did you reboot your computer ? Did you also try using Ekiga again and work with the settings ?

---

### Post by nikkkko on 2008-05-06
Sorry for the delay in replying - I never got a notification.

Anyway, yes, I rebooted and I tried Ekiga again.  Where would the driver appear if it is being loaded properly?  Is it a module which would show up with lsmod?

---

### Post by justing1319 on 2008-05-20
I have the same monitor/webcam and thankfully I have gotten video from the camera however it's still not a simple process. I followed the steps to install Linux-UVC from this post:
[http://ubuntuforums.org/showthread.php?t=593231](http://ubuntuforums.org/showthread.php?t=593231)

However even after the reboot the webcam was not detected in Ekiga. 

output of dmesg:
> [ 1121.239425] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[ 1121.239761] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 1121.240021] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[ 1121.240026] uvcvideo: Failed to initialize the device (-5).
[ 1121.240054] usbcore: registered new interface driver uvcvideo
[ 1121.240084] USB Video Class driver (SVN r209)


So i searched a little further and found this post:
[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg02417.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg02417.html)

after 2 or 3 rounds of
> sudo rmmod uvcvideo
sudo modprobe uvcvideo
dmesg

It resulted in: 
> [ 1772.667413] usbcore: deregistering interface driver uvcvideo
[ 1775.367615] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[ 1776.363820] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[ 1776.364917] input: Monitor Webcam (SP2208WFP) as /devices/pci0000:00/0000:00:1a.7/usb7/7-2/7-2.1/7-2.1:1.0/input/input9
[ 1776.385278] usbcore: registered new interface driver uvcvideo
[ 1776.385286] USB Video Class driver (SVN r209)


And I was able to use the webcam. Just keep running through that cycle until dmesg doesn't display the "Failed to query (129)"

---

### Post by nikkkko on 2008-05-27
A belated thanks for this information:
> Just keep running through that cycle until dmesg doesn't display the "Failed to query (129)"
I rmmoded and modprobed twice and hey presto, my webcam works.  Don't know why it doesn't work first time but at this point I'm not worrying about it.

Thanks again.

---

