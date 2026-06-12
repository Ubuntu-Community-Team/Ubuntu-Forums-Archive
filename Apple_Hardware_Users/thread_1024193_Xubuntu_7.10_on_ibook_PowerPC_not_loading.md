---
title: "Xubuntu 7.10 on ibook PowerPC not loading"
date: 2008-12-28
forum: Apple Hardware Users
---

### Post by ringsofsaturn on 2008-12-28
Hello,

Have an ibook G3, 500mhz PowerPC, 192 MB RAM and have installed Xububtu 7.10. When booting loading does not load and after a while screen changes to BusyBox. Have re-installed but no improvement. Ibook ran Xubuntu 6.06 with no problem.

Any thoughts please?

Have also tried Xubuntu 8.04 (and 8.10) but it didn't install. Can't remember why now though.

Many thanks.

---

### Post by mkvnmtr on 2008-12-28
When you start up and the very first writing comes up press tab. I don't remember on 7.10 but there should be several options listed Such as nosplash or linux= no splash. Pick them one at a time until you get one that works to get you to a login screen. When you type it in then press enter. If you wait to long to press tab you will wind up in the busy box. I

---

### Post by ringsofsaturn on 2008-12-29
Have tried as you said mkvnmtr but with no success. After pressing the tab key I get: "Welcome to yaboot version 1.3.13. Enter "help" to get some basic usage information". 
"boot: Linux old".

When entering "help" (without quotes) I get "Press tab key for a list of defined images" plus lot more stuff about booting kernal image (will quote if need be...).

So I press tab key and get: "boot: Linux old" yet again.

Any further thoughts please?

Thanks.

---

### Post by stream303 on 2008-12-29
> **ringsofsaturn said:**
> Have an ibook G3, 500mhz PowerPC, 192 MB RAM and have installed Xububtu 7.10. When booting loading does not load and after a while screen changes to BusyBox. Have re-installed but no improvement. Ibook ran Xubuntu 6.06 with no problem.

Gutsy 7.10 had a modprobe issue much like intrepid does:  (modprobe ide-core vs modprobe ide-scsi)

