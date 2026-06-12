---
title: "auto logout problem"
date: 2012-01-05
forum: Any Other OS
---

### Post by HappyLinux on 2012-01-05
this may seem like a strange problem, but it's an annoying one though.

I'm currently running Mint 12 64bit. For some reason, whilst I'm working it logs out into the login screen. Whenever it logs out, I lose the work that I was working on.

As part of my work, I write a lot. I've ended up losing chunks of work. This forces me to hit save very frequently. I closed down an email only for it to logout. Browsing files on a USB HDD. Doesn't really matter. It just logs out.

I can log back in, but I've got to reload programs or files or whatever it was that I was doing.

I had this exact same problem with Xubuntu and Kubuntu 11.10 before I moved to Mint.

Can anyone help??

---

### Post by jjex22 on 2012-01-05
My intial gut feeling here is a display issue - quite possibly relating to your hard ware, do you use any proprietry display drivers? This was quite a common problem for 11.04, but I've not seen it for a while. 

One thing that does occur to me is that Xubuntu 11.10, Kubuntu 11.10 and Linux Mint 12 are basically the same operating system under the hood - Ubuntu 11.10. But atleast you've ruled out it being a Gnome/Unity Issue, and as you say it doen't seem to be conflicting programs as the circumstances are always different.

I'd say the two main things to try would be to change your display driver or try upgrading your kernel to 3.2.x? you could also fall back to Mint 11

---

### Post by bluexrider on 2012-01-05
It does sound like a hardware issue. Are the fans working properly?

---

### Post by HappyLinux on 2012-01-06
I have attached a couple of images of my graphics driver. It's the one installed by Mint 12 when I did a fresh install. It was the one used when I clicked on the activate driver option.

The recent version provided by NVidia is version 290.

