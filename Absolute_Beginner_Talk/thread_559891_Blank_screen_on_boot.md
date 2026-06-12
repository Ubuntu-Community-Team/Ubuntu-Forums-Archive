---
title: "Blank screen on boot"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Gzus666 on 2007-09-25
ok, here goes. im posting this again cause someone came in and did a off topic post, and i got no help. lets start with PC setup.

EVGA 680i mobo
Core 2 duo 2.4 overclocked to 3.2
2GB OCZ 800MHZ retimed to 4-4-4-12
EVGA 8800GTS 320
22" Samsung monitor (1680X1050)

gave as much info as possible without going nuts, so if more is needed let me know. downloaded the Ubuntu 7.04 X86-64bit yesterday. the live CD would not work, i would get a black screen after it loaded the kernel to install. so, i used the alternate and it worked like a charm. 

GRUB is working great, boots to that menu fine, and i can load windows XP just fine. i have windows on a 250GB SATA300 drive, and i installed the Ubuntu on a 500GB SATA300 drive. now when i choose to load the kernel from the GRUB menu, it goes black with a command line at the upper left (much like old Apple command lines).

seems to me like a graphics problem of some sort, cause after the command line, it completely blanks out. any ideas?

---

### Post by overdrank on 2007-09-25
> **Gzus666 said:**
> ok, here goes. im posting this again cause someone came in and did a off topic post, and i got no help. lets start with PC setup.

EVGA 680i mobo
Core 2 duo 2.4 overclocked to 3.2
2GB OCZ 800MHZ retimed to 4-4-4-12
EVGA 8800GTS 320
22" Samsung monitor (1680X1050)

gave as much info as possible without going nuts, so if more is needed let me know. downloaded the Ubuntu 7.04 X86-64bit yesterday. the live CD would not work, i would get a black screen after it loaded the kernel to install. so, i used the alternate and it worked like a charm. 

GRUB is working great, boots to that menu fine, and i can load windows XP just fine. i have windows on a 250GB SATA300 drive, and i installed the Ubuntu on a 500GB SATA300 drive. now when i choose to load the kernel from the GRUB menu, it goes black with a command line at the upper left (much like old Apple command lines).

seems to me like a graphics problem of some sort, cause after the command line, it completely blanks out. any ideas?

Hi I can offer this 
Boot in Recovery Mode (select it from the GRUB menu)
type:


