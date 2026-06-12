---
title: "Brick wall with ubuntu install [Resolved]"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Jesiah76 on 2007-01-02
I got a quick question maybe someone will be able to help me out. I downloaded both ubuntu and kubuntu but i decided not to install on my main pc for fear of irreversibility to windows(being that i know very little about linux). I do have linspire 5.0 and have not installed it on this pc for somewhat of the same fear. 

the fear comes from the fact that the pc came with a system recovery tool but i cannot burn to a disc or dvd because it says only one copy per pc is allowed even though i don't remember ever burning a single copy. so my alternative was to install onto my daughter's pc which is a similar just less capable, mine is a hp pavilion 1530 and hers is a compaq something. she doesn't use it except to go online and play games so i figured she wouldn't lose anything.  

I tried to manually partition and it came at me with crazy stuff i didn't recognize so i tried to let it do it automatically and it didn't happen so I had it format the whole drive. but when i restart it still gives me the option of system recover by hitting F10 but it didn't work.  

now part one of my problem is this: can i go back to windows if i need to or is it too late? 

and part two is: when i tried to configure the network it did not work at all. I'm lost when I opened up the network folder and on top of that, her computer has a wifi card that i installed since it's in her room and it goes online through the router which is next to my pc. how can i correct this? I don't know how to look up the IP address for this router or the modem or any of that. 

can anyone help me please, I'd greatly appreciate it.](*,)

---

### Post by moffa on 2007-01-02
Firstly, I found your post very hard to read.  Please use paragraphs next time.

If you formatted your windows installation, it would not be easy to recover it.

For your wifi access, I recommend using network-manager.

---

