---
title: "Widescreen??"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Jarnz on 2006-08-27
Is this posible? I need to run Linux at 1366x768 widescreen on my 37" LCD. As I'm new to this, I dont know what is needed. I've install the nvidia drivers from the repository, and I've added the res I want to the xorg.conf (I think) file. But I'm not being given the option to go any higher than 1024x768.Any ideas?

---

### Post by Jarnz on 2006-08-28
any one?? I managed to get the res to 1280x960, I also put in the res I wanted 1366-768 into xorg.conf, but X rejected it

---

### Post by Skia_42 on 2006-08-28
37 inch LCD? That thing must be a beast. Are you sure you are editing the xorg.conf file as superuser? you should be using this command:
> sudo gedit /etc/X11/xorg.conf
Or editing with some other text editor of your choosing other than gedit. if that is not working are you getting any error messages?

---

### Post by Jarnz on 2006-08-28
I dont know if this is an issue, but I install ubuntu on a 4:3 CRT monitor, because the 37" LCD cant handle text based screens, only GUIs. and now that I've changed over to the LCD, Xorg is still saying that its the CRT attached in the logs (Xorg.0.log).

Everytime I look in the logs, it says something like: 1366x768 is not a supported modline, removing.

I dont know if its because X cant handle it, or its limitted to the info it knows about the CRT I had running since it wont get rid of the CRT and thinks its still there.

But yeah, I used that command to edit the xorg.conf file as sudo.

The LCD is a bit of a beast, but it looks crap with the 4:3 low res images. I can hardly navigate around its so distorted, hence the need for help.

---

### Post by Skia_42 on 2006-08-28
Okay, wanted to make sure you weren't just editing the file in nano and trying to save it without root access. I suppose if you removed the script that checks the xorg.conf file it would not remove your resolution change but I do not think that is a very smart thing to do, you could break your system and I have no idea where that script would be stored.

---

### Post by Jarnz on 2006-08-28
Is there anyone that has done this before? Everywhere I've looked its all people asking if it can be done, and no answers

---

### Post by daou on 2006-08-28
Do the NVIDIA drivers support widescreen well? Is there an NVIDIA equivalent to the 915resolution drivers for Intel chipsets?

---

### Post by Jarnz on 2006-08-28
Which has the better drivers, nVidia or ATi?? if the answer is ATi and there is widescreen support, I'm re-installing.

I found a command that reconfigures X and gives you the list of resolutions and 1366x768 isnt there, and there is nothing close

---

### Post by daou on 2006-08-28
>  Which has the better drivers, nVidia or ATi?

So far NVIDIA. That could all change, but at the moment NVIDIA has better drivers.

---

### Post by gn2 on 2006-08-28
You don't mention what graphics hardware you're using?

Has the hardware you're using previously given the desired resolution with a different operating system installed?

---

### Post by Jarnz on 2006-08-28
This PC before had an ATi X800pro 256MB running Windows Media Center Ed. I had enough of Windows and did some reaserching on a Linux version. I also noticed that nVidia drivers were better. So I bought a nVidia 6600GT 126MB card and wacked it in. since my old GF 5200 could handle a res of 1366x768, I would think that the 6600GT would as well.

---

### Post by gn2 on 2006-08-28
What model is your screen?
What type of cable are you using to connect with?

[http://forums.guru3d.com/showthread.php?p=1904552](http://forums.guru3d.com/showthread.php?p=1904552)

What is the exact model of graphics card?

[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=143&p_created=1100037537&p_sid=GCEbwbgi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTImcF9jYXRzPTU5JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU5OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD0xMzY2eDc2OA**&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=143&p_created=1100037537&p_sid=GCEbwbgi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTImcF9jYXRzPTU5JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU5OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD0xMzY2eDc2OA**&p_li=&p_topview=1)

Have you tried 1360x768?

---

### Post by Jarnz on 2006-08-28
I'm using a Toshiba 37WL58 37" LCD connected via VGA cable. I've tried 1360x768 and it had the same effect. Exact model of video card, all I know its a 6600GT 128MB APG

---

### Post by Anarchy99 on 2006-08-28
I am running unbuntu at 1440x900 on an Nvidia GeForce FX Go 5200.  It took me a long time to get this resoltion, you have to modify your xorg.conf file.

Near the end of xorg.conf there are two sections, Section "Monitor" and Section "Screen".  In Monitor, you have to change the resolution, horizSync, vertRefresh, and Modeline to the proper resolution, sync range, etc. that you want.  It may take some expirementation.

In the Screen section, you have to change the Modes to the resolution you want (you can also change the color depth).  Here is what those sections on my xorg.conf look like:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-64
	VertRefresh	50-100
	Modeline "1440x900" 97.54 1440 1472 1840 1872 900 919 927 946

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection





Hope this helps

---

### Post by gn2 on 2006-08-28
Refer to page 29 of your TV manual, when connecting via VGA it will only accept maximum of 1024x768 and stretch it to fit.

Worse, read page 52.

[http://www.castel.com.au/toshiba/manual/37WL58.pdf](http://www.castel.com.au/toshiba/manual/37WL58.pdf)

All is not lost, you may be able to get the full resolution using the TV-out on the graphics card and fool the TV into thinking it isn't connected to a PC.

---

### Post by gn2 on 2006-08-28
Error in previous post, for page 29, should have been page 49

---

### Post by Jarnz on 2006-08-28
I can swear on my life that I was running windows mce at 1366x768 on the VGA cable. I dont use the HDMI input, it sucks

---

### Post by gn2 on 2006-08-28
If it worked in Windows hopefully it should work in Linux.

Explanatory page about LCD tv's: 

[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=143&p_created=1100037537&p_sid=GCEbwbgi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTImcF9jYXRzPTU5JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU5OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD0xMzY2eDc2OA**&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=143&p_created=1100037537&p_sid=GCEbwbgi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTImcF9jYXRzPTU5JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU5OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD0xMzY2eDc2OA**&p_li=&p_topview=1)


Suggest looking at this: [http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html)

Driver here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Once you have confirmed you have the latest driver and it's working try reconfiguring the Xserver again, try 1360x768

If you still can't get it running, here's how to make it work with TV-out: [http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-h.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-h.html)

Hope that gets you sorted.

---

### Post by gn2 on 2006-08-28
As a "canny" scot, a people known for being careful with their cash, why abandon MCE if you've already paid for it?

I keep XP on my PC for the wife to use (she refuses to learn new software)and dual-boot.

When XP support gets turned off however, it's Linux all the way, no more money to Bill...

---

### Post by Jarnz on 2006-08-28
I didnt pay for MCE, I got it free with the PC.

Well, thanks everyone for your help. I just cant get it to work. I reinstall Ubuntu with my ATI X800 card, istalled the driver (to my supprise was a gui install), and it worked straight away, well, close: 1360x768. The ATI config program let me add any resolution I wanted and it put the closest into the xorg.conf file

---

### Post by gn2 on 2006-08-28
If the MCE came with a ready built PC then you've paid for it as part of the package... 

Glad you got it sorted, that's the first time I've known of ATI being more user friendly than Nvidia.

---

### Post by jdong on 2006-08-28
> **daou said:**
> Do the NVIDIA drivers support widescreen well? Is there an NVIDIA equivalent to the 915resolution drivers for Intel chipsets?

915resolution is an Intel related hack. It's to address a bug in the video BIOS of many Intel chipsets that they do not list all the resolutions they support.

NVIDIA cards are not affected by this bug.

---

