---
title: "xorg- minor mishap or disaster?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-10-02
Sorry about this ...

I tried installing a new graphics card. It is an AGP unit. I went into BIOS and recorded a preference for the AGP card rather than PCI.

Still no luck, so I followed some instructions and thought I'd installed some nvidia drivers. I then got into etc/X11/xorg.conf and edited out "savage"  after Device Drivers and replaced it with 'nvidia".

Now all I can get is the xorg messy screen, which means I can't get the graphical interface up and running. The last few comments mention that xorg couldn't load the nvidia module and that it doesn't exist, there are no drivers available, and that a fatal server error means no screens found.

There must be a way for me to interact with the xorg screen, so that I can get into etc/X11/xorg.conf or run another command .....is there?

Help greatly appreciated. 

Mike.

---

### Post by overdrank on 2007-10-02
> **MichaelSM said:**
> Sorry about this ...

I tried installing a new graphics card. It is an AGP unit. I went into BIOS and recorded a preference for the AGP card rather than PCI.

Still no luck, so I followed some instructions and thought I'd installed some nvidia drivers. I then got into etc/X11/xorg.conf and edited out "savage"  after Device Drivers and replaced it with 'nvidia".

Now all I can get is the xorg messy screen, which means I can't get the graphical interface up and running. The last few comments mention that xorg couldn't load the nvidia module and that it doesn't exist, there are no drivers available, and that a fatal server error means no screens found.

There must be a way for me to interact with the xorg screen, so that I can get into etc/X11/xorg.conf or run another command .....is there?

Help greatly appreciated. 

Mike.

Hi and what model of video card? You may try and reconfigure you xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nowshining on 2007-10-02
always deleting the xorg.conf file for me always let into a graphical interface - GUI - :)

Ctrl + alt + F1 then input ur username and then password
sudo /etc/init.d/gdm stop
sudo rm /etc/X11/xorg.conf
sudo /etc/init.d/gdm start

if not try a reboot by hitting ctrl + alt + delete

NOT backspace - the DELETE KEY.. but back up the xorg.conf file first unless ur willing to take a chance and in that case or u can try this

sudo /etc/init.d/gdm stop
cd to the folder of where the driver is downloaded
sudo sh and then the file name goes here --uninstall

now at the command prompt type the above again but not typing --uninstall you can go back a line by hitting the up arrow key and then hitting the backspace one by one until ur at the end of the driver extension .run and then hit enter.

u could ALSO at the command prompt do this

sudo nano /etc/X11/xorg.conf

nano is a command line text editor the ^ = the ctrl key 

I'm going to assume u'll know how to edit once in nano to save press ctrl + x
Then the letter Y then hit enter. :) make sure gdm is stopped first and then restart it or and if not do a reboot by pressing ctrl + alt + delete key.

---

### Post by MichaelSM on 2007-10-02
Hello again Overdrank! I think you've helped me before.....

The AGP card was given to me. It is a gigantic unit with huge heat sinks and a MGA chip on the back of it. It has VGA, DVI, ans S-video ports. I plugged it in to another box with Feisty (my main box is Edgy) and it worked like a charm, which was my testing procedure before trying it with the Edgy box.  Does that help?

BUT! I don't know how to access terminal on the Edgy computer from the xorg blue and white screen to run the command you have suggested, which I guess will re-configure xorg so that at least I can plug my monitor into the onboard video and go from there.

Hope that makes sense.

Thanks again.

Mike.

PS the onboard video is a ProSavage product. That's all I can tell you.

---

### Post by nowshining on 2007-10-02
press okay then u should be at the terminal then type ur username and then password. From there u'll have to stop gdm with the sudo /etc/init.d/stop command.

edit: it's called the COMMAND LINE INTERFACE or CLI for short. :) the terminal is just a GUI front end to it.

edit2: in other words I should of watched my words a little more. :/

---

### Post by PmDematagoda on 2007-10-02
Hey nowshining, you can't just remove the xorg.conf file in 6.10 because it doesn't have Bullet-proof X, only Gutsy does, so it will not work. But the problem about the driver may be because you don't have the necessary drivers. Get the Linux drivers for Nvidia here, install them and then post the results:-

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by overdrank on 2007-10-02
> **MichaelSM said:**
> Hello again Overdrank! I think you've helped me before.....

