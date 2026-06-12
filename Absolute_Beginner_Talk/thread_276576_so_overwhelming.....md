---
title: "so overwhelming...."
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by weird_c00kie on 2006-10-13
i first installed ubuntu last week (or maybe the week before that) and i've had to reinstall it 3 times so far

the first time was while i was trying to get glx/compiz to work and i somehow corrupted the visual interface
the second time i just turned the computer off, and then when i turned it back on, the interface was gone once again

in frustration, i formatted the drive again and installed fedora core on it. the installation went on without a hitch and at the end, when asked, i rebooted. that's when it all fell apart.

some 'GRUB' thing i'd never heard of before would come up everytime i tried to boot off my other drive with Windows XP on it, quoting "Error 15".
infuriated, i wrestled with my second drive (the linux one) for several hours until it finally allowed me to reinstall ubuntu on it. i spent all of yesterday doing all the updates again and trying to get things to work.

i got wine working, i got automatix working, i got realplayer working, and the list goes on.


today, i spent most of the day trying to work out how to fix that grub error thing. after trying several guides, all of which resulted to... well... nothing, i decided i'd back up everything i needed from my XP drive, format it and then reinstall windows
and that's where i ran into MORE problems!

if i back my stuff up on the linux drive, then obviously windows is not going to see it. so i thought "phew! good thing i have that 3rd external drive!" but can i write stuff on it? NOOOOOOOOO, it's read-only.
so i went through those ntfs-mounting guides again and everything seemed to be doing fine, but the drive is still read-only.

so i thought.... screw this! i'll just burn it onto dvd.
but can i do that? NOOOOOOOOO!
gnomebaker decides to be evil to me as well ([http://www.ubuntuforums.org/showpost.php?p=1612019&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1612019&postcount=12))

everywhere i turn, i go from one brick wall to another. it's just so overwhelming....

last night i was up until 3am trying to make an rvmb file work. today when i finally sat down to play it, it was all choppy and crap... so i spent another hour or two trying to find ways to convert it into a different format. guess what i discovered! those programs are a lot easier to find for windows than for linux! but can i use windows? nooooooooooo, grub doesn't want to let me

... i think i'm done now. i'll just go back to what i was doing before..

[CENTER]====> ](*,) ](*,) ](*,) ](*,) ](*,) <====[/CENTER]

---

