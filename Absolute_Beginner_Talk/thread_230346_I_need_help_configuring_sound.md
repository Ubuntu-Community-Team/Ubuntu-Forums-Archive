---
title: "I need help configuring sound"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Ambimom on 2006-08-05
Okay, this is my second week....and I'm getting used to everything but here's my problem....

I installed Skype and was able to make PC to PC calls....

Then I installed Audacity and it worked fine....

I installed AMSN and now my webcam is working as it should, except it has to be turned off manually with Camorama on bootup.

Today, I installed Easy Ubuntu ...which in retrospect, I probably shouldn't because now nothing works....

Audacity doesn't recognize my sound card and won't install...I tried disabling ESD...no luck

My sound preferences default sound card won't change.  I have intel sound card and it keeps defaulting to usb, which is baffling.... 

As for Skype, it only works intermittently...and I can't figure out why.  I'm sooooo frustrated.

I've removed Easy Ubuntu, which removed Skype, I've uninstalled Audacity, but I'd like to use them if I can.

Please do not give me a list of written text commands to be put into the system thingy.....I'll start crying immediately....I don't know how to do that anyway...I've tried...I'm not doing it correctly.:-& 

What am I doing wrong?:confused:

---

### Post by tkiesel on 2006-08-05
Hi Ambimom,

You're going to be just fine. ;)  I had similar issues with Skype recently. My trouble came from the fact that I've made little customizations and tweaks to my computer ever since installing Ubuntu in early 2005, and I think I'd messed up the sound system with one of my experimental little hacks.

Here's how I got my sound system back to it's shiny like-new self!

(Disclaimer: actually, I used the text commands, which was quicker, but the way I'm going to tell you here will do the exact same thing! :) )

1. Go to System->Administration->Synaptic Package Manager

2. Enter your administrator password to access the program.

3. Synaptic spends a few seconds thinking while it loads. When it's ready to go, click on the "Search" button.

4. Search for alsa

5. Synaptic will spend some time looking for software with the word alsa in the name or description, like a miniature Google searching your computer.

6. After a while, it brings up a list of software in the right hand column.  Scroll down in there till you see something called alsa-base

7. Right click alsa-base and choose "Mark for Complete Removal". (What we're doing here is preparing to totally reinstall the sound configuration on your computer!)

8. A little warning window comes up, telling you that this removes some other software.  

9. Very Important: WRITE DOWN THE NAMES OF THESE PROGRAMS FOR LATER. For me it lists ubuntu-base and ubuntu-minimal. Losing those won't break your computer, but it can keep you from getting every suitable update in the furture. I doubt it'll list programs other than those two, but if it does, write down their names too.

10. Click the "Mark" button.  That small pop up window will close.

11. Click the "Apply" button and the "Apply" button on the window that pops up.

12. Wait for Synaptic to process your request and (de)install your software. It'll tell you when it's done and you can click the button to close that notification window and bring you back to the main Synaptic window.

13. Now you're in Synaptic again. Time to cleanly reinstall the things that you just uninstalled!

14. If alsa-base is still right there on your screen, great. If it isn't, find it with the "Search" button as before.

15. Right click alsa-base and choose "Mark for Installation"

16. Find each of the software names you wrote down earlier using Search. (I searched for ubuntu- with the dash on the end to easily find both ubuntu-desktop and ubuntu-minimal side by side. :) )

17. Right click and choose "Mark for Installation" for each of those pieces of software that you lost with alsa-base.

18. Once you have done "Mark for Installation" on alsa-base and the names you wrote down, click "Apply" on Synaptic and "Apply" on the window it pops up.

19. After Synaptic works out it's installation and says it is done, you can safely close Synaptic and you are done!

To give you some perspective on why a lot of people generally give command line answers to problems like this, look at how many steps I took to do this same procedure with the command line.

1, Go to Applications->Accessories->Terminal

2. Type in **sudo apt-get --purge remove alsa-base** and hit enter.

3. Enter your password when asked.

4. Type in **sudo apt-get install alsa-base ubuntu-base ubuntu-minimal** and hit enter.

5. Done!!

It's not for everyone, but it is much quicker! ;)

Good luck Ambimom!
-T

---

### Post by Ambimom on 2006-08-05
Thanks tkiesel.....here's what I did...First I removed the Easy Ubuntu. Thankfully it came with a removal tool. When I removed Easy Ubuntu, it removed Skype too.

 Then I searched here and found a similar thread:
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
 which instructed me on getting fresh ALSA drivers. 

I'm pretty comfortable in Windows, so this was really scary but I figured I could always reboot and reinstall Ubuntu from the Live CD if I had to...

After I rebooted, my correct sound card was showing and now Audacity is working too. 

As for Skype...I give up.  Frankly, it just doesn't work that great yet in Linux.  I'll forego skype until it gets improved and updated.  

Thanks for your help!

---

### Post by tkiesel on 2006-08-07
> **Ambimom said:**
> As for Skype...I give up.  Frankly, it just doesn't work that great yet in Linux.  I'll forego skype until it gets improved and updated.  Thanks for your help!

Skype has been an interesting bit of semi-frustration for me too. It works a bit more smoothly now that I did the procedure I descibed to you above, but they certainly could use some more specific and easier configuration options in Skype.  I might try the 1.3 beta.  I might not. ;)

