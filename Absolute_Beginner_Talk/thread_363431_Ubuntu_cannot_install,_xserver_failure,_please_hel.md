---
title: "Ubuntu cannot install, xserver failure, please help"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by GedDarkstorm on 2007-02-16
I'm frustrated to no end right now. Ubuntu 6.10 will not install under its liveCD as it runs into this horribly annoying xserver error where the xserver fails to load, it cannot find a display? Telling me this, of course, through my display. 

It seems, from when I looked at the error message, that Ubuntu cannot load drivers to run with the Geforce 8800 graphics card, or something. That's the only guess I have as everything else loads up till that point (where it lists a huge thing of nvidia products, all excluding the newest 8000 series).

How do I get around this and get ubuntu installed? I tried alt-control-F1 to get into the command prompt, and I can't get it to work whatsoever to try some "fixes" I found while ripping through the boards here to try to find a solution.

Arg, this has me so agrivated.. if I can't interface with the machine... and all I need to do is get ubuntu to install and then I can download the latest nvidia graphics card drives. Please, does anyone have any instructions on how to fix this issue?

---

### Post by fjf314 on 2007-02-16
Have you tried installing in Safe Graphics mode?  I had the same problem with the X configuration when I tried to install 6.06, but I was able to install it in Safe Graphics mode (which you pick from the menu when you boot to the live CD.)  Once you get the system installed, then you can look into playing with your X file to get your video card working.

---

### Post by GedDarkstorm on 2007-02-16
Yes, safe graphics mode changes nothing, same error and no difference whatsoever. 

I just want to get it installed so I can go on to fix everything manually, but if I can't get passed this stupid xserver thing, I can't get it installed : (

---

### Post by Duffasaurus on 2007-02-16
Holy hell...There's no way an 8800 is getting used to its full potential in Ubuntu. I'm sorry but this is when I must say get Vista. It is a sight to behold, Vista on a DX10 card. I have yet to see any Linux theme rival the Vista directx10 desktop. It's breathtaking...Other than that people should just get Ubuntu though.

---

### Post by GedDarkstorm on 2007-02-16
*raises a brow* Vista has more problems than a drunkin russian in Afganistan, as it is now anyways. That and I have no want of vista. But that isn't the issue. The issue is I can't even get Ubuntu installed. 

Besides, the WINE emulator allows DirectX to work on Ubuntu, so I'm sure it can eek out alot of the 8800's power. Then there's Beryl. But I really don't want anything fancy, just something not so full of broken and security issues like Windows (which gets progressively slower the longer you use it, which is why I have grown distasteful of it).

---

### Post by fjf314 on 2007-02-16
You can always try to go through the X configuration once you get to the command prompt after the error.  At the command prompt type:

```
sudo dpkg-reconfigure xserver-xorg
```

When in doubt, use the defaults.  There might be a better way, though, so you might want to wait until someone who isn't a newbie with Ubuntu reads the thread.

---

### Post by Duffasaurus on 2007-02-16
> **GedDarkstorm said:**
> *raises a brow* Vista has more problems than a drunkin russian in Afganistan, as it is now anyways. That and I have no want of vista. But that isn't the issue. The issue is I can't even get Ubuntu installed. 

Besides, the WINE emulator allows DirectX to work on Ubuntu, so I'm sure it can eek out alot of the 8800's power. Then there's Beryl. But I really don't want anything fancy, just something not so full of broken and security issues like Windows (which gets progressively slower the longer you use it, which is why I have grown distasteful of it).

Yeah, I suppose your right...But Beryl just doesn't have glossy, 3-dimensional workspaces...And glossy windows on an already glossy screen is tRiPpy...It's like you could reach into the screen.

---

### Post by GedDarkstorm on 2007-02-16
Thank you fjf314, for trying to help me :).

I've run into that code and others on the board, however... How do I input that code correctly? Yes, I hit alt-ctrl-F1, after the error, to get into command prompt. Then I type in the code exactly as shown, hit enter and... Nothing. It just goes down to the next line. How the heck do I get it to accept commands? What am I doing wrong :/ (or what more must I do after the alt-ctrl-F1 thing to let me start inputing commands. The first place I can input at is at this ubuntu@ubuntu>!@` , or something, thing.

---

### Post by GedDarkstorm on 2007-02-16
Lol at Duffasaurus. True true.

Yeah, I've seen Vista in action, not on a 8800, but nevertheless. Still, I also don't have 300 bucks to shelve out for the thing : P. I'm sure it may look pretty though.. but something that works is more important than pretty at the moment if that makes sense hehe.

---

