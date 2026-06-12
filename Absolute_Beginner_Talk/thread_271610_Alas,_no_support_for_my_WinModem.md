---
title: "Alas, no support for my WinModem"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Quiltkid on 2006-10-04
Hello out there,

Just got Dapper 6.0.6 recently dual booted w/Window's (I know, shudder..).  However, according to ScanModem, my internal Agere WinModem is NOT supported by Ubuntu.  

I have dial-up, only.  No DSL or broadband here in this rural mountain community.  Don't know how long we'll be waiting, either. So, I've heard I could plug in an external serial modem, but I'm finding the Linux/Unix compatable ones aren't cheap - around $75 for the Zoom 3048 model.  I've seen a couple others around $50, but they're only warrantied for 1 year, Zoom is 7.  Sounds like a good buy for the extra $25, but I don't want to spend that kind of money until I know that's my best option.  Sure would appreciate some feedback on this one.  Thanks in advance.

Regards, Quiltkid

---

### Post by crokett on 2006-10-04
craigslist is your friend.

a very quick search turned this up.  he has linux drivers too.

[http://raleigh.craigslist.org/sys/214512270.html](http://raleigh.craigslist.org/sys/214512270.html)

---

### Post by Quiltkid on 2006-10-05
Thanks,

That might be an option, I'm afraid I don't know enough to know what my options are yet.

Regards,  Quiltkid

---

### Post by Neobuntu on 2006-10-05
The easy way.

1) Get DSL. Else...

2) If it doesn't just work in ubuntu (be sure it really doesn't because most now do). Stop there and replace it. It cost maybe $2. $5 (shipped) can get you one known to work with ubuntu. 

3) The best dial-up modem is an external and serial connected seperate modem. You may say yuck, a box, but that would be a mistake because they have the best throughput, almost zero setup and work off any computers(laptop or not) serial port. The 3com USR one are renound. DO NOT get a "Best Data" brand serial modem, they (in fact) lie.

Of course you'll not get 50K unless your phone line is crystal clear. Pick it up, push a button and listen real close to a real hard wired phone, if you hear anything, fix it (inside; start with one phone only). Tell the phone company that your faxes are not working and/or you hear static on the line and they will probably reconnect your line (new connections?) and make it cleaner and louder(thus faster.) If you are twenty houses or so away from your hoods "switch", you may never acheive 50K (56K is a myth, if the planets aline you might see 53K connect once in your life but THAT'S NOT ACTUAL THROUGHT. AKA how fast you can download.) After all this, you should be happy to get over 40KBps. (That's only about .32 MBits max compared to broadband at **over** 1 MBits a sec. This isn't even including some download overhead and that uploads are slower.

Also, the external modem I recomend should have excellent latency for gaming. Never as good as broadband though.

These are easy in Linux, as well. Use KPPP and Kubuntu recomended.

4) Even though a **new** external serial v90 or V91(doesn't practically matter) USR modem might cost you $50, BUT many people will GIVE you theirs, as they have gone to DSL or better Cable.

Keep it simple and don't waste time on old $2 modems; even if they work in Win 98. The companies that make thier (unsuported) chip-sets suck, and are not worth our time. Avoid Broadcom/Conexant anything and never buy a Linuxant driver. Modems(that just work) are cheaper. 

Start at step one above.

P.S. Get that modem posted above. :)

---

### Post by Quiltkid on 2006-10-05
Hi Neobuntu,

Hey, thanks for all your insight.  DSL and Broadband haven't come to this rural mountain community yet.  So, broke down today and bought a Zoom External Serial 56k Modem.  $62 at Staples, supports Linux (says so on the box) and has a 7 year warranty. V.92/V.44, "Modem on hold", call waiting, caller ID, Quick Connect, On-board DSP and Controller and Advanced Power Handling for protecting date during brown outs and after power losses.  My Unix Syst. Engineer son uses one and recommended it to me.  

Since I'm dual booted with XP, I'm assuming that I'll be installing it on both OS'es, correct?  And, would you happen to know if it really is necessary to uninstall the internal winmodem or if I can or even should leave it installed?  Thanks a bunch!