The AGP card was given to me. It is a gigantic unit with huge heat sinks and a MGA chip on the back of it. It has VGA, DVI, ans S-video ports. I plugged it in to another box with Feisty (my main box is Edgy) and it worked like a charm, which was my testing procedure before trying it with the Edgy box.  Does that help?

BUT! I don't know how to access terminal on the Edgy computer from the xorg blue and white screen to run the command you have suggested, which I guess will re-configure xorg so that at least I can plug my monitor into the onboard video and go from there.

Hope that makes sense.

Thanks again.

Mike.

PS the onboard video is a ProSavage product. That's all I can tell you.

Ok, nowshining has given you the info to help with you getting to the command line. Good luck!

---

### Post by nowshining on 2007-10-02
> **PmDematagoda said:**
> Hey nowshining, you can't just remove the xorg.conf file in 6.10 because it doesn't have Bullet-proof X, only Gutsy does, so it will not work. But the problem about the driver may be because you don't have the necessary drivers. Get the Linux drivers for Nvidia here, install them and then post the results:-

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

I think that it is also feisty that does this - however i think mine just reverts to the NVIDIA drivers located with the Ubuntu release tho - the resolution is a problem, however I didn't read the edgy part on there distro in the info. on the side or wherever urs is :P until late however If read correctly it should be pretty much the same.

---

### Post by MichaelSM on 2007-10-02
OK. I appreciate the mail.

I'll re-start the Edgy box with the AGP card out and the screen plugged into the onboard VGA.

I think I've tried what's been suggested. In other words, hit Enter when the OK is lit in red. There's a black line at bottom screen but I don't know how to get a command into it. It doesn't have a blinking cursor or anything.

Is there an F-command input I ought to use to get that?

Cheers.

Mike.

---

### Post by overdrank on 2007-10-02
> **MichaelSM said:**
> OK. I appreciate the mail.

I'll re-start the Edgy box with the AGP card out and the screen plugged into the onboard VGA.

I think I've tried what's been suggested. In other words, hit Enter when the OK is lit in red. There's a black line at bottom screen but I don't know how to get a command into it. It doesn't have a blinking cursor or anything.

Is there an F-command input I ought to use to get that?

Cheers.

Mike.

Hi you can use alt,ctrl, F1.

---

### Post by nowshining on 2007-10-02
try hitting enter and see what happens if it shows ur computer name/etc.. type ur username hit enter and then ur password note it will not be shown while you type so just type it out and hit enter and this also accours while doing anything with sudo.

---

### Post by MichaelSM on 2007-10-02
Hi everyone.

Your help was incredible!

I found the 'savage' note and all is up and running on this Edgy box.

To save all of you some time, is there a tutorial or how-to re. customizing my screen resolution?

I've got a 22-inch widescreen,. and fiddling through the xorg non-graphical interface, I had an opportunity to set the screen resolution and wound up with 1024x760 whilst my screen's native res.  is around 1600x1050. I'd like to get the higher res. back.

I obviously mucked it up when I was full of concerns ...

Back to the AGP monstrous card. It's only identification seems to be A1264-66501 Rev A. It has a mantrox mga chip and came from a graphical mapping machine. I think it's 32meg ...

My only reason for trying to use that card is that the ProSavage onboard video is maxed at 32 meg in BIOS and can't handle short movies without screen stutter.

Sorry about all the questions.

You guys are amazing with your patience.

Mike.

---

### Post by nowshining on 2007-10-02
maybe u got the wrong drivers because it looks like with the ID it's an Hewlett packard OEM video card. If nvidia works then that's great hmmm..odd tho..

---

### Post by nowshining on 2007-10-02
oh and what is a savage note by the way?? :) i could be wrong if u didn't use the Nvdia drivers.

---

### Post by MichaelSM on 2007-10-02
NowShining you have got it!

Up on one corner of the huge card is a 'HP' note!

I've just done the nvidia download scenario, plus ENVY which I haven't looked at yet.

Of course I'm back to the onboard 'savage' video card. What I meant by the 'savage note' was I figured out how to implement that card in a menu which appeared in the non-graphical interface after I entered 'sudo dpkg-reconfigure -phigh xserver-xorg' 'savage' was one of the options amongst many.

