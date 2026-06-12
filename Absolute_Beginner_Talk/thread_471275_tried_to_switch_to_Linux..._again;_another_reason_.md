---
title: "tried to switch to Linux... again; another reason not to?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Sarke on 2007-06-11
I've tried to make the jump to Linux several time over the past few years.  First Red Hat, then Mandrake, and I've installed Ubuntu maybe 3 times over the past two years.  But each time I feel it's not quite there yet.

Last time it was the web browsing because the flash wasn't working properly, and this time it's something (probably) really simple but I'm still back in Windows as we speak.

I really do want to switch because Windows is slowly getting more frustrating, and I want to just use Windows for gaming and then the normal stuff in Ubuntu.


Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it.  **Is this still true?**

I'm fairly well versed in computers, but I just find the manual config stuff very tedious and awkward.  So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.  

How do I change it to that resolution without having to poke around in config files?

---

### Post by KIAaze on 2007-06-11
> Last time it was the web browsing because the flash wasn't working properly, and this time it's something (probably) really simple but I'm still back in Windows as we speak.
Flash works well for me. In fact it probably helped spend more time under Ubuntu thanks to youtube.

> Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it. Is this still true?
Unfortunately yes I would say.
Mainly because of hardware support problems, but also because GNU/Linux users are generally used to the CLI and it doesn't bother them that much.
A lot can be done without CLI now, but I still use it quite often, either because I don't know a GUI way, or because it's faster.

Can't help you for the resolution thing. :/

Personally, I would recommend you to keep on dual-booting. One day, you might suddenly get addicted to Ubuntu, who knows. :)

---

### Post by HackingYodel on 2007-06-11
> **Sarke said:**
> So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.  

How do I change it to that resolution without having to poke around in config files?

What graphics card/monitor combination are you using and which version of Ubuntu are you using?  We may just be a few clicks of the mouse away from the proper resolution for you.

---

### Post by Lord Illidan on 2007-06-11
> **Sarke said:**
> I've tried to make the jump to Linux several time over the past few years.  First Red Hat, then Mandrake, and I've installed Ubuntu maybe 3 times over the past two years.  But each time I feel it's not quite there yet.

Last time it was the web browsing because the flash wasn't working properly, and this time it's something (probably) really simple but I'm still back in Windows as we speak.

I really do want to switch because Windows is slowly getting more frustrating, and I want to just use Windows for gaming and then the normal stuff in Ubuntu.


Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it.  **Is this still true?**

I'm fairly well versed in computers, but I just find the manual config stuff very tedious and awkward.  So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.  

How do I change it to that resolution without having to poke around in config files?

Do you have an nvidia card or an ATI card?

Normally, there is no need to "poke around" in config files, but it depends on your hardware, and on your temperament. Personally, I have nothing against it.

---

### Post by Sarke on 2007-06-11
> **HackingYodel said:**
> What graphics card/monitor combination are you using and which version of Ubuntu are you using?  We may just be a few clicks of the mouse away from the proper resolution for you.

NVIDIA 7800 GS, HP f2105, latest.

---

### Post by mcurtiss1970 on 2007-06-11
my laptop is by no means powerful, but all I've had to do in the command lines so far is tweak the xorg so i could fix my touchpad.  not such a big deal...and i'm a n00b

---

### Post by ramjet_1953 on 2007-06-11
If you follow this link and choose the particular sections that apply to you, there isn't too much that you should not be able to sort out.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Regards,
Roger :cool:

---

### Post by malathia on 2007-06-11
> **Sarke said:**
> I've tried to make the jump to Linux several time over the past few years.  First Red Hat, then Mandrake, and I've installed Ubuntu maybe 3 times over the past two years.  But each time I feel it's not quite there yet.

Last time it was the web browsing because the flash wasn't working properly, and this time it's something (probably) really simple but I'm still back in Windows as we speak.

I really do want to switch because Windows is slowly getting more frustrating, and I want to just use Windows for gaming and then the normal stuff in Ubuntu.


Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it.  **Is this still true?**

I'm fairly well versed in computers, but I just find the manual config stuff very tedious and awkward.  So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.  

How do I change it to that resolution without having to poke around in config files?

you can try sudo dpkg-reconfigure xserver... I think that's the right command. I'm not on my machine and I usually just straight edit /etc/X11/xorg.conf

if you want help, could you post an output of /etc/X11/xorg.conf to this thread? I may be able to help you deal with the resolution problem while I'm at work.

---

### Post by Cypher on 2007-06-11
> **Sarke said:**
> I've tried to make the jump to Linux several time over the past few years.  First Red Hat, then Mandrake, and I've installed Ubuntu maybe 3 times over the past two years.  But each time I feel it's not quite there yet.

