---
title: "MythTV Questions!"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-01
Ok so I had ago at installing MythTV today. And It's awesome. I have not setup the TV section yet as I don't have a tuner card yet. I couldn't wait to play around with MythTV.

I'm very happy with the music, weather and DVD features. But I do have some questions about MythTV about how I can get more out of it, and about how it works.

I used this [gudie]("http://parker1.co.uk/mythtv_dapper.php") here to setup MythTV but insted used xubuntu because that was what I had. Since I have found this [gudie]("https://help.ubuntu.com/community/MythTV_Dapper_Frontend") and I'm thinking that this way might be better because it is ligther? but its only a "frontend"?

So could somebody please tell me if this is a better way to go? And what is the differnece between the frontend and the backend? is the frontend the part I see on my screen? Does it make sence to have just a frontend? Some help on this subject will be very helpfull.

Now for my next question. Can I add my own menu/entrees etc. I want to be able to play backed up DVD images. So I would like to add entrees for each move like so
```
xine dvd://path/to/dvd.iso
```

Anyone please help.

Edit: Also any ideas on what sort of remote I should get?

---

### Post by Titus A Duxass on 2007-01-02
If you want a stand-alone myth box then you need a Backend/Frontend combination.  For more info read the ubuntu guide: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

For tailoring menus take a look at this [http://www.myhdbox.com/mythtips/2006/04/tip-2-how-to-customize-mythtvs-menus.php](http://www.myhdbox.com/mythtips/2006/04/tip-2-how-to-customize-mythtvs-menus.php).

For the Remote, I have no idea.  I am looking for a suitable one myself.

---

### Post by superm1 on 2007-01-03
> **guysmiley25 said:**
> Ok so I had ago at installing MythTV today. And It's awesome. I have not setup the TV section yet as I don't have a tuner card yet. I couldn't wait to play around with MythTV.

I'm very happy with the music, weather and DVD features. But I do have some questions about MythTV about how I can get more out of it, and about how it works.

I used this [gudie]("http://parker1.co.uk/mythtv_dapper.php") here to setup MythTV but insted used xubuntu because that was what I had. Since I have found this [gudie]("https://help.ubuntu.com/community/MythTV_Dapper_Frontend") and I'm thinking that this way might be better because it is ligther? but its only a "frontend"?

So could somebody please tell me if this is a better way to go? And what is the differnece between the frontend and the backend? is the frontend the part I see on my screen? Does it make sence to have just a frontend? Some help on this subject will be very helpfull.

Now for my next question. Can I add my own menu/entrees etc. I want to be able to play backed up DVD images. So I would like to add entrees for each move like so
```
xine dvd://path/to/dvd.iso
```Anyone please help.

Edit: Also any ideas on what sort of remote I should get?
Well I wrote the dapper and edgy guides at help.ubuntu.com so of course i'll be a bit biased, but you know how I would feel about that ;)

Using Xubuntu is also a very lightweight way to go.  The big difference between following the help.ubuntu.com guide will be that it will walk you through step by step and use openbox.  The machine will be tailored specifically for exclusive mythtv usage.

The idea for the backend is that this is where you will have mysql installed, where your tuners will be and where a lot of the hard processing happens.  The frontend can be on this same machine, or another machine elsewhere on your network.  The frontend baiscally is where you have all the interface stuff.  So if you have just one machine, you have a backend/frontend.  If you want to be able to do other stuff with it other than myth, its a backend/frontend/desktop.

As for playing your DVD iso's, if you have mythvideo include .iso as a valid type, it will show up in mythvideo.  You will have to go to mythvideo settings and add .iso as an extension.  Put all your ISOs in a common place, and allow mythvideo to read all of its files from this area.

---

### Post by SyvanX on 2007-01-03
What tuner are you using?  I have a Hauppauge remote that came with the PVR-350 and I really like it.  

You should be able to set up your lirc to use pretty much any remote, so you can find a remote you like and check for a config file.  You can use superm1's How To to get it all configured.
[Lirc Config files]("http://lirc.sourceforge.net/remotes/")

---

### Post by guysmiley25 on 2007-01-05
Thanks for all the guys, that has straighten it all out for me.

Thanks superm1 I have done so with mythvideo to play iso and it works just how I like :-) .