[https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

> Any thoughts please?

For now, I'd definitely stick to the LTS releases.  7.10 is about to go end-of-life with support, so 8.04 would be your best bet.  You said it failed to install for you - with only 192mb of ram, did you use the "alternate" install image?  If you used the desktop live-cd image, that is probably the source of your install problem with 8.04 since 192mb of ram may not have been enough to support a graphical install in the first place.

If you want to continue on with 7.10 anyway, just use that modprobe ide-core fix mentioned above.

The funny thing is that PPC on Ubuntu is harder to install than Debian is.  You may also want to consider moving to Debian since we share the same basic support.

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Either Etch 4.0r6 stable or testing (Lenny) is fine, although most would say just use Lenny at this point since it is about to be released as stable itself.

If you have an existing install, be sure to copy down your /etc/X11/xorg.conf file, since you might need it as a reference to manually configure it later on with a newer release of either Ubuntu or Debian.

---

### Post by mkvnmtr on 2008-12-29
Just last night we helped a guy get 7.10 ubuntu on a G4. He had a bit of trouble and then if finally went on. I think you will have an easier time with 8.04. The alt. install is the way to go for lack of ram. As U remember installing 8.04 I had to choose the kernal option "live-nosplash-powerpc" but other than that it was an easy install and once I enabled the driver things worked well.

---

### Post by ringsofsaturn on 2008-12-29
Stream 303:

Tried the 7.10 fix via the link you posted but didn't work for me (the fix, not the link!). Probably my incomptence with a computer.

Remembered that I did "server" install with 8.04 as it was suggested elsewhere, and then I was supposed to have installed Xubuntu desktop. But my poor little brain was confused with so much "computer speak" text!
Tried 8.10 but there were CD-ROM driver issues I think.

Installed Debian 4.0r6 but had display problems. Only got 2 inches of screen to display on left of screen and that was repeated underneath. Rest of screen was black with a cross on it. Re-installed but with same result. Found another person on Debian forum with same problem but couldn't fathom the reply. Might as well have been written in Martian (to me anyway)!!!

Will try the Debian Lenny distro you mentioned I think.

MKVNMTR:

Where do I find "kernal option"? Sorry if it's a stupid question.

My thanks to you both for taking the time and trouble to respond.

---

### Post by mkvnmtr on 2008-12-29
I have no experience with the server install. I would not think it is a good idea unless you are going to use it as a server. That is why we are seeing different things on boot up I guess. With less than about 350 Mb of ram you should try the alt install. This is not a server. It is just a low ram way nto get a desctop with a complete Ubuntu install. When I have booted any lo the live disks from 6.06 through 8.10 at the moment the first writing comes up on the start if I press tab a page comes up. This page will list the kernal options you can use to type in before it loads the kernal. I have only used the alt install a couple of times and I believe it works the same way. I don't know about the server disk. I hate to see you have to down load again but it sounds like the best idea. I would go with 8.04. It is the long term support distro and has been pretty friendly to ppc.

---

### Post by ringsofsaturn on 2008-12-30
Stream303:

Have re-installed 4.0r6 and still got same dispaly issues. Have tried "lenny" but had similar problem but this time with 2 thirds of display usable.

mkvnmtr:

Will try 8.04 after the above debacle unless anyone knows a fix for it.

Am assuming I'll have to download Ubuntu 8.04 and somehow install xfce to "Xubuntu" it as can't find Xubuntu 8.04 for PPC.

Hope you both have a happy and prosperous New Year and once again, thank you.

---

### Post by mkvnmtr on 2008-12-30
With 192 Mb of ram you probably need to be sure to use the alt. install disk. I think you are right there is not yet an Xbuntu in 8.04. It is a simple matter to download the desktom and pick it on the log in.

---

### Post by stream303 on 2008-12-30
Well, at least you get a little bit more with Debian. :)

This may not make a difference, but when starting up, have you tried stopping the second-stage yaboot: boot prompt by hitting TAB, and then issuing:

```
Linux nosplash
or
Linux nosplash video=ofonly
```

(nosplash not needed when using debian)

Just to make sure that the cards aren't put into a weird state before X starts?

In the end, it looks like you'll need to manually edit your /etc/X11/xorg.conf file in either Ubuntu or Debian.  There is a nice writeup here on a similar model:

[http://pierre.baudu.in/ibook/](http://pierre.baudu.in/ibook/)

It looks to have nice xorg.conf that may give up a few hints...

---

### Post by ringsofsaturn on 2008-12-31
Stream 303:

Followed the link and attempted what was suggested (I think!!!) although I did feel somewhat out of my depth. Nothing worked so I'm assuming I've messed up somewhere along the way unless Pierre's info was just specific to Etch. Think I'll go and try 8.04 install as there are other issues such as keys not working etc and it's slower than a dead snail stuck to a stone with superglue! Although I'm assuming xfce could be installed if need be.At least when I had 6.06 (briefly) installed the display was ok.

One further thing though, will it be possible to use my wireless usb adaptor in whichever distro I eventually settle with as the ibook doesn't have a airport card?

BTW I entered "Linux nosplash video=ofonly" as you said and got blue screen with ""Failed to start the X server (your graphical) interface. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" and then a yes or no. Pressing "yes" resulted in another window with much unintelligble (to me) text. Perhaps it's written in Martian dialect ;) ?

All I want with the old ibook is for it to work competently and be simple as possible to configure. I will really only use it as a sort of "net book". Am prepared to buy extra RAM and an airport card if I really must but would rather not.

Yet again, very many thanks.

Am always impressed when people, on whichever forum I subscribe to, give of their time freely so others can benefit. Despite what the media likes to portray (at least in the UK) there are some very decent people out there willing to help others :) .

---