At least that got my screen back, which is why I can talk with you now.

So, back to the hp card.

It was free. Should I ditch it? HP has a way of  taking over things. I have an extra HP Vectra box and had to do a fair bit of niggling to tell it that it wasn't HP product any more.

Maybe I'm wasting my time with the big card. BUT! It was not an issue in my test box. It just plugged in and played.

I'll admit that my computer has a Shuttle motherboard, so I am at the **** end of the universe.

Any hints greatly appreciated.

Maybe I'll see what ENVY can do.

Very kindly your friend.

Mike.

---

### Post by MichaelSM on 2007-10-02
Back to square one.

I am amazed how resilient a computer can be. 

After plugging in and mucking around with all sorts of graphics cards, I'm fortunate to be back where I started. Sort of ... awful screen resolution etc. but at least up and running.I plugged in an SIS-chipped 3D card and thought that I was on a winner re xorg having learnt a bit how to manage it. I'd seen SIS in the non-graphical interface as an option along with lots of others. Too bad I couldn't get that card up.




Going back to my original comments re. the ginormous hp graphics card which fired up instantly 
in a very old box.

I think I must have a problem with my Shuttle motherboard.

That's all it can be ....

Thanks to all.

Mike.
Any ideas gratefully received and acted upon.

Mike.

---

### Post by nowshining on 2007-10-02
I suggest another card - i'm using a CHEAP 36dollar Fx5200 underclocked by the way - :P to surf the web in command line mode and lynx might be installed on edgy - type lynx and then the url

example:

```

lynx ubuntuforums.org

```

anyhow I don't know much on graphics for HP cards but I heard about how tough it was to get the branded HP printers to work... U may have a problem with the MotherBoard, or you could if you can try using a more recent version of Ubuntu such as feisty or the Upcoming Gutsy which by the way is much better. :P

---

### Post by master_kernel on 2007-10-02
Try reconfiguring xorg -- sudo dpkg-reconfigure xserver-xorg

---

### Post by MichaelSM on 2007-10-03
Hi if anyone is still watching this thread.

This morning (sober!) I managed totally to crash XORG on my Edgy box, trying to effect screen resolution changes. Put it this way, the /etc/X11/xorg.conf file is now completely empty, and yes I didn't back it up. 

I always intended to update to Feisty(I have a disc) and I guess this is the time to do it.

A couple of questions:

1) The Edgy install occupies only 8% of my hard drive, but I want to keep it there. I abandoned the Feisty install because I couldn't be sure of the partitioning as in there's a slider control and I don't know which way it works. As in does the slider govern what the new Feisty install will occupy, or does it regulate the space for the Edgy OS? In other words, I want the Edgy space at a bare minimum, and Feisty to be the major component.

2) There's a lot of good gear on the Edgy install. Will I be able to access it at any stage? I've read a few posts about partitioning and swapping files. Is that the way to go?

I am majorly embarrassed and was very foolish.

Any advice greatly appreciated, yet again!

Thanks everyone.

Mike.

---

### Post by nowshining on 2007-10-03
hehe, :P the slider got me to when I tried to use it myself so I just reformated. :P.

---

### Post by MichaelSM on 2007-10-03
Hi again Nowshining, and thanks for the follow-up!

Unfortunately I don't know what you mean by 're-formating.'

Can we talk about the only interface I have a hope of understanding, which is the Feisty install scenario and which way to move the slider?

Cheers as always,

Mike.

---

### Post by nowshining on 2007-10-04
re-formatting is the same as saying re-installing - when u first installed linux or any operating system today it will auto format the hard drive for you. You could read up more on what Formatting is. :)

---

### Post by MichaelSM on 2007-10-05
Hi Nowshining...

All is up and running again. Just took a bit of quiet figuring-out minus just a lot of worrying. 

Fortunately there is a computer recycler not far away and he gave me a pile of cards to fiddle with.

Thanks for your advices!

Great Forum, great people.

Mike.

---

### Post by nowshining on 2007-10-05
wow what parts did you get :) lucky you lucky you.. :P

---

### Post by MichaelSM on 2007-10-05
WOW! Fast reply ......

To cut a long story short. (No hope!)