Just a couple of things. What is the benefit of having a machine as a frontend an other as a backend? In what situations would you do this?

Also I have not got a TV tuner card yet or a remote and I would like some help choosing. I have cable TV and I would like to be able to use it without using the box they gave me. I heard this could be done. I want either one that can show/record two or more channels at once or I guess I want two or more cards. Also they do not yet have in New Zealand (Where I am) have HDTV but I do believe that it is just a matter of time so I would like to be prepared.

I have found [this]("http://www.ascent.co.nz/productspecification.aspx?ItemID=349072") one here but I'm not sure if it will do what I want.

[http://www.ascent.co.nz/]("http://www.ascent.co.nz/") is probably where I'll be getting them from so yeah.

Thanks for the help guys.

---

### Post by superm1 on 2007-01-05
> **guysmiley25 said:**
> Thanks for all the guys, that has straighten it all out for me.

Thanks superm1 I have done so with mythvideo to play iso and it works just how I like :-) .

Glad this worked :D

> **guysmiley25 said:**
> Just a couple of things. What is the benefit of having a machine as a frontend an other as a backend? In what situations would you do this?

Well if you have a bunch of frontends (like in my apartment), it silly to have a backend on each one.  That is way too many tuners and too much money.  It makes more sense to have just frontends on these boxes.  I do it mainly for stability.  If something goes wrong with one of my frontends, its not that big of a deal, because things still record and I can figure out what happened to it.  For a starting user a backend/frontend is the way to go, but as your network grows, and you see more uses for the box, you might consider adding a backend only machine instead/in addition.

> **guysmiley25 said:**
> 
Also I have not got a TV tuner card yet or a remote and I would like some help choosing. I have cable TV and I would like to be able to use it without using the box they gave me.

Well the hauppauge pvr-*** cards are really the way to go.  They work wonderfully for anything NTSC.  If you are living somewhere that you get DVB though (which I gather you might), you might want to look into a DVB tuner instead since you can pick up a lot more content this way.  I don't know much about DVB though since i'm a US user.  I can help you with any information about US broadcasting stuff (HD/ATSC/OTA, HD/QAM256/cable, regular OTA, regular cable).

As for a remote, some of the tuner cards come with remotes.  I'm personally very fond of the microsoft mceusb2 remotes.  You can find PVR-150 combos that comes with these.  Also, i've heard some pvr-150s come with hauppauge remotes, and these work well too.

> **guysmiley25 said:**
> 
 I heard this could be done. I want either one that can show/record two or more channels at once or I guess I want two or more cards. Also they do not yet have in New Zealand (Where I am) have HDTV but I do believe that it is just a matter of time so I would like to be prepared.

Should have read further before typing the start of my reply!  Do you guys use DVB in new zealand?  If not, then a PVR-500 will suit your fancy.  Its basically 2 PVR-150s in one.

> **guysmiley25 said:**
> 
I have found [this]("http://www.ascent.co.nz/productspecification.aspx?ItemID=349072") one here but I'm not sure if it will do what I want.

[http://www.ascent.co.nz/](http://www.ascent.co.nz/) is probably where I'll be getting them from so yeah.

Thanks for the help guys.
If you guys do indeed use DVB out there, that is the way you have to go with that card from what I gather.  You will have to double check with someone out there that is experienced in that area to make sure though. :)

---

### Post by guysmiley25 on 2007-01-05
Ahh OK I see. What I meant was Digital indeed. We do not have it but it is meant to be coming later on this year. When I did a search for DVB in New Zealand stores I only found three cards. I guess this is because there is no need for them yet.

