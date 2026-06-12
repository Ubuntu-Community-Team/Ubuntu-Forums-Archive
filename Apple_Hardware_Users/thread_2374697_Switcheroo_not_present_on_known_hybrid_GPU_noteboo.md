---
title: "Switcheroo not present on known hybrid GPU notebook - Ubuntu 16.04"
date: 2017-10-18
forum: Apple Hardware Users
---

### Post by capriotti-carlos on 2017-10-18
Hello fellow Ubuntu dwellers. 


A quick note to moderators: please do not move this thread to Apple hardware. There is a related (not the same) thread going on there, and this one really belongs here.


**TL;DR:** **Hybrid GPU notebook** with Ubuntu 16.04 **does not have switcheroo installed**. Need to find a way to **force the system to use the Radeon GPU**.


I am one of those unfortunate souls, owner of a flawed macbook pro 2011 (**8,2 early 2011 for the initiated ones**). This specific platform needs a special hack on grub in order to be able to use the Intel HD 3000 GPU (integrated, low power GPU) AND disable the AMD (ATI, for those as old as I am) Radeon 6000m series. This hack is required for Ubuntu installation AND regular operation, otherwise we have the purple screen of death, where the sytem DOES work, but the radeon driver kicks in and no image (other than a solid cursor on the upper left corner of the screen) is shown.


It turns out that, among other things, the external monitor won't work off the Intel GPU on this specific model. It is a known limitation, already stated by Apple. 


After a fair amount of research, several installs, I found out a few articles pointing to the switheroo mechanism, and I concluded that I can twist this mechanism to make my system run the Radeon only, outputting video to the external monitor, which is the only monitor I have on this particular machine (destroyed screen, beyond any repair). 


Here is the catch: most likely because the Radeon GPU was disabled during boot, Ubuntu's installer has never installed switcheroo; The folder simply isn't there, and associated binaties do not seem to exist either.


And now the cry for help: How do I manually install swicheroo ? 


Some more information to this case, that adds to (my) confusion: There is a lot of confusion about if this specific AMD GPU is supported or not by each system driver. The Radeon drivers shipped with Ubuntu 14 and 16 clearly do not like this Apple implementation. AMD's proprietary amdgpu-pro does not support it. Open source amdgpu SEEMS to support it, but I could be wrong; don't quote me on this one. On the other hand, xf86-video-ati and xf86-video-amdgpu (both open source) claim to support it. (If it makes any sense to you, this chipset is supported under Northen Islands, and TURKS, whatever those fancy names are).


What I am hoping to do, and where I need help:
- Have switcheroo manually instaled (how ? Need your help here. I could not find a single clue on how to do this)
- have a system that boots on text mode, no framebuffer enabled (grub; perhaps nomodeset + console option. Suggestions ?). I could even live without any output at all during boot.
- trigger switcheroo to force the Radeon ONLY (grub also, but I am not very sure. Maybe a script somewhere in the system. )
- auto-login to some user and have X start with the supported xf86-video-ati or xf86-video-amdgpu driver. (I am guessing this is on xorg.conf. Suggestions ?)


As an alternative, I thouht of installing Ubuntu with the text mode installer (but with the full desktop environment), no framebuffer at all, thus, without disabling any GPU on grub for ths installation, hoping that the system would detect both GPUs and install switcheroo. The limitation: netinstall (the only text mode intaller I know) does not work with UEFI, which is the preferred methid for macs, specially if one needs dual boot. This is not my case, but it is a valid situation to other users, and should be definetely documnented. Comments ?


Many thanks.

---

### Post by howefield on 2017-10-18
Thread moved to the "*SupportApple Hardware Users*" forum.

---

### Post by oblonsky on 2017-10-20
EDIT:
this might well fix it for you, or at least help you understand what is going on.