Well, I assumed I'd killed any hope of getting into the gdm on the Edgy box. By inserting a command amongst many (can't remember but it was a result of a web page tutorial) next thing I know the /etc/X11/xorg.conf file was empty. DISASTER.

I have a few spare boxes from the tip, and a hard drive with Feisty on it. 

I put that drive into a box WITHOUT an onboard video card. I tried a few old cards, both PCI and AGP, until I got one which my new LCD screen could read the output of.  That was the hard bit.

Naturally I got the xserver crash, but I'd made sure I knew what chip was on the card, so, with previous experience I could happily do Ctrl+Alt+F1, then enter my login and password.

'sudo dpkg-reconfigure -phigh xserver-xorg'  was next, which

got me into the graphical interface which enabled a selection of drivers in a drop-menu to be accessed and by using the up/down arrow keys enabled me to find the relevant drivers for the chipset on the card I was using. In that case, with the Feisty hd in the box , I was using an old nVidia card, but something I read somewhere had suggested using the VESA drivers, which I selected. There were no updated nVidia drivers on the Feisty hard drive. That's important.

I had to pull out the power plug to re-boot. Got on line. BEWDY! So I knew the card worked. NOTE! With VESA drivers....! And excellent screen res. as well.

So I put the nVidia card into the Edgy box just for fun, knowing that previously I'd downloaded to Edgy the latest nVidia drivers. To my surprise and astonishment the boot-up went like a dream,  but instead of that funny-coloured gdm screen it went white. The little drums rolled but there was no login box. Hmm. Let's see, Michael. Very old nVidia card, latest nVidia drivers. Overload? Hmm.

Having learnt to manage the xserver-xorg crashes, I inserted  an old ATI card I had from the tip computers into the AGP slot on the Edgy box. At least I knew that ATI was on the drop-menu in reconfiguring xorg. Cool. Up and down arrows to find ATI. Tab>OK>Enter.Follow the prompts. Select screen resolutions with up and down arrows, using space bar to insert asterisks. Tab>OK>Enter. Re-boot. (I only went to 1200xwhatever becos that's all I wanted.)

To my delight I'm back on my Edgy hard drive. 

Screen resolution is just right. I could have more if i wanted it but no point.

The antique ATI card I'm using now on Edgy couldn't be better, but that's in an environment with 1.5g RAM. On the older Feisty box with a slower PIII processor, and only 300-odd megs RAM, I couldn't get screen resolution better than 800x600 with this ATI card.

HOWEVER! 

That little PIII box with Feisty and its tiny RAM, but with the ancient nVidia card running on VESA drivers will accomplish the  same screen resolution! With my big LCD monitor ...

This is a long answer to a short question.

I guess I hope others read our discourse.

There have been heaps of posts about this matter.

I have put in too much information, but there might be something to help others.

Mike.

PS. The only reason I got into this mess was trying to get rid of stutter and hang-ups with video replays. This only happened when I got my new screen. Fortunately the BIOS on my 'bigger' box, with its built-in card (Shuttle MB) defaults to whatever you plug in. One just has to select in BIOS whether its a PCI or AGP as preference. Also,l the ancient card I'm using is obviously pinching as much RAM as it can from the board. That card doesn't have any heat-sinks at all, so it must be running pretty hot. Better put the cover back on!

---

### Post by nowshining on 2007-10-05
i thought i told u in one of the posts to select VESA as the drivers. However I'm glad you got it working which is more important.

---

### Post by MichaelSM on 2007-10-05
Hi Nowshining.

In the midst of my worries, I forgot where that came from. 

That certainly helped with the Feisty hard drive, otherwise I wouldn't be talking with you now. Your VESA driver suggestion enabled the nVidia card to work in Feisty without a problem, which assisted me greatly with getting my Edgy hard drive up again on this other box.

I never properly replied to your 'lucky you'  except with balderdash. 

In Australia we've got some issues with 'obsolete' computers, as in the bloke who lends me graphics cards is running a small business which simply takes on piles of hardware sent from large companies doing an upgrade. Rather than sending the whole lot into land-fill,  Geoff extracts whatever he can which is useful and on-sells it. 

One of the great things about Linux distros is that they can run very happily on a PII or PIII processor, we just need a bit of extra RAM. 

Since a lot of companies are unfortunately being forced to upgrade their MS entourage, from XP to Vista, piles of handy bits and pieces turn up at my friend's small business.

A nine-year-old graphics card with a nice out-dated chip can do all I want. I'm not a gamer, and those dudes will move heaven and earth to accomplish what they need.

Most of us just wanna do what's reasonable. Geoff sells cheap computer modules to people who can't afford the latest whiz-bang. 

I couldn't imagine anything more horrid than being stuck with a problem re. graphics cards etc. and actually having to BUY one at vast cost, when the obsolete versions can swap memory and run just about anything. I am pretty new to computers, as you can tell, but a crap graphics card without much memory of its own can utilise whatever spare RAM is on the MB(in my case, a fair bit) even with an awful Shuttle all-in-one motherboard .

Thank you again for your help.

Mike.

---

### Post by nowshining on 2007-10-05
wow lucky :) we just throw our stuff in the garbage can here in California where I live. hehe oh and about the balderdash well that's quite alright.

