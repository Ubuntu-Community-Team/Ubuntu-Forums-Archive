---
title: "Linux First Timer"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by DCM101 on 2007-09-15
Hey, I'm a long time Windows user and I wanted to try out Ubuntu. I want to install it, but I want to keep all my windows files. And I want to be able to jump back and forth between Ubuntu and Windows. Is there any way to do this? I've heard about Dual Boot, but I'm not quite sure what that is.

P.S. I've already tried Live CD and I didn't really like it.

---

### Post by graywizard on 2007-09-15
if you did not like the live Cd than why try to install it. I did not like the Live Cd because it was slow and relatively useless; but the real linux Ubuntu when loaded is quite nice and NOT like the live CD.

If you did not like the taste then why order the food?

---

### Post by Irihapeti on 2007-09-15
Dual boot gives you the choice of which OS you want to use, each time you start up.

You say you didn't like the liveCD. What exactly didn't you like about it? What that is may be a deciding factor on whether Ubuntu is for you.

---

### Post by Tyke91 on 2007-09-15
the live cd is like a very slow/default version of ubuntu. 

 to dual boot:

1. Defrag your windows hard drive a few times

2. load the live cd

3. press install

4. when you get to the partitions page of the install, go to manual

5. shrink your windows partiton to create enough space for ubuntu

6. create an extended partition out of that space, and in that partition, create 3 partitions. one should be the root partition (/) one should be the swap partition, and the rest should be the home partition.

7. proceed with installation

8. enjoy.

---

### Post by oilchangeguy on 2007-09-15
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and the live cd runs slow because you're running an operating system from a cd. once installed it'll be faster.

---

### Post by marco123 on 2007-09-15
You could also try the Kubuntu live CD if the UI is the problem?

---

### Post by DCM101 on 2007-09-15
There's no install button to press. The reason I don't like Live CD is because it won't work. I load the CD, I reboot, and nothing happens.

---

### Post by oilchangeguy on 2007-09-15
> **DCM101 said:**
> There's no install button to press. The reason I don't like Live CD is because it won't work. I load the CD, I reboot, and nothing happens.

have you actually tried the cd? once the desktop loads one of the icons is install. uh, click it. and make sure your computer is set to boot from the cd drive first.

---

### Post by DCM101 on 2007-09-15
> **oilchangeguy said:**
> and make sure your computer is set to boot from the cd drive first.

how do I do that?

---

### Post by Celegorm on 2007-09-15
The psychocats installation guide oilchangeguy posted a link to has a section describing how to boot from cd first.

---

### Post by Roaster on 2007-09-15
Just put the cd into your computer and boot it. Press key when asked to. When cd loads and Install icon is on desktop double click and follow directions. Not that difficult. Have fun!

---

### Post by DCM101 on 2007-09-15
I got into the BIOS page but I have no idea on how to set it to boot from cd.

---

### Post by marco123 on 2007-09-15
> **DCM101 said:**
> I got into the BIOS page but I have no idea on how to set it to boot from cd.

There should be an option to set the device boot order.

---

### Post by marco123 on 2007-09-15
In my BIOS it's under Advanced BIOS Options>CD-ROM Boot Priority, if that helps?

---

### Post by DCM101 on 2007-09-15
So I set it to boot from CD, but nothing happened. The screen just stays black for a few seconds with a blinking underscore in the top left corner and then windows boots up.

---

### Post by Roaster on 2007-09-15
If you are running Windows XP the default Bios settings are: floppy, cd rom, and 1st hard drive in that order. Just put the Ubuntu cd in the cd drive and reboot when it says, press any key to boot from cd", just press any key. Once the cd is loaded and there is an install icon on your desktop double click it and GO! It just gets better:)!

---

### Post by DCM101 on 2007-09-15
It doesn't say to press any key to boot from cd. Just a blinking underscore.

---

### Post by sloggerkhan on 2007-09-15
Sometimes people burn a copy of an image instead of burning the iso properly...

---

### Post by DCM101 on 2007-09-15
How do i burn the ISO properly? Now that I think about it, I found the guide on the official website a little vague.

---

### Post by oilchangeguy on 2007-09-15
read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by DCM101 on 2007-09-15
Oh. Well that makes sense. When I downloaded it of the website, I just got a WinRAR file. I didn't know it needed to be an ISO.

---

### Post by splintercellguy on 2007-09-15
It is an ISO file, but WinRAR installs a shell handler for ISOs. Burn the ISO, don't extract.

---

### Post by DCM101 on 2007-09-16
> **splintercellguy said:**
> It is an ISO file, but WinRAR installs a shell handler for ISOs. Burn the ISO, don't extract.