```
sudo dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:

```
reboot
```

and boot as usual
Hopefully this will get you to the desktop and the you can try Envy to install the proper drivers
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Good luck!

---

### Post by Gzus666 on 2007-09-25
ok, booted into recovery as you stated. it drops down a huge line of hard drive info attempts, and finally finishes with Done, and gives me a blinking cursor that i could hardly call a command prompt. at this point i typed in the command you gave, and it responded by dropping to the next line blinking again, as if it wasnt responding. 

any other ideas on how to deal with this? i tried reinstalling, and thats no go. could this be a bad ISO file or what?

---

### Post by overdrank on 2007-09-25
> **Gzus666 said:**
> ok, booted into recovery as you stated. it drops down a huge line of hard drive info attempts, and finally finishes with Done, and gives me a blinking cursor that i could hardly call a command prompt. at this point i typed in the command you gave, and it responded by dropping to the next line blinking again, as if it wasnt responding. 

any other ideas on how to deal with this? i tried reinstalling, and thats no go. could this be a bad ISO file or what?

Hi, start ubuntu normally and use the keys (at the black screen)  alt,ctrl, F1 all at the same time and this should bring you to the command prompt. Where you are asked to login and then use what was posted first.

---

### Post by Gzus666 on 2007-09-25
i just cant seem to get a command line. anyone have any idea how i can get a command line here? the one it gives me when i do recovery has no function, it just lets me type with no effect. i tried the alt ctrl f1 at both prompts, not working.

---

### Post by overdrank on 2007-09-25
> **Gzus666 said:**
> i just cant seem to get a command line. anyone have any idea how i can get a command line here? the one it gives me when i do recovery has no function, it just lets me type with no effect

See post #4

---

### Post by Gzus666 on 2007-09-25
it still wont give me a command line. i did the normal boot, it does the blink thing, then does the kernel alive prompt, then goes blank, and i cant get to a prompt with ctrl alt f1 with that or recovery.

---

### Post by overdrank on 2007-09-25
> **Gzus666 said:**
> it still wont give me a command line. i did the normal boot, it does the blink thing, then does the kernel alive prompt, then goes blank, and i cant get to a prompt with ctrl alt f1 with that or recovery.

Ok then you have nothing to loose by trying to reinstall Ubuntu because you have not been able to access it. Good luck !

---

### Post by Gzus666 on 2007-09-25
> **overdrank said:**
> Ok then you have nothing to loose by trying to reinstall Ubuntu because you have not been able to access it. Good luck !

already tried, same thing. this is driving me nuts, i cant even fight it to work, cause i get nothing. maybe i should have tried SUSE, ha

---

### Post by overdrank on 2007-09-25
> **Gzus666 said:**
> already tried, same thing. this is driving me nuts, i cant even fight it to work, cause i get nothing. maybe i should have tried SUSE, ha

I understand your frustrations but did you check the cd for errors? Also you can check and verify the cd with this link
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
It could have been a bad burn or a bad download. I can offer this link on the burning of the cd also
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I hope this helps and good luck in whatever choice you make.

---

### Post by Gzus666 on 2007-09-25
well, CD checks out, so thats not the problem. any other ideas? this is wearing me out, ha. i do appreciate your help though

---

### Post by overdrank on 2007-09-25
> **Gzus666 said:**
> well, CD checks out, so thats not the problem. any other ideas? this is wearing me out, ha. i do appreciate your help though

HI have you tried the live cd again, and try to get to the command prompt there?
Edit I know I am grasping for straws here just some signs of life.

---

### Post by Gzus666 on 2007-09-25
live cd is completely dead. anything i tried on it failed, including the cd test. it would do the kernel load, then just die. anyway, off to bed, guess i will have to work on it again tomorrow night. anymore help you can give would be appreciated.

---

### Post by overdrank on 2007-09-26
> **Gzus666 said:**
> live cd is completely dead. anything i tried on it failed, including the cd test. it would do the kernel load, then just die. anyway, off to bed, guess i will have to work on it again tomorrow night. anymore help you can give would be appreciated.

Well the last thing I can think of is the overclocking and the ram. I had a system that I could not install on until I removed a stick of ram. Good night and sorry for the lack of knowledge on my part good luck!

---

### Post by Gzus666 on 2007-09-26
ok, well, i have found that the live CD seems to be corrupt, so time to redownload and make sure everything is legit. hopefully i can get this working with the live cd. i tried to load the graphic safe mode and it gave me an error about the CD. wish it was the weekend so i had more time to mess with this

---

### Post by overdrank on 2007-09-26
> **Gzus666 said:**
> ok, well, i have found that the live CD seems to be corrupt, so time to redownload and make sure everything is legit. hopefully i can get this working with the live cd. i tried to load the graphic safe mode and it gave me an error about the CD. wish it was the weekend so i had more time to mess with this

Please post back if you have success or if you have problems.

---

### Post by Gzus666 on 2007-09-27
ok, got the live CD working (why does the ISO burner default to 40X write speed? i can never burn anything over 8X successfully) it wouldnt work at first until i switched the resolution by pushing F4 or whatever it was, and switched it to a resolution. as suspected, it appears to be a graphical issue. 

now, my problem still lies with this, as i cannot switch the resolution from the GRUB menu. is there anyway to either get a command prompt from the boot/grub text interfaces, or add a command line to the boot line for Ubuntu to change the resolution?

---

### Post by overdrank on 2007-09-27
> **Gzus666 said:**
> ok, got the live CD working (why does the ISO burner default to 40X write speed? i can never burn anything over 8X successfully) it wouldnt work at first until i switched the resolution by pushing F4 or whatever it was, and switched it to a resolution. as suspected, it appears to be a graphical issue. 

now, my problem still lies with this, as i cannot switch the resolution from the GRUB menu. is there anyway to either get a command prompt from the boot/grub text interfaces, or add a command line to the boot line for Ubuntu to change the resolution?

Hi I am a little confused, You were able to get the livecd to boot to the desktop?

---

### Post by Gzus666 on 2007-09-27
yes, i got it to go to the desktop from the live CD. at the desktop, i did a reinstall. the way i got to that was to adjust the resolution from VGA to a basic resolution. im thinking my card doesnt support VGA and thats why its not working there (DVI outputs on my card, DVI monitor, full digital, no analog.) starting to think thats why everyone is having problems with the 8 series cards. anyway, from there after the install, i get to the grub, and i still cant load up the desktop, cause the resolution cant be changed from the grub menu that i know of.

now, what i need to know is how to adjust this, it has to be possible, i just dont know the way to do it. once i get in, then i can load the drivers and rock and roll, but until then, i cant get into the desktop except for on the live CD. has to be a way to do it either from the boot/grub text interface, or editing the boot lines in grub, i just dont know how yet.

got any ideas?

---

### Post by overdrank on 2007-09-27
> **Gzus666 said:**
> yes, i got it to go to the desktop from the live CD. at the desktop, i did a reinstall. the way i got to that was to adjust the resolution from VGA to a basic resolution. im thinking my card doesnt support VGA and thats why its not working there (DVI outputs on my card, DVI monitor, full digital, no analog.) starting to think thats why everyone is having problems with the 8 series cards. anyway, from there after the install, i get to the grub, and i still cant load up the desktop, cause the resolution cant be changed from the grub menu that i know of.

now, what i need to know is how to adjust this, it has to be possible, i just dont know the way to do it. once i get in, then i can load the drivers and rock and roll, but until then, i cant get into the desktop except for on the live CD. has to be a way to do it either from the boot/grub text interface, or editing the boot lines in grub, i just dont know how yet.

got any ideas?

Ok so you can boot to the grub and then it hangs at the grub menu. Like it will let you choose from ubuntu or windows. Or does it continue and then stops with a black screen with some text?

---

### Post by porkbird on 2007-09-27
Ok, I am having the exact same problem you are. I can was able to boot from the Live CD after changing the resolution by hitting F4. I was able to install Ubuntu, but when I restarted and selected to boot in grub nothing happened. I have almost the same setup you do. I also believe that it is an issue with the 8800's. I hope someone here has a suggestion. But to clarify, in grub I select Linux and then the screen goes black and nothing happens at all.

---

### Post by overdrank on 2007-09-27
> **porkbird said:**
> Ok, I am having the exact same problem you are. I can was able to boot from the Live CD after changing the resolution by hitting F4. I was able to install Ubuntu, but when I restarted and selected to boot in grub nothing happened. I have almost the same setup you do. I also believe that it is an issue with the 8800's. I hope someone here has a suggestion. But to clarify, in grub I select Linux and then the screen goes black and nothing happens at all.

Ok then you may try to reconfigure your xorg. Use the keys alt,ctrl,F1 and that should bring you to the command prompt to login. After you login then use the command 
```
sudo dpkg-reconfigure xserver-xorg
``` and choose vesa for the driver then answer the questions if you don't know the answer then leave as the default is given then use the command 
```
sudo shutdown -r now 
``` and the system will reboot. Good luck!

---

### Post by Gzus666 on 2007-09-27
the problem is, if he has the same one i do, he wont be able to get a command prompt, cause the screen blanks out before we can log in and get a prompt. there are 2 prompts i can get from the GRUB, one involves the text based GRUB by pressing escape at GRUB. from here i can do text GRUB commands. the other involves the text based boot, which throws me in a boot command line, only doing boot commands. is there any way to get to the command line from either of these?

from what i can see, this is a VGA issue. the 8800 is full digital output, this version of Ubuntu defaults to an analog mode(VGA). there has to be a way to adjust this friggin resolution from the GRUB. is there anyway to find out what the command line is for the resolution control in the live CD menu? cause then i think i could edit the boot command for the kernel to change the resolution and then install any drivers i need when i hit the desktop

---

### Post by overdrank on 2007-09-27
> **Gzus666 said:**
> the problem is, if he has the same one i do, he wont be able to get a command prompt, cause the screen blanks out before we can log in and get a prompt. there are 2 prompts i can get from the GRUB, one involves the text based GRUB by pressing escape at GRUB. from here i can do text GRUB commands. the other involves the text based boot, which throws me in a boot command line, only doing boot commands. is there any way to get to the command line from either of these?

from what i can see, this is a VGA issue. the 8800 is full digital output, this version of Ubuntu defaults to an analog mode(VGA). there has to be a way to adjust this friggin resolution from the GRUB. is there anyway to find out what the command line is for the resolution control in the live CD menu? cause then i think i could edit the boot command for the kernel to change the resolution and then install any drivers i need when i hit the desktop

This is where I am getting confused. If you can reach the grub and choose ubuntu and then it continues to load and then blackscreen you should be able to reach the command line with the alt, ctrl F1 keys or at least boot in to recovery mode because it is command line only.

---

### Post by Gzus666 on 2007-09-27
> **overdrank said:**
> This is where I am getting confused. If you can reach the grub and choose ubuntu and then it continues to load and then blackscreen you should be able to reach the command line with the alt, ctrl F1 keys or at least boot in to recovery mode because it is command line only.

i agree, it doesnt make much sense. but im sure the prompt is physically there, but the monitor/GPU wont display it. i have seen just about everyone with an 8 series card with this similar problem. to me, it seems an output problem from the card to the kernel. the way i came to this conclusion is by changing from VGA to a resolution, i could load the desktop. also when the screen blanks out in the load from the GRUB, after a while it will automatically go into standby mode after a bit, which means its getting no video signal.

i pretty much know the reason for the problem, i just dont know Linux command lines well enough to be able to fix it yet.

---

### Post by overdrank on 2007-09-27
Ok lets try this, When you see the grub load press the esc key, this will open another screen and here you can edit the kernel which should be the second line down. Press e and edit the kernel line and remove quiet and replace with vga=771. Then press enter then b to boot. This will at least let us see if there are any errors.

---

### Post by Gzus666 on 2007-09-27
> **overdrank said:**
> Ok lets try this, When you see the grub load press the esc key, this will open another screen and here you can edit the kernel which should be the second line down. Press e and edit the kernel line and remove quiet and replace with vga=771. Then press enter then b to boot. This will at least let us see if there are any errors.

ok, removed Quiet, replaced it with VGA=771. it did the normal cursor blinking, after a short bit, it rebooted. didnt give me the live kernel message like it usually does before it goes blank.:confused:

---

### Post by overdrank on 2007-09-27
> **Gzus666 said:**
> ok, removed Quiet, replaced it with VGA=771. it did the normal cursor blinking, after a short bit, it rebooted. didnt give me the live kernel message like it usually does before it goes blank.:confused:

Ok I have to ask you did not use capital VGA ? And you can try adding noacpi to the kernel and I hope this works as I am out of idea's.

---

### Post by porkbird on 2007-09-27
Hey, I have tried all of your suggestions as well and I am still having the same problem. Although for whatever reason when I start in recovery mode and then startx it loads. I would almost be happy with that if I could use my wifi card. But anyway, thanks for all the help, I hope I can figure this out before it drives me crazy.

---

### Post by overdrank on 2007-09-27
> **porkbird said:**
> Hey, I have tried all of your suggestions as well and I am still having the same problem. Although for whatever reason when I start in recovery mode and then startx it loads. I would almost be happy with that if I could use my wifi card. But anyway, thanks for all the help, I hope I can figure this out before it drives me crazy.

Ok here it goes, this is my last idea. If the both of you can boot the live cd then do that and try and modify you xorg on your installation to have the vesa as the driver that will look like this 

Section "Device"
    Identifier     "nVidia Corporation NV28 [GeForce4 Ti 4800 SE]"
    Driver         "nvidia"
EndSection
 
Then select the resolution that are the lowest like 800x600 and it will look like this 
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV28 [GeForce4 Ti 4800 SE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"

```
Then save the file and reboot with out the live cd and hope it works. [-o<

---

### Post by Gzus666 on 2007-09-27
well, good news. i guess i wasnt editing the correct boot menu file. i changed the root kernel file, amending the line by adding vga=795 (found another thing on the forum about the 8800 series cards, seems to be the work around) got to the graphical interface and got to log in. from there i ran to the command line, FINALLY!!!. from there, i did "sudo dpkg-reconfigure xserver-xorg". went through all the options, and did the vesa thing, and setup the rest of the options. i then did a "sudo reboot". now im kinda stuck, as it still wont boot without putting the vga=795 in there.

should i still put the vga=795 in there and then boot? i ask because booting this way takes like 20 minutes, swear to you, so its extremely time consuming and i dont want to get into it tonight since its almost time for me to sleep. i tried doing a "sudo apt-get-install nvidia-glx-new" to try to get the driver, but it gave me an error. anything else that should be done, or can i just boot with the vga=795 thing and then set everything up?

---

### Post by overdrank on 2007-09-27
> **Gzus666 said:**
> well, good news. i guess i wasnt editing the correct boot menu file. i changed the root kernel file, amending the line by adding vga=795 (found another thing on the forum about the 8800 series cards, seems to be the work around) got to the graphical interface and got to log in. from there i ran to the command line, FINALLY!!!. from there, i did "sudo dpkg-reconfigure xserver-xorg". went through all the options, and did the vesa thing, and setup the rest of the options. i then did a "sudo reboot". now im kinda stuck, as it still wont boot without putting the vga=795 in there.

should i still put the vga=795 in there and then boot? i ask because booting this way takes like 20 minutes, swear to you, so its extremely time consuming and i dont want to get into it tonight since its almost time for me to sleep. i tried doing a "sudo apt-get-install nvidia-glx-new" to try to get the driver, but it gave me an error. anything else that should be done, or can i just boot with the vga=795 thing and then set everything up?

Great glad to hear, now you will have to add that to the kernel in the grub but not tonight I will find the how to for tomorrow great glad you got somewhere. :guitar:

---

### Post by Gzus666 on 2007-09-27
> **overdrank said:**
> Great glad to hear, now you will have to add that to the kernel in the grub but not tonight I will find the how to for tomorrow great glad you got somewhere. :guitar:

cool, sometimes being on the cutting edge of technology is a pain in the ***, ha. you think they would have patched this already, since it can be fixed with commands](*,) 