I do not know a lot about TV broadcast but I am guessing that DVB is "Digital Video Broadcast" and that's the new digital way opposed to the analog system. Or I could be very wrong. I'm not sure if it is Digital or HD nor do I know the difference. However I know I want to use cable,

Also here we use PAL as opposed to NTSC, what is the difference anyways? I don't think this is a problem because all the cards I have found say that they can do NTSC/PAL or PAL.

So I have found two cards:

[Hauppauge WinTV-PVR-500MCE]("http://www.ascent.co.nz/productspecification.aspx?ItemID=342426")
[Hauppauge WinTV-PVR-500MCE with Remote]("http://www.ascent.co.nz/productspecification.aspx?ItemID=344815")
[Leadtek WinFast PVR2000 with Remote]("http://www.ascent.co.nz/productspecification.aspx?ItemID=224358")

Now the WinTV-PVR-500MCE card look good for what I want. Because it's like two cards. But the Leadtek WinFast PVR2000 implies more to me that it will work with cable. What are your thoughts?

Thanks for all the helps so far.

---

### Post by superm1 on 2007-01-05
> **guysmiley25 said:**
> Ahh OK I see. What I meant was Digital indeed. We do not have it but it is meant to be coming later on this year. When I did a search for DVB in New Zealand stores I only found three cards. I guess this is because there is no need for them yet.

I do not know a lot about TV broadcast but I am guessing that DVB is "Digital Video Broadcast" and that's the new digital way opposed to the analog system. Or I could be very wrong. I'm not sure if it is Digital or HD nor do I know the difference. However I know I want to use cable,

Also here we use PAL as opposed to NTSC, what is the difference anyways? I don't think this is a problem because all the cards I have found say that they can do NTSC/PAL or PAL.

So I have found two cards:

[Hauppauge WinTV-PVR-500MCE]("http://www.ascent.co.nz/productspecification.aspx?ItemID=342426")
[Hauppauge WinTV-PVR-500MCE with Remote]("http://www.ascent.co.nz/productspecification.aspx?ItemID=344815")
[Leadtek WinFast PVR2000 with Remote]("http://www.ascent.co.nz/productspecification.aspx?ItemID=224358")

Now the WinTV-PVR-500MCE card look good for what I want. Because it's like two cards. But the Leadtek WinFast PVR2000 implies more to me that it will work with cable. What are your thoughts?

Thanks for all the helps so far.

NTSC and PAL are two different TV standards.  Different frequency that the TV runs at, different resolutions.  

Again with DVB stuff, if your current cable box picks up via dvb, then you need to go with the DVB cards and not the PVR-500.

The PVR2000 by leadtek, i can't claim whether it works or not.  The chipsets look very similar to the IVTV project's (hauppauge cards), but i don't know for a fact.  This being the case, if your sure you dont need a dvb card - go with a PVR500.  They are very well supported ( I've got howto's for getting them working ) and great cards.  I didn't realize myself that the 500's did PAL as well, but this is good.

Now if you want to use cable and a pvr-500, you will only be able to tune stations up to about 80 or so.  Basically, you can tune only what a TV could tune without the set top box).  The rest (the ones that you normally get with your set top box) you need to plug in your set top box to the tuner to make work.  You also need a method to control the set top box.  This can be a ir transmitter, a serial control cable, or a firewire cable - depending on what your box supports.  If you don't see a serial port or firewire, then you would have to buy an IR transmitter and configure that.

Also, if you want to record the higher stations on the PVR-500 using both tuners, that's two set top boxes and two ir transmitters to setup.

---

### Post by TmP on 2007-01-05
If I were you I would not by the Leadtec WinFast 2000XP.

I got it for christmas last year and not only did I find the Windows software to by buggy and flawed. Since my frequency set was not in the defaults I had to scan the band to create a custom set which took about 5 minutes and after the reboot it would dissapear. I spend some time searching fot the damned file that would hold the custom set with no success. Finaly I found out that when I edit one of the sets manually ( by typing in each frequency ) it stays there ( untill something goes wrong with the Win or my Girlfriend accidentaly presses "refine channel").