Regards,

Quiltkid

---

### Post by ieee488 on 2006-10-05
I see no reason not to leave the internal modem inside. It is not hurting anything.

For others in the same boat as you, and who don't want to spend $62 on a new modem, eBay is your friend. :) 

I bought an used external modem for $13 including shipping, and it works just fine with Ubuntu.

---

### Post by podunk on 2006-10-05
Taking the win modem out will help your windows - don't know about Ubuntu.

---

### Post by Quiltkid on 2006-10-05
Hi Podunk,

How will taking out the winmodem "help Windows"?  Thanks.

Regards, Quiltkid

---

### Post by Quiltkid on 2006-10-05
Hi ieee488,

Thanks for the tip on ebay - didn't even think about that..

Quiltkid

---

### Post by halitech on 2006-10-05
if you use the external in windows as well as Ubuntu, your computer will not have to work to make your connection and keep it, the modem will do the work, thus freeing up some resources for you OS

---

### Post by Quiltkid on 2006-10-06
Thanks Halitech,

I appreciate your reply.  Learning more every day!

Quiltkid

---

### Post by halitech on 2006-10-06
very welcome and glad I could be of assistance. We are all here to learn and maybe I'll learn something from you someday :)

---

### Post by Bartender on 2006-10-06
I bought a coupla USR 56K modems on ebay.  About $10 each.  Updated the firmware on USR site by connecting it to the PC, going online with Windows, and getting updates at their website.  It was kinda confusing but not rocket science.  One thing to watch out for on Windows - I had to go into Modems and reset the speed.  The modem connected at 9.6 kbps at first.

Windows was snappier on the internet with my internal Intel 536 chipset modem than the external, even after firmware updates.  

Ubuntu recognized the modem just fine - go into System, Administration, Networking, look for the modem, go into Properties, give it your phone number, password, etc. and ask Ubuntu to "Autodetect" the modem.  It should be tty/0 or something like that if the external is on the #1 serial port.  Oh, yeah, activate it.  You can dial several ways - put the Modem Monitor on the panel, from Networking, etc.

I've tried going online with Ubuntu at our house (Juno) and some neighbors' (MSN).  In my opinion, not worth the effort.  Both ISP's kicked me off without notice after about 20 minutes or so, something they didn't do in Windows.  At least not so quickly and without notice.  Updates on dial-up is excruciating.  Something like Automatix would be damn near impossible. 

Ubuntu on dialup is like driving on the rims.  You can't do much of anything because of the limited bandwidth, and the frustration gets old real quick.

---

### Post by harry555 on 2006-10-06
You could leave your old winmodem in the pc but go to device manager and disable it.  It should then have a red cross next to it.   
In XP I'd prob. trash the dial-up connection relating to your old win modem as well.
After doing that turn off your PC, connect up your new serial modem.  With any luck XP will detect and automatically install a driver that is just fine.
Then just make a new dial-up connection in control panel.
I can vouch for the ease of setup with an external serial modem using Mandrake 10.1.  I used KPPP.   It was real easy.

---

### Post by Quiltkid on 2006-10-06
Well, I think I've officially lost my sense of humor guys.

The new Zoom External 56k Serial Modem would not play nicely with Windows, or Ubuntu for that matter. I couldn't even get through the complete boot up process before "Window's is now shutting down..".  I even disabled my winmodem, same thing.  I even physically uninstalled the winmodem, ditto.  I went through the install directions again, etc.  I called a Zoom Tech Support person.  His only offer was for me to download a stripped, beta driver without all the bells and whistles (making a $75 modem pretty useless, I think, OR I could always return the modem to Staples for a refund.  Real helpful, huh?](*,) 

There must be an easier way to do this.  I can't imagine having to try modem after modem until I find one that works.  What am I missing here?  I'm running a 2 year old Compaq Presario desktop, 80 GB, 512 RAM, now dual booted with Ubuntu.  Thanks for any help.

:confused: Regards, Quiltkid

---

