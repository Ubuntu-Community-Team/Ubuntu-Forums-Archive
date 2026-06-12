---
title: "Thinking Of Swapping To Ubuntu"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Noyminibin on 2007-06-05
I currently use Vista and tb its a load of crap so i was thinking about starting to use ubuntu but only if you can confirm that the following things can be done.

The version i was thinking about using was going to be Ubuntu Ultimate 1.3

1.All of my hardware must be compatable the list is as follows
[LIST]
[*]Nvidia GeForce 7600 GT
[*]ASUS M2N - E Motherboard
[*]+ onboard sound card
[*]Logitech G15
[*]Logitech G7
[*]Epson stylus photo R300
[/LIST]

2. Must support dual view with 2 monitors
3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's
4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd
5. Must have beryl pre installed hence the reason why i was going to be using ubuntu ultimate
6. Must support the new ipod nano's
7. Any thing else that comes to my mind later.

---

### Post by phr0ze on 2007-06-05
I'm not sure why it must have beryl preinstalled... Seems easy enough to install after.

Boot the Ubuntu 7.04 CD and see if your devices work fine. Thats the best way to do it. You don't have to install it, just try it off the CD.

---

### Post by Noyminibin on 2007-06-05
I tried to install beryl on a different pc and had no luck i just ended up in screwing the pc up something about images or something carnt remember now

---

### Post by steeleyuk on 2007-06-05
The R300 does print using the Gutenprint driver, and it should be detected by Ubuntu (it did on Edgy for me) but I never managed to get the CD printing working. There are methods using The GIMP but I never managed it...

---

### Post by linux noooob on 2007-06-05
get ubuntu! i am not kidding it is awsome it runs so much smoother than windows it is compatible with all of the things you request exept i am not shure about the ipods. Also when installing it you can have two os's!! i run windows xp and ubuntu what happens is on boot up it will ask you if you want to use ubuntu or any other os you have! so if somthing does not work you can use it in vista!! (hint when using the demo live cd run in safe graphics mode it is so much faster and is the exact same!) it is really worth it and also if you are looking to make your computer total eye candy go to youtube and search:windows vista aero vs ubuntu beryl   and that will show you how much greater ubuntu is!!

ps. how do i post a thread? (i dont use forums that much)

---

### Post by steeleyuk on 2007-06-05
> **linux noooob said:**
> ps. how do i post a thread? (i dont use forums that much)

Click 'Make New Post' at the top of the screen...

---

### Post by Noyminibin on 2007-06-05
3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's
4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd

can any one answer these ?

---

### Post by Nekiruhs on 2007-06-05
well, in feisty, beryl is in the repositories (GIANT SOFTWARE SERVERS) so all you have to type is ```
sudo apt-get install beryl beryl-manager emerald-themer
``` and you should be good to go!
@ Above poster: Just press the new thread button above the thread list, its kind of orange/tan colored. I attached a screenshot to show.

---

### Post by steeleyuk on 2007-06-05
> 3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's

There is a Linux version of Nero or alternatively you can use Brasero or GnomeBaker (both installable from the repos)

---

### Post by Noyminibin on 2007-06-05
what are the repos can you give me a simple explenation that anyone can understand lol thanks ?

---

### Post by aysiu on 2007-06-05
I'll be honest. My instinct is telling me that you're not a good candidate for a Ubuntu migration.

Even if you can get dual monitors working on Ubuntu, which could be a real headache, your needs seem a bit particular (especially the part about Beryl being preinstalled... and keep in mind that Beryl is still beta software).

I guess a good question to ask yourself is: What do I hope to gain by using Ubuntu? What compromises am I willing to make to achieve those gains?

---

### Post by aysiu on 2007-06-05
> **Noyminibin said:**
> what are the repos can you give me a simple explenation that anyone can understand lol thanks ?
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Noyminibin on 2007-06-05
reading that it sound like you have to be a pc programmer to do anything in ubuntu why carnt they just use a simple .exe thing like in windows instead of having to type all this code and stuff into things to install anything ?

