---
title: "Strange 8800GTS performance.."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-06-21
Hi,

I have installed my 8800GTS drivers with Envy, and all seemed fine. But after loading up a few of my favourite games (Sauerbraten and AssaultCube) I have found inconsistent performance.

For one, Sauerbraten runs at 120FPS with AntiAliasing on etc on one of the most taxing maps. The same settings and map in Windows and I get 30FPS, thats all good. But in Windows on some maps I can break 400FPS, in Ubuntu it never breaks 172 (exactly 172) and tends to fly around to 150 and back up. This causes tearing (I am used to 200 FPS flat on Windows) and this makes it hard to aim.

The same happens in AssaultCube, which can drop to less than 100 FPS in online matches, whereas on Windows I'd be hard pressed to find it drop below 300FPS.

Is it shoddy support for the 8800GTS with Nvidia Linux drivers at the moment? Also, my Nvidia CP forgets all my Antialiasing etc settings on reboot..

Please help, thanks :)

---

### Post by insane_alien on 2007-06-21
seeing as the human eye has trouble detecting more than 50 FPS and the screen itself will be rendering at 75Hz(thats the usual for LCD's yeah?) i don't think framerates above this will matter too much. i certainly can't tell the difference between 60FPS and 300FPS even on the most fast paced shooters/flight sims/whatever

---

### Post by Happy_Man on 2007-06-21
You have to choose "save to xorg.conf" for them to hold between boots.... and perhaps it is shoddy support. I know I have the same issues on my (very old) card, it doesn't perform as well.... even without Beryl.

---

### Post by uncleted on 2007-06-21
The tearing is caused by your vsync being switched off.

vsync forces the graphics card to write data according to the speed the monitor is synced at.  Obviously you will probably get somewhere between 60-85 FPS because of this in most cases, but you don't actually need any more than 60 anyway.

If you're using an LCD there's no reason to go above 60Hz, as most can't really refresh that fast, and they don't flicker anyway.

---

### Post by Pas_sa on 2007-06-21
> **uncleted said:**
> The tearing is caused by your vsync being switched off.

vsync forces the graphics card to write data according to the speed the monitor is synced at.  Obviously you will probably get somewhere between 60-85 FPS because of this in most cases, but you don't actually need any more than 60 anyway.

If you're using an LCD there's no reason to go above 60Hz, as most can't really refresh that fast, and they don't flicker anyway.

*sigh*

Please re-read my post. I said that the FPS hits a max of 172FPS, but flirts down to 150, even in Sauerbraten on a newmap (blank empty map). Same issue with AssaultCube, or any 3D game really...

Also, please people don't tell me this 'human eye cant detect more than 30fps' crap.. anything below 60 is unplayable for me, thats my personal preference, please don't tell me what FPS I should live with (especially considering this is an 8800GTS, it shouldn't run like this, end of story).

Happy_Man, there is no 'save to xorg.conf' button in the CP.

---

### Post by uncleted on 2007-06-21
I know what your post said.  I'm simply responding to your complaint about tearing.

Your monitor won't sync to 172Hz or whatever FPS you're getting.  Any FPS over what your monitor's actually synced to is wasted because it can't be fully drawn.

Your monitor IF it's a CRT may do 85Hz, even up to 100Hz or a little bit more.  If it's an LCD, in spite of advertised 2ms gray to gray or whatever they're saying now, realistically anything over 60Hz will be lost.

The [tearing IS because of vsync being off]("http://www.tweakguides.com/Graphics_9.html").  What happens is your monitor syncs at 60Hz for example.  That's 60FPS being displayed maximum.  If your card is trying to draw to the screen at 170FPS, what's going to happen is that your image will change nearly 3 times while your monitor is drawing one frame.

Since your FPS never dips below 60FPS there should really be no side effect from you turning vsync on, aside from losing the tearing, and your ability to brag about how high your FPS is.

---

### Post by psyopper on 2007-06-21
I'm with uncleted on this one. A few question should be asked here:

What version of the nVidia drivers are you using? 
How did you install those drivers?
What type of monitor you do have? Make, model and resolution please.

If I were to complain of a car that only turned left no matter how hard I tried to turn it right, turning right was extremely difficult and asked you how to fix it, wouldn't you want to know that it was a NASCAR car and barely ever turns right to begin with? And if I didn't know that about NASCAR cars wouldn't it be reasonable to expect to hear from someone who does know about NASCAR to explain to me that I am wasting my time trying to make my car turn right and that I should be happy that it turns left wonderfully at 200 mph?

---

### Post by Pas_sa on 2007-06-22
> **psyopper said:**
> What version of the nVidia drivers are you using? 
How did you install those drivers?
What type of monitor you do have? Make, model and resolution please.
100.14.09 drivers

Installed via Envy scripts

I have a BenQ 17" FP71E+ and its native res is 1280x1024. Thats what I run games at.



Look guys, I don't want you to tell me to live with 172FPS. Thats not what I'm asking. I want to know why my FPS flatlines at 172, no matter how simple the graphics are, and why it fluctuates down to 150 and then back up, just randomly. And for the record, I cannot play nearly as well with a fluctuating FPS than with 200 flat. I also can't stand playing at 60 fps, and even if I wanted to, there is no option to turn Vsync on in the Nvidia CP. And as I said, it does not save my settings!

---

### Post by Pas_sa on 2007-06-22
Bump, help required, this is driving me nuts heh :)

---

### Post by psyopper on 2007-06-23
A couple of problems here...

1. You are using beta drivers. The 97xx series are the latest supported drivers by Ubuntu, even nVidia admits the 11 series drivers are beta.

2. Your installation method - Envy. Envy is not a supported method of installation by either nVidia or Ubuntu. Even if you had installed the supported drivers, doing so through Envy makes them unsupported. The only Ubuntu supported method is using the nvidia-glx-new with nvidia-kernel-common packages in Synaptic.

3. You are running a bleeding edge video card on a bleeding edge machine. The bleeding edge bleeds because sometimes that edge is a little sharp.

Ok, I got the not-so-nice out of my system, lets try some solution ideas. I DO know that the 11 series drivers are the only ones that support your video card; I actually pay attention to these kinds of things (even if I only run a crappy 6200), I really do recognize that if you want your video card to work you need to use those drivers. 

I would recommend starting with using Envy to uninstall the drivers that it installed. Then download and install the nVidia drivers from their website following their directions to the letter. You will need to do one more thing... edit /etc/default/linux-restricted-modules-common and change the line in there to read DISABLED_MODULES="nv" 

If you are still having problems with the beta nVidia drivers, I would suggest filing a bug report with them on their web site. They may actually be happy to know that you are having a problem so that they can potentially resolve it in the next driver release. Many developers assume that where one person is having an issue there are sure to be others with it as well.

By the way, [nVidia is now up to 100.14.11]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html"), looks like there may have already been a few updates to potentially resolve your issue. I would start with these drivers first. If they don't work start working backwards, maybe even past .09 to see if the potentially broke something along the way.

---