Than I tried to run it under Ubuntu. Guess what? The driver was bugged. It took me almost 2 months to find the solution ( surprisingly simple as most good solutions). It should still be somewhere on the forums. 

When I finally run it and stated enjoying my XAVTV my Girlfriend pointed out that the remote is very annoying with Lirc ( no repeat when kea was pressed - lots of clicking to turn up the volume and so on ).

And I lost my patience when I go to playing with MythTV ( for some reason I could not install a MySQL database untill the Breazy Badger). And than i found out that I couldn't get a decent xml programme guide for Poland ( and when I did, My Myth wouldn't load it for some reason).

Guess what? Im a stubborn idiot. I intend to buy a dual tuned Hauppage card.( or similar with good support ). Than I'm gonna beef up my computer, drill a couple of holes in the box for better ventilation, get some large and slow ventilation devices ( one for intake and one to remove the heat), a quiet large HDD ( oil bearings or such) and a passive coling graphics card. Add a WIFI router, stick the bastard in some drawer or cupboard and run a backend Myth. 

BTW, any reccomendations for a well supported dual DVB card?
I'm guessing Hauppauge WinTV-PVR-500MCE PCI but it's kinda pricey. Will Myth use the hardware acceleration?

---

### Post by superm1 on 2007-01-05
> **TmP said:**
> If I were you I would not by the Leadtec WinFast 2000XP.

I got it for christmas last year and not only did I find the Windows software to by buggy and flawed. Since my frequency set was not in the defaults I had to scan the band to create a custom set which took about 5 minutes and after the reboot it would dissapear. I spend some time searching fot the damned file that would hold the custom set with no success. Finaly I found out that when I edit one of the sets manually ( by typing in each frequency ) it stays there ( untill something goes wrong with the Win or my Girlfriend accidentaly presses "refine channel").

Than I tried to run it under Ubuntu. Guess what? The driver was bugged. It took me almost 2 months to find the solution ( surprisingly simple as most good solutions). It should still be somewhere on the forums. 

When I finally run it and stated enjoying my XAVTV my Girlfriend pointed out that the remote is very annoying with Lirc ( no repeat when kea was pressed - lots of clicking to turn up the volume and so on ).

And I lost my patience when I go to playing with MythTV ( for some reason I could not install a MySQL database untill the Breazy Badger). And than i found out that I couldn't get a decent xml programme guide for Poland ( and when I did, My Myth wouldn't load it for some reason).

Guess what? Im a stubborn idiot. I intend to buy a dual tuned Hauppage card.( or similar with good support ). Than I'm gonna beef up my computer, drill a couple of holes in the box for better ventilation, get some large and slow ventilation devices ( one for intake and one to remove the heat), a quiet large HDD ( oil bearings or such) and a passive coling graphics card. Add a WIFI router, stick the bastard in some drawer or cupboard and run a backend Myth. 

BTW, any reccomendations for a well supported dual DVB card?
I'm guessing Hauppauge WinTV-PVR-500MCE PCI but it's kinda pricey. Will Myth use the hardware acceleration?
The PVR500 cards have mpeg2 encoders built in to them.  There is no way to disable the encoder.  You will always get out a mpeg2 file, with very very minimal cpu usage.  So in short yes, myth uses the hardware acceleration :)

---

### Post by guysmiley25 on 2007-01-05
Thanks guys I think I'll go with the PVR500. I'll risk that we don't have DVB. ok superm1 so If I cannot tune in all the stations, will that mean that I do indeed need to run though the cable box? And if so if I get either a ir transmitter, a serial control cable, or a firewire cable. Then can I control my box though myth? Also could I still record/watch two channels at the same time?

Thanks for all the help so far superm1.

---

