---
title: "Video cards and grubs"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Hydrargyri on 2006-08-18
Hello! I have two more questions about Ubuntu, both of which are rather dire.

I type this message from Windows, the reason for which you'll find out soon.

I recently acquired a spanking-new (relatively budget) video card! I thought that this would both allow the computer to go faster, and all that jazz. It does for Windows, but Ubuntu is a slightly different story. Namely, I get strange lines of stranger text, a blue and black background, and a strange message saying "Ubunut cannot load xserver" or something similar. I know that the xserver is the graphics doohicky, and that I fiddled with the .conf file in an attempt to get widescreen (I put the backup file back, though!), and that's where my knowledge end. It then jumps me back to the text-style command line stuff. Something tells me that I need new drivers, but two questions arise:
1) How can I download anything from the text interface? I know that you can, don't get me wrong, but I'm inept. A few members of this board already gave me very nice links that I'm reading through, but assuming that the file is at a website, how do I "click the link", so to speak?
2) Where can I get video drivers? I've looked through the forums, and people have mentioned acquiring them (I think), but I've no luck finding anything. Is there a special site? Its an Albatron Geforce 7300, if that's important.

I'm happy to format the partition, anything to get Ubuntu working, really.

And on to the second question. I'll be more brief. When I installed Ubuntu, that grub doohicky plopped itself on my BIOS, I assume. Its what allows me to choose what operating system I want to run, I guess. The problem is this. I have a USB keyboard. I like my keyboard (ergonomic and all that). For some reason, I cannot move the selection bar in the grub with the arrow keys on my keyboard. The keys themselves work, so I don't know what's the problem. To switch operating systems I have to borrow a friend's older PS/2 interface keyboard, which works just fine. Do I need a usb/ps2 converter (I found exactly 1 type being sold online thats the needed USBF-PS/2M), another keyboard, or am I just missing something obvious?

Thank you!

---

### Post by zxee on 2006-08-18
Both your problems are xserver related. I believe what you have is a nvidia gpu. 
Just to get you logged into the graphical interface (from there you can learn how to set up your card with the propritary nvidia driver)
type this from the commandline that you're finding yourself in when you boot to ubuntu.> sudo dpkg-reconfigure xserver-xorg 

You will get a chance to select nv for your video driver and also set up your usb keyboard. For questions you don't know the answers for (in dpkg) just press enter. Hope that helps.

---

### Post by Hydrargyri on 2006-08-18
Hmm...

First, thank you for the help - it seemed to get me to the right place. However...

Well, here's what's happened. I typed in that command, and everything went well. It asked me some questions about my video card, and I think I answered them correctly (it is nvidia, btw). I said it was "nv" format card, and said it says it has 256 onboard memory. Some other stuff happened, and then it said what monitor I had. It correctly auto-detected, and then I said the preferred resolution (1440-900, the same I use on Windows), and then some more stuff happened.

Namely, keyboard stuff. It said that most keyboards are 104, while 101 are the older keyboards, so I selected that 104, and that pretty much wrapped it up.

However, a few bad things happened afterwards...
First, the keyboard still wasn't detected. Is there another number I should have put in? Its a new keyboard ([http://www.newegg.com/Product/Product.asp?Item=N82E16823109148](http://www.newegg.com/Product/Product.asp?Item=N82E16823109148), if its any use) and it simply wouldn't be detected until the ubuntu login prompt.

Now, about the login prompt. I typed in my name and password, and then, in a great surprise, the monitor flipped to a sudden "input not recognized" or some similar error message. I got that before, when I had a bad video card. But this one works.

So, I'm guessing that I put in the wrong stuff and options and... stuff. The biggest concern I have, however, is I can't seem to do anything - that is to say, how can I get back to the text-only, to truly correct the xserver settings?

Thank you!

---

### Post by zxee on 2006-08-18
Pressing these keys> Alt+Ctrl+F1 should put you into a commandline environment.
One of the snags I saw when you posted in the usb-to-ps2 keyboard thing.
Are you switching keyboards? 
Type this > cat /proc/bus/input/devices
and that should give you your keyboard and the correct label to use in your xorg.conf

---

### Post by Hydrargyri on 2006-08-18
Well, this is beginning to get a little annoying.

Edit: All this keyboard stuff is now fixed - see below for the embarassing story.

In addition, when it again prompted me for video card information, I was as precise as possible, and specified that I would rather have it use 1280X768 (or some numbers quite similar, I forget exactly) with 60hz refresh rate. Now, though the resolution is smaller than that I would prefer, it somehow does seem a bit more tolerable than the really stretched resolution before, and certaintly better than the "bad input" message before. However, the whole display seems to be offset about a centimeter - the left side of the screen is black, and the right side of the screen extends beyond the monitor. How on Earth can I fix that?

Thank you, zxee, for your help,

And a pre-emptive thanks to anyone else who will also help. (Hint). :)

Edit: Well, I feel like an idiot. At a friend's insistence, I checked my BIOS settings. Sure enough, "USB Keyboard support: Disabled"

I'm awfully sorry for wasting everyone's time. But I did learn a lot, if that's any condolence. :)

---

