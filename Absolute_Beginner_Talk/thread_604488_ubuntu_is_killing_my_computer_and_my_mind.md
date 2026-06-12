---
title: "ubuntu is killing my computer and my mind"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by omnicorp on 2007-11-06
hi folks, i love what ya'll are trying to do here, but ubuntu just isn't working out for me. i installed the latest version a couple days ago and other than some configuration for my wireless adapter it seemed to run pretty smooth at first. since then its been all down hill to the point where i just want to start over and try something different. in my endless searching of online forums trying to get help to all the problems i've been having with ubuntu i've come across the jacklab distro, and i think i would like to try it as audio is my main application anyways. who knows, maybe i'll have better luck with that one. anyway, i've been trying to make that switch for about 30hrs now to no avail. the online support community for jacklab and opensuse (which its based on i understand) isn't nearly as robust as this one, so in desperation i've returned here hoping some charitable soul will help me with this even though i'm trying to migrate, at least for the time being, away from ubuntu. my main problem is that i'm totally new to linux and most of the help on this and other forums seems to come in the form of command line/programmer type stuff and i can't even figure out how it relates to what i see on my screen. i don't usually understand what i'm being told to do or even how to do it. i realize i've brought this on myself by trying to install ubuntu without understanding anything about linux or how it works, but as i wiped my whole hard drive when i installed ubuntu and have no windows installation cds, there's no going back now. and i don't really want to anyway - i want to learn all the stuff about linux - i just need a basically operable computer to facilitate this learning. so...  i realize i'm asking for some major handholding here, but if anyone can spare the time, i desperately need step by step instructions on how to switch from ubuntu to jacklab or opensuse 10.2 that don't involve any of the programmer stuff, or if that's unavoidable, explains exactly how i execute the steps involved starting from the regular ubuntu desktop. my circumstances are as such:

i have:  a compaq laptop about a year and a half old with windows xp and an amd processor running at 1.8ghz with a 40gb hd. it has a cd-r/dvd rom drive, but no dvd burner. this is the computer i installed ubuntu 7.1 on and now want to install jacklab on. 

my resources:  your wisdom, blank cdr and dvdr media, roomate's newer model windows desktop with dvd burner, 2gb usb jumpdrive that works/worked with ubuntu except that now a file i thought was the install dvd for jacklab called liveDVD-JAD-beta2 is taking up 1.6 of the 2gb and i can find no way to delete this file or otherwise remove it from my usb stick. (opening the trash or trying to move something to it in ubuntu freezes everything except my mouse cursor) 

so this will take a true samaritan i understand, but if anyone can help, my gratitude would be immense. cheers.

---

### Post by LowSky on 2007-11-06
JACK is availible in the repositories, so you dont need to switch to openSuse.

Go to add/remove and type jack and see what pops up.

What are the issues you are having, other than command line, Sad to say you will need to at least learn to cut and paste the commands. command lines can be you friend when the GUI fails.

---

### Post by kevinatkins on 2007-11-06
Hi,

Sounds like you're struggling a bit there. I don't know anything about Jacklab, but I am a bit familiar with OpenSuse and it's a nice product. I prefer Ubuntu personally, and find it suits my needs, Certainly OpenSuse has better configuration tools in the shape of the excellent YaST, and it's quite a 'polished' system which perhaps is easier for users migrating from Windows, ut software management in OpenSuse isn't a patch on Ubuntu - believe me, in five years of using Linux, the Debian package management system is the best in the business....

Anyway, enough of that... Could you try and explain what problems you've been having? It might be possible to rescue your Ubuntu installation, from which you can then install Ubuntu Studio, which may fit your audio needs perfectly... If there are really odd problems, it's possible that other Linux distributions will stumble, too, so we need to determine exactly what's going on..

cheers

kevin.

---

### Post by svalding on 2007-11-06
i'm afraid that if you are switching to linux, no matter what distro, learning the command line will be inevitable. Once you get a basic understanding, how to move around inside the terminal for instance, things will get easier and easier, until one day you are writing advanced shell scripts that Windows couldn't even fathom doing!

---

### Post by omnicorp on 2007-11-06
at this point i want to switch to jacklab/opensuse both for the collection of audio software besides jack that it includes and also in hopes of avoiding the myriad problems i've been having to with ubuntu. i won't try enumerate them in detail here as i've spent literally days online scouring this forum for answers and i'm gaining problems way faster than i'm solving them. i've already made the decision to switch if that's ok, but really do need the help i mentioned above. i do understand how to cut and paste and i do hope the command line stuff can be my friend and ally in the future... again, i just really need my computer to work while i'm busy mastering linux.

---

### Post by kevinatkins on 2007-11-06
OK.. so the issue then is how to get that massive file off your usb stick and on to disk...