### Post by stream303 on 2008-12-31
> **ringsofsaturn said:**
> Although I'm assuming xfce could be installed if need be.At least when I had 6.06 (briefly) installed the display was ok.

That might actually be the easiest thing to do for the time being.  Reinstall 6.06, and copy/save/print out the /etc/X11/xorg.conf file for reference.  While you're at it, also print out your /etc/yaboot.conf file.

If you want to stick with 6.06 because it is actually working, you can get xfce by using synaptic to download xubuntu-desktop.  Once all that is downloaded, when you log back in, before supplying your username and password, go to Session, and change the session to Xubuntu or XFCE, and bingo.  You now have an XFCE/Xubuntu desktop present instead of Gnome.

Thing is, while it may prove to a tad faster on the desktop itself, once you launch several programs like Firefox or Gimp, things will slow down again.  So with only 192mb of ram, you just have to keep in mind that a quicker desktop might not be a panacea to low memory.  You may be able to live with it if you only run one program at a time, and have a bit of patience.  This could also be a great time to learn the cli, all kidding aside.

If you want to go back to say Debian 4.0r6, you can use what you found in your old Ubuntu 6.06 xorg.conf, and manually edit it to include much of what you found there if you feel like experimenting.  However if you are just getting a feel for things, there's no shame in running Dapper 6.06.  It is supposed to have support until what - 6.09 for desktops?  That might give you enough time to get a feel for things if you want to upgrade to a more recent distro and manually hack up xorg.conf etc.

> One further thing though, will it be possible to use my wireless usb adaptor in whichever distro I eventually settle with as the ibook doesn't have a airport card?

Funny you should mention this.  I just dragged myself into the 20th century with wireless, and although I could easily get my Netgear and Belkin wireless usb adapters up and running on my Debian AMD64 box, and on OSX, I couldn't do it on my ppc box - I could get the sticks recognized and working from a receive-standpoint in either network manager or from manually configuring my /etc/network/interfaces file, but it is almost as if there might be something preventing a usb wireless stick from working on the mac with anything but osx?  It probably deserves a separate thread - maybe I'll pop that up.

One option is to run a pair of wireless routers that support WDS - although the router pair needs to be of the same manufacturer - such as Netgear WGR614-v9.  This way you don't have to worry about loading binary blobs, etc, and just hook up to your ethernet port.  A great intro to this technique is here, and I might have to use that on my ppc:

[http://forums.debian.net/viewtopic.php?t=28456](http://forums.debian.net/viewtopic.php?t=28456)

Not every router supports WDS, so check carefully - probably more in the networking forums here on that one.  Ah, but that kind of rules out portability now with the ibook. :)

> All I want with the old ibook is for it to work competently and be simple as possible to configure.

At this stage, I'd just stick to 6.06x because it is working.  Make sure you are getting updates - if not we can fix the repository settings.

> I will really only use it as a sort of "net book". Am prepared to buy extra RAM and an airport card if I really must but would rather not.

Hmmm... I don't know if the expense would be worth it, or if that money would be better spent on a real netbook to begin with - and which would probably have linux or be linux friendly to begin with.

> Am always impressed when people, on whichever forum I subscribe to, give of their time freely so others can benefit.

It's all about community - and in my case I am just standing on the shoulders of giants and trying to "pay it forward" so to speak.

---

### Post by ringsofsaturn on 2009-01-01
Stream:

Thought I'd just "have a go" with 8.04 for the, erm, "fun" of it. Interesting to note that I have same display issues as with Debian and it makes Debian look super-charged! But expected the latter if not the former. Tried the wireless adaptor (ZyXEL) and it was recognised but didn't make a connection despite much fiddling (great technical term!). Am sure I've read somewhere about a person being successful with wireless adaptor and PPC. Maybe with a G4 though. Would that make a difference?

Will go back to 6.06 as you advised.

I said this in earlier post: "Despite what the media likes to portray (at least in the UK) there are some very decent people out there willing to help others". Should have made it clear that there are decent people EVERYWHERE. And not just in the UK as it might have sounded. :)

