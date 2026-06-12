---
title: "What do you think is running out first?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-22
Alright, I have this old *** system which is my daily.  Please refrain all your comment about how sucky my system - I put it together when it was all brand new, which makes it like 5 or 6 years old.

System:
P4 3.0Ghz hypterthread
Abit IC7-G mobo
PNY(Nvidia??) GeForce 7600GS (512mb)
1 GB .. I think it's DDR1 ram..think it's running at 800 (that's a lot of "think" - I know)

Right, so when playing a 720p movie, sometimes it gets blotchy (skips) if doing anything else.  My friend claims it's my piece of **** processor, but when I use the "top" command it says only 50-60% is being used, it straightens out if it's the only thing running - mostly - it still shakes a tiny bit little every 10m or so).

I feel it's my video card's drivers as when I'm in windows it plays fine - and I'm using the Ubuntu generic drivers (and I don't really like them).  GLXGears rates my video as so:
```
$ glxgears -display
14797 frames in 5.0 seconds = 2959.257 FPS
14848 frames in 5.0 seconds = 2969.199 FPS
14760 frames in 5.0 seconds = 2951.851 FPS
14837 frames in 5.0 seconds = 2967.399 FPS
14806 frames in 5.0 seconds = 2961.128 FPS
13501 frames in 5.0 seconds = 2700.114 FPS
12606 frames in 5.0 seconds = 2521.164 FPS
11007 frames in 5.0 seconds = 2200.500 FPS
14112 frames in 5.0 seconds = 2821.893 FPS
14854 frames in 5.0 seconds = 2970.378 FPS
14514 frames in 5.0 seconds = 2902.762 FPS
X connection to :0.0 broken (explicit kill or server shutdown)

```

I got an itching it's the drivers though the load seems to point otherwise, so we got drivers, video card, ram, and processor, which one you think is topping out and causing this?

EDIT:
PS:  I forgot to tell ya, when it's under hard load (ie downloading something from my ftp server) programs load very slow (like a 15-20 second lag time before it even opens something like VLC or Konsole) and if it does sometimes it quickly stops responding (grays out) for 10 seconds or so.

---

### Post by toa on 2008-02-22
Your big shot is the 'Drivers' , for having the same hardware working properly in Windows is your proof.

And Ubuntu is a good hardware utilizer same as windows, so no doubgt its your drivers, which im sure you have some settings to fix specially when it comes to nVidia Cards.

Other tweaks on ubuntu might help to increase performance, buts thats another stage.

---

### Post by Whiffle on 2008-02-22
Video drivers.

Considering I've managed to play 720p on a 1.6GHz (oc'd to 2.23) P4, with that video card, and 1 gb ram...  I didn't know these were considered old.  Oh well, mine works great.

---

### Post by Malta paul on 2008-02-22
Hi,
I have a smiler computer setup to you and everything runs OK and fast.
Have you tried the latest Nvidia driver? I used Envy to get the latest. 
You could also disable any eye candy you may have enabled.
Good luck:)

---

### Post by Syndacate on 2008-02-22
> **Malta paul said:**
> Hi,
I have a smiler computer setup to you and everything runs OK and fast.
Have you tried the latest Nvidia driver? I used Envy to get the latest. 
You could also disable any eye candy you may have enabled.
Good luck:)

You mean compiz?

Yeah, sure I'll try disabling that - though I didn't know it was very active when you're not opening windows and such.

Like I said, if it is the drivers, it seems pretty iffy that it's only happening (or happening 20x more) when the computer's under load - so it's quite confusing.

I've been fighting with the drivers for this thing since I got it and I'm starting to get real pissy about it.

I'll try disabling my restricted drivers and using the ones with Envy and see if anything changes.

Though you guys feel it definitely is a driver issue?

I want to say driver issue so badly, but the way it lags more based on load points otherwise.

---

### Post by Syndacate on 2008-02-23
Here's info from the **glxgears -info** from using the Envy drivers

```

11911 frames in 5.0 seconds = 2382.088 FPS
6322 frames in 6.9 seconds = 916.587 FPS
12121 frames in 5.0 seconds = 2423.563 FPS
12042 frames in 5.0 seconds = 2408.381 FPS
12115 frames in 5.0 seconds = 2422.837 FPS
12153 frames in 5.0 seconds = 2430.489 FPS
12163 frames in 5.0 seconds = 2432.412 FPS
X connection to :0.0 broken (explicit kill or server shutdown

```