I'm glad to hear that Audacity and your sound card are working out well now!  :)

-T

---

### Post by Ambimom on 2006-08-07
I give up on Audacity!  AFter all that....it gave me that silly error message again....I know it's probably a very simple quirk that I haven't discovered yet...like having to tick some box or twirl around three times and chant, but I don't have the time to mess with it....It just doesn't work the way it should in Linux. 

I've used the Windows version of Audacity for ages, so I know how responsive and easy it is to use.  I capture a stream from This American Life with VLC and use Audacity to trim and convert it to MP3 so I can load it onto my Ipod. More's the pity.

The same for Skype.  It works seamlessly in Windows. I know there's Ekiga, but that's for Linux, not to mention the $$ I've got in Skypeout. All my friends are on Skype. I removed the Linux version because it was too painful to keep fussing with it.  

As for Totem as the default media player in Ubuntu, it doesn't work for me either.  Thankfully, VLC always does!
  
So far, VLC and Firefox are the only two applications that just work pretty much the way they are supposed to work. 

I just wish Linux applications were a bit more seamless.

---

### Post by deadgobby on 2006-08-07
> **Ambimom said:**
> I give up on Audacity!  AFter all that....it gave me that silly error message again....I know it's probably a very simple quirk that I haven't discovered yet...like having to tick some box or twirl around three times and chant, but I don't have the time to mess with it....It just doesn't work the way it should in Linux. 

I've used the Windows version of Audacity for ages, so I know how responsive and easy it is to use.  I capture a stream from This American Life with VLC and use Audacity to trim and convert it to MP3 so I can load it onto my Ipod. More's the pity.

The same for Skype.  It works seamlessly in Windows. I know there's Ekiga, but that's for Linux, not to mention the $$ I've got in Skypeout. All my friends are on Skype. I removed the Linux version because it was too painful to keep fussing with it.  

As for Totem as the default media player in Ubuntu, it doesn't work for me either.  Thankfully, VLC always does!
  
So far, VLC and Firefox are the only two applications that just work pretty much the way they are supposed to work. 

I just wish Linux applications were a bit more seamless.

 What kinda of error message are you getting running Audacity? Are you trying to convert a file to mp3? There is alot of Linux apps that work seamless, but times it will need some help to sew the seams up a tad bit. Some are simple and some tend to need more fanagle to get the app or HW to work. 
 Linux is a on going Metamorphosis and people who voluntee there own time writing drivers and such to make the train go. 
 Gobby

---

### Post by Ambimom on 2006-08-07
"Error initializing Audio" which apparently is a known bug.  Some people turn off the Sound Effect and it seems to work...but for me I just couldn't seem to get it coordinated.  I actually reloaded the ALSA drivers completely to start afresh and it did work...once...and then for some unaccountable reason...it stopped again and gave the "error initializing audio" again. I'm sure it is something simple, but I don't have the time or energy to find out what ....

It's not really the conversion to mp3 for which I need Audacity... I capture a streaming audio radio program on a server with VLC.  The stream is much larger than I want so I use Audacity to trim it.  Then I use Audacity to export the portion I want as an MP3 that I can play on my ipod.  

I'm sure I could spend a few more days on this, but really I don't want to...it's not worth the aggravation when I can accomplish my task in about 10 minutes in Windows, instead of spending days trying to get it to work in Linux.

I am confident that Linux will eventually be a suitable replacement for Windows users like me, but I don't think I'm ready to abandon Windows until I can do what I need to do without spending a lot of time tinkering.

---