### Post by Bartender on 2006-10-07
Quilt-
You sure the external is keeping you from getting into Windows?  Can you get there with the external uninstalled?  
On the one hand, I'm thinking "take it back for a refund, go to EBay for a USR external".  
On the other, I don't understand how an external modem on the serial port would interfere with Windows starting up.  Can you take the Zoom to another Windows PC and see if it causes the same kind of trouble?

---

### Post by harry555 on 2006-10-07
Try this.   With the PC turned off disconnect your zoom modem from the serial port.  Restart the PC. go into control panel and delete any dial-up connections or modems that are listed there.

Then go into device manager again and delete any references to the win modem or your new zoom modem that may be there.   Then start and shut down the PC a couple of times.  I think the techs call it a cold re-set or something!
Doing this will help the XP registry 'realise' that there are no modem devices in the PC.  This type of procedure works well with Win 95 and 98 so it may be useful in XP as well.

With the PC turned off re-connect your zoom modem turn it on.  Restart the PC
and see if it will complete a boot up successfully.   See if it will detect and install default type XP drivers for the modem.  Don't bother with the zoom software (if any) 
If you still have problems try the modem on another PC.  It's quite possible that you are doing nothing wrong and something is wrong with the serial port or modem itself.

---

### Post by Quiltkid on 2006-10-07
Thanks guys for your ideas, etc.

I have actually done all the items that you suggested harry555, except for the "cold reset" and actually unplugging the serial cable, that you refered to, but am willing to try it all again.  Unfortunately, I don't readily have access to another computer, we're pretty rural out here.

Bartender, yes the Zoom tech and I went through the appropriate steps to determine that it was the serial modem crashing my Windows.  When we turned that modem off, my 'puter booted fine and acted it's "normal".  Is "USR" a brand name of an external modem?  It that US Robotics?  I think it was someone here that found one of those on craigslist that the guy was selling for $20, but would need to buy a cable.  I don't have any insurance that a used one will work either, and I wouldn't be able to return one if it didn't.  Any other thoughts?

Thanks guys,

Eagle7

---

### Post by Quiltkid on 2006-10-07
Hey guys,

Is there a difference between "Dial-up Modems" and "FaxModems"?  Please be gentle, I'm new at this.  I was checking out some US Robotics modems that were suggested, and I see where some are listed as one or the other  - Fax or Dial up.  The Zoom modem that I bought says "56k Data, Fax, Voice Mail, DSP & Controler". Looks like it'll work for dial-up, right?  I'm still learning..

Regards,  Quiltkid

---

### Post by podunk on 2006-10-07
Before DSL got here (I understand the rural thing<smile>) I had both Zoom and USR externals - the zoom got taken out by a thunder storm and I replaced it with a USR that I was *very* happy with - still have it just in case.

To install the zoom – it was weird in the fact that I installed the software then the modem- I sorta recall that I had to
Remove the old modem
Go to device manager (Settings Control Panel System Device Manager) click on the Winmodem to remove it (it was in there in 2 places - one under ports (COM 3 or 5) and one that was by itself out in the main tree
Restart
Insert install Cd and run the set up wizard
When prompted connect and power up the modem

A fax modem can send faxes as well as connect to the internet, and a voice modem can run a voice mail and if your ISP has the right protocols supported you can take voice calls and not lose your net connection. Often in the sticks ISPs don't support the right protocols.

Assuming the old modem is completely uninstalled and out of the machine I would strongly suspect that the modem is defective – Winduhs is pretty good with modems. I don't know yet how Ubuntu handles hardware that just disappears – but it has done such a good job of detecting hardware for me that if i saw a modem fail on both OS's I would send it back without any more thought.

Tiger direct has a Trendware 56k V.90 that has +very+  positive reviews – especially from Linux folks for only 30 bucks.   I wouldn't worry to much about a long warranty – living out in the sticks the only thing that will take a modem out isn't covered by a warranty anyway – lightning and transients. If it makes it 90 days your good for life. :-)

---

### Post by Bartender on 2006-10-07
Hi, Quilt -
Yeah, by USR I mean US Robotics.  Sorry.  If you search "us robotics 56k external" on EBay you'll see lots of 'em.  Watch out - some of the externals being offered are ancient 28K's.  You want to make sure you can see the 56K sticker on the front of the modem.  The newer ones (about 2000 or later) came in black.  Older ones are beige.
EDIT: Make sure they're including the serial cable and the wall cube!