### Post by riven0 on 2007-01-02
If you formatted the whole drive, I think windows is lost for good. Sorry. :( 

As for the network, you may have to install the drivers. What is your wireless card model?

---

### Post by Jesiah76 on 2007-01-02
Thanks for the quick reply. I tried that and for some reason either ubuntu won't recognize the wifi card or I don't know.

I know that with windows I can install something and have the computer search for newly installed hardware. I don't know how to do this on ubuntu. 

when I search on device manager I see it but don't know where to go from there. I do an initial test under device manager but it gets stuck at the network test.

---

### Post by Jesiah76 on 2007-01-02
err it's a linksys wireless card but I don't remember the model.

---

### Post by riven0 on 2007-01-02
When you're in ubuntu can you run this command?

First go to Applications >> Accessories >> Terminal. Copy and paste this and give us the result:

> lshw -businfo

Edit: But it would be really helpful if you can somehow get the model no.

---

### Post by Jesiah76 on 2007-01-02
it's either WMP54G or WMP54GS. Same thing except the second one is with a speed booster.

---

### Post by riven0 on 2007-01-02
> **Jesiah76 said:**
> it's either WMP54G or WMP54GS. Same thing except the second one is with a speed booster.

You might be in luck. I suggest first checking this howto and following the directions there:


[ HOWTO: Wireless with Rt2500 cards (wmp54g in particular) using WPA and latest driver]("http://www.ubuntuforums.org/showthread.php?t=241565&highlight=WMP54G")

Hopefully, your card has the rt2500 chip.

---

### Post by Jesiah76 on 2007-01-02
Thanks I will try it tomorrow when she's awake and I'll get back and let you know what happened. thank you very much for your support Riven0

---

### Post by riven0 on 2007-01-02
> **Jesiah76 said:**
> Thanks I will try it tomorrow when she's awake and I'll get back and let you know what happened. thank you very much for your support Riven0

No problem. :D Just tell us if it works or not...

---

### Post by Jesiah76 on 2007-01-02
No problem, I will come back to this same post to let you know

---

### Post by Jesiah76 on 2007-01-02
My wifi card does have the rt2500 chip. I can see it under device manager but I'm stuck from there. I read that how to but I still don't know where to go since I'm a new user.

---

### Post by mscclr3 on 2007-01-02
About yoru windows install:

Compaqs have a recovery partition built in so you likely didn't format the whole drive, If I remember correctly it is a hidden partition so the installer likely would have left it alone.

Pressing F10 on startup would recover the system back to a factory state

---

### Post by Jesiah76 on 2007-01-02
I kind of figured that but I didn't know if it had erased everything or not. but for some reason when I press F10 it doesn't want to start the recovery. the F1 and ESC for boot setup and what not works but F10 doesn't  want to start.

---

### Post by Frak on 2007-01-02
What brand of card do you have Jesiah76?

---

### Post by Jesiah76 on 2007-01-02
Linksys wmp54g

---

### Post by Jesiah76 on 2007-01-02
linksys wmp54g

---

### Post by Frak on 2007-01-02
> **Jesiah76 said:**
> linksys wmp54g
Same one as mine, but what version is it, 4.0 or 4.1, if you don't know its okay, well figure it out, I've worked on hundreds of cards, some work, some don't, but I know all linksys cards work, so I should be able to help you.

---

### Post by Jesiah76 on 2007-01-02
how do I find that out?

---

### Post by Frak on 2007-01-02
Okay, what version of Ubuntu do you run.

---

### Post by Jesiah76 on 2007-01-02
6.10

---

### Post by Jesiah76 on 2007-01-02
that's what it says when it loads up under mycomputer but when I open it it says 6.06 on top of the window

---

### Post by Frak on 2007-01-02
Downgrade to 6.06, I know downgrading isn't good, exept, I've never gotten any Linksys card to work under Edgy, they have all worked under Dapper, this is because the developers rolled back the drivers until Fiesty Fawn is released (7.04 I think), seriously downgrade though, it wont work, even with NDISWrapper, but they do have the drivers, but I don't think your up to compiling the kernel.

EDIT
You'll see there below my location I use Dapper, and thats the reason why, Kubuntu just because my video card won't work under Gnome, don't know why though?

---

### Post by Jesiah76 on 2007-01-02
you said Kubuntu? I downloaded that one too but I figured I'd start with ubuntu before I went onto kubuntu

---

### Post by Frak on 2007-01-02
Use Dapper not Edgy is what I'm saying, use LTS, dapper has the drivers, edgy doesn't.

EDIT
Ubuntu or Kubuntu even Xubuntu, it doesn't matter, use 6.06 Dapper LTS **NOT** Edgy 6.10!

---

### Post by Jesiah76 on 2007-01-02
my kubuntu says the same, once the dvd-rom reads it, it will say 6.10 i38 but the window tha topens up says 6.06 (disk tree). what does that mean?

---

### Post by Jesiah76 on 2007-01-02
ok so that was my first mistake. now the computer I installed it on has a AMD Sempron 3200. does that make a difference?

---

### Post by aysiu on 2007-01-02
> **Jesiah76 said:**
> my kubuntu says the same, once the dvd-rom reads it, it will say 6.10 i38 but the window tha topens up says 6.06 (disk tree). what does that mean?
I know you may not be a big fan of the terminal, but that's really the surest way to know what version you have.

Go to [the terminal](http://www.psychocats.net/ubuntu/terminal) and type in this command: ```
cat /etc/issue
``` If you're using dapper, the output should say ```
Ubuntu 6.06
``` If you're using Edgy, the output should say ```
Ubuntu 6.10
``` > the computer I installed it on has a AMD Sempron 3200. does that make a difference? I don't think that should make a difference.

---

### Post by Jesiah76 on 2007-01-03
thank you LOL, I thought I was imagining things. for the second time. 

one quick question though...the computer has a 100GB hard drive. before it became ubuntu it had a partiton of about 6 or 7GB for recovery. I mistakenly formated the hard drive but I've checked it under ubuntu in the device manager and it only reads 90GB. is it possible it left the recovery partition alone? everytime I restart I get the option to press F10 for recovery but it does not do it. I'd rather have it as a dual boot until I learn the OS.

---

### Post by aysiu on 2007-01-03
Yes, it's possible the recovery partition is still there. Whether it's usable or not is another story, of course.

If you are willing to put up with a little bit of terminal, we can find out quite quickly what your partitions look like. Just type this command in and post back the output: ```
sudo fdisk -l
``` That last character is a lowercase L (not an uppercase i or the number one).

If you'd prefer to do it graphically, take a screenshot, and then upload the screenshot... I can walk you through that, too, but it'll be more involved.

---

### Post by Jesiah76 on 2007-01-03
ok for the first reply for you and Frak, yes it was 6.10. the good news is that I've just downloaded and burned 6.06 and will install shortly that is unless you are able to help me out with the partition.
and by the way if I may seem slow is because I have the other computer here next to me but I have to share monitors so I'm going back and forth with one monitor.

---

### Post by aysiu on 2007-01-03
> **Jesiah76 said:**
> ok for the first reply for you and Frak, yes it was 6.10. the good news is that I've just downloaded and burned 6.06 and will install shortly that is unless you are able to help me out with the partition.
and by the way if I may seem slow is because I have the other computer here next to me but I have to share monitors so I'm going back and forth with one monitor.
You're not slow at all, actually. These are pretty quick replies!

During installation, you'll get to a part about partitioning. Can you select "manually edit the partition table"? That will allow you to see how many partitions there are and what sizes they are.

So you'll be able to easily see whether the recovery partition is still around.

---

### Post by m.musashi on 2007-01-03
I've been following both your threads and you seem to be getting some good help, but I'll add a couple observations for what it's worth.

First, if you are using edgy and having trouble it's probably not worth fighting. Dapper is kind of the flagship release. I have both dapper and edgy and edgy seems a bit more experimental whereas dapper should be more stable. I know it's a hassle to reinstall but Ubuntu is one of the easiest OSs I've ever installed. It shouldn't take more than 30 min from start to log in.

Second, you mentioned something about your wireless being recognized but not knowing what to do next. Can you elaborate on that? Networking with Ubuntu can be a bit confusing so it might just be a matter of knowing where to go and what info to enter. If your card is not working then that's another issue.

Finally, just some words of encouragement. Don't get too flustered. I know what a pain it can be to get a computer working - I've dealt with that on both windows and linux more times than I care to remember (just broke apt yesterday :)). The people here are great. I started with Ubuntu a year ago and didn't know jack. I've learned a lot this past year and it's all thanks to the people on this forum. It may take days or weeks (yeah, your daughter isn't going to be too happy) but unless you simply have very linux unfriendly hardware you will likely be able to get it to work.

---

### Post by Jesiah76 on 2007-01-03
umm, this is gonna take a bit. because I have to type it

---

### Post by aysiu on 2007-01-03
> **Jesiah76 said:**
> umm, this is gonna take a bit. because I have to type it
I appreciate the dedication.

---

### Post by Jesiah76 on 2007-01-03
it says:
Disk /dev/hda:  100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

            Device Boot             Start                End             Blocks       Id     System
/dev/hda1            *                    1             11998         96373903+  83      Linux
/dev/hda2                           11999             12161           1309297+   5       Extended
/dev/hda5                           11999             12161           1309266     82      Linux swap / Solaris

---

### Post by aysiu on 2007-01-03
Yup... the recovery partition is gone.

It's **all** Ubuntu now.

Might as well install 6.06 right over 6.10. There's nothing left to save.

---

### Post by Jesiah76 on 2007-01-03
ok...i just installed 6.06 and everything on the screen is huge and i don't even see the wireless card anymore under device manager unless it's named something different.

---

### Post by aysiu on 2007-01-03
> **Jesiah76 said:**
> ok...i just installed 6.06 and everything on the screen is huge and i don't even see the wireless card anymore under device manager unless it's named something different.
So I guess 6.10 had better screen resolution detection than 6.06.

Let's fix that first, since I know almost nothing about wireless cards.

Log out.

Then, press Control-Alt-F1. This will take you to a screen that looks like the terminal, but it fills up the whole screen.

Log in.

Then type ```
sudo dpkg-reconfigure xserver-xorg
``` This will launch a little wizard for re-detecting/configuring your video card and monitor. Answer the questions as best you can. If you don't know the answer, just go with the default.

When you're done, you'll be back at the command prompt.

Press Control-Alt-F7 to get back to the graphical user interface. Finally, press Control-Alt-Backspace to reset the graphical interface for your new settings to take effect.

---

### Post by Jesiah76 on 2007-01-03
I did all of that and somehow it reverted itself to 6.10 so I will try to reinstall

---

### Post by aysiu on 2007-01-03
> **Jesiah76 said:**
> I did all of that and somehow it reverted itself to 6.10 so I will try to reinstall
What's indicating to you that's it's "reverted" to 6.10?

When you reinstall, make sure you select the option to Erase the Entire Hard Drive.

---

### Post by Jesiah76 on 2007-01-03
ok it seems that before i fix the screen resolution I have to install 6.06 while logged in which makes it hard because I cannot see the whole screen.
but I am now at the part where it asks me about partition, what should I do?

---

### Post by Jesiah76 on 2007-01-03
I actually had to log in and install and I did that thing in the terminal again and it said 6.10 so I am now reinstalling 6.06

---

### Post by aysiu on 2007-01-03
> **Jesiah76 said:**
> ok it seems that before i fix the screen resolution I have to install 6.06 while logged in which makes it hard because I cannot see the whole screen.
but I am now at the part where it asks me about partition, what should I do?
There should be an option to resize and use free space, an option to manually edit the partition table, and an option to erase the whole disk. Select to erase  the whole disk.

If you follow the instructions I gave before (Control-Alt-F1, etc.), you should be able to see the options--it uses a text-based graphical wizard.

---

### Post by aysiu on 2007-01-03
> **Jesiah76 said:**
> I actually had to log in and install and I did that thing in the terminal again and it said 6.10 so I am now reinstalling 6.06
Is it possible you *think* you're installing 6.06, but you're really installing 6.10?

Can you try the ```
cat /etc/issue
``` command *before* you go through the installation procedure? That is, can you run the command during the live session?

---

### Post by Jesiah76 on 2007-01-03
no I have 6.06 on a dvd and it boots up when I log back in but I guess I have to erase 6.10 first like you said so let me try that

---

### Post by Jesiah76 on 2007-01-03
I installed 6.06 fine but everyting is still huge even after reconfiguring the screen

---

### Post by Jesiah76 on 2007-01-03
well I fixed the screen problem and now I'm trying to figure out everything else but you've helped me a lot showing me where to start and now that I know that "terminal" is the Alpha in ubuntu I think I'll be better off.
I will continue this tomorrow because it's late so thanks.

---

### Post by Jesiah76 on 2007-01-03
thanks everyone for the help, I finally got the wireless network working about a half hour ago. 
Now I feel more confident with figuring out linux.

If any moderators see this post you can now close it. thanks.

---

### Post by aysiu on 2007-01-03
Can you post how you did it? That way future frustrated new users can benefit from your experience. In the meantime, I'm marking this resolved.

Glad it worked out for you.

---

### Post by Jesiah76 on 2007-01-04
Thank you. well I did a lot of research on other posts about wireless network and the more I read the more I bored. 
But easiest way to resolve all those problems would be to get online so that I could copy and paste. well I couldn't since the wifi card was not working. 
I figure I'd move the computer here next to this one but like I said before I had to share monitors wich was painful. 
I looked online for windows RUN Commands so I could find the IP address and that way I could input it.  All this was after I installed ubuntu 6.06(Dapper). I think that was the main problem. Edgy made it harder for me. I went to Networking and tried to get online through Ethernet since my router is here too and didn't work but I was able to activate it. so instead I deactivated it and activated the wifi and there it was.

I know it seems confusing but the best advise I got was to go with Dapper instead of Edgy and a little bit of research.

---

### Post by Jesiah76 on 2007-01-04
By  the way, the only other thing I did different was that I found this on another post and executed it:

:~$ sudo gedit /etc/init.d/xrt61
type this into that file:
Quote:
#!/bin/bash
sudo /sbin/modprobe rt61
sleep 3
sudo /sbin/dhclient ra0
save and exit
then again in terminal:
:~$ cd /etc/init.d
:~$ sudo update-rc.d xrt61 default

// comment out all ra0 : auto ra0 , end rest of ra0. in /etc/network/interfaces

reboot


It should be under Networking & Wireless forum.

---