---

### Post by PhatStreet on 2007-06-05
> **Noyminibin said:**
> reading that it sound like you have to be a pc programmer to do anything in ubuntu why carnt they just use a simple .exe thing like in windows instead of having to type all this code and stuff into things to install anything ?
A.deb works essentially the same way as a Windows .exe install program. Apt-get/Synaptic Just makes the process easier and allows you to keep everything up to date automatically.

---

### Post by Nekiruhs on 2007-06-05
> **Noyminibin said:**
> reading that it sound like you have to be a pc programmer to do anything in ubuntu why carnt they just use a simple .exe thing like in windows instead of having to type all this code and stuff into things to install anything ?
If you really wanna know, heres the truth, its easier. In windows assume you want to install application X. Well, in order for application X you have to install framework Y (Java, .Net, w/e) and you must have program Z installed. One line ```
sudo apt-get install PROGRAM
```Does all that. Ill break it down

sudo - tells it to run as root (like run as administrator in windows)
apt-get - the software management tool
install - tells it to install it 
PROGRAM - name of the program

---

### Post by aysiu on 2007-06-05
> **Noyminibin said:**
> reading that it sound like you have to be a pc programmer to do anything in ubuntu why carnt they just use a simple .exe thing like in windows instead of having to type all this code and stuff into things to install anything ?
Well, considering I'm not a PC programmer (or any kind of programmer), I think you're exaggerating a little bit.

You might have missed the link to this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

Installing software is far easier in Ubuntu for the vast majority of software. But if you like to have the absolute latest and greatest (can't wait six months for a new release) or like to have weird obscure software, then, yes, you might have to start compiling software from source.

---

### Post by sailor2001 on 2007-06-05
typing code is half the fun. makes you feel like a quasi geek.......k2b is a really great dvd burner......
Beryl is on my desktop and stays on all the time (who knows when someone may drop in that I can entertain on the computer)...I only use ubuntu as windows has nothing to offer as far as I'm concerned.......by the way, happy to report that with 150,000 files, I only have 4gig used +600mb in boot and swap..... I've never had so much fun.......and this forum has to be the greatest ever

---

### Post by phr0ze on 2007-06-05
They have that too. Most people on here like to scare off the newbs with command line stuff. :o

Although, it is easy enough to copy and paste that command.

The dual monitors with Beryl might be extra tricky. And it may take some work and thought to relearn what you want to do. But it is worth it in the long run. There are just short-term down sides.

As far as burning ISO's, it's easy in ubuntu. Right click the ISO and select burn. On windows you have to install extra software for that.

---

### Post by jamesford on 2007-06-05
its not as complicated as it looks. sudo apt-get install mozilla-thunderbird does the same as opening a program called synaptic, search for thunderbird and click apply. both methods  will download and isntall thunderbird.
the reason howtos usually give u the text way of doing things is because its much quicker to tell the user to paste "sudo apt-get install mozilla-thunderbird" than  explaining the clicking process (go to the systems menu, click administration click synaptic, click search etc - plus that it will be called didfferent things in differend languages) it also minimizes the risk of the user doing smt wrong.

---

### Post by hummingbird59 on 2007-06-05
The best advice I was given is:

1.  Try it for two weeks via the Live CD or WUBI.  Make sure your hardware works to the extent you can live with it.
2.  BTW, the Live CD downside, is that it will not save any of your settings.   WUBI is nice because you can try Ubuntu without changing anything on your hard drive.
3.   If you like Ubuntu (and I bet you will if you enjoy learning something new), dual boot if you have the hard drive space.  That way, you'll have the best of both worlds until you can find a way to make everything work in Ubuntu.

Good luck and take your time!:D

---

### Post by lazyart on 2007-06-05
> **Noyminibin said:**
> I currently use Vista and tb its a load of crap so i was thinking about starting to use ubuntu but only if you can confirm that the following things can be done.

The version i was thinking about using was going to be Ubuntu Ultimate 1.3

1.All of my hardware must be compatable the list is as follows
[LIST]
[*]Nvidia GeForce 7600 GT
[*]ASUS M2N - E Motherboard
[*]+ onboard sound card
[*]Logitech G15
[*]Logitech G7
[*]Epson stylus photo R300
[/LIST]

2. Must support dual view with 2 monitors
3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's
4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd
5. Must have beryl pre installed hence the reason why i was going to be using ubuntu ultimate
6. Must support the new ipod nano's
7. Any thing else that comes to my mind later.

That's a scary list, especially #7.  And beryl is not necessarily stable.  I'm with our resident cat.  You are certainly invited to the party, but you might be disappointed with the punch.

---

### Post by Znupi on 2007-06-05
About installing sofware... I'm amazed no one introduced **Add/Remove...** so far. Here's how it works:

1. You go to **Applications -> Add/Remove...**
2. You get a (huge) list of software you can install. You can filter that by searching different categories (Games / Multimedia / etc)
3. You check a checkbox near the program you want to install.
4. You click Apply.

And you're done. Trivial!

I installed Beryl in less than 3 minutes. Of course, my case was a happy one, as I understood, few people achieve that.

Dual monitors... no idea, tricky.

DVD converter - I dunno, I never needed one, but I bet there is.
DVD burner - no probs there, there are a few good software for that.
iPods -- as far as I know there shouldn't be any problem with them. (I don't own one)