---

### Post by ringsofsaturn on 2009-01-02
Stream:

Have now actually managed to get ibook working wirelessly :D . A stroke of genius? No, I just managed to actually put in the correct network key!!! :oops: Yes I'll now go and stand in the corner with a hat on my head with large letter "D" on it ;) .

Question for you or any one else: when I had 6.06 on the ibook there wasn't a "wireless settings" under the Network Manager. How do I find/enable or whatever this?

Am now going to re-install 6.06 hoping there is a answer to above query.

Many thanks.

---

### Post by stream303 on 2009-01-02
You've done a great thing by not fearing multiple reinstalls. :)  That's will pay off handsomely, believe me, to get exactly what you want from your ppc as your skills improve.

It has been a long time since I installed 6.06, but in any case you'll need the wireless firmware - and for airport cards that is typically the b43 firmware cutter.  However, you don't have that, and I'm not sure if one can get the Zyxel usb stick to work.  I haven't received any replies about why my netgear and belkin usb wireless sticks seem to be "receive-only", despite being able to manipulate them with either Network Manager, or directly from /etc/network/interfaces file.  If I come across anything, you'll be the first to know. :)  So for now, it looks like usb wireless may be out of the question for the time being.  I might skirt the issue by using a pair of WDS-capable routers from the same manufacturer, but of course that's not really portable.

Once you get 6.06x up and running again, be sure to copy or print out your /etc/X11/xorg.conf file, and /etc/yaboot.conf file.  You can use those if you later want to try 8.04 or Debian again, although they might not work as simple replacements - but some of the vital data found may be included in your custom-written xorg.conf if you do decide to try and run these later releases.

No problems with the community issue - everyone understands that it is global in scope.  Amazing, huh?

---

### Post by ringsofsaturn on 2009-01-03
"You've done a great thing by not fearing multiple reinstalls. :)"

Thanks for the kind comment - have done 8 so far on the ibook and about 8 million on my P3 desktop :) !

Would there be any problems downloading and installing latest (for 8.04 or 8.10) Network Manager or even Wicd? Would it work in 6.06?

Or am I missing something?

At the risk of sounding a complete "thicko" ;) , where do I find my /etc/X11/xorg.conf file, and /etc/yaboot.conf file?

BTW 6.06 up and running nicely - there's something SO satisfying upgrading an old piece of computer kit and breathing new life into it, isn't there? You feel like you're beating the "system" somehow :D . Even though it drains hours from your life :( ;) .

Thanks once again.

---

### Post by stream303 on 2009-01-03
> **ringsofsaturn said:**
> Would there be any problems downloading and installing latest (for 8.04 or 8.10) Network Manager or even Wicd? Would it work in 6.06?

I suppose, but we're still at the point where it might not be a software issue, but a lockout from Apple.  My suspicion is that they wanted to promote the use of their own airport wireless cards and not allow the use of a usb-wireless stick a convenient option.  I haven't confirmed that yet.  I have not heard of a single usb-wireless success story on ppc's.  But there's bigger fish to fry at this stage. :)

> At the risk of sounding a complete "thicko" ;) , where do I find my /etc/X11/xorg.conf file, and /etc/yaboot.conf file?

That's the standard *nix hierarchical file system.  It might be easier to think of these as folders and files.  Knowing how to traverse this is essential when it comes to Linux and ppc, otherwise at the first sign of trouble, you'll be sunk and at the total mercy of gui developers. :)

Basically, think of the / as designating a "folder" followed by the name of the folder.  So, in this case we have the "/etc" folder.  Inside that folder is yet another folder with the name of /X11.  And now, inside that is a file named xorg.conf.  Since there is no trailing slash after xorg.conf, there are no deeper folders within.  That's my best (poor) analogy.

So how do you get to it?  In this case, one might want to copy that file within all those folders using the file manager to say a usb pendrive.  However, we'll go cro-magnon and just write it down.  That way in case the install totaly screws up, you'll have a record of what worked.