by add that, do you mean the vga=795? just curious, i will have to mess with it tomorrow of course. if its the vga=795, i assume thats so i can get in, setup my network, and then load my video drivers? i assume thats the case, but ive been wrong before, ha. 

anyway, appreciate the help, finally getting somewhere. also to the other guy in this post with the problem. just to walk you through, when you get to the GRUB menu, push "e". from there, the 2nd line down i believe it was is a LONG command line, starts with root i believe. push "e" on that line. add "vga=795" to that line, then push "b" to boot. this took literally about 20 minutes for mine to boot up, so wait it out. once you get to the desktop screen, you will be asked to log in. from there hit ctrl alt and F1 at the same time, and you will get a command line.

from there, type your login name, and hit enter, then type in your password, and enter again (there will be nothing showing when you type the password, not even ****, so dont worry, its typing) from there, type "sudo dpkg-reconfigure xserver-xorg" (dont do the quotes). now this will probably take a while too, but when it loads, select Vesa as the first option, the rest is pretty self explanatory. after that it will put you back at the prompt. from there type "sudo reboot" and thats where im at.

---

### Post by overdrank on 2007-09-28
Hi and hope things are well this morning and I think this link will help you amend the kernel in the grub list. Good luck and hope this completes your issue.
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

---

### Post by Gzus666 on 2007-09-28
cool, thanks for the link. dumb question though, i assume im amending this with "vga=795" right? so far it takes like 20 minutes to boot into the desktop, god i hope thats not going to be the norm in this case. wasnt sure if there was supposed to be anything else i needed to change. im hoping that the load time is reduced when i finally get ot the desktop for the first time, otherwise i wont be using this long, ha.