---

### Post by Quiltkid on 2006-10-07
Okay, I actually think some of this is starting to sink in.  Sounds to me like I'm going to be better off taking the Zoom back to "Staples"land and just pick up a USR off ebay.  I will consider the trendware one, too.  

You know, I did query HP by email, and here's the machinations they want me to go through just to make an external modem work:

Thank you for contacting HP Total Care.

Uninstall original modem driver by going to Device manager, restart the 
system and go to BIOS and reset it first by pressing F5 and then, and 
set "no" to Plug and play OS. 

To do that scroll to Advanced menu options, scroll to Plug and play OS 
and say NO and save the BIOS settings by Pressing F10. And now, install 
standard modem driver instead of original drivers after restarting. 
Once
you find it working satisfactorily, replace standard driver to its 
original driver.

Does this make sense to you folks?  Why do you suppose they want me to say "No" to Plug n Play at the BIOS?  By "standard modem driver" are they referring to the new external modem?

I'm not going to touch anything at present.  I'll wait until I get a USR or whatever, try to install it and then see.  Sound reasonable?

Podunk, you're absolutely right on the weird install on the Zoom.  Doesn't make much sense to me.  At this point in time, as I just mentioned - think I'll wait and try and different modem.  I DO appreciate you walking me through the steps, and I will keep them.  Thanks.

Bartender, I appreciate your heads-up on the USR modems and what I should watch for.  Are there a lot of them for sale because more folks are going to DSL?  Thanks to you as well.

Quiltkid

---

### Post by Stettin on 2006-10-07
[http://staples.shoplocal.com/staplessneakpeek/Default.aspx?action=browsepagedetail&storeid=2278819&rapid=323515&pagenumber=1&listingid=-2094296113]("http://staples.shoplocal.com/staplessneakpeek/Default.aspx?action=browsepagedetail&storeid=2278819&rapid=323515&pagenumber=1&listingid=-2094296113")

Free after rebate starting sunday @ Staples. Not sure if it works in Ubuntu or not.

---

### Post by Bartender on 2006-10-07
I think someone mentioned earlier in your thread that people are moving on to cable, DSL, satellite, etc. and these expensive externals are just sitting around collecting dust.  I wanted to mention that USR makes the hardware modem in an internal version too.  
Search "us robotics internal hardware" or something like that.  You're looking for the USR5610B or C. A is the earliest version.  Make sure you get a full hardware version if you look at internals.  It HAS to be a full hardware modem if it's an external so there's no marketing confusion.  As soon as you go internal, it gets a little tricky.  Some of the manufacturers claim they're "hardware" but still rely on Windows.
When I looked at internals a year ago they were noticeably more expensive than the externals.  I just looked a minute ago and they're down in the $10 range.
I understand that you want to see it work, but will repeat that dial-up is just plain frustrating with Linux.  Better than nothing I guess.
EDIT:  Yes, it does make sense that they want you to turn PNP "Off" in BIOS.  I've been told several times to turn it off in W2K and XP.  Don't understand why, just did what they said to do.

---

### Post by Quiltkid on 2006-10-07
Hi Stettin,

Thanks for the link/tip on the modem at Staples that'll be free after rebate.  I checked it out and saw where that's an internal, and according to HP I can't put ANY other internal modem in my 'puter because it will have compatability issues.  So, guess I'm stuck with needing an external for now.  

Hey Bartender,

Thanks too, for the info on the internals, but as stated above, guess I can't change my internal.  I appreciate you reminding me of the earlier statement as to why there's so many externals out there right now.  I'm pretty tired, and sorry, didn't look back to the other posts before I asked the question.  I also appreciate your comment regarding the PNP, thanks.  Oh, and yes, I'm hearing folks talk about Dial-up and Linux being frustrating. I may be forced to wait, but my dear son is really excited for me to at least give it a try (obviously he's got DSL, actually FIOS now.  He says the fiber optics are "rediculously fast".  He lives in a "test area", so gets to try it out before the rest of us.

Quiltkid

---

### Post by Stettin on 2006-10-08
> **Quiltkid said:**
> Hi Stettin,

Thanks for the link/tip on the modem at Staples that'll be free after rebate.  I checked it out and saw where that's an internal, and according to HP I can't put ANY other internal modem in my 'puter because it will have compatability issues.  So, guess I'm stuck with needing an external for now.  
Quiltkid

Sorry, didn't read the whole thread. You might be able to pick up an old USR External (9 or 25pin serial) at a garage sale or something cheap. You can't beat those, they are rock solid.

---

### Post by Quiltkid on 2006-10-08
No problem, Stettin,

I'll be watching out for a USR external.  Thanks for the tip on the garage sale, I hadn't thought of that! :) 