We can take a look at it with almost any editor, gui or commandline.  Let's use the commandline file viewer, named *less* to do it.  Call up a terminal and issue

```
less /etc/X11/xorg.conf
```

Use the up and down arrow keys to scroll through the file.  Write down what you see.  When you are done, just hit the "Q" key to quit.

Now do the same for the /etc/yaboot file:

```
less /etc/yaboot.conf
```

These two files are key to the system working properly, and will be very valuable if you decide to upgrade as the recent releases of *any* Linux distro are going more and more towards a smart setup that is *supposed* to make this easier for the average user.  Unfortunately, apple ppc hardware doesn't like to talk much, and the recent installers miss key information that forces us to write this stuff manually to fill in the gaps.

The catch-22 here is that unless you do this from the commandline in many cases, you can't get to a gui editor to fix it in the first place! 

So that's why I recommend learning to love your Dapper install for learning some basics in the terminal.  You have to look at it in a different light to overcome the job as a chore.

Get this:  Using that command shown above with the less command has been around for what - 30 years or so?  Anyone who has sat behind a terminal in their bell-bottoms or uptight suit at a university would feel right at home. :)  Thing is, you have learned something that will probably last another 30 years!  Getting your wifi to work with Network Manager will be lost quickly in the coming years.  The value of that little Apple box is much more than it appears.  It might die in a few years, but your knowledge of how to just view a file with *less* and the hierarchical file system navigation is priceless.  I'm waxing romantic here so I'll stop. :)

The most important thing at this point is to get those two files written down as hardcopy.

---

### Post by ringsofsaturn on 2009-01-04
Stream:

 Thanks for the response. Have followed your "tutorial" and will do as you advise.

R the wireless issue you say: "I suppose, but we're still at the point where it might not be a software issue, but a lockout from Apple. My suspicion is that they wanted to promote the use of their own airport wireless cards and not allow the use of a usb-wireless stick a convenient option. I haven't confirmed that yet. I have not heard of a single usb-wireless success story on ppc's. But there's bigger fish to fry at this stage."

But whem I had 8.04 installed the USB adaptor DID work (as per my earlier post - #14)!! Hence the idea that if I could install 8.04's Network Manager it would work in 6.06.

How does one actually find this version of Network Manager to download?

---

### Post by stream303 on 2009-01-04
Wow!  I guess that teaches me not to post after coming home from a holiday party. :)  That's great news and means I have to dig some more to find out why my brands aren't working with Debian....

Ok, so all that's really a problem is just the display in 8.04 - otherwise the usb wireless and everything else works.  Ok.

In Dapper, perhaps you can go to System > Administration > Network and see if you can bring up the Zyxel from there?  If it doesn't work, maybe someone else can tell you how to bring NM down from 8.04, but I think that probably won't work due to the dependencies - but I could be wrong.

If that works, great, you can ignore all of the following......


If you feel up to it, and with your system stable with dapper for the time being, perhaps reinstall 8.04 again, but know upfront that you'll have to manually edit your /etc/X11.xorg.conf file.  Luckily you have a working reference now from Dapper.

So...  I think the easiest thing to do is just learn how to edit from the commandline with Dapper, since your display is jacked on 8.04 temporarily.

Can you get to a virtual terminal via ctrl-alt-f2 ?

Once there, you can login and be at a shell prompt.  (To get back to the gui, you can do ctrl-alt-f7.)

Get to the virtual terminal, and after logging in, fire up an editor just to do a quick editing job on a testfile.

```
nano testfile.txt
```

Type in a few lines of some random text.  To save this file, hit ctrl-O (the letter not the number).  To quit the nano editor, type ctrl-x.

This is essentially what you'll be doing to your /etc/X11/xorg.conf file with 8.04:

```
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.original
```

(make a copy of the original for safekeeping)

```
sudo nano /etc/X11/xorg.conf
```

And then change or add values that might be suggested here or in the faqs guided by your xorg.conf from dapper.