I think you're going to need to find a machine with a DVD burner with which to transfer the Jacklab installer image file (the big one you downloaded) onto DVD.... then you should be able to boot from the DVD and wipe Ubuntu and install Jacklab..

---

### Post by bsh on 2007-11-06
when you want to master linux, you must start with the command line... even if modern linux distros try to help people with nice graphical tools, these are nearly not perfect yet and they don't cover everything, so you can't live without the command line (yet)
i also believe that ubuntu is the most user friendly (ie least command line stuff for beginners), so i'm afraid if you move to suse, the knowing of the command line stuff will be even more important.

---

### Post by StooJ on 2007-11-06
People give commands for you to cut & paste because it's the easiest and quickest way to accomplish what you're asking for.

I understand that you'd like to know what you're doing when you paste in commands - I've felt the same way when I've been recommended a command line to run without any explanation, but because I too wanted to learn my way around I went and read up on what each command meant when I was given it.

It sounds like you don't have the time just now.

So, why bother just now? Give the people here a problem, and someone is bound to give you a command line to solve it. Run the line, and live happily ever after (unless it doesn't work. If it doesn't work, copy & the results and post them in your thread. Someone will sort out your command line and give you something else to try).

There are probably ways to accomplish most things via a GUI in Ubunutu, but asking someone to paste ```
sudo apt-get update && sudo apt-get install mozilla-thunderbird
``` is far far easier than saying "OK, is your menu bar on the bottom of the screen? Click on Add/Remove. Wait for it to update and then type "Thunderbird" into the search bar at the top. Press Return. Thunderbird will appear on the right hand side, and if double click it, a tick will appear. Once that happens, click OK. Then Click Apply.

That was for something very very straightforward, but you can see walking someone through a GUI is much more involved than walking someone through pasting a command into the terminal.

It also has a lot more room for error.

I appreciate that you probably won't need such a step-by-step handholding, but having worked for years in support of one kind or another, I've learned never to over-estimate abilities, just in case you might be speaking to someone who really doesn't know what you're talking about. I had a phone call last week asking why a (scripted) network backup wasn't working. It turned out that they were switching off the server before they tried to run the backup. :)

Sorry for this overly general post, but I wanted to reassure you a bit. End users will work with Ubuntu day after day, almost exclusively without touching of seeing a terminal. However, for a quick "get something working properly" there is no equal.

As an illustration, I use OS X fairly often as well, and after discovering the bash terminal, I sometimes nip into it to move a bunch of files, or back up stuff, or half a dozen other things. No one ever says you need to be a programmer to use OS X, even though the terminal is a great way to provide definitive support that isn't affected by OS setups.

Incidentally, why do people feel the need to "master" linux? I mean, brilliant if they do, spread the word and all that, but people just need to use Windows, but they need to master linux? You don't *need* to understand the terminal to use Ubuntu day-to-day.

*Anyway*, back to the problem at hand.

Since your flatmate has a DVD burner, I would plug your USB dongle into his machine and burn the livedisk from there.

Does your flatmate have any CD/DVD burning software installed on his machine?

Once that's done you can backup any files from your Ubuntu installation that you want to keep. Do you have a seperate Home partition at the moment? (And it's command line time!)

Please post the results of ```
sudo fdisk -l
```

(This shows a list on all the hard drives and hard drive partitions on your computer. The -l part is just the bit that tells fdisk to list the results)

---

### Post by smotsie on 2007-11-06
First, let me preface this by saying I think you really would be much better off with Ubuntu, simply because it really does make life easier and the community support is awesome. I have had a brief look at JackLab, and it looks good, for experienced Linuxers! For someone wanting to learn it lacks the basic howto get started stuff. However, accepting you want to move...

As you said you have a friend with a DVD burner, that's the place to start. MS Windows may allow you to move / delete the 1.6GB file if you are careful - clicking on it with almost any OS is likely to make the system try to open it. You need to select it and then either delete it, or move it  to a hard disk. Once there, you need a DVD burning app which will open it (Nero perhaps?) as it should be a DVD disk image of the ISO type. If you can get that far, and persuade some windows software to burn a DVD, and if that is successful, then you should be able to boot from that DVD. That will run the Linux as a "LIVE" system, which means it all runs from the DVD and not from your hard disk. From there, you can test that things work, but it will run slowly (DVD's are MUCH slower than hard disk drives)

If you want to install to hard disk, there should be a way to do that from the live DVD, however I could not find a howto on the jacklab site (search time 5 minutes, so not exhaustive). They do have an installer DVD image available which might be a better place to start - if you can download and burn that it should walk you through the process of installing a complete system.

Best of luck, and maybe you could start some posts on the jacklab forum ( [http://forum.jacklab.net/](http://forum.jacklab.net/) )

Cheers

Smotsie

---