either way, thanks for the help. my C++ book comes in today, great time to fall into my programming, oh boy. (i got a bug up my a$$, and decided to teach myself C++, since i have heavy hardware knowledge, but no programming knowledge) cross your fingers and hope this all goes smooth from here out. 

one last stupid question, im assuming when i actually get to the desktop, setting up my wireless network is simple? on the alternate CD it setup the network during the install, but the live CD did not. anyway, still at work, so i will mess with it when i get home, and update you with how things go

---

### Post by 005david on 2007-09-28
i have a similar problem, and when i try "reboot" the computer says "you need to be root"

how the hell do i 'be root'

and it denies me access to xserver...

---

### Post by Gzus666 on 2007-09-28
> **005david said:**
> i have a similar problem, and when i try "reboot" the computer says "you need to be root"

how the hell do i 'be root'

and it denies me access to xserver...

need to make sure you are typing "sudo" (dont put the quotes) in front of the command

---

### Post by 005david on 2007-09-28
i did type sudo.

---

### Post by 005david on 2007-09-28
> **005david said:**
> i did type sudo.

but apparently you don't care.

---

### Post by Gzus666 on 2007-09-28
ok, got everything loaded, now i got a GNOME interface error. only thing i can think is there was a problem loading it (i had something fail on the initial load of the kernel, and im starting to suspect it was an error when i installed since i had to reboot so many times without fully loading it after the installation.) is there a way to reload just GNOME off the live CD simply? or would it just be easier to do another install?