Can you post your Dapper /etc/X11/xorg.conf file here via cut-n-paste?  You can find gedit or just issue at the terminal

```
gedit /etc/X11/xorg.conf
```

then highlight and copy and paste the contents of your xorg.conf file here.  We're not going to edit it in dapper since it already works, but just use gedit to look at the file and make it easy for cut-n-paste.

That way we might be able to find a suitable modificaton to 8.04's somewhat bare version.

---

### Post by ringsofsaturn on 2009-01-04
Stream:

Downloaded Network Manager 0.6.6 0ubuntu5 but wouldn't install: "Error: Dependency is not satisfiable: dhcdbd".

Will attempt your fixes soon (ish) when I get a moment.

Thanks yet again for your help.

---

### Post by ringsofsaturn on 2009-01-04
Stream:

You say: 
"In Dapper, perhaps you can go to System > Administration > Network and see if you can bring up the Zyxel from there? If it doesn't work, maybe someone else can tell you how to bring NM down from 8.04, but I think that probably won't work due to the dependencies - but I could be wrong."

There isn't that exact pathway in Dapper but followed System>Networking which I assume is same thing and it brings me to "network-admin". No info re ZyXEL there unfortunately.I assume this IS NM. 

Will post on a new thread re "bring down NM from 8.04" and see if anyone has experience of this. If no joy then I'll folow your advice.

 You say: "Ok, so all that's really a problem is just the display in 8.04 - otherwise the usb wireless and everything else works."

Seemed to do (didn't test EVERYTHING though...) but the ibook was really unusable because of it's speed - or lack of. I enjoy a cup of tea like most Brit's but don't really want to "brew up" every time I open a new window ;) .

Cheers!

---

### Post by stream303 on 2009-01-04
Drat!  This sounds a lot like the problem I had with Gutsy+ when I still had my 12" G4 ibook:  everything was running REAL slow, and the little fans started running too.

Turned out that ONLY on my ibook, network manager was eating up nearly 100% of the cpu resources.  I disabled network manager, and all was ok.  I wasn't running wireless at the time, but it was still hurting my ibook performance on regular ethernet.  So I just removed network manager.  It took a while to actually run the command. :)

I saw it when I ran top in a terminal.  (actually, my favorite is to grab "htop" from the repos and use that instead of top)  Sure enough, NM wasn't being friendly to the ibook.  On my G5, no problem.

Check that out if you still have 8.04 running.  Problem is, this won't help you in your wireless needs, but if NM can be removed, at least 8.04 on regular ethernet should run at normal speeds again.

---

### Post by ringsofsaturn on 2009-01-04
Stream,

Haven't got 8.04 running as yet, would rather I could get wireless running with 6.06 if possible so as not to have all the "bloat" of 8.04. With out wireless I might as well use my desktop - then the ibook could act as a paperweight ;) . Portability is key.

Have you ever tried Wicd? Sorry if I've asked you this before.

Thanks as usual.

PS Just remembered - when 8.04 was installed before I'm sure it was snail-like even when disconnected from the 'net.

---

### Post by stream303 on 2009-01-05
Re: wicd - I've heard that it might be a popular replacement for network manager.  Speaking of which, even when not connected to the net, NM by itself was just hogging all the cpu time - but only on my ibook.

The good thing is that at this point, your apple is just another machine so maybe the folks in the networking forum can pinpoint it for you faster than we could.

That would be fantastic to get the zyxel working on 6.06.  And thanks again for giving me hope that my usb wireless isn't a lost cause either.

---

### Post by stream303 on 2009-01-05
Guess what?  I got usb wireless working on my Debian G5 box!  Thanks for the motivation!  Details in netgear thread...

---

### Post by ringsofsaturn on 2009-01-07
Hello Stream,

Glad you've got that working. Another question for you: I thought of installing 8.04 (or Debian) on an external drive so as I can "play" with it and try out some of the fixes you've posted on this thread. Would save me keep re-intalling 6.06 if I "mess it up". Will the ibook and 6.06 boot from an external drive and if so, how?