So how exactly do I convert it to an ISO from WinRAR. In case you haven't noticed, I'm a complete computer newb, so talk to me slowly so I can understand.

---

### Post by Celegorm on 2007-09-16
I think what's going on here is that it is an iso, but it looks like some sort of winrar file just because you have winrar installed. Just ignore that part, and follow the steps in this guide to burn the iso: [http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

---

### Post by oilchangeguy on 2007-09-16
> **DCM101 said:**
> So how exactly do I convert it to an ISO from WinRAR. In case you haven't noticed, I'm a complete computer newb, so talk to me slowly so I can understand.

did you read post #20? and there are some people who should just stick with what they've got, (windows) it seems you are one of those people. you are making something that's fairly easy, into something needlessly hard.

---

### Post by DCM101 on 2007-09-16
I'm really trying to do everything right, but it's not going well.

When I try to burn the image, all the options are locked up.

[IMG]http://img174.imageshack.us/img174/2696/screenshot008cc0.png[/IMG]

---

### Post by splintercellguy on 2007-09-16
Um...are you sure you have a burner? Looks like you don't, or am I missing something? If it's the recording software at fault, then I suggest trying CDBurnerXP.

---

### Post by oilchangeguy on 2007-09-16
> **splintercellguy said:**
> Um...are you sure you have a burner? Looks like you don't, or am I missing something? If it's the recording software at fault, then I suggest trying CDBurnerXP.

see post #25.

---

### Post by splintercellguy on 2007-09-16
> **oilchangeguy said:**
> see post #25.

I'm not quite sure what you're trying to say, but I can see he has no recording device whatsoever, or am I wrong?

---

### Post by oilchangeguy on 2007-09-16
> **splintercellguy said:**
> I'm not quite sure what you're trying to say, but I can see he has no recording device whatsoever, or am I wrong?

i'm saying this poor uninformed computer user needs to stick with windows. after 3 pages of posts on how to burn the cd, i'd say that's enough. the user doesn't get it. and those of us trying to help are wasting our time.

---

### Post by DCM101 on 2007-09-16
> **oilchangeguy said:**
> i'm saying this poor uninformed computer user needs to stick with windows. after 3 pages of posts on how to burn the cd, i'd say that's enough. the user doesn't get it. and those of us trying to help are wasting our time.

Oh. I'm sorry. You see, I was born with this genetic mutation because, unlike a caddilac of men such as yourself, I wasn't born with knowledge of all technology.

Get over yourself. "We're all just wasting your time." Maybe if you'd jump down from that pedastal of yours high up in the clouds, you'd realize we're all not computer wizards. I appreciate all the help that's been given to me, but don't be a prick if I don't get it at first. A-hole.

---

### Post by splintercellguy on 2007-09-16
I think we all need to chill out and assume good faith. Anyway, are you sure you have a CD recorder? Because it sure looks like you don't.

---

### Post by oilchangeguy on 2007-09-16
> **DCM101 said:**
> Oh. I'm sorry. You see, I was born with this genetic mutation because, unlike a caddilac of men such as yourself, I wasn't born with knowledge of all technology.

Get over yourself. "We're all just wasting your time." Maybe if you'd jump down from that pedastal of yours high up in the clouds, you'd realize we're all not computer wizards. I appreciate all the help that's been given to me, but don't be a prick if I don't get it at first. A-hole.

cadilac only has one d. if you don't get it at first? it's been 3 pages. how much more time do you need? you've been provided with answers and links, what more do you need? and now you're trying to burn a cd, and your computer does not even have a cd burner?????????? what else would you have us do to help you? just keep windows, go to the local public library, check out books on computers, and operating systems. when you've learned more, come back.

---

### Post by DCM101 on 2007-09-16
> **splintercellguy said:**
> I think we all need to chill out and assume good faith. Anyway, are you sure you have a CD recorder? Because it sure looks like you don't.

I have CDBurnerXP Pro 3. I tried burning the ISO using that, but when I tried to boot it, nothing came up.

---

### Post by splintercellguy on 2007-09-16
Did you burn it as an image, or a new data session? You should do File -> Write CD from ISO, something like that, and remember to close the session.

---

### Post by Celegorm on 2007-09-16
> **DCM101 said:**
> I have CDBurnerXP Pro 3. I tried burning the ISO using that, but when I tried to boot it, nothing came up.

I think he was asking if you have a cd writer, as in, the hardware.

If all else fails you could order a cd from shipit [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/") Delivery takes a long time though.

---