Also, as you can see, the temperature gauge shows that the fan is working. To get the graphics cards temperature gauge up into the yellow at the highest, I log into windows (I'm on a dual-boot system with Win7) and play a game.

I don't really play recent games that require a modern day graphics card, but rather games that are a few years old and thus modern cards can easily handle without breaking much of a sweat at high graphics settings.

In addition, if I go into Mint's update manager and tick the settings to view unsafe and dangerous updates (the only way to view kernel updates) the most recent version to update to is version 3.0.0.14.16. My current version is 3.0.0.12.14.

Looking at the kernel.org website, I do see that the most recent version is 3.2. however, I've never done a manual install of a kernel update before.

So, any suggestions from the info I've provided?

---

### Post by bluexrider on 2012-01-06
The reason I agree that the problem is a hardware issue is because of what you stated. This problem occurred using different distros. I would examine the memory, run memtest. Boot from a live CD and start the test from there.
If the system passes then I would move on to the physical portion of the PC. Open the box and methodically remove each PCI card and reset it. Then the memory sticks and finally the connections to the motherboard and drives. 
Remove and inspect.

---

### Post by HappyLinux on 2012-01-06
Are you guessing some dust is affecting a connection somewhere?? Or something else?

I thought if there's a faulty piece of hardware, it just wouldn't work, or cause major problems? Problems far more extreme than this logout annoyance??

If though I will still open up the machine and do a spring clean so to speak, I just don't see it actually being a hardware fault, but rather a software problem.

---

### Post by bluexrider on 2012-01-06
I doubt its a software issue with what you originally stated. Unless noted that the issue occurs at the same moment using the same program each and every time.

It may be a loose connection or a piece not seated properly.

Infrequent issues are harder to diagnose. Begin with the obvious, move to the obscure.

---

### Post by HappyLinux on 2012-01-07
OK, I ran the memtest and there was no problems found.

I also opened up my machine and did a spring clean and checked all the connections. I don't know if this has solved the problem or not.

---

### Post by TheKojuEffect on 2012-01-07
I have the same problem with ubuntu 11.10 x64.
I am using HP pavilion g6-1037tx

---

### Post by HappyLinux on 2012-01-08
As far as I can tell, this problem only seems to happen with Ubuntu 11.10 64bit and it's alternatives. The problem doesn't happen with 11.04 64bit. So in my case, Mint 11 doesn't have this problem, but Mint 12 does. Kubuntu and Xubuntu 11.10 does, but not Ubuntu, Kubuntu and Xubuntu 11.04.

This is why I think it's a software problem somewhere within 11.10.

---

### Post by jjex22 on 2012-01-08
> **HappyLinux said:**
> As far as I can tell, this problem only seems to happen with Ubuntu 11.10 64bit and it's alternatives. The problem doesn't happen with 11.04 64bit. So in my case, Mint 11 doesn't have this problem, but Mint 12 does. Kubuntu and Xubuntu 11.10 does, but not Ubuntu, Kubuntu and Xubuntu 11.04.

This is why I think it's a software problem somewhere within 11.10.

Hi HappyLinux, Sorry, I mistakenly thought the problem had been resolved - glad to hear mint 11 is working for you , I found it more stable, myself. The good news is that if you're no longer having the problem it's definitely not your hard ware (Woo!) and as I'm guessing mint 11 uses the same driver as mint 12 by default for your graphics. As I said in my earlier post, the xubuntu, kubuntu and mint were all the same underneath, and as it's working for you in 11, you may just want to hold out until 12.04 in april.

However if you did want to learn the basics of compiling a kernel have a look [here]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/"). It only shows you how to compile a kernel with the same configuration as the one you have - but it's a good place to start? At the end of the day if you make a bodge of it, you just boot with the old kernel and delete it :)

---

### Post by HappyLinux on 2012-01-08
I apologize for the slight misunderstanding. I didn't say which Linux I'm currently using. I'm currently using Mint 12. I was using Mint 11 before. Before that, it was the various Ubuntu derivatives that I was experimenting with to find out which would work for me. When Ubuntu abandoned Gnome, I tried searching for a suitable alternative. Couldn't find one till I tried Mint 11.

After moving to Mint 11, I was more happy than I was with any of the Ubuntus. Even Mint 12 with this auto logout problem, I find Mint far better.

I don't want to move back to Mint 11 unless I really really need to. This logout problem isn't severe enough to force me to do that.

Also, I don't want to be messing about installing a kernel update in case it causes for problems than it fixes. I can be a patient person.

---

### Post by lgomez on 2012-01-14
I experienced the same problems on my laptop. I have a MacBook Pro 4.1 (around 2007 then) and on Ubuntu 10.04 x32, Ubuntu 10.10 x32 and Linux Mint 12 x64, it sometimes logout with no apparent reason while doing nothing special (writing a doc, reading an article on the web, ...).
I can't find any relevant informations in the logs on the time it happens, just the normal logout stuff (unloading this, stopping that service...).
But it seems that I don't have the problem while using MacOS (mostly for Steam games and sometimes for watching movies with low battery. Apple seems to have a more efficient power management system on their own laptops...). It may be because I use much more often Linux systems than MacOS and therefore I can remark the phenomena,  but I'm not sure about that...
If it's an hardware problem as stated before, should I find anything in those logs? Or where should I try to look? I will also try to see if Mint 11, as stated before, is not subject to that problem.

Thx a lot!
Lucas

P.S. I dont know if it is a symptom of the same problem, but I'll expose it too, just in case it can help to understand. On Ubuntu 10 and Mint 12, still on my MBP, sometimes the internal keyboard is like inactivated. No keystrokes or mouse pad moves are recorded during a time varying from a second to around 30 seconds... But the function keys (volume up/down, backlight up/down, etc.) still works and if an external keyboard or mouse are connected, those still works while the internal ones are inactive. In the syslog, I can see that at the moment of the problem, many message like "usb 7-2: USB disconnect, device number 20" are printed...
Bad devices connecti
Here is an extract from the log when that happens. As the original problem (logout) do not trigger that kind of messages I tend to believe that it is not related. But if the keyboard can appear as disconnected/reconnected, maybe a virtual Logout button can be pressed?
> Jan 14 13:45:22 lgomez-MacBookPro mtp-probe: checking bus 7, device 79: "/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2"
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.338323] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input160
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.338582] apple 0003:05AC:0231.009B: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.437777] usb 7-2: ctrl urb status -75 received
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.438012] apple 0003:05AC:0231.009C: hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.439960] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input161
Jan 14 13:45:22 lgomez-MacBookPro mtp-probe: bus: 7, device: 79 was not an MTP device
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.499733] bcm5974: bcm5974: could not read from device
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.499737] bcm5974: mode switch failed
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.568216] hub 7-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.568221] usb 7-2: USB disconnect, device number 79
Jan 14 13:45:22 lgomez-MacBookPro kernel: [ 8194.860260] usb 7-2: new full speed USB device number 80 using uhci_hcd

---

### Post by HappyLinux on 2012-01-16
I don't know if that is relevant either Igomez. However, I am running a wireless keyboard and mouse. Logitech K350 keyboard and Microsoft Mouse 5000.

---