Will attempt your solutions anyway don't really mind re-installing different distro's as we've discussed before, but I can save the hassle....

Thanks.

---

### Post by ringsofsaturn on 2009-01-07
The above is so as I can install (hopefully) Wicd etc etc and not lose the 'net if things go wrong.

---

### Post by stream303 on 2009-01-07
Yes, you can install to an external *firewire* drive and boot from that.  However, it is guaranteed not to boot without some manual editing of the /etc/yaboot.conf file.  Which means that after the install, one has to back in with single-user mode, or rescue mode and do the editing, typically with the vi editor, as that's the only editor available (at least that I could get to work) in those modes.

Check this out from about 2 years ago:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

That worked for me, although I was comfortable with vi editing from long ago...

---

### Post by emmary on 2009-01-07
China Computer Peripherals Wholesale 
[www.tradestead.com](www.tradestead.com)
  
Computer peripherals manage to expand the abilities of your computers. Here we introduce you these pleasantly useful gadgets, including cordless optical mouse, DVB-T USB stick, pen pointer, memory card reader, wireless stereo headset, and other USB devices. Just spend a few minutes to browse and register as a member of our online store, you will get the latest computer peripherals you will appreciate. Our products brag about their high quality. Furthermore, TRADESTEAD offers you the competitive price. 

Related Categories:MP3 Players Bluetooth headset Mobile Phones Flash Drives Digital Photo Frames MP4 player

---

### Post by ringsofsaturn on 2009-01-10
Stream,

Thanks for the info re firewire, don't have any relevant leads so it's a non-starter.

Have tried to update 6.06 to 8.04 thro' update manager but it won't let me. Thought I might get Xubuntu 8.04 that way and get decent display but no joy. Think it's to do with 8.04 for PPC not being official and isn't in the repositories or some such. Read about editing a file in /etc/apt but forgotten which one at time of writing. Seemed very complicated to me and I'm rapidly losing patience with the project.

Feel quite "stuck". Can't install Debian as screen is so small I'd doubt I'd be able to modify the file you mentioned in previous post. In any case Debian was slow if you recall. Possibly the only way to install 8.04 (to get wireless) is from CD but then that will be Ubuntu and even with XFCE desktop it is VERY tardy. Is there any way of speeding distro up without resorting to buying more memory? At least there is enough of the display visible to modify the file you've previously mentioned.