### Post by superm1 on 2007-01-05
> **guysmiley25 said:**
> Thanks guys I think I'll go with the PVR500. I'll risk that we don't have DVB. ok superm1 so If I cannot tune in all the stations, will that mean that I do indeed need to run though the cable box? And if so if I get either a ir transmitter, a serial control cable, or a firewire cable. Then can I control my box though myth? Also could I still record/watch two channels at the same time?

Thanks for all the help so far superm1.
Like I said, checkout what channels you only get through the cable box.  If you can't get them directly on the TV, you need to use the cable box with the tuner card too.

Now if you set up the cable box for one of your inputs on the PVR-500, and then your ordinary cable on the other input, you can watch/record two things at the same time (but not that would show up on the cable box).  So if you want to be able to watch/record from two cable box only sources, you need two cable boxes from your cable company.

There's a little more to it then just needing the ir transmitter, serial cable, or firewire cable to control it, but I've got it outlined at this wiki page:
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

---

### Post by guysmiley25 on 2007-01-05
Chears. So if I want to watch/record two channels that I can only get though my cable box, then I need to cable boxs.

Ok so my cable box is a [General Instruments SURFview]("http://broadband.motorola.com/noflash/customer_docs/user_guides/473614-001-99.pdf") when I did a search it came up with the manual. It looks like it says something about a serial port but it looks like its for a printer?

---

### Post by superm1 on 2007-01-06
> **guysmiley25 said:**
> Chears. So if I want to watch/record two channels that I can only get though my cable box, then I need to cable boxs.

Ok so my cable box is a [General Instruments SURFview]("http://broadband.motorola.com/noflash/customer_docs/user_guides/473614-001-99.pdf") when I did a search it came up with the manual. It looks like it says something about a serial port but it looks like its for a printer?
Well this isn't one of the generally supported boxes (General Instruments).  Even if that serial port is indeed active, no guarantees the motorola channel changer code works as expected.  If your cable company has no motorola boxes, your only option will be an IR transmitter.

---

### Post by guysmiley25 on 2007-01-06
Awesome. Thanks for all the help superm1. It has been great. I'm just waiting for my PRV500 to arrive in the mail, then I'll use your method to setup my box.

Have a good one!

---

### Post by guysmiley25 on 2007-01-12
Ok so I have got my PVR500 and installed it. It came with a remote and a ir transmitter! YAY

So I have myth setup using [this]("https://help.ubuntu.com/community/MythTV_Edgy") guide. The Edgy Backend Frontend setup.

Now I have a problem. mythtv works fine on my computer monitor but when I plug it into my TV it does not display right. It cuts off the bottom. If I use the manual zoom it just moves the picture around. Only when in watching TV, displays fine in menus etc.

Any Ideas?

I have looked at [this]("https://help.ubuntu.com/community/MythTV_External_Channel_Changer#head-240983a4786cdcf3cae0ffa9607ef9ec70d8dc83") part of the guide here to setup Channel Changer. I do not quite understand how it works.

Do I have to use the script to tell mythtv what to do? What I was hoping I could do was customize my setup a bit so I could make it so the numbers on the remote change the channel on the decoder, the volume controls the volume on my sound system, and the arrows and menu buttons etc would control myth.

Can this be done?

---

### Post by guysmiley25 on 2007-01-12
Bump

---

### Post by guysmiley25 on 2007-01-13
Oh and by the way my TV is widescreen. And it is doing it with DVD's too. I did have this problem once before when I had it setup before I got my card but I don't know how I fixed it and infact I don't think it did. It just started working!!!

---

### Post by superm1 on 2007-01-14
> **guysmiley25 said:**
> Oh and by the way my TV is widescreen. And it is doing it with DVD's too. I did have this problem once before when I had it setup before I got my card but I don't know how I fixed it and infact I don't think it did. It just started working!!!
Hi, a couple of answers to your questions:

