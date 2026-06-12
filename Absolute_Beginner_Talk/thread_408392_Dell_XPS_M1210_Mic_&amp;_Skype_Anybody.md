---
title: "Dell XPS M1210 Mic &amp; Skype Anybody?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by HokkaidoHillbilly on 2007-04-13
My M1210 has a built in mic/webcam just above the screen that I'd really like to get working in Skype...well the mic in anycase.  Seeing as Skype for Linux doesn't even support video yet, the webcam'd just be icing on the cake. :)

Anyhoo, under System->Preferences->Sound, I can play around w/ the sound capture settings a little bit, but since the cam/mic is technically a USB connection (although built-in), I can only hear my voice when I select "USB audio" (and even then it's gotta heckuva echo).

The problem is that when I do Skype test call w/ the USB audio or any other device selected for sound capture, nothing gets recorded.  Bummer, seeing as I live in Japan and Skype is the main way I keep in touch w/ my family in the US. :(

Does anybody else have a M1210 and know how to figure this out or at least lead me in the right direction?  I've Googled the subject till my eyeballs fell out, but still haven't been able to find a very definitive answer.

Thanks! :D



HH

---

### Post by Fascination on 2007-04-13
This seems to be a recurring problem in the Dell laptop line when faced with linux, and to date Ive not heard of a resolution Im afraid. :(
Is it possible you could use an external mic? I know this is annoying considering you have one built in to the laptop, but it would be a suitable work around till a driver appears on the scene to resolve this. :)

---

### Post by HokkaidoHillbilly on 2007-04-13
Yeah, even w/ the mic plugged in, which I wouldn't mind at all if it worked, I unfortunately still get no love.

Oh well, at least rebooting into XP & using it there is still an option, eh? :roll:

---

### Post by sailor2001 on 2007-04-13
check with alsa (synaptics) to see if your setting are correct. a plug in mic may need mic2 setting

---

### Post by HokkaidoHillbilly on 2007-04-16
Even w/ the mic2 setting turned up to max and mic plugged in...nothin'.

Guess for the time being, when anybody Skypes me, I'll just log out & into XP.

That said, does anybody know if it looks like Feisty'll offer better hardware support?

---

### Post by tommi on 2007-04-16
i use feisty kubuntu. install it, install skype and it works out of the box. misterious hing: i couldnt hear something in the testcall but if i call a friend, all works.

---

### Post by medley on 2007-04-16
> **HokkaidoHillbilly said:**
> My M1210 has a built in mic/webcam just above the screen that I'd really like to get working in Skype...well the mic in anycase.  Seeing as Skype for Linux doesn't even support video yet, the webcam'd just be icing on the cake. :)

Anyhoo, under System->Preferences->Sound, I can play around w/ the sound capture settings a little bit, but since the cam/mic is technically a USB connection (although built-in), I can only hear my voice when I select "USB audio" (and even then it's gotta heckuva echo).

The problem is that when I do Skype test call w/ the USB audio or any other device selected for sound capture, nothing gets recorded.  Bummer, seeing as I live in Japan and Skype is the main way I keep in touch w/ my family in the US. :(


HH

Does anybody else have a M1210 and know how to figure this out or at least lead me in the right direction?  I've Googled the subject till my eyeballs fell out, but still haven't been able to find a very definitive answer.

I also use Ubuntu on an M1210 and have no success with the microphone. I have seen several other posts by people complaining about this. It appears there is no solution at the moment. I think it might have to do with the intelligent switching of configuration that the chipset does around the headphone/mic jacks.

My machine is configured to dual-boot to XP, and if I want to use Skype, I go to Windows.

Sorry.

---

### Post by Krag on 2007-06-20
Don't know if this helpful to anyone anymore, but in Skype you need to switch the Audio In device (under Sound Devices in Tools ->Options) to USB. I don't know why it shows up as a USB device, but I'm able to make a skype test call using the built in mic with this option.

HTH.

---

### Post by bjtaylor01 on 2008-05-10
JUST FYI.

I am using 64 bit hardy, I googled "skype 64 bit hardy" and found a great forum how to with copy and paste installation commands. Worked great, so I know have Skype working with the built in webcam (Using skype 2.0) but no sound.

Went into options/sound devices and changed "Sound in" from Default device to USB Device 0x46d:0x8c6. Then when I did my test call everything worked great. 

*To use skype I have to make sure you am not using any other sound program or I get an error. 

I would like to know if there is a way to port my CHEESE video effects into skype output, so the other person can see an effect. 

So EVERYTHING works now with my M1210 xps dell. It is just a matter of taking the time on google (Ubuntu forums) to work things out.

---