Right, so I'm going to go out on a limb here and say the restricted drivers are functioning better than the envy drivers - as they were hitting about 2900, or is the frames per second not really a direct clock of the video card itself.

Anybody have any other ideas?  It really is a weird problem, the whole way it happens under load makes me believe it's a CPU issue - but the CPU is reading ~60% under top (I don't know how accurate that is), does anybody think it's the ram running out or low?

EDIT:
My friend claims like the word of god that it's my CPU, and it's simply an old processor with lots of hours on it and it's functioning like an old man, so even though it's only at 60%, it's topping out there.

Now this guy talks out of his *** a lot so i don't know if that's accurate or not :-\

---

### Post by JoshuaRL on 2008-02-23
Instead of Envy, go to the Nvidia site and download the driver for your card.  Then run it from recovery mode.  It'll make sure to install the newest one, and configure your kernal modules correctly for your system.  Nvidia does a great job making drivers for linux.

---

### Post by Syndacate on 2008-02-24
> **JoshuaRL said:**
> Instead of Envy, go to the Nvidia site and download the driver for your card.  Then run it from recovery mode.  It'll make sure to install the newest one, and configure your kernal modules correctly for your system.  Nvidia does a great job making drivers for linux.

A)  What do you mean by run it from recovery mode?
B)  What is recovery mode?

C)  Sometimes peoples' definition of "easy" on this forum is slightly skewed, though if you tell me what recovery mode is I'd be willing to give it a shot.

---

### Post by JPotter on 2008-02-24
why would anyone make fun of that computer?? 

A. everything in it is better than I have.
B. my computer still plays anything I want it to.

Keep in mind, while computers have gotten faster, they haven't changed a whole lot since the P4 (when speaking about single threaded processes)

Qualification: yes they have changed, just not as fast as they did in the old days.

My Computer:
AMD Athlon XP 2500+ @ 2193MHz
1Gb PC3200 @ 200MHz
ATI Radeon 9800 Pro
GIGABYTE 7N400-L mobo

---

### Post by Syndacate on 2008-02-24
> **JPotter said:**
> why would anyone make fun of that computer?? 

A. everything in it is better than I have.
B. my computer still plays anything I want it to.

Keep in mind, while computers have gotten faster, they haven't changed a whole lot since the P4 (when speaking about single threaded processes)

Qualification: yes they have changed, just not as fast as they did in the old days.

My Computer:
AMD Athlon XP 2500+ @ 2193MHz
1Gb PC3200 @ 200MHz
ATI Radeon 9800 Pro
GIGABYTE 7N400-L mobo

Dude, I go to the **Rochester Institute of Technology** - I'm ALWAYS taking heat for how unbearably slow and archaic my computer is.  You have to remember that like 75% of the people here have the latest and greatest ****.  I saw a mac air here like 3 days after it was unveiled, it's pathetic.

That's why I use my laptop (my 1.61 Ghz TL-60 64x2 with 2GB of DDR2) for XP and gaming.

---

### Post by Mike'sHardLinux on 2008-02-24
> **Syndacate said:**
> 
EDIT:
My friend claims like the word of god that it's my CPU, and it's simply an old processor with lots of hours on it and it's functioning like an old man, so even though it's only at 60%, it's topping out there.

Now this guy talks out of his *** a lot so i don't know if that's accurate or not :-\

It is definitely NOT accurate. :-) I don't think electronics wear out *in that way.* If the hours were really taking their toll on your processor, you would most likely be getting tons of errors, lockups/freezes, or it just would not even work at all.

That's actually a pretty good processor. While it isn't as fast as more modern processors, it should be able to handle current software without any problems. You know, there's plenty of Ubuntu users with P2 and P3 class systems. With that said, I also know that decoding HD video really does eat up some cpu. I have a friend with an Athlon 2600+, 1GB, 9800 Pro, and when he watches those HD trailers from apple.com, they are choppy.

You may want to do some of the more basic troubleshooting on your system like running memtest, and checking your temps.

> EDIT:
PS: I forgot to tell ya, when it's under hard load (ie downloading something from my ftp server) programs load very slow (like a 15-20 second lag time before it even opens something like VLC or Konsole) and if it does sometimes it quickly stops responding (grays out) for 10 seconds or so.