For the video card - what are you attaching it to the tv with?  Is this a nvidia graphics card?  If it's nvidia - use component cables, dvi, or vga.  The card should be able to detect the resolutions supported by your tv with these cables.  If you are using component, you will also need to add the highest tv standard that you tv supports (480i, 480p, 540i, 540p, 720p, 1080i, 1080p) to your xorg.conf.  This is explained in the nvidia proprietary driver readme.

As for the external channel changer stuff, if you are using an ir transmitter, you can use it for changing channels by mythbackend or to send out commands to change other devices.  You will need to find remotes for whatever device you want to control with it.  So if you need to change an audio receiver, you will need to add that remote to your /etc/lirc/lircd.conf.  Once added there, you will be able to send commands to change things on the receiver via
```
irsend SEND_ONCE remote command
```
where 
remote is your remote as listed in /etc/lirc/lircd.conf
command is your command as listed in /etc/lirc/lircd.conf

Once you can verify that this works, you will need to set up lirc to use two devices, the ir transmitter and the whatever remote you receive with.  Preferably make the ir transmitter the secondary remote.  This is described in the lirc howto on help.ubuntu.com, so I won't go into it too much.

Make sure that lirc is functioning with the primary remote, and that you can send using 
```
irsend -d /dev/lircd1 SEND_ONCE remote command
```
where /dev/lircd1 is the file in /dev that points to your lircd process for the ir transmitting device.  Usually this is indeed /dev/lircd1.

Almost - there, now modify your ~/.lircrc.  You will need to add sections to it for the buttons on the primary remote that you want to trigger sending device change commands.
```
begin
    prog = irexec
    button = power
    config = irsend -d /dev/lircd1 SEND_ONCE Samsung power
end
```
In that example, I am using a remote called **Samsung,** and a button called **power. **This is actually something that I do use for one of my setups.  I map the power button on my remote to power on an off the tv by this method.

---

### Post by theToolman on 2007-01-16
For those in NZ: I bought a [Hauppauge WinTV-PVR-150MCE TV Tuner, FM Radio, PCI, OEM from ascent.co.nz]("http://www.ascent.co.nz/productspecification.aspx?ItemID=342425") and I'm in Wellington.  Correctly picks up all terrestrial and sky uhf encrypted channels fine (but encrypted in the case of sky)  given a good aerial.  We are PAL (PAL-B) in NZ, not 100% sure about DVB; but believe that it is that the same technology NZs sky digital uses but the DVB card has no decryptor (like the hauppague).  The unencrypted channels on the visible satellites in australasia etc. which include all the terrestrial NZ channels and a few asian channels, NASA tv, a few others.

But still need a solution for the xml feeds in NZ - can blast the sky digital boxes, but sky seems to 'cease and decist' anyone who puts a scraper feed up :(

Balls that is.

---

### Post by superm1 on 2007-01-16
> **theToolman said:**
> For those in NZ: I bought a [Hauppauge WinTV-PVR-150MCE TV Tuner, FM Radio, PCI, OEM from ascent.co.nz]("http://www.ascent.co.nz/productspecification.aspx?ItemID=342425") and I'm in Wellington.  Correctly picks up all terrestrial and sky uhf encrypted channels fine (but encrypted in the case of sky)  given a good aerial.  We are PAL (PAL-B) in NZ, not 100% sure about DVB; but believe that it is that the same technology NZs sky digital uses but the DVB card has no decryptor (like the hauppague).  The unencrypted channels on the visible satellites in australasia etc. which include all the terrestrial NZ channels and a few asian channels, NASA tv, a few others.

But still need a solution for the xml feeds in NZ - can blast the sky digital boxes, but sky seems to 'cease and decist' anyone who puts a scraper feed up :(

Balls that is.
I might want to point you in the direction of this mailing list if you haven't already found it: 
[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/)

Its a mythtv mailing list for those of you guys in New Zealand.  Hopefully you will find some luck in it with regard to setting up some sort of scraper that you can keep going...

---