> [COLOR=#000000][COLOR=#000000]*Out of desperation I used my wife's macbook *[/COLOR][/COLOR][COLOR=#417394]*pro*[/COLOR][COLOR=#000000][COLOR=#000000]* (identical to my shattered one) and installed the system on it, successfully, BUT with the Intel hack from point 3. *[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]*Still on her notebook, with my SSD connected directly (not USB), I tried installing AMD's latest drivers (proprietary), and removing the hack lines from grub configurations on boot, but something wrong must have happened. The system booted to a black screen (system is running in the background). Re-enabling the hack, I see that Ubuntu fails auto-login in X, and keeps prompting me for a password. I enter the password, it tries logging on, fails, and quits back to the login manager again. *[/COLOR][/COLOR]

For linux kernel to use the open-source drivers to power the GPU and external monitor they SOMETIMES need to have Legacy BIOS calls enabled by the macs efi firmware.   (references in footnote 1)  The way the mac decides whether its Legacy mode will be available to linux (or windows or other) is by noting the presence of a MBR disk.  So if you boot linux from a GPT formatted disk you will boot in 'efi mode' and get a black screen, no graphics, unless you shut down the gpu and use only integrated graphics.  Which kills you as you have only external monitor.  If you boot from a mbr formatted disk then the efi firmware will provide the Legacy Bios functions that the linux open source drivers use to run the accelerated graphics and the external monitor through the GPU.  So you *may* just need to copy your install to a MBR disk if it is on a GPT disk.  Or convert the disk to MBR, which is dicey but instructions are found at [http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

You can see this illustrated on a macbook pro with a cd/dvd drive by booting from a dvd with say, a recent ubuntu installer iso on it.  If you boot the mac with the option key held, then wait for the dvd drive to spin up, eventually you will see TWO icons of a cd, one labeled WINDOWS, the other labeled EFI BOOT.  The iso has a hybrid image that will boot either way.  You may get different graphics display results depending on which you choose, or you may not, but you *WILL* get a very different linux install depending on which you select to start the process, because one will install linux to boot through efi, the other through the Legacy MBR method.  (Or you may wind up with some confused mixture that won't boot or run.  Most of the how-to-install-linux-on-a-mac guides on the web do not mention this very crucial distinction.)

(1)  the rEFIt website explains:  [http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)
> **Fact: You need BIOS compatibility for 2D/3D accelleration**

[COLOR=#000000][FONT=&amp]If you want good graphics support in Linux, you must boot it using BIOS compatibility mode. This also means using LILO or GRUB, and having a MBR partition table (either hybrid GPT/MBR or plain MBR).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]The X.org / XFree86 drivers for Intel and ATI hardware require a Video BIOS to initialize the card. The Linux text console also relies on the Video BIOS. Apple&#8217;s firmware only provides a Video BIOS when booting in BIOS compatibility mode. Without it, you only get unaccellerated frame buffer graphics.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Side note: James McKenzie published a [/FONT][/COLOR][hack to elilo]("http://www.madingley.org/macmini/")[COLOR=#000000][FONT=&amp] that activates the Video BIOS without activating the full BIOS compatibility mode. This actually allows the accelerated drivers to work without booting through LILO/GRUB. Unfortunately it only works on the Mac mini and hasn&#8217;t been updated in months[/FONT][/COLOR]

My own experience is that this is ***SOMETIMES*** **TRUE**, but **NOT ALWAYS**:  I have two late 2011 macbook pro laptops, one 17", and one 15".  The **15" model runs happily on pure efi boot** using refit/linux mint 18.1 (Which is ubuntu for our purposes, same kernel, same ubiquity installer, same version grub2beta etc.).  The 15" MBP will run linux on efi happily, external monitor works fine.  The **17" MBP will not run linux on efi unless the GPU is disabled** and only integrated graphics are used.  (Actually, it will probably run if you ssh in, just no display)  BUT if you boot the 17" MBP from the cd icon labed "WINDOWS" (ubuntu installer DVD, SuperGrub2 DVD, &c) then linux runs happily  in legacy mode and the full graphics work including the external monitor, so I run the 17" MBP in Legacy boot from a MBR disk.

/end EDIT

Hi Carlos,

I have (ubuntu 16.04 LTS based) linux mint running on two 2011 macbook pros, one 15" and one 17".   The 15" has both drivers installed and can run an external monitor.  The 17" is capable of running the external monitor and does so while running from an install dvd, however I have not been able to get an installed version to do everything properly - I believe this is due to quirks in how ubiquity and grub2 handle EFI booting vs legacy booting.

Both of these machines have new motherboards installed under Apples extended warranty program after GPU failure.  I am *reasonably certain* that if your GPU is bad then you will be able to run on the integrated graphics only and will not be able to switch.

There are hardware differences in whether ubuntu will install on these machines.   The 15" will run fine on either the 4.4.0-53 kernel or the 4.8.0 kernel.  The 17" will run fine on the 4.4.0 kernel, but the 4.8.0 kernel will only run with the GPU support disabled so no external monitor.  

You have not specified exactly what hardware you have.  There may be some kernel choice or install choices that will help you.  How the ubiquity installer chooses EFI install vs Legacy install also seems to vary between MBPro models, or due to differences in partitioning and menu choices.  I have gotten both EFI and Legacy installs on the same machine.

Good Luck

---

### Post by oblonsky on 2017-10-20
I just read your other thread which gives a much better explanation of your problem.  Due to the oddities of how the ubiquity installer deals with minor variations in hardware/partitioning, I would try two things:

1) Try booting from different version install isos.  My 15" (late 2011 i think) will boot from all I have tried.  My 17" (late 2011) is fussy and will boot from linux mint 18.1 with no special parameters.  linux mint 18.2 has a later kernel (ubuntu 4.8.0-53-generic vs 4.4.0) and it won't boot without disabling the GPU by adding a long list of parameters.

2) I have successfully used dd to clone an install from the 15" model to the 17" model - HOWEVER, so far I can only boot it with SuperGrub2 disk.  So I have some grub settings to fix.  I am using rEFInd on this machine.  The 15" uses rEFIt as it has had linux installed since 2012ish.  

Hope that helps, let us know how it turns out.  By the way, I fell on a staircase while holding the 15" and it warped the case on one edge but fortunately everything still works.
-David
> **capriotti-carlos said:**
> 
[COLOR=#000000]Hello everyone. [/COLOR]

[COLOR=#000000]Bear with me while I present my case; It is not straightforward at all.[/COLOR]

[COLOR=#000000]I am the sad owner of a nearly defunct MBP 15-inch early [/COLOR][COLOR=#417394]2011[/COLOR][COLOR=#000000] (it could be late [/COLOR][COLOR=#417394]2011[/COLOR][COLOR=#000000] also. I could be mistaken).[/COLOR]

[COLOR=#000000]This particular model has a few peculiarities:[/COLOR]

[COLOR=#000000]1) the curse of the dying discrete graphics ([/COLOR][COLOR=#333333]Radeon HD 6490M or [/COLOR][COLOR=#333333]HD 6750M[/COLOR][COLOR=#000000]), where the high power GPU simply stops working. My machine DOES NOT have this problem yet, for I can boot MacOS from 10.7 to High Sierra with any graphics mode enabled, without a problem (toggled on the power management area).[/COLOR]

[COLOR=#000000]2) a low power [/COLOR][COLOR=#333333]Intel HD Graphics 3000 GPU, which is known **not **to be very well managed by Apple itself. There are two known facts about this particular GPU/setup: Apple recognizes this low power GPU cannot manage an external monitor (using the mini displayport) and from some Linux posts, from several falvors - not just on Macs - if more than one GPU is present on the system, there are severe conflicts that will cause many side effects, among them the black (purple-ish) screen after boot. Well, do not quote me on this last one. 

[/COLOR][COLOR=#000000]3) Installing Ubuntu on such a machine (and possibly Arch, Mint, Debian) will require the Radeon to be disabled. As a matter of fact, this is a very popular hack (FIX ???...) used by people who suffer from the horrible death of the main GPU: completely disabling the GPU. ([/COLOR][https://help.ubuntu.com/community/MacBookPro8-2/Raring](https://help.ubuntu.com/community/MacBookPro8-2/Raring)[COLOR=#000000] and also the very good [/COLOR][https://orville.thebennettproject.co...1-macbook-pro/]("https://orville.thebennettproject.com/articles/installing-ubuntu-14-04-lts-on-a-2011-macbook-pro/")[COLOR=#000000])[/COLOR]

[COLOR=#000000]None of this is the reason why my mac is nearly defunct. The problem is that it fell and irreparably damaged the body, shattered the screen and pretty much rendered it useless as a notebook.[/COLOR]

[COLOR=#000000]Long story short, I've taken it apart, every piece, moved the system board to a regular case, and am running the MAINBOARD ONLY, with an SSD, connected to the external displayport. That means, no sound, WIFI, BT, DVD, camera or anything that is a regular "peripheral". It is the mainboard and the SSD. That's that. All the rest is connected via USB (except the power supply, of course).[/COLOR]

[COLOR=#000000]As I mentioned, MacOS runs fine in that "configuration". I've installed it with the internet installer, and it is happy. Following that, I tried installing Debian 9.2.1 (Strech), whose installer works out of the box (no hacks required), but when it reboots, graphics go to hell. You can ping and SSH the machine, which HAS X running, but that 's it: no image. Haven't spent much time on it, and jumped to Ubuntu, which is what I want on that, well, system, for lack of a better word. I was also able to install ubuntu SERVER in text mode like that.[/COLOR]

[COLOR=#000000]With all of that background in mind, here is the problem I need help with:[/COLOR]

[COLOR=#000000]If I apply the hack described on point 3 above, I don't have any image at all. It is rather predictable, since the Intel card cannot generate images to the external monitor. [/COLOR]

[COLOR=#000000]Among the many attempts on this system (about 30 to 40 hours of tests), I was able to disable the framebuffer (I think), quite and splash options, and got the system to continue the installer. It freezes (does it ? Or is it unable to output to screen, but continues to process in the background ?), and the last line I see stated it is switching from the EFI FB (framebuffer) to the radeondrmfb. Sounds clear that the radeon framebuffer is not a happy camper here.[/COLOR]

[COLOR=#000000]Out of desperation I used my wife's macbook [/COLOR][COLOR=#417394]pro[/COLOR][COLOR=#000000] (identical to my shattered one) and installed the system on it, successfully, BUT with the Intel hack from point 3. [/COLOR]

[COLOR=#000000]Still on her notebook, with my SSD connected directly (not USB), I tried installing AMD's latest drivers (proprietary), and removing the hack lines from grub configurations on boot, but something wrong must have happened. The system booted to a black screen (system is running in the background). Re-enabling the hack, I see that Ubuntu fails auto-login in X, and keeps prompting me for a password. I enter the password, it tries logging on, fails, and quits back to the login manager again. [/COLOR]

[COLOR=#000000]What I think I have to do (and where I need help):[/COLOR]

[COLOR=#000000]1) Install the system from scratch using the working notebook.[/COLOR]
[COLOR=#000000]2) Boot in text mode (for the old timers like me, runlevel 3), with no framebuffer either. (I tried a few options, like nofb, nomodeset, and CONSOLE on grub. How to make sure it will have no framebuffer active, to avoid conflicts ?) [/COLOR]
[COLOR=#000000]3) Disable the Intel GPU completely (I don't know the commands, but I guess i915.modeset=0 could be a hint. Need help here.)[/COLOR]
[COLOR=#000000]4) Install proprietary or open source AMD drivers (suggestions ? opinions ? most importantly, procedures ? )[/COLOR]
[COLOR=#000000]5) Force radeon only on boot (Maybe with radeon.modeset=1 on grub. Need help with the commands)[/COLOR]

[COLOR=#000000]I THINK that, if I install the right drivers, force the Intel GPU to be off, and the Radeon GPU to be on, Ubuntu will use the correct drivers and will finally work for my VERY particular setup.[/COLOR]

---

### Post by capriotti-carlos on 2017-10-20
David, hello and thank you very much for taking the time and answering my humble cry for help.

You deserve a good explanation for my two separate posts: on one I was aiming for a Mac-oriented answer, sharing my pain and fostering mac-centric ideas. The other was originally posted on the installation/upgrades list, but it got moderated, and ended up on the same list, which was not what I intended.

The generic post was meant to discover how to install switcheroo manually, which would benefit anyone using a hybrid GPU notebook: everyone nowadays. Macs are by far not the only platform facing this issue.

Now, back to the main task: The problem is now solved, but not in the way I hoped for: Fedora 26 installs and runs, after a quick grub fix. Its installer must be using a different radeon driver, since it not only boots and works with either GPU active (tested that myself), but also installs switcheroo flawlessly. For reference, Fedora's installer seems to run kernel 4.11. The installed system runs 4.11 and the first update took it to 4.13. 

So, I am happy to see my mac come back from the dead, and turn into a fantastic and useful server, but very sad it is not using Ubuntu, which I had been using for years on macs and other platforms.

Now readers, it does not feel quite right to share a Fedora solution here, but, for the sake of completion, and since it is a very simple hack, which will probably be useful on Ubuntu in the near future, here is what I did:

-On the INSTALLER, edit the grub options, adding to the line with "[COLOR=#000000][FONT=Menlo]/vmlinuz-blahblahblah[/FONT][/COLOR]" this parameter: [COLOR=#000000][FONT=Menlo]systemd[/FONT][/COLOR][COLOR=#666600][FONT=Menlo].[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]mask[/FONT][/COLOR][COLOR=#666600][FONT=Menlo]=[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]alsa[/FONT][/COLOR][COLOR=#666600][FONT=Menlo]-[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]state ([/FONT][/COLOR]alsa-state.service is buggy and stops switcheroo from working. This prevents is)

Note: At this moment, if you, like me, want to force the AMD (ati) Radeon to be on and NOT the Intel card, add also these parameters: radeon.modeset=1 i915.modeset=0 radeon.dpm=1

- After the system installs, reboot, edit grub AGAIN and add just the video parameters (the alsa thingy is no longer an issue). The system boots normally. 
- On your newly installed system, edit your /etc/defaults/grub and add radeon.modeset=1 i915.modeset=0 radeon.dpm=1 to your GRUB_CMDLINE_LINUX.

- Update your grub configuration; On Ubuntu, you must run update-grub. On Feroda you do grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg

Notes: 
1) This was done on a fully operational Macbooc Pro early 2011, and on the back-from-the-dead Macbook Pro late 2011 (this last one was stripped from ALL peripherals. It is just a system board, HD and power supply)
2) This is not an extensive list of commands, and is far, FAR from a copy-and-paste solution. Those are just pointers. 
3) Those grub parameters reflected my needs. You may have to play with them to get where you need with your system. 
4) Just to properly document this, I am going to add a last line with all of the relevante key words. For Google :) 
5) I don't know if the issue should be marked "solved"... Technically, it was not solved under Ubuntu.

Macbooc pro early 2011, late 2011, switcheroo working, radeon HD TURKS working, Intel HD 3000 working.

---