---

### Post by Noyminibin on 2007-06-05
OK if the dual view thing is hard to do then i guess i can live with 1 monitor lol seen as you have desktop spaces to use. So the only question tleft to answer is #4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd

---

### Post by Znupi on 2007-06-05
Ok, so I opened up **Add/Remove...** and typed in '**dvd**'. So like the 10th or so result was this:
[QUOTE=Add/Remove]
AcidRip
ripping and encoding DVD tool using mplayer and mencoder 
AcidRip is a Gtk::Perl application for ripping and encoding DVD's. It neatly wraps MPlayer and MEncoder, which I think is pretty handy, seeing as MPlayer is by far the best bit of video playing kit around for Linux. As well as creating a simple Graphical Interface for those scared of getting down and dirty with MEncoders command line interface, It also automates the process in a number of ways:
[http://acidrip.thirtythreeandathird.net/](http://acidrip.thirtythreeandathird.net/)
Version: 0.14-0.2ubuntu4 (acidrip)
[/QUOTE]
I suppose that's what you need? :)

**Edit**: It seems that link is broken. Here's its homepage: [http://untrepid.com/acidrip/](http://untrepid.com/acidrip/)

---

### Post by aysiu on 2007-06-05
By the way, you may want to read this:
[A home user&#8217;s successful migration strategy from Windows to Ubuntu](http://ubuntucat.wordpress.com/2007/05/25/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)

---

### Post by viciouslime on 2007-06-05
> **Noyminibin said:**
> I currently use Vista and tb its a load of crap so i was thinking about starting to use ubuntu but only if you can confirm that the following things can be done.

The version i was thinking about using was going to be Ubuntu Ultimate 1.3

1.All of my hardware must be compatable the list is as follows
[LIST]
[*]Nvidia GeForce 7600 GT
[*]ASUS M2N - E Motherboard
[*]+ onboard sound card
[*]Logitech G15
[*]Logitech G7
[*]Epson stylus photo R300
[/LIST]

2. Must support dual view with 2 monitors
3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's
4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd
5. Must have beryl pre installed hence the reason why i was going to be using ubuntu ultimate
6. Must support the new ipod nano's
7. Any thing else that comes to my mind later.

I can confirm everysingle one of these except the logitech stuff in point 1 and point number 2 as I haven't done this myself. All the other things I do on ubuntu myself though and can give you any help you need. Also, it is worth noting that there are lots of guides for dual-screens so this shouldn't be too hard.

As for using ubuntu ultimate, if the only reason was for beryl then it porbably isn't worth it. I haven't tried ubuntu ultimate myself, but in feisty fawn it is now one click enabling of compiz and two/three click install of beryl. Couldn't be much simpler :)

---

### Post by Noyminibin on 2007-06-05
so is this feisty fawn ? [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and the edscription for acidrip just hurts my head lol this is what convertxtodvd looks like if you havnt seen it before and it is something like this that i am looking for

[IMG]http://www.vso-software.fr/faq/create_menu/create_menu_DVD_with_convertxtodvd_clip_image005.jpg[/IMG]

---

### Post by aysiu on 2007-06-05
Ubuntu 7.04 (Feisty Fawn)
6.10 (Edgy Eft)
6.06 (Dapper Drake)
5.10 (Breezy Badger)
5.04 (Hoary Hedgehog)
4.10 (Warty Warthog)

---

### Post by Nekiruhs on 2007-06-05
Version 7.04 is Feisty Fawn. Feisty Fawn is the dev name for it, and just like the others (6.10 = Edgy Eft, 6.06 LTS = Dapper Drake) its sticks really well to the release.
EDIT: Darn beat to it. BTW, Aysiu, I need your help bad, see my thread.

---

### Post by Rui Pais on 2007-06-05
> **Noyminibin said:**
> OK if the dual view thing is hard to do then i guess i can live with 1 monitor lol seen as you have desktop spaces to use. So the only question tleft to answer is #4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd

just to add my 2ct. 
dual boot was tricky and hard in the past. 
It still is, except if one have a NVidia card (that you have :)) 
In that case is pretty much run nvidia-settings, set what you want in the graphical interface and save (boring, boring i know)

But i agree with one thing others have said... You sound like someone that will have troubles with Linux.
Check first liveCD, and, of course, go with dual boot.

---

### Post by Znupi on 2007-06-05
> **Noyminibin said:**
> so is this feisty fawn ? [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and the edscription for acidrip just hurts my head lol this is what convertxtodvd looks like if you havnt seen it before and it is something like this that i am looking for

[IMG]http://www.vso-software.fr/faq/create_menu/create_menu_DVD_with_convertxtodvd_clip_image005.jpg[/IMG]
And this is how AcidRip looks like:
[IMG]http://taltan.free.fr/images/screenshot/acidrip02.png[/IMG]
It's not the same exact interface, but the purpose is the same. If you take 10 or so minutes I bet you can get the hang of it. If you can't, you can try to wine ConvertXtoDVD

---

### Post by shearn89 on 2007-06-05
> 4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd

I found this after a quick google search:

[http://www.linuxjournal.com/article/6953](http://www.linuxjournal.com/article/6953)

doesn't look as simple as your method, but it means that there are perhaps other tools out there... Thats one of the great things in linux - a quick google search/repo search will more often than not turn up someone/thing to solve your problem, and the various communities provide much better support than manufacturers websites...

---

### Post by Noyminibin on 2007-06-05
Looks simple enough to use from that ss just one question can use backgrounds and menus ?

And it might sound like a total noob question just like the rest of my questions lol but what do you mean by you can try to wine ConvertXtoDVD

---

### Post by aysiu on 2007-06-05
Wine is a compatibility layer that allows you to run *some* native Windows applications in Linux:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Znupi on 2007-06-05
It seems like it [works under wine](http://appdb.winehq.org/appview.php?iVersionId=6294) with only one problem: no preview.

---

### Post by Noyminibin on 2007-06-05
kk a preview isnt that important anyway so does wine come with 7.04 or do you have to download it throught that add/remove thing ?

---

### Post by Noyminibin on 2007-06-05
something else has poped in to my mind that i need, a cover printing program like cover xp

---

### Post by aysiu on 2007-06-05
> **Noyminibin said:**
> something else has poped in to my mind that i need, a cover printing program like cover xp
Like [kover](http://packages.ubuntu.com/feisty/graphics/kover)? > Kover is a WYSIWYG CD cover printer. You have the ability to enter the title, contents, set background colors, enter text, embed images or stream the title and tracks from CDDB (including CDDB Code 211). Kover can authenticate through a proxy (Basic, but not Digest) for accessing CDDB, and make a CDDB request just by entering the CDDB ID (i.e., no need to have the CD inserted).

I think you're getting way ahead of yourself, though. Start with the live CD. Play around with Ubuntu a bit. Get to know package management.

The migration shouldn't happen overnight.

---

### Post by Noyminibin on 2007-06-05
i think you misunderstud me all cover xp is is a program that resizes images so that they are the same size as a dvd cover

---

### Post by Znupi on 2007-06-05
> **Noyminibin said:**
> kk a preview isnt that important anyway so does wine come with 7.04 or do you have to download it throught that add/remove thing ?
Just run
```

sudo apt-get install wine

```
in a terminal.

Don't know about the cover thing.

But like aysiu said, you should first try the LiveCD and possibly install Ubuntu and some basic things you need... Then you should start fiddling around and looking for cover makers :-P.

---

### Post by aysiu on 2007-06-05
> **Noyminibin said:**
> i think you misunderstud me all cover xp is is a program that resizes images so that they are the same size as a dvd cover
How about [*koverartist*](http://packages.ubuntu.com/feisty/kde/koverartist), then? > The main idea behind KoverArtist is to be able to create decent looking covers with some mouseclicks.

Homepage: [http://kde-apps.org/content/show.php?content=38195](http://kde-apps.org/content/show.php?content=38195)  I still think you should run a live CD and just get to know Ubuntu. You can easily browse for applications using the package manager (something Windows doesn't really have). It's a whole new world.

---

### Post by Noyminibin on 2007-06-05
kk so how do i install beryl in 7.04 in like 3 clicks like someone said before ?

---

### Post by aysiu on 2007-06-05
> **Noyminibin said:**
> kk so how do i install beryl in 7.04 in like 3 clicks like someone said before ?
I don't know if it's *three* clicks, but it is all clicking.

First, you'd have to enable the Nvidia drivers:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

Then you go to Applications > Add/Remove, look for Beryl, and check the boxes for it. Then click Apply.

---

### Post by Znupi on 2007-06-05
> **aysiu said:**
> Then you go to Applications > Add/Remove, look for Beryl, and check the boxes for it. Then click Apply.

Hmm... are you sure that will work? Will that create the Xgl session, too?

---

### Post by aysiu on 2007-06-05
> **Znupi said:**
> Hmm... are you sure that will work? Will that create the Xgl session, too?
It worked for me. I tried Beryl a few days ago (didn't like it, went back to Metacity).

---

### Post by Znupi on 2007-06-05
> **aysiu said:**
> It worked for me. I tried Beryl a few days ago (didn't like it, went back to Metacity).
It works (at least for me) with Metacity, too. Just right-click on the gem and choose **Select Window Decorator -> Heliodor (GNOME/Metacity Decorator)**. All the effects will work, only you'll have metacity-like windows. Was that your problem or did I understand something else?

---

### Post by aysiu on 2007-06-05
> **Znupi said:**
> It works (at least for me) with Metacity, too. Just right-click on the gem and choose **Select Window Decorator -> Heliodor (GNOME/Metacity Decorator)**. All the effects will work, only you'll have metacity-like windows. Was that your problem or did I understand something else?
I didn't have a problem, actually. I didn't like all the effects. I don't like wobbly windows or genie effects, or zooming in and out. I'm a plain Jane kind of guy.

---

### Post by LostArt on 2007-06-05
> **Noyminibin said:**
> I currently use Vista and tb its a load of crap so i was thinking about starting to use ubuntu but only if you can confirm that the following things can be done.

The version i was thinking about using was going to be Ubuntu Ultimate 1.3

1.All of my hardware must be compatable the list is as follows
[LIST]
[*]Nvidia GeForce 7600 GT
[*]ASUS M2N - E Motherboard
[*]+ onboard sound card
[*]Logitech G15
[*]Logitech G7
[*]Epson stylus photo R300
[/LIST]

2. Must support dual view with 2 monitors
3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's
4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd
5. Must have beryl pre installed hence the reason why i was going to be using ubuntu ultimate
6. Must support the new ipod nano's
7. Any thing else that comes to my mind later.

Why not try installing Ubuntu studio to begin with, then you'll have a lot of "creative" programs preinstalled.
But I agree with the cat man, (or woman, don't want to appear sexist) give the live cd a try, ubuntu is not for everybody.

---

### Post by caro on 2007-06-05
> **Noyminibin said:**
> I currently use Vista and tb its a load of crap so i was thinking about starting to use ubuntu but only if you can confirm that the following things can be done.

The version i was thinking about using was going to be Ubuntu Ultimate 1.3

1.All of my hardware must be compatable the list is as follows
[LIST]
[*]Nvidia GeForce 7600 GT
[*]ASUS M2N - E Motherboard
[*]+ onboard sound card
[*]Logitech G15
[*]Logitech G7
[*]Epson stylus photo R300
[/LIST]

2. Must support dual view with 2 monitors
3. Must be able to run nero or some other dvd burner that can burn dvd movies and iso's
4. A dvd converter that can put menus in to hte dvds preferable ConvertXtoDvd
5. Must have beryl pre installed hence the reason why i was going to be using ubuntu ultimate
6. Must support the new ipod nano's
7. Any thing else that comes to my mind later.

I could be reading you wrong, but it sounds like you want everything to work just as it does with Windows.  Ubuntu is very easy to use, but you have to be open to learning some new things -- you may even find programs you like better than you are using in your Windows environment.  

Like others suggested, give LiveCD a try first.  I did and found I liked Ubuntu enough to switch.  I haven't booted my Windows computer in 5 days and have been able to do everything I want.  Good luck.

---

### Post by Noyminibin on 2007-06-06
I have managed to install the dual view and beryl myself can any one guide me through installing my printer the epson r300

---

### Post by Rui Pais on 2007-06-06
> **Noyminibin said:**
> I have managed to install the dual view and beryl myself can any one guide me through installing my printer the epson r300

run gnome-cups-manager and simply choose your printer from the Epson section (it should be auto detected, but if not, just search on the dropdown list)

---

### Post by Noyminibin on 2007-06-06
can someone tell me how to install nero or do you have to pay if you do can someone tell me how to install another program that does the same things it must be able to burn dvd video files

# The printers working now thanks by the way

---

### Post by Rui Pais on 2007-06-06
> **Noyminibin said:**
> can someone tell me how to install nero or do you have to pay if you do can someone tell me how to install another program that does the same things it must be able to burn dvd video files

# The printers working now thanks by the way

yes,  nero is payed (they have a trial version but must have limitations or a period of time of activity)

Try k3b (is for KDE but runs nicely on gnome or anyother) that may be more similar to nero or check brasero (never use it, but read a lot of people talk nice of this). 
Or try both and make you mind after trying ;)

Edit: only now i read you done the printer (easy isn't it?)

---

### Post by Noyminibin on 2007-06-06
I think i have just about everything i need just need to test convertxtodvd and k3b just one more thing azearus or utorrent ?

---

### Post by Dennis the Menace on 2007-06-06
> **hummingbird59 said:**
> The best advice I was given is:

1.  Try it for two weeks via the Live CD or WUBI.  Make sure your hardware works to the extent you can live with it.
2.  BTW, the Live CD downside, is that it will not save any of your settings.   WUBI is nice because you can try Ubuntu without changing anything on your hard drive.
3.   If you like Ubuntu (and I bet you will if you enjoy learning something new), dual boot if you have the hard drive space.  That way, you'll have the best of both worlds until you can find a way to make everything work in Ubuntu.

Good luck and take your time!:D


That's exactly what I'm doing now,I've only ever used XP but I've installed Ubuntu on my spare HD and having loads of fun learning different things [mostly via this GREAT forum and the links they provide], I've got the added security of knowing that if I do manage to mess up I can re-install via the live cd and start again, a lot easier and quicker than re-installing windows, which btw always seems to manage to mess itself up.
Thanks to all for what I'm learning.
keep up the good work.

---

### Post by Rui Pais on 2007-06-06
> **Noyminibin said:**
> I think i have just about everything i need just need to test convertxtodvd and k3b just one more thing azearus or utorrent ?

Those are torrent clients, isn't it? Just launch synaptic and do a seach for the word "torrent"
azureus can of course be installed directly (utorrent i think is an app exclusively for Windows... not sure):
sudo apt-get install azureus

---

### Post by Noyminibin on 2007-06-06
i thought utorrent was for linux as well i'll just use azureus anyway

---

### Post by Nekiruhs on 2007-06-06
> **Noyminibin said:**
> I think i have just about everything i need just need to test convertxtodvd and k3b just one more thing azearus or utorrent ?
Well, uTorrent runs very nicely on wine. Theres also linux native Deluge, and Frostwire operates both the Gnutella Protocol (Same as Limewire) and BitTorrent.

---

### Post by Rui Pais on 2007-06-06
> **Noyminibin said:**
> i thought utorrent was for linux as well i'll just use azureus anyway

i don't know utorrent (never use it, i mean)
but according to its site a linux version is just planned:
[http://www.utorrent.com/faq.php#Is_there_a_Linux_or_Mac_version.3F](http://www.utorrent.com/faq.php#Is_there_a_Linux_or_Mac_version.3F)

edit: Nekiruhs was fast and gives a nice suggestion :)

---

### Post by Noyminibin on 2007-06-06
I have a  second hard drive in my pc how do i wipe it so that its blank so i can get rid off all the old windows stuff on it and then put just general files on it ?

---

### Post by Rui Pais on 2007-06-06
Use gparted. 
Don't know if it's installed by default but you can easily apt-get it.
Just delete partitions and format as you which (ext3 better for safeness, xfs better for big files, vfat if you want to make a shared partition with Windows).

You can then mount them on My Computer at nautilus or adding them to /etc/fstab if you want the partitions always mounted.

---

### Post by Noyminibin on 2007-06-06
and 2 more questions for now as well as the one about wiping the second hard drive

1. How do i get beryl to start when i start up the pc instead of having to load it each time.
2. How do i play the bbc radio player without having to play it in wmp then choose use standalone player then taking that url and loading it in to vlc to play it ?

---

### Post by Noyminibin on 2007-06-06
also a firewall anti virus anti spyware programs

---

### Post by aysiu on 2007-06-06
> **Noyminibin said:**
> also a firewall anti virus anti spyware programs
Not needed:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Nekiruhs on 2007-06-06
> **Noyminibin said:**
> and 2 more questions for now as well as the one about wiping the second hard drive

1. How do i get beryl to start when i start up the pc instead of having to load it each time.
2. How do i play the bbc radio player without having to play it in wmp then choose use standalone player then taking that url and loading it in to vlc to play it ?
For Beryl goto 
System > Prefrences > Sessions click the buttoon with a plus sign on it and add the command  beryl-manager

---

### Post by Noyminibin on 2007-06-06
kk so theres no need to have protection on ubuntu i have just done the beryl thing will have to wait until i restart me pc to see if it worked.

# and does any one know a good pop up blocker for firefox

---

### Post by Crafty Kisses on 2007-06-06
> **linux noooob said:**
> get ubuntu! i am not kidding it is awsome it runs so much smoother than windows it is compatible with all of the things you request exept i am not shure about the ipods. Also when installing it you can have two os's!! i run windows xp and ubuntu what happens is on boot up it will ask you if you want to use ubuntu or any other os you have! so if somthing does not work you can use it in vista!! (hint when using the demo live cd run in safe graphics mode it is so much faster and is the exact same!) it is really worth it and also if you are looking to make your computer total eye candy go to youtube and search:windows vista aero vs ubuntu beryl   and that will show you how much greater ubuntu is!!

ps. how do i post a thread? (i dont use forums that much)
I agree, I think Ubuntu is really better than Windows, I swapped from Windows and that's the best thing I've ever done.

---

### Post by jellygoeswobble on 2007-06-06
Everything on your list works, including ipod support. Plus its all ridiculously easy to set up. Go for it, you wont wnat to go back! Try Dual- booting with windows vista as your optional boot if you want first. If you need help on this, type 'dual booting' into these forums. Hope this helps!

---

### Post by Noyminibin on 2007-06-06
I have done everything the only thing i need doing is

1. A good pop up blocker for firefox
2. How do i play the bbc radio player without having to play it in wmp then choose use standalone player then taking that url and loading it in to vlc to play it ?
3. A dvd encoder like convertxtodvd where you can have menus
4. And possibly being pointed in the direction to a copy of nero for linux

---

### Post by Shazaam on 2007-06-06
Pop-up blocker- open Firefox-Edit-Preferences
Open Content tab.
Make sure Block popups is checked.
Open Advanced next to Enable Javascript- uncheck all boxes in the window that opens.
Go to Tools-Extensions-Get more extensions and search for NoScript and AdBlock.

Nero- (NOT FREE!)  [http://www.nero.com/enu/NeroLINUX_Info_Page.html](http://www.nero.com/enu/NeroLINUX_Info_Page.html)

---

### Post by aysiu on 2007-06-06
Nero for Linux costs money, and I've heard it's not as fully featured as Nero for Windows:
[http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html)

Why not just use K3B or Gnomebaker? Those are free and fully-featured CD/DVD burning programs.

I'm not sure why you need a pop-up blocker for Firefox. Maybe you should install NoScript:
[http://noscript.net/](http://noscript.net/)

---

### Post by LCC on 2007-06-06
As a heavy multimedia user I can tell you that we got everything we need in this sector but because most softwares are still having bugs to be fixed you might find it frustrating at first but if you are going to give it a try don`t give up and perhaps stay with dual boot for a while toll you`re fully confident to format the windows partition or at least reduce it to a minimum, I would suggest k3d and if you need a basic video converter try iriverter, if you need a video editor you could try KDEnlive (still beta but accepts most known codecs out there)
or you could use Lives, not that many bugs but it takes a while to import the videos. But over all remember that the best thing in Ubuntu is the support you can have here on the community.

---

### Post by fjf on 2007-06-06
DVDshrink works in wine:  [http://ubuntuforums.org/showthread.php?t=36112](http://ubuntuforums.org/showthread.php?t=36112)

---

### Post by Noyminibin on 2007-06-06
Just gone to burn a video dvd after encoding it in convertxtodvd in k3b and i get the following error message "could not determine size of resulting image file"

The debugging output is:

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4167B DL12 (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.2

mkisofs
-----------------------
Unknown file type (unallocated) /tmp/kde-craig/k3bVideoDvd0/.. - ignoring and continuing.
Unknown file type (unallocated) /tmp/kde-craig/k3bVideoDvd0/.. - ignoring and continuing.
/usr/bin/genisoimage: No such file or directory. 
Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: 
Can't open VMG info for '/tmp/kde-craig/k3bVideoDvd0/'.
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-craig/k3bVideoDvd0/'.
/usr/bin/genisoimage: 
Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: No such file or directory. 
Can't stat 109509_the_loudness_war_1/
/usr/bin/genisoimage: No such file or directory. Can't stat 109509_the_loudness_war_1/
/usr/bin/genisoimage: 
Can't open device '109509_the_loudness_war_1/'
/usr/bin/genisoimage: Can't open device '109509_the_loudness_war_1/'
/usr/bin/genisoimage: 
Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: 
Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid 109509_the_loudness_war_1 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-craig/k3b5Fedgc.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-craig/k3becLENb.tmp -dvd-video -f /tmp/kde-craig/k3bVideoDvd0

Any ideas ?

---