Unlike yourself (and many others who inhabit this forum) I'm not a computer enthusiast really, I just want to use the old ibook to 'net surf wirelessly and do very basic tasks. All this "fiddling" is taking me much longer than anticipated which is no fault of anyone but myself, I do know that but.... :( .

If I can't resolve this soon, ibook is going "int' bin" as they say round here ;) .

Sorry to whinge, just feeling frustrated with the thing. You (and others) have been SO helpful and I'm very grateful for your efforts to explain what must be second nature to you to a slow-brained novice like me. Just don't send me the bill!!!!

Just where do you find the time?

Thanks once again.

---

### Post by stream303 on 2009-01-10
> **ringsofsaturn said:**
> Seemed very complicated to me and I'm rapidly losing patience with the project.

No problem - we've all been there. :)  You gave it your best shot.

> Unlike yourself (and many others who inhabit this forum) I'm not a computer enthusiast really, I just want to use the old ibook to 'net surf wirelessly and do very basic tasks. All this "fiddling" is taking me much longer than anticipated which is no fault of anyone but myself, I do know that but....

Don't be so hard on yourself - maybe return to it at a later time.  Reconfiguring files and whatnot just to get it to work isn't everyone's idea of fun.

You might want to make an attempt with OpenSuse before binning it. Perhaps it might get you over some of the hurdles if you don't mind downloading a DVD, or doing a netinstall.

[http://software.opensuse.org/](http://software.opensuse.org/)

Or just use OSX.  Maybe try using Firefox, or the Camino browser, Thunderbird for email etc as a way to stay in the FOSS camp.

Gotta' keep it fun that's for sure.

---

### Post by Archaeology_Student on 2009-01-10
Read through this...

Been a while since I played with Xubutu, but I feel I am ready to give it a shot again.

I have a Apple Lombard 333MHz with 512MB ram, and a 12GB hard drive. What is the most recent version of Xubuntu that I can install and run? From the posts, am I correct to assume 8.04 and 8.10 will not run on the Powerbook?

I saw a [download]("http://http://cdimage.ubuntu.com/xubuntu/ports/releases/8.10/release/") to 8.10 for PPC and was not sure.

---

### Post by ringsofsaturn on 2009-01-10
Hello Stream,

> You might want to make an attempt with OpenSuse before binning it. Perhaps it might get you over some of the hurdles if you don't mind downloading a DVD, or doing a netinstall

I'll take a look at OpenSuse but will have to attempt a netinstall as the ibook doesn't have a DVD drive. Wouldn't REALLY bin it, just feel like turning into a skimming stone at times :) . It's now back in a cupboard and I'll look at it again in the future.


Many, many thanks.

---

### Post by ringsofsaturn on 2009-01-10
> I have a Apple Lombard 333MHz with 512MB ram, and a 12GB hard drive. What is the most recent version of Xubuntu that I can install and run? From the posts, am I correct to assume 8.04 and 8.10 will not run on the Powerbook?

 6.06 runs OK on my ibook except for the wireless issue. Others seem to have installed 8.04 though.

---

### Post by ringsofsaturn on 2009-02-01
Hi Stream,

Quick update; I had brief attempt at oponsuse but despite burning 2 discs couldn't get ibook to boot (net install). Did a re-install of Debian Etch AND managed to reconfigure xserver so as display now A1. Yay! Amazed myself that I could do this :).So now have Debian running ok, slug-like but usable. STILL can't get it to work wirelessly with my Zyxel USB adaptor :( .

How did you get your G5 to go wireless?

BTW have posted on Debian forums but no reply as yet.

Thanks

---

### Post by ringsofsaturn on 2009-02-14
Hello again,

You may, or indeed may not, be interested to know how this issue was eventually resolved. 

After much search engine work (usually leading back to this forum) I installed Ubuntu 8.04 server edition with Xubuntu desktop. Ni problem setting up wireless with my Zyxel adapter but still had the previously mentioned display problem. Could not get screen to display more than 75% or so of the desktop.

I eventually modified the xorg.conf file as Stream wisely had suggested I save this file from my 6.06 install (which displayed just fine - wouldn't connect wirelessly though) and cut n'pasted  it's display/screen contents to 8.04's xorg.conf file. I made a multiplicity of mistakes with saving it and re-installed 8.04 on numerous occasions as I did not understand that I could save the previous xorg.conf flie :confused: ! Go on, have a laugh, I might just deserve it :lolflag: !!! Have probably installed various versions of Ubuntu/Debian over a dozen times on this ibook.Hmmm....Perhaps I deserve a plus for persistence (or  being just stubborn..?).

Anyway I gave myself one last go at this task so cut and pasted JUST the screen/display sections from 6.06 to 8.04 AND saved it correctly. I was  so confident in the knowledge that it would NOT work, so  whilst ibook was re-booting I deleted all my Linux bookmarks from my XP desktop  machine as I was DEFINITELY not going to EVER, EVER attempt this task again! 

And it worked, a wireless 8.04 ibook g3 with a proper display :). Amazing. 

Just shows what a non-technical person can do with help (from this forum) and a little determination. Please forgive me if I sound self-congratulatory, What I have achieved might be simple to most of you but to me it was a mammoth task.

Now all I need is the sound issue to be resolved, the over sensitive touchpad (it's on the least sensitive setting) and the foul plasticky smelling keyboard. Really is disgusting :evil:.

Thanks to all especially Stream 303.

---

