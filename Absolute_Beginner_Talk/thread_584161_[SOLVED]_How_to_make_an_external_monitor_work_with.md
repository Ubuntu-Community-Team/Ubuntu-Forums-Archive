---
title: "[SOLVED] How to make an external monitor work with laptop?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-10-20
I am running Feisty on my Gateway laptop (year 1999) and everything works really well, but I want to hook up an external monitor (Dell Ultrascan P780) and have both screens work simultaneously. Right now when I hook up the external monitor and then boot up Feisty, the external monitor just remains blank. 

I read around a bit, and people are mentioning "Xorg", "Xorg.conf", and just "X" in this connection. I do not know if that is something I need to install, or something which is already in Feisty but which needs to be configured?

I have a dual boot with Win98, and when I boot into Win98 both monitors work fine. But when I boot into Feisty, only the laptop monitor works and the external monitor is blank. How can I set up both to work? Thanks!

---

### Post by ofb on 2007-10-20
> **swarup said:**
>  "Xorg", "Xorg.conf", and just "X" 

They are talking about X Windows, which is your base GUI system.
[http://en.wikipedia.org/wiki/X_windows](http://en.wikipedia.org/wiki/X_windows)

The file /etc/X11/xorg.conf is the configuration file. As stated inside, "Edit this file with caution." Make sure you understand what you're doing first, and make a backup of the original before you make any modifications.

I haven't used an external laptop monitor with Ubuntu, so I'm not going to advise you on that. Possibly there is something specific (and simple) that must be done for your laptop. It may help to mention the model name here, and use that in the searches you do.

---

### Post by candtalan on 2007-10-20
I have used a laptop with (an external) lcd projector, and I also found that I could only see one display at a time, as you describe. 
I note that the latest version 7.10 is said to be better at handling dual displays, although I have not yet tried it. It might be easy to try it for yourself by using a live CD of 7.10.

btw be careful with any editing of xorg.conf because if you get to a situation where you cannot see any GUI but only a text command line, it can be a big problem unless you are comfortable with the rescue mode - easy with some experience, but very confusing if you are inexperienced with it.

good luck

---

### Post by swarup on 2007-10-21
Thanks to both of you for the helpful hints. I went to that file xorg.conf and looked in it just now-- yes, I remember now it is familiar to me. I added one section in there months ago in order to get my touchpad recognized as a touchpad and not a mouse. 

That does look like the file where one might put a section to enable the computer to recognize a second monitor. Now I just have to find out how those lines are supposed to read. Here below are the code lines for the monitor and screen in my laptop. My guess is that another such set of code will be needed for the external monitor and its screen. If anyone has info on this, please let me know.


```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by ofb on 2007-10-21
> **swarup said:**
>  My guess is that another such set of code will be needed for the external monitor and its screen.

Perhaps, but not necessarily. For example I use two monitors with my desktop, but only one is mentioned in xorg.conf. In this case the dual display is handled by the proprietary Nvidia driver.

With your laptop there may be an option in BIOS to turn on, or simply a combination key to hit. I have vague memories of something like the latter for my old Thinkpad. As I say, have a look around to see if there is information specific to your laptop.

---

### Post by ofb on 2007-10-21
Hmmm. Have a look at this,
[http://www.linux-laptop.net/hosted/gateway-9300-slackware.html](http://www.linux-laptop.net/hosted/gateway-9300-slackware.html)

If that matches your model, then try the key combo to see if that works first.

If you wish to try modifying your xorg.conf to add that section for the external monitor I should caution that Slackware is not Ubuntu - do you know how to use a LiveCD to change your xorg.conf back to original configuration if the experiment fails?

---

### Post by swarup on 2007-10-21
> **ofb said:**
> Hmmm. Have a look at this,
[http://www.linux-laptop.net/hosted/gateway-9300-slackware.html](http://www.linux-laptop.net/hosted/gateway-9300-slackware.html)

If that matches your model, then try the key combo to see if that works first.

If you wish to try modifying your xorg.conf to add that section for the external monitor I should caution that Slackware is not Ubuntu - do you know how to use a LiveCD to change your xorg.conf back to original configuration if the experiment fails?

Hey, you did a great job. How did you find this? Actually, this site you found is discussing the very model I have: a Gateway 9300 laptop. Now, it is true as you say-- I am using Ubuntu not Slackware. So their suggestion (see below) to add the 2nd monitor into xorg.conf although it worked with his slackware, it may or may not work with Ubuntu. But as you mention above, I do not know how to use LiveCD to change my xorg.conf back to original configuration if the experiment fails. I'll try the key combo first as you suggest to see if it works--but as I recall I tried it some months ago and it didn't work. Presuming that doesn't do it, then what do you suggest-- should I try doing the below add-on for my xorg.conf?


> Setting up additional features for Slackware

    * Using External Monitor and/or TV: For external monitor support, add to /etc/X11/xorg.conf the crt_display option as follows:

```
      Section "Device"
          Identifier  "ATI Rage"
          Driver      "ati"
          BusID       "PCI:1:0:0"
          Option      "crt_display" "On"
          Option      "accel"
      EndSection
```

      You can then do Fn-F3 to toggle between LCD, External, LCD & External. TV Out (aka Theatre Out): also use Fn-F3 and it works.

---

### Post by ofb on 2007-10-21
> **swarup said:**
> How did you find this?

I did a bit of a google using your "ATI Technologies Inc Rage Mobility P/M AGP 2x" as a starting point. Probably added 'Gateway' and 'Ubuntu' to start, then settled on 'Linux'.

Okay, the business about LiveCD -- if you change your xorg.conf and things go badly wrong you can have trouble like not being able to see anything on boot. So you'd reboot with the LiveCD, then go into your /etc/X11 and change the xorg.conf back to the original form.

If you're not familiar with editing configuration files at all, then we should cover some basics.

Right now, your /etc/X11/xorg.conf is owned by root, so it you try to open xorg.conf with an editor like Gedit, you'd be able to read the file but not change it.

To change it you'd need to be root, so you'd fire up a terminal and enter 'sudo gedit /etc/X11/xorg.conf', then your password at the prompt. Now you can edit that file.

Remember I said you should make a backup first? So before that, do something like 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confBAK'

That'll make a copy called xorg.confBAK.

Then if the experiment is a disaster, you could go in via the LiveCD and just delete xorg.conf, then rename xorg.confBAK to xorg.conf. And you wouldn't need to be root during that because you're running from the LiveCD.

IMPORTANT DISCLAIMER: advice from some random guy on the net is just advice from some random guy on the net. Make sure things make sense to you before you do it, and realize that whatever happens is your own responsibility. Also, I'm just waking up with my first coffee here.

So, yeah, with all that out of the way, I think I'd try adding those lines next and see what happens.

If you're very new to all this, why not do a bit of a dry run first? Like fire up the LiveCD and go into /etc/X11 with nautilus and make a backup copy of xorg.conf with the usual GUI method.

How's that? Any questions?

EDIT: I should probably add that changes to xorg.conf don't do anything until you reboot.

---

### Post by swarup on 2007-10-21
You know, your explanation is really clear and helpful, and I learned a lot from it.

But I feel like a fool. I just tried hooking up the monitor and rebooted with it, and found that it works perfectly with the key combo Fn+F3. 

So I guess I won't be needing to edit that xorg.conf file-- but even then it was a very good lesson about how to manage that file and I appreciate your helpful explanations. And also, it was your suggestion that I retry the key combo. So altogether, you've really been a big help. I feel badly I made you go through all that xorg.conf explanation-- although as I say I learned a lot from it. I'd say the thread is solved!

---

### Post by ofb on 2007-10-21
> **swarup said:**
>  I just tried hooking up the monitor and rebooted with it, and found that it works perfectly with the key combo Fn+F3. 

Yay team!  -- Yeah, that's the thing I'm finding with Ubuntu. An awful lot just works, and more works as time progresses. It's worth pausing before digging into the traditional CLI and looking for a simple method the developers have already put in place.

"Ubuntu - it's not your grandfather's Linux"

---