Last time it was the web browsing because the flash wasn't working properly, and this time it's something (probably) really simple but I'm still back in Windows as we speak.

I really do want to switch because Windows is slowly getting more frustrating, and I want to just use Windows for gaming and then the normal stuff in Ubuntu.


Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it.  **Is this still true?**

I'm fairly well versed in computers, but I just find the manual config stuff very tedious and awkward.  So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.  

How do I change it to that resolution without having to poke around in config files?
I guess it's a matter of perspective. What you would consider tedious and awkward, I consider extremely fast and efficient. I can do a lot more things, faster and perhaps better through command line utilities then I could ever possibly accomplish with any GUI.

A lot of things can be done with the GUI in hand, but vowing never needing to use the command line will only put you at a disadvantage. And frankly that isn't where you want to be.

As far as the resolution goes, try the "dpkg-reconfigure" command given and if X has properly detected your video card/monitor, it should give you the option. If not, you can always edit the "/etc/X11/xorg.conf" file appropriately..

---

### Post by DBStevens on 2007-06-11
"Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it. Is this still true?"

That all depends on what needs fixing and when it needs to be fixed, just like it really does under any other system I've seen in the last 38 years.

"I'm fairly well versed in computers"

Oh that so?

", but I just find the manual config stuff very tedious and awkward."

Different stokes for different folks I guess.

Selecting options from a clicky menu is wonderfull,  editing the same file the clicky menu tool outputs is horrible.  Just don't ever get caught with unrecognized hardware or a non functioning window manager.

Tell me how do you ever use a word processing program, you can't really point and click your text easily now can you.

"So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.

How do I change it to that resolution without having to poke around in config files?"

Well if your monitor and video adapter are recognized and the card can support the resolution, there are several available point and clicky utilities that will handle the chore of editing those config files for you they are frequently found on Settings or System Settings and named Display or Viedio Settings.   It all depends on the flavor of the window manager you have installed.

---

### Post by igknighted on 2007-06-11
> **Sarke said:**
> I've tried to make the jump to Linux several time over the past few years.  First Red Hat, then Mandrake, and I've installed Ubuntu maybe 3 times over the past two years.  But each time I feel it's not quite there yet.

Last time it was the web browsing because the flash wasn't working properly, and this time it's something (probably) really simple but I'm still back in Windows as we speak.

I really do want to switch because Windows is slowly getting more frustrating, and I want to just use Windows for gaming and then the normal stuff in Ubuntu.


Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it.  **Is this still true?**

I'm fairly well versed in computers, but I just find the manual config stuff very tedious and awkward.  So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.  

How do I change it to that resolution without having to poke around in config files?

If you really want to avoid the CLI, look into openSUSE or Mandriva (or PCLinuxOS or SAM Linux).  Especially OpenSUSE, it has awesome GUI tools for most every task you could need.  The monitor config worked for me where no others would, for example.

---

### Post by malathia on 2007-06-11
> **DBStevens said:**
> "Now, my biggest problem with Linux is that there's still seems to be the need to use the command line and manually edit config files if you want to do anything with it. Is this still true?"

That all depends on what needs fixing and when it needs to be fixed, just like it really does under any other system I've seen in the last 38 years.

"I'm fairly well versed in computers"

Oh that so?

", but I just find the manual config stuff very tedious and awkward."

Different stokes for different folks I guess.

Selecting options from a clicky menu is wonderfull,  editing the same file the clicky menu tool outputs is horrible.  Just don't ever get caught with unrecognized hardware or a non functioning window manager.

Tell me how do you ever use a word processing program, you can't really point and click your text easily now can you.

"So, getting to my problem, which is that Ubuntu just gives me the standard SVGA, XGA, etc resolutions while my monitor is a 1680 x 1050 widescreen.

How do I change it to that resolution without having to poke around in config files?"

Well if your monitor and video adapter are recognized and the card can support the resolution, there are several available point and clicky utilities that will handle the chore of editing those config files for you they are frequently found on Settings or System Settings and named Display or Viedio Settings.   It all depends on the flavor of the window manager you have installed.


don't you think this was a little over the line? Some people don't want to deal with CLIs and config editing. I thought the purpose of Linux was ideally to get to a point that would allow all users to have the experience that THEY want, including point-clicky operability?

No reason to be so disparaging. Different strokes for... you get the point. No reason to be so hostile about it.

---