---

### Post by MichaelSM on 2007-10-05
Hi Nowshining.

Well, that's the way it goes....

I for one am pretty rapt with maxing an obsolete graphics card or two!

It's just memory-sharing after all. Why buy something more than you already have?

Mike.

---

### Post by nowshining on 2007-10-07
oh my on my side my fx5200 or something is taking some memory however i disabled AGP modules and at startup, etc.. set internal graphics to 1mb - lowest it can go and i sill only have 503mb out of 512mb..so yeah as long as the Card doesn't use the CPU then ur fine. ;)

---

### Post by MichaelSM on 2007-10-07
Hi Nowshining. The difference between you and me is that you know what you're talking about, and and I only THINK that I do. 

Re. sharing RAM with the CPU. With the ancient graphics card.

I don't mind it at all. I bought another RAM card the other day, which got me up to 1.5 g which means I guess that the ancient graphics card pinches RAM from my CPU but if it works why worry?

I wish I knew more about this and I am embarrassed to make my lack of education known.

What you throw in the bin in California is food for small industry over here.

We aren't a poor country at all, by any means, but it's become more imperative to save and re-use useful parcels like RAM.

As you well know, Ubuntu can run like a dream on P2 and P3 chips. You just need enough  RAM.

Thank you again.

Mike.

---

### Post by nowshining on 2007-10-08
lolz 1.5g that's a lot - mine only takes 4gigs and I only 512mb, and lolz on the poor country and food part. ROFLMAO dude. About the know soo much - well I just read and try to understand and of course i did tweak windows TO DEATH which helped VERY little and messed it up more in the end. 

Don't worry tho I bet you know A lot of things I DO NOT know. ;) and I'm just glad u got all done and fixed. 

Yep the more RAM the better. :) however just to let u know an external card with an external CPU on itself will not use the CPU for graphics but a tiny bit, the RAM is shared tho with the Main computer a bit, an internal card utilizes both the CPU and CPU of the main computer which slows things down a bit and puts load on the computers' CPU which then in return just well like i said make things a bit slow.

---

### Post by MichaelSM on 2007-10-08
Hi Nowshining.

I think I know what you were getting at .... some of the time!

No, I never tried to 'tweak' Windoze and probably wouldn't have wanted to.

Yes it's hard-ish with Linux distros -and I've tried a few- but I'm happy as Larry with Ubuntu and won't be going anywhere else in the foreseeable future.

I came into computers fairly late -40's- and it's been a hazardous experience recently but that's called WANTING to learn something new, rather than stagnating on Windoze.

My youngest brother reckons I'm an idiot using Linux-anything. Yet he's the dope having to do  Windoze re-installs time after time, or sending his box into the fiix-it man to have his registry repaired and re-vitalised.

I like a bit of uncertainty. It's brain food mucking around with alternatives. Every disaster can be rectified with patience, and

Thanks to help from people like you.

Don't trip over the San Andreas fault line.

Cheers again,

Mike.

---

### Post by nowshining on 2007-10-09
lolz well if ur bro should install the OS himself or goonline which would actually be cheaper in the end to do since one is already paying for the Internet Connection the fixes are incl.

OOPs i tripped over the Andreas faultline - EARTHQUAKE..


:D

---