### Post by HappyLinux on 2012-01-29
Here's an update.

After going through the insides of my computer to make sure connections are sitting right, the problem of auto log out remained. So, I decided to try a kernel update.

After going through reading the website that was linked too earlier in this thread, I ended up going too [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.2-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2.2-precise/") and downloading the most recent version. For me, it's the 64bit parts.

After updating to 3.2.2, it took a day before the log out problem happened. 10 minutes after that, it happened again. That was about 8am, it's now 9pm as I'm writing this.

What else can I try? This problem is really irritating.

I don't really want to return to Mint11 as it will no longer be supported sometime this year.

---

### Post by HappyLinux on 2012-01-31
OK, I think I may have found the cause for the problem, but I don't know how to find the solution.

This problem only ever happens whenever I press the "Enter/Return" key on my keyboard. It's a Wireless Logitech K350.

Is it possible for that button to glitch in the settings and be used as logout? I checked my keyboard settings. Everything seems fine. I even noticed the shortcut keys to logout is "ctrl+alt+del".

Oh yes, I also noticed that kernel 3.2.2 increases the rate of this logout glitch.

---

### Post by HappyLinux on 2012-01-31
Has this thread gone dead from lack of responses? I know people are viewing the thread. Surely there's someone who can make a small suggestion?

---

### Post by HappyLinux on 2012-02-09
UPDATE - I believe I've finally solved this problem, I'm not sure. Since just before my last entry, I moved the keyboards wireless receiver into a different USB socket. Since then, I've not had a single log-out problem. So, until further notice, I'll mark this thread as solved.

---

### Post by meandog on 2012-04-29
I'm having the same problem on Ubuntu 12.04 LTS (Kernel 3.0.0-16-generic X86_64). Display suddenly gets black and after a few moments I find myself in the sign in screen. When I sign in back, all my previous work is lost.

Btw, I have a PS/2 keyboard...

---

### Post by takvera on 2012-05-05
I have a problem with my system - Ubuntu 12.04 - auto logging me out after a couple of minutes, whether or not I am running any application.

I have gone into System settings --> Brightness and Lock --> and turned off the Lock setting.But no change.

I am running a desktop machine (intel CPU) with usb keyboard and mouse.

I have checked the syslog and attach  2 recent crash excerpts. I was also having this problem when I upgraded to 11.10 (i386) a week ago (so the problem has been ocurring for one week) and upgraded to 12.04 in the hope of eliminating the problem.. I have tried to find other threads offering solutions,

I attach the syslog excerpt of two recent crashes. Can anyone suggest a solution? 


Next step is to try and archive all data on the drive and then do a clean reinstall.from a boot CD.. but I want to exhaust all possibilities before doing this.

---

### Post by HappyLinux on 2012-05-05
I'm afraid that the logout problem has returned on my set-up again. Every few days or so, whenever I press the "Enter" key, my computer logs out, losing whatever work I was doing.

Doesn't matter what it is; hitting enter after keying in my password for the update screen. Hitting the button for a new paragraph in a document, or to open a file.

Maybe Mint 13 will solve the problem. I certainly hope so.

---

### Post by songhk on 2012-05-08
Recently I also have same problem. (auto logout)
Ubuntu 12.04, and 64 bit.

---

### Post by HappyLinux on 2012-05-09
This is proving to be a widespread annoyance for many people, and from what you just said, it remains in Ubuntu 12.04. That means it stands a chance of remaining in Mint 13.

---

### Post by PedroPan on 2012-05-10
Hi, I have had probably the very same problem for a while on my Dell Latitude 2100 netbook. It appeared as far as I can remember on all 3 of the most recent Kubuntu versions 11.04, 11.10, 12.04.
I noticed other people here writing about possible hardware/USB issues, but one other person here uses an PS2 keyboard.
I'm actually connecting my mouse (PS2), keyboard (USB on PS2 adapter) and external screen to the laptop through an old PS2-based KVM switch (Adder). The 2 PS2 outputs from the KVM switch are then muxed into a USB plug using a special adapter, which is then going into my laptop.

I also have sometimes an issue where for example the context menu (right click) pops up without me doing anything. In my particular case that could actually be because of the KVM setup, most likely because of some cable cross-talk or an issue inside the KVM or the PS2-USB adapter.
I thought that the logging out issue might be related, but since a lot of other people experience it, too, I wonder if it's something else (USB or keyboard driver, etc.).

So far I haven't managed to get anything useful from the system logs.
But the behaviour is like described by others. Most of the time, when I log in for the first time, I get logged out shortly afterwards (2 minutes). Then, after logging in again, it is OK for a while (sometimes the whole work day).

I now plugged my keyboard directly into the USB (well, via a USB hub), to see if that changes anything. So far (10 minutes) everything seems OK.

Peter

---

### Post by HappyLinux on 2012-05-11
I don't think it's a hardware problem as so many people with a wide selection of hardware are having this problem. I reckon it's a kernel problem,  but I'm usually wrong.

I never had this problem with Ubuntu 11.04, or Mint 11 which I switched too. Then again, I switched to a wireless keyboard during the early days of Mint 12.

---

### Post by lastboy on 2012-05-12
> **HappyLinux said:**
> UPDATE - I believe I've finally solved this problem, I'm not sure. Since just before my last entry, I moved the keyboards wireless receiver into a different USB socket. Since then, I've not had a single log-out problem. So, until further notice, I'll mark this thread as solved.

I think it worked for me too (10x)
Although I'm not using my wireless keyboard nor wireless mouse I thought it was my issue, but it seems that I was using USB 3.0 for the mouse and when I switched to my other USB connections it solved the problem.

---

### Post by lastboy on 2012-05-12
> **lastboy said:**
> I think it worked for me too (10x)
Although I'm not using my wireless keyboard nor wireless mouse I thought it was my issue, but it seems that I was using USB 3.0 for the mouse and when I switched to my other USB connections it solved the problem.

I'm not sure about that fix. 
It still occurs but rarely and I get a freeze once in few hours :-k

---

### Post by HappyLinux on 2012-05-12
I haven't had any freezes since very early Mint 12. As for the logout problem, I can sometimes hold it off by switching the adapter into a different USB socket.

Oh yes, I haven't got USB3

---

### Post by Nines on 2012-06-04
This bug has been affecting me as well.  Two spontaneous logouts in 1 day wherein the screen will go dark for a few seconds after which the login screen appears.  All work lost.   

After extensive forum searching, I have applied the following "fixes" without success :

Updating graphics drivers, not-using-chrome, disabling the screen lock, switching peripheral (keyboard / mouse combo) USB port

Distro : Ubuntu 12.04
System : Intel (i7), nvidia

---

### Post by Rodney9 on 2012-11-03
I have the same log-out issue when I hit enter as well, I am using Xubuntu 12.04 on my Toshibal L500 laptop.

Any news on fixes, I am using the laptop keyboard and a wireless mouse.

Rodney

---

### Post by koenr on 2012-11-22
We have this problem too. We have about 60 Ubuntu 12.04 identical software installations, 25 + 25 + 10 on the same hardware. Only in one lot of hardware are a few that have this symptom. The other 35 are fine. I'm monitoring now which of those 25 logout.
It happened up to now using LibreOffice and Firefox and seems to happen when pressing the enter key.
I checked the ones I'm sure that do it for excessive dust in fans or broken condensors on the mainboard, but could not find anything yet. Also syslog doesn't show anything that alerts me.

---

### Post by isa saids on 2012-12-18
Excuse me,

I have the same problem. I should share my problem thus may everyone could get if they're have the same too.

I got different problem in automatically logout, I have read about the topic and no one in relevant, I'm sorry before if my English is bad.

This is my laptop (Axioo Neon MNW) information:

I use Ubuntu 
Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-29-generic-pae
GNOME 3.4.2

And my Hardware is
Memory : 1,7GB
Processor : Intel® Core™2 Duo CPU P7370 @ 2.00GHz × 2

my VGA is SiS 671


Yes, About six hour ago I got my laptop is suddenly automatically logout when I'm trying to play a video by totem (the file is *.flv).

I was looking for what the problem is, and I feel that someone advice me to use other videos player in other forum threads, then I install smplayer 

At the first, I'm trying to play with smplayer and the result is still the same, then I'm trying to use vlc player and still the same too.

Then I back to install the smplayer again.
I open the screwdriver icon to open the video player preferences. In the general tab i open the video which is at the next to general. I change output driver to the x11(slow) then I change the qualities value become 3, then I change default zoom to 0.80, then I gave a check mark to the (use software video equalizer). And the last is in advanced tab I changed my monitor aspect setting to 16:10 (I make the same as my screen resolution in display which is 1280x768).

Then I try to play my video again and it is normal, then I try to play the video with other file format (*.dat) and the video is normal. I just solve my own problem by the simple. 

That is my story and I should share to everyone I'm sorry before. And Thank you.

---