### Post by jimrz on 2007-06-11
most everything can be done through gui interfaces and more and more of this is coming on with each new release.

 the reason that you see so many cli references on these forums is that it is simply more accurate to post that way. with all the various window managers and apps that are available, you frequently do not know exactly what the questioner is using. even when you do it may be different from what the responder is most familiar with. it only makes sense that, since the cli instructions will work regardless of the window manager etc, it is more accurate to post solutions in that manner. face to face saying "click there then ..." is ok, but here it leaves to big an opportunity tu inadvertantly mess somebody up.

---

### Post by DBStevens on 2007-06-11
malathia,

It ain't there yet on any system.   

Wanting it to be there doesn't make it any closer.   

People who want it there have a platform to start from, however most of those people are too busy whining instead of doing it to get the job done.

From what I've seen over the years most folks do just fine editing files be they configuration files or letters.

When your favorite tool has bit rot fever and for some reason doesn't work, it is only prudent to have other means in your tool kit.

---

### Post by steveneddy on 2007-06-11
I just learned to go with the flow. I learned the CLI commands that I find most useful to me and I just CP the rest. It's really not that hard. I was the point/click king until I learned how powerful the CLI was.

I guess I have two points of advice.

1. When going to a new computing environment, don't complain that it's not like the last one you used that may have been much different than the one you are trying to learn how to use. Just accept that this the way that it is and if you find an easier way, cool - use it.

2. If you aren't happy with any operating system, go with the one that you feel most comfortable with. It's just an operating system, for goodness sakes.

My two cents.

---

### Post by Sarke on 2007-06-11
> **steveneddy said:**
> 
1. When going to a new computing environment, don't complain that it's not like the last one you used that may have been much different than the one you are trying to learn how to use. Just accept that this the way that it is and if you find an easier way, cool - use it.

I'm not complaining that it's not like my last one, I'm simply asking if it can do what I want; if not then it's not for me.  Something as simple as changing the resolution to my monitor's native resolution should be straight forward IMO (still no straight forward answer to that btw).  


Some people are mechanics, and they can fix most things with their car when there is a problem, and they can tune it to give the best performance.  Like most people though, I don't have time to (or want to) learn all that stuff, I just want to drive it.  I thought Ubuntu was the desktop alternative, but it looks like it's still not there.

Don't get me wrong, I can look up the sudo stuff, and I remember doing the custom resolution xorg.conf edit last year sometime (during one of those installs), and really, it's not that hard.  My point is though that it seems that's just how Ubuntu and Linux works, and I don't want to spend time having to look up CLI commands etc.


Basically, I wanted to see if I missed something obvious or not; I guess not.  Thanks for your time.



EDIT:  I wish to re-iterate, I'm not complaining, just asking.  Seems like a very fine line between asking and being "too busy whining"...

---

### Post by lazyart on 2007-06-11
You'll need to reconfigure X and perhaps tell it manually the resolutions you wish to use.

The command for that is```
sudo dpkg-reconfigure xserver-xorg
```

Blast thru it but when it gets to the section with the resolutions tick the higher resolution boxes as well.

If you have the nvidia driver installed already, skip all of this and just enter```
nvidia-settings
```You can set resolutions from there (and it's GUI).

Linux is deep rooted in the command line and it's not gonna change anytime soon.  I'm from the era where everything was command line so I do okay with it.  Just know that at the command line, hitting the up and down arrow keys will scroll through everything you've ever entered (or it seems that way).  So if you need to recall a command you typed yesterday, or last week, it will be there.

---

### Post by steveneddy on 2007-06-11
> **Sarke said:**
> I'm not complaining that it's not like my last one, I'm simply asking if it can do what I want; if not then it's not for me.  Something as simple as changing the resolution to my monitor's native resolution should be straight forward IMO (still no straight forward answer to that btw).  


Some people are mechanics, and they can fix most things with their car when there is a problem, and they can tune it to give the best performance.  Like most people though, I don't have time to (or want to) learn all that stuff, I just want to drive it.  I thought Ubuntu was the desktop alternative, but it looks like it's still not there.

Don't get me wrong, I can look up the sudo stuff, and I remember doing the custom resolution xorg.conf edit last year sometime (during one of those installs), and really, it's not that hard.  My point is though that it seems that's just how Ubuntu and Linux works, and I don't want to spend time having to look up CLI commands etc.


Basically, I wanted to see if I missed something obvious or not; I guess not.  Thanks for your time.



EDIT:  I wish to re-iterate, I'm not complaining, just asking.  Seems like a very fine line between asking and being "too busy whining"...

have you tried - I know this a command line thing - but it pulls up a GUI - at least if you are running nVidia graphics

```
gksudo nvidia-settings
```

---

### Post by steveneddy on 2007-06-11
And asking in the forums or even searching the forums is a great tool

You may also[ look here]("http://doc.gwos.org/index.php/Main_Page")

---