and to the other guy, sorry, i answered while i was at work, and i was about to leave when i answered. i do have a life outside the forum, ha. im not sure what to tell you, "sudo reboot" is the correct command. unless youre not logged in correctly, im not sure why it wouldnt work

---

### Post by Gzus666 on 2007-09-29
well, crap. when i get the desktop running, it gives me a "error loading GNOME Daemon" and it doesnt give me access to any of the taskbars. i can go through my folders just fine, but no system or anything like that. its very strange. also cant reinstall, or setup my wireless network. the partition manager on the live CD is now giving me errors, and i cant find a back way into any of the system functions like networking from the file folders. any ideas? im about to just reformat the stupid drive, and start over.

---

### Post by overdrank on 2007-09-29
> **Gzus666 said:**
> well, crap. when i get the desktop running, it gives me a "error loading GNOME Daemon" and it doesnt give me access to any of the taskbars. i can go through my folders just fine, but no system or anything like that. its very strange. also cant reinstall, or setup my wireless network. the partition manager on the live CD is now giving me errors, and i cant find a back way into any of the system functions like networking from the file folders. any ideas? im about to just reformat the stupid drive, and start over.

Hi and i am sorry to hear about the problem, I cant remember but did you check the disc for checksum? if not [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Gzus666 on 2007-09-29
yup, everything checked out with that. strange thing is, on the live cd desktop, i get the same error, but i can use everything just fine. not sure what the hell the deal is, but this is wearing me out, ha. im about to just wipe the damn drive and start over, or just wait for gutsy gibbon. hopefully you have some ideas, cause this just isnt making sense to me.

---

### Post by porkbird on 2007-09-30
Hey guys, I did get it to boot with the advice here, and in another thread. But now I cant install Nvidia drivers at all. I think I am just going to try and reinstall this. Thanks for all the help.

---

### Post by overdrank on 2007-09-30
> **porkbird said:**
> Hey guys, I did get it to boot with the advice here, and in another thread. But now I cant install Nvidia drivers at all. I think I am just going to try and reinstall this. Thanks for all the help.

HI have you tried envy for the drivers?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