Quiltkid

---

### Post by Bartender on 2006-10-08
Quilt, I just don't understand your problems with the 2 modems.   I'm running W2K, not XP (wouldn't that would make any dif) but in W2K if I go to Control Panel>Modems it sees the Intel 536 internal and the external modem and there are no conflicts.  I can ask W2K to use one or the other.  Have gone back and forth between the 2 several times over the last few months without any prob's.

If you did get an internal USR full hardware modem, you'd just uninstall the old one, make sure the old drivers were gone, and install the USR.  The USR should work better than your Winmodem in Windows and would work for Linux too.

---

### Post by Quiltkid on 2006-10-08
Hi Bartender,

I did the steps HP recommended, including changing a few settings in the BIOS.  That seemed to help, at least initially.  I finally got Windows to recognize "New Hardware" and from there was able to install it - somewhat.  I ran into a problem while querying the modem (per instructions fr Zoom), got the following message: "The port that the modem is using is currently opened by another application.  Exit any application that may be currently using the port".  Well, I couldn't figure that one out, as my Agere Winmodem is on COM 3 (even after I disabled it), and my new Zoom was on COM 1.  Any ideas on this one?

I called my ISP to do some final configuring with them, thought I had that resolved, rebooted - and Windows preceded to crash again, just like it did in the beginning of the Zoom story.

Normally, I have the patience of Job, so to speak, but this is really getting to me.  Ubuntu was telling me that it "Didn't recognize this interface" or something like that, so couldn't get it to work their, either.  This is SO frustrating. ](*,) 

Regards, Quiltkid

---

### Post by podunk on 2006-10-09
Com 1 and Com 3 are in reality the same thing - they both use the same IRQ. Same with 2 and 4. I think they share the same IO range also.

ah, is the old modem still in the machine? :-) If it is UNPLUG your computer, take a screw driver and pull that baby out. You'll never be able to get your com 1 port open if the old modem is sitting on com 3.

Precisely which HP computer do you have?

---

### Post by Quiltkid on 2006-10-09
Hi podunk,

Well, your post shines a bit of light on the situation for me, thanks.  I am curious tho, Bartender states that he's able to have two modems installed simultaneous and they work well and play nicely together.  Why won't mine?

You asked what 'puter I'm using?  A two year old Compaq Presario desktop with AMD Athlon XP 2500+ operating at 1.83GHz.  80 GB's, 512 RAM with Windows XP, dual booted with Ubuntu Linux, which I can't use w/internet until I get this dastardly modem issue resolved.  

Quiltkid

---

### Post by podunk on 2006-10-10
If you install one modem on com 1 and 1 modem on com 2 they won't fight for an IRQ.  Back before Winmodems started their push for world dominion you could chose your com port, IRQ and IO with jumpers. If you had 2 phone lines you could gang them into one machine with 2 modems and get about 80K downstream – the podunk DSL I called it. :-)

One thing you might check on – boot your computer and enter the BIOS setup program. Look and see if you have a Port section. Older mother boards you could chose the IRQ on the serial port – effectively turning it from com 1 to com 2.

Compaqs are nice machines to work on – every one I've seen have plenty of room to route cables and stuff. Folks make fun of them some, but they are easy to work on, and I love their drive bays.

---