I would not consider downloading via FTP to be a hard load, even on an older computer much older than yours. Don't forget that when loading a program, the bottleneck on a modern system is likely to be the hard drive and possibly the amount of RAM a person has (1GB should be plenty, though). Downloading a file from FTP also is using the hard drive since you are copying files to it.

I tend to agree with toa, that it is the drivers. But while you seem to thinks it is only a performance issue, I think there are also other issues going on...bugs/glitches. I don't know anything about driver development, but it stands to reason that they will focus more energy on good solid drivers for windows. It is quite likely that the drivers they make for Linux will have bugs or performance issues not found in the corresponding windows driver. Of course, that is just my opinion.

What movie are you talking about? Is it a DVD, or a file? Tell us some specifics like what codec is it using? This may give us some more clues. If I can get a hold of the same movie, I will play it and see how it performs on my system.

Also, have you tried disabling Compiz yet? I know for a fact that having Compiz running does affect performance of other programs, even if it doesn't seem "active". It happens to me on all my systems. I used to disable Compiz before playing games.

---

### Post by JoshuaRL on 2008-02-24
> **Syndacate said:**
> A)  What do you mean by run it from recovery mode?
B)  What is recovery mode?

C)  Sometimes peoples' definition of "easy" on this forum is slightly skewed, though if you tell me what recovery mode is I'd be willing to give it a shot.

Not a problem dude, we all start somewhere.

Recovery Mode.  You get it from the Grub menu.  When you see the message on the screen saying Grub Loading, press ESC and get to the Grub Menu.  Then go to the Ubuntu Recovery Mode option.  It will load a GUI-less version of Ubuntu.  A lot of loading info will scroll by and you'll be dumped into the Command Line Interface as root.  Something like:
```

root@yourcomputer-: $ 

```

