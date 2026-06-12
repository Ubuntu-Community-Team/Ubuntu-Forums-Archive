---
title: "Couple of problems with Ubuntu 6.10"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Villa on 2007-05-26
Hi I'm a Linux noob, and I pretty much just installed Ubuntu 6.10 on my computer. (For the sake of trying it out =p)  I have a 9200se, and the latest ATi 'driver package' from the app adder/remover thing program.

I have a couple of problems.

1. How do I check whether the computer has detected a RAM stick I Just put in? Windows had cpu-z, is there a Linux equivalent? Plus, how do I check the RAM for errors? Is there a memtest equivalent?

2. When I try to use Mplayer to play any video files, it comes up with this Fatal error:

"Error opening/initializing the selected video_out (-vo) device" (word for word).

How can I fix it?

3. How do I change it so that all media files, when opened by Firefox, open them with VLC or anything else BESIDES Totem player? Because I can't get Totem player to work as well. It says: 
"You do not have a decoder installed to handle this file. 
You might need to install the necessary plugins"
How do I fix this and change the default media player to something else?

4. How come all WMV files screw up when played with VLC? The VLC in Windows worked fine with WMV files... it's really annoying, as a large amount of my movies are in WMV format. =( How do I fix this?


If someone could give me simple instructions (I can't really use the Terminal very well as I don't know much commands), although I can do simple stuff sort of, =p it would be really appreciated. ^^ 

Thanks! =)

---

### Post by Ek0nomik on 2007-05-26
*If* you want to test your ram, you can install memtester.

```
sudo aptitude install memtester
```

After you have installed it, it will probably show up under some category in your programs, or you can probably run memtest or memtester via the Terminal.

*If* you want to see how much RAM you have:

Administration/System Monitor/System (it's a tab)

*Regarding*:  "Error opening/initializing the selected video_out (-vo) device"

Edit your .mplayer/gui.conf file and make sure that you have vo_driver line like this:
vo_driver = "x11"

You can edit it a few different ways:

```
gedit ~/.mplayer/gui.conf
```

or

```
nano ~/.mplayer/gui.conf
```

*Regarding* wmv files, try this:  [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

It may not work because it is for Feisty (the newer Ubuntu).  Why did you choose to install Edgy over Feisty by the way?

I hope some of this helps you!  If not, reply and post exact output and I will try to help.  :)

---

### Post by Villa on 2007-05-26
Hi thanks for the help with the RAM things. =)

Now I just changed the Mplayer drivers to "x11", but it still can't play WMV files. I'm using Edgy Eft, what does that mean? =p 

So how do I get the w32 codecs (I think that's what I need in order to play WMV in both VLC and Mplayer?) is there any easier way to get the codecs? I don't understand some of the instructions. 

Thanks for the help so far again. =)

---

### Post by Ek0nomik on 2007-05-26
Ubuntu has weird names, I know.  :)

4.10 	Warty Warthog
5.04 	Hoary Hedgehog
5.10 	Breezy Badger
6.06    LTS Dapper Drake
**6.10    Edgy Eft**
7.04 	Feisty Fawn

You are using 6.10.  Most people on this forum use Dapper, Edgy, and now the majority probably use Feisty, as it's the newest version released.

Here is a guide on how to get your W32 codecs working:

[http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278)

If you need help just send me a message or reply to this thread, I'll keep an eye on it.

---