### Post by fjf314 on 2007-02-16
I believe that the directory listed at the command prompt before you install is "ubuntu@ubuntu-desktop:~$" or something similar.  If the commands you enter aren't working when your cursor is next to that, then I'm not sure what's wrong.

---

### Post by GedDarkstorm on 2007-02-16
> **fjf314 said:**
> I believe that the directory listed at the command prompt before you install is "ubuntu@ubuntu-desktop:~$"  If the commands you enter aren't working when your cursor is next to that, then I'm not sure what's wrong.

Hm, it was missing the -desktop part of it, but the rest is the same.

Well.. I don't know what was wrong either. I started just hitting buttons and found that if I hit the up arrow key I'd get a list of everything I'd tried to input later. Fiddling with that, I brought my cursor under the command string you told me to input earlier, hit enter, and voila, it worked.

At list point, all I can say is... my head hurts.. but, it seems it's going somewhere? I hope it wasn't just a lucky fluke, but.. I'm still going through the xserver config prompts so let's hope this works! Thank you kindly.

Edit: Urg, I spoke too soon. Once I have to reboot to get into the liveCD install system again, all the configurations I made are lost and the error returns... What's the command for installing from the command prompt, as that's what I really need.

---

### Post by GedDarkstorm on 2007-02-17
bump

---

### Post by arthur_kalm on 2007-02-20
GedDarkstorm, you might want to give the Alternative CD a try. I also have an 8800 (GTS that is) and I'm having the same problems. I'm going to try Feisty out though and I'll post back, but give the alternative CD a try since it doesn't use X.

---

### Post by kiaran on 2007-02-22
I am in the same boat. I have an 8800 GTS and Ubuntu throws the X-server failed error "could not find screen".

I am downloading fiesty-fawn at the moment because some people have recommended that. Has anybody with an 8800 had any luck?

---

### Post by kielcary on 2007-03-05
Hey there guys - I've also been in the same boat for the last few days, and here's what I had to do...

I had a Nvidia 7900 on hand, so I was able to install with this card in.  I'm going to assume there's an easier way to do it from the command line, but I tried everything I could and it just wouldn't work.  So, my recommendation right now is to use another supported card, whether it is yours or you borrow it for someone else.  If you can't find a supported card, download, install, and run Envy from the command line (I'm not sure exactly how to go about this as I am a complete and utter newb).

However, I DID get 6.10 running on an 8800 with the following steps:
To start, I installed 6.10 using the alternate CD (which allows a non-graphical install) with the supported card in.  I didn't try the graphical installation with the supported card, but it would work I would imagine.  

After installation, I ran Alberto Milone's Envy scrip from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).  It was recently updated and the updated version didn't work for me.  I downloaded the 0.8.2 version.

If the GUI version doesn't work for you (0.9.0) download this version (0.8.2), install it by double-clicking it, and then hit ctrl-alt-F1 to go to your terminal outside of GNOME.  Log in, then type "envy" (no quotes).  Select the first option.  Even if you are given an error stating that your card is not supported, continue on.

After the script has finished and the new driver is installed, restart your xserver (the script will give you the option) to verify your installation.

Shut down your computer, put your 8800 in, and turn it back on.  After the Ubuntu load screen, you should an NVIDIA splash screen, then  you should be able to log in!

YAY!  Right?

Wrong, sadly.

Now  you need to update Ubuntu.  There are roughly 10 xserver updates, important and recommended together, and when you update via the auto-updater one of these breaks the work you've just done.  

When I restarted my computer, I made it to the Ubuntu boot screen.  After that, a curser begins to flash in the top left hand corner and keeps flashing.  The command line flashes at you a couple of times as xserver tries to start, and then you get the xserver's version of the blue screen of death.

Skip through this, it will take you back to the command line.  Log in.  Run envy again from the command line by logging in and typing "envy" (again no quotes please, heh)... and now it works :)

Hope this has helped someone... I almost gave up on Linux trying to get my 8800 working (I recently decided I hate MS enough to make the switch despite my software's dependency on that damn OS).


Things I haven't tried:
1.)  Update using the supported card and then install and run Envy.
2.)  Install using the text installer with the 8800 in, then download, install, and run Envy from the command line.

---

### Post by agent42 on 2007-03-08
i also have the same prob, and a bit unlucky is while booting for installation, ubuntu seems like trying to find and configure my graphic and this made my DVI slot on my LCD malfunction. Now i forced to use the VGA slot. I have check with different graphic cards but still the same and i have try everything possible on my LCD. 
BUT I STILL LIKE UBUNTU!!!!!!!!!

---