To run the Nvidia installer from recovery mode, go [here to find it](http://www.nvidia.com/object/linux_display_ia32_169.09.html) and dowload it to your desktop.  Then make sure you **write these steps down exactly** and go into the Recovery mode and do:
```

cd /home/(your user name)/Desktop
sh NVIDIA-Linux-x86-169.09.pkg1.run

```
Where (your user name) is your username, "cd" is Change Directory, and "sh" means to run in a Shell.

A text-based GUI program will come up, and go through all the defaults.

**NOTE:** a warning will come up about you running in runlevel 1 instead of runlevel 3.  I just told it to go ahead and had no problems.  And when it asks to write kernal modules, let it.  It should configure your system for the driver and your card.

---

### Post by zerhacke on 2008-02-24
> **JoshuaRL said:**
>  "sh" means to run in a Shell..

Untrue.  sh means to run in the SH shell, not the BASH shell which is the default for Ubuntu.

---

### Post by doorknob60 on 2008-02-24
I'd like to say that it's probably not your CPU, because I can have my 2.6 GHZ CPu and my crappy Geforce FX 5200 output videos to the TV and use Firefox on my monitor at the same time with no problem. Did you try playing the video again after updating the drivers with envy? Also you shouln't need to install the drivers from Nvidia manually, because you'll be doing the exact same thing that Envy is doing for the most part.

---

### Post by JoshuaRL on 2008-02-24
> **zerhacke said:**
> Untrue.  sh means to run in the SH shell, not the BASH shell which is the default for Ubuntu.

You're right, I guess i just oversimplified.  Sorry.

> **doorknob60 said:**
> I'd like to say that it's probably not your CPU, because I can have my 2.6 GHZ CPu and my crappy Geforce FX 5200 output videos to the TV and use Firefox on my monitor at the same time with no problem. Did you try playing the video again after updating the drivers with envy? Also you shouln't need to install the drivers from Nvidia manually, because you'll be doing the exact same thing that Envy is doing for the most part.

Envy is great, and it makes things easy.  But if you want to be absolutely sure you have your Nvidia card configured right, installing the Nvidia driver directly is the way to go.

It's not really that hard anyway, and it's a good thing to know how to do.

---

### Post by LaRoza on 2008-02-24
> **zerhacke said:**
> Untrue.  sh means to run in the SH shell, not the BASH shell which is the default for Ubuntu.

Nope, Dash is the default, not Bash. [Dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell")

@OP Your specs are good. Your processor is not bad, in fact, it is a good processor. It is a hot processor, so keep it cool.

---

### Post by lamalex on 2008-02-24
> **JoshuaRL said:**
> You're right, I guess i just oversimplified.  Sorry.



Envy is great, and it makes things easy.  But if you want to be absolutely sure you have your Nvidia card configured right, installing the Nvidia driver directly is the way to go.

It's not really that hard anyway, and it's a good thing to know how to do.

SH is also not a shell, it's a link to whatever the default shell on your system is. so in Ubuntu sh -> dash, some systems sh -> bash, or any other shell, ksh, csh, zsh, the list goes on and on. But this is irrelevant. You also forgot to chmod +x the nvidia installer, if he doesn't do that the script won't be executable.

---

### Post by JoshuaRL on 2008-02-24
> **Iamalex said:**
> SH is also not a shell, it's a link to whatever the default shell on your system is. so in Ubuntu sh -> dash, some systems sh -> bash, or any other shell, ksh, csh, zsh, the list goes on and on. But this is irrelevant. You also forgot to chmod +x the nvidia installer, if he doesn't do that the script won't be executable.

Okay, you obviously know more about this than I do.  When I followed those exact steps on my computer, I thought everything worked fine.  Do I need to redo it with the chmod?  Does that fix the runlevel error that comes up?

Just to be completely honest, I didn't know that Dash was the default shell, or that "sh" was just a link to whatever shell is default.  But I do now, so thank you LaRoza and Iamalex.

---

### Post by Syndacate on 2008-02-24
> **Mike'sHardLinux]It is definitely NOT accurate.  I don't think electronics wear out in that way. If the hours were really taking their toll on your processor, you would most likely be getting tons of errors, lockups/freezes, or it just would not even work at all.

That's actually a pretty good processor. While it isn't as fast as more modern processors, it should be able to handle current software without any problems. You know, there's plenty of Ubuntu users with P2 and P3 class systems. With that said, I also know that decoding HD video really does eat up some cpu. I have a friend with an Athlon 2600+, 1GB, 9800 Pro, and when he watches those HD trailers from apple.com, they are choppy.

You may want to do some of the more basic troubleshooting on your system like running memtest, and checking your temps.[/quote]

I didn't think it was accurate, especially if top only says ~50-60% use, he often talks out his *** so it doesn't surprise me.

[quote=Mike'sHardLinux]I would not consider downloading via FTP to be a hard load, even on an older computer much older than yours. Don't forget that when loading a program, the bottleneck on a modern system is likely to be the hard drive and possibly the amount of RAM a person has (1GB should be plenty, though). Downloading a file from FTP also is using the hard drive since you are copying files to it.

I tend to agree with toa, that it is the drivers. But while you seem to thinks it is only a performance issue, I think there are also other issues going on...bugs/glitches. I don't know anything about driver development, but it stands to reason that they will focus more energy on good solid drivers for windows. It is quite likely that the drivers they make for Linux will have bugs or performance issues not found in the corresponding windows driver. Of course, that is just my opinion.

What movie are you talking about? Is it a DVD, or a file? Tell us some specifics like what codec is it using? This may give us some more clues. If I can get a hold of the same movie, I will play it and see how it performs on my system.

Also, have you tried disabling Compiz yet? I know for a fact that having Compiz running does affect performance of other programs, even if it doesn't seem "active". It happens to me on all my systems. I used to disable Compiz before playing games.[/quote]

It's not quite FTP, it's DC++.  I don't know why I said that, if I'm FTP'ing something to or from my Windows machine actually has little (if any noticeable) effect on my system speed.

Uhh, as far as the movie goes, I don't know much about it, it's a 720p rip in .avi format - there's a lot of those floating around campus on DC++ hubs....which obviously you can only snag if you have the original version on disc, which I do, of course.  I wouldn't break any of those laws or anything.  This happened with more than one movie.  Most 720p if I'm downloading heavy with DC++ also, and it doesn't happen with regular 700mb .avi rips.  If I'm not heavy downloading it glitch a bit, but nowhere near as much.

No, I haven't tried disabling compiz yet, since I used the envy drivers it's topping out at a lower frames per second, so I didn't even get around to trying that yet, you'll have to forgive my slow response time and slow action (or lack of action) - it's finals week and everything's all twisted up schedule wise :-X.  I'm actually going to go do a project as soon as I finish this :(.

[quote=JoshuaRL]**Not a problem dude, we all start somewhere.**[/quote]

Too bad all linux users don't think that way.  Some claim to be born with the info.

[quote=JoshuaRL]Recovery Mode. You get it from the Grub menu. When you see the message on the screen saying Grub Loading, press ESC and get to the Grub Menu. Then go to the Ubuntu Recovery Mode option. It will load a GUI-less version of Ubuntu. A lot of loading info will scroll by and you'll be dumped into the Command Line Interface as root.[/quote]

Can I access the same "*recovery mode*" by hitting "**<alt> + <F2>**" from my Desktop?

[quote=JoshuaRL]To run the Nvidia installer from recovery mode, go here to find it and dowload it to your desktop. Then make sure you **write these steps down exactly**[/quote]

lol, I'm not that newb, I just wasn't sure what recovery mode was  said:**
> I'd like to say that it's probably not your CPU, because I can have my 2.6 GHZ CPu and my crappy Geforce FX 5200 output videos to the TV and use Firefox on my monitor at the same time with no problem. Did you try playing the video again after updating the drivers with envy? Also you shouln't need to install the drivers from Nvidia manually, because you'll be doing the exact same thing that Envy is doing for the most part.

Yeah, I don't feel like it's the CPU, though it's not like I know a whole lot :|.  Plus the way it's under stress makes it seem like it's a hardware limitation over a driver problem, like CPU or RAM.  I didn't bother trying to play teh video again after updating the drivers with envy, I didn't feel it would be relevant as I was hitting about 500FPS lower with the envy drivers, though I'll try after I post this.  I'm also willing to re-try it doing it manually, as I'm pretty much willing to try a lot to get it to work right.

> **LaRoza]@OP Your specs are good. Your processor is not bad, in fact, it is a good processor. It is a hot processor, so keep it cool.[/quote]

Yeah, I know it's a hot running processor, I never had any problems, but you do gotta look at the facts.  I go to a tech school (RIT), lots of engineering and computer majors, tuitions a ********...it's not uncommon for lots of people to have the newest & greatest stuff.  I mean with room and board it easily goes past the 30k/ yr marker (about 35k).  I take a lot of heat just for running a single core, none-the-less an older P4 3.0...  I like this processor, but a lot of people are going with the core 2 duos and the quad cores and such.  I'm probably going to build another computer over the summer and was thinking about putting a quad core in it, but then I heard they make dual core P4 3.0Ghz and I was all O.O!! - but I don't know.  I like the raw power of a 3.0 opposed to the lighter 1.6's of my laptop, which you can notice it loads slower if it's a single threaded process, but most processes aren't single threaded anymore - except my lame *** java programs  said:**
> ou also forgot to chmod +x the nvidia installer, if he doesn't do that the script won't be executable.

Yeah, i can always change that if it's a problem, but it should still run under *sudo*, no?

I got the basic commands, I'm not that new T_T.

---

### Post by Syndacate on 2008-02-24
I tried installing it manually in recovery mode, it had about 50,000 errors and kicked Ubuntu into low gfx mode.

---

### Post by JoshuaRL on 2008-02-24
Alright, let's try with Iamalex's suggestion:
```

cd /home/(your user name)/Desktop
chmod +x NVIDIA-Linux-x86-169.09.pkg1.run
sh NVIDIA-Linux-x86-169.09.pkg1.run

```

---

### Post by Syndacate on 2008-02-25
> **JoshuaRL said:**
> Alright, let's try with Iamalex's suggestion:
```

cd /home/(your user name)/Desktop
chmod +x NVIDIA-Linux-x86-169.09.pkg1.run
sh NVIDIA-Linux-x86-169.09.pkg1.run

```

I doubt that was the problem.

It gave me errors in the process, of trying to connect the module, it didn't say anything about permission errors.

I sudo sh'ed it, so it shouldn't make a bit of difference.

It asked if I wanted it to search nvidia's FTP for the drivers - then that failed, then it started trying to make the module for my kernel since it couldn't find the right one for my kernel - then that failed as it was looking for files and folders that it couldn't find.  Stupid.

So I went back to Envy - pressed manually install drivers, hit 169.09 and it installed there - so I guess that driver is installed through Envy - doesn't make a difference really, pretty much back to square one.

---