### Post by meborc on 2006-10-13
well... i'm sorry you have experienced some freeky s*it... i can only give advice on one thing... that is, your windows ntfs CAN read and write to ext3 fileformat in linux... you just need to install a driver which you can find by google'ing ([http://www.fs-driver.org/)](http://www.fs-driver.org/))... hope you are not yet giving up... the 2 hd setup is a bit more complicated as you need to set the grub to the right place... i can't help you more as i have never needed to look more into it... BUT the interface not coming up after reboot... you probably need to reconfigure your xserver after installing new videdrivers... you can do it by ```
sudo dpkg-reconfigure xserver-xorg
```...

---

### Post by weird_c00kie on 2006-10-13
hey meborc, thanks for that. i'll definitely look into that driver thing.

i had a feeling there would be a way to fix the GUI once it got screwed up, but given my 0 knowledge of the terminal and of linux in general, it was a bit hard :p

---

### Post by meborc on 2006-10-13
no problem... we are here to support :) ... the fact that you loose the gui after video driver install is pretty normal (unfortunately) the xserver just needs a bit of tinkering... after running the reconfigure command you will be asked a series of questions regarding your setup... if you don't know what to chose, just leave the default value.. the important bits are the video driver, that should be nvidia (not nv) and the resolutions... just mark the ones you need to use... and let us know how it went ;)

---

### Post by xyz on 2006-10-13
About Grub Error 15:
[http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap4](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap4)

---

### Post by TheWizzard on 2006-10-13
*nix systems like linux are completely different from ms-windows. i would advice you to understand the basics of linux before you play around with stuff like compiz. it is your impatience that put you in the trouble you described. 
if you ever want to give ubuntu another try: 
- install the x86 version 
- read howto's 
- be patient

---

### Post by BLTicklemonster on 2006-10-13
You are to be commended for diving into a new operating system head first and taking on so much, but try to slow it down a wee bit and take things a wee bit slower?

---

### Post by weird_c00kie on 2006-10-13
the x86 version, as in, not the x86_64 version?
isn't that a waste of a cpu though?

i won't refute your statement though; impatience does get the best of me from time to time :p
it's how i learn most of the time though hehehe crash, burn, analyse, move on :)

i've been doing a lot of reading. i've learnt now to search the forums here before i do anything or install anything new heheheh


thanks again to meborc and to xyz for the link :D

---

### Post by weird_c00kie on 2006-10-13
> **BLTicklemonster said:**
> You are to be commended for diving into a new operating system head first and taking on so much, but try to slow it down a wee bit and take things a wee bit slower?

hehehe i would've loved to do that, but:
#1 when i start something new, i exploit the energy burst that goes into it before it runs out and try to learn/achieve as much as i can during that period of time

#2 once my windows drive was out, i had no choice but to spend extra time on setting linux up so i wouldn't be left without a computer :p

---

### Post by TheWizzard on 2006-10-13
> the x86 version, as in, not the x86_64 version?
isn't that a waste of a cpu though?

using the 32 bit version is indeed a waste of cpu. but you'll only notice the difference if you perform heavy tasks like video editing. using the 32 bit version saves you a lot of trouble, on the other hand. 

> 
i won't refute your statement though; impatience does get the best of me from time to time :p
it's how i learn most of the time though hehehe crash, burn, analyse, move on :)

in that situation i would advice you to use a crash-pad. 
to save yourself some time after the next re-install, burn the deb-files in /var/cache/apt/archives to a cd. 

to find software:
- active the universe repo's. and some others. check the unofficial dapper guide.
- use synaptic (or another package manager) to install your programms. 

cheers

---

### Post by gn2 on 2006-10-13
Have you read this?

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by weird_c00kie on 2006-10-13
> **TheWizzard said:**
> using the 32 bit version is indeed a waste of cpu. but you'll only notice the difference if you perform heavy tasks like video editing. using the 32 bit version saves you a lot of trouble, on the other hand. 

buying a dual core 64bit processor was such a bad move.... i've been regretting it since the first time a game went haywire because of it :p
alas, i'm not quite keen on spending another sleepless night or two setting ubuntu up again after a 32bit installation :p

> **TheWizzard said:**
> 
in that situation i would advice you to use a crash-pad. 
to save yourself some time after the next re-install, burn the deb-files in /var/cache/apt/archives to a cd. 

to find software:
- active the universe repo's. and some others. check the unofficial dapper guide.
- use synaptic (or another package manager) to install your programms. 

cheers

oooo, thanks for that directory path. 500mb+ of goodies sittiing in there :)

and yeah, synaptic is what i mostly use when i know what i'm looking for. most of the time though i'm just copying and pasting lines from How-Tos into the terminal and acquiring stuff that way :p


thanks again :)

---

### Post by TheWizzard on 2006-10-13
> oooo, thanks for that directory path. 500mb+ of goodies sittiing in there 
that's where everything you download with synaptic goes.

---

### Post by weird_c00kie on 2006-10-13
OHHHHHHHH

all the magical little things you learn from whining....... :)

---

### Post by Rhubarb on 2006-10-13
> **weird_c00kie said:**
> the x86 version, as in, not the x86_64 version?
isn't that a waste of a cpu though?
It is but a small waste of a cpu, 32bit won't slow it down too much.
But, as your cpu has two cores, make sure you install linux-686-smp .
- Could be linux-k7-smp, have a look for kernel and smp in the forums here.  This made a HUGE difference on my dual core machine at home.

Once you feel reasonably confident with 32bit ubuntu (ie you understand simple commands in the terminal, like cp, nano, rm, mv, cd, and man), then when you're feeling enthusiastic jump and plough straight into 64bit.

And more importantly: have fun learning it all!

---

### Post by weird_c00kie on 2006-10-13
how about this? next time i corrupt ubuntu and have to reinstall, i'll give the 32bit version a try heheh
if i don't manage to mess it up again and you guys survive the onslaught of questions i throw, i'll stay with the 64bit version :)

who knows, maybe by the time my machine becomes obsolete there will actually be some use for dual-core 64-bit processors :p

---

### Post by weird_c00kie on 2006-10-14
well, i've concluded on my action plan

1. back external drive up on the linux drive
2. format external drive into fat32
3. back windows drive up onto fat32 drive
4. format windows drive and reinstall windows
4a. if need be, if grub is going to give me trouble, i'll unplug the linux drive, install windows, and then plug it back in, following [gn2's guide]("http://www.ubuntuforums.org/showthread.php?t=275728")
5. restore data from fat32 drive onto windows drive
6. restore data from linux drive back onto fat32 drive

oh and:
7-10. pray nothing goes wrong :p

---

### Post by weird_c00kie on 2006-10-16
i've finally completed the backing up and XP reinstallation process... it went well enough. XP runs now.

i unplugged the master linux drive and left the XP one plugged in as the slave. i formatted it and installed windows on it and then plugged the linux one back in

until i fix the grub file, if i want to boot into windows, all i need to do is change the hard disk boot sequence from the bios

unfortunately, once again, i managed to screw up the visual interface in ubuntu....

i'll try the line
> sudo dpkg-reconfigure xserver-xorg
someone offered on the first page and see what happens..... wish me luck :p

---

### Post by Josey on 2006-10-16
I've broke my gui a few times also.
Having the alternate xfce desktop enviroment helps alot in these situations

---

### Post by junglepeanut on 2006-10-16
Wishing luck

---

### Post by weird_c00kie on 2006-10-16
what's an xfce desktop?

i've just wiped my linux drive once again. i corrupted the hard disk when i tried resizing my partitions to squeeze a fat32 out of it.... bad move :p

decided to try a slightly different setup....


on the 320gb drive, i'll have 2 partitions
118gb one for linux and a 180gb fat32 one on which i'll store files that both linux and windows will be accessing (movie files, music, etc)
and then on the 200gb windows drive it'll just be... well, just the windows drive.

i was thinking of maybe putting both operating systems on the same drive and keeping the 320gb one for data, but.... i think i've had enough formatting and reinstalling during the last 2 weeks... i certainly don't want to be reinstalling XP again :p
i grew to appreciate ubuntu so much more after i had to reinstall XP... with ubuntu, just about everything works as soon as the OS is installed... with XP, network card didn't work, graphics card didn't work, monitor wasn't recognised, printer was unknown, etc etc

hurray for linux

---

### Post by junglepeanut on 2006-10-16
xfce=lightweight desktop, just a little heavier than say fluxbox or icewm. I actually use it more than gnome and kde with a one year old laptop.

---

### Post by TheWizzard on 2006-10-16
> i grew to appreciate ubuntu so much more after i had to reinstall XP:biggrin: 
good to hear you're starting to enjoy the benefits of linux!

---

### Post by weird_c00kie on 2006-10-18
i am indeed, but right now i'm annoyed at it again because wine isn't working :p

---

### Post by weird_c00kie on 2006-10-18
> **junglepeanut said:**
> xfce=lightweight desktop, just a little heavier than say fluxbox or icewm. I actually use it more than gnome and kde with a one year old laptop.

fluxbox? icewm? :confused: 

you're talking to a complete n00b here heheh

---

