---
title: "Network printer on airport always &quot;busy&quot;"
date: 2008-07-12
forum: Apple Hardware Users
---

### Post by John Chambers on 2008-07-12
Well, I've spent several days on this forum and google, finding that this is an extremely common problem, but all the sketchy suggestions I've tried have failed in exactly the same way:  The printer is found, but when I try to print something, I just get the message "recoverable: Network host '192,168.1.100' is busy; will retry in <N> seconds...", where <N> is a multiple of 5.  

Funny thing:  If you google for the fixed strings in this message, the first hit is to the source code.  The message comes from a block that begins:
   if (error == ECONNREFUSED || error == EHOSTDOWN | error == EHOSTUNREACH) {
      ...
So the "busy" claim is clearly wrong.  The message appears when the host "refused", i.e., didn't complete the connection, or is "down", whatever that means, or is unreachable.  None of these is remotely similar to "busy" in any sense that I know.  And I can tell from a simple ping that the host (the airport) is alive and talking on the network.  I can also tell that the printer is up and working, because I can send a print job to it from my Mac, and it prints just fine.

Also, a few weeks ago, I had a machine that was running the latest knoppix for a while. Its CUPS found the airport's printer instantly, and printed on it with no problems.  (Funny thing was that it failed to detect or use a directly-attached printer until I begged and pleaded and sacrificed a chicken to it. ;-)

So how do I diagnose and the real problem on ubuntu?  I've looked in the files in /var/log/cups/, and there are zillions of messages about the printer, but none of them look at all like error messages.  Of course, most of them are just gibberish, but they don't seem to contain any of the common keywords that indicate errors.  And when I try to print something, nothing appears in the error_log file.

Is there something somewhere that will explain how to figure out what I'm doing wrong here?

BTW, the printer is an HP LaserJet 1300.  There are lots of choices of config thingies for this model in the printer setup stuff, and by now I've tried most of the possible combinations.  But the fact that all of them fail in exactly the way hints that this isn't the problem at all, and there's something more fundamental wrong.  And it's not that the printer is busy.  It's sitting there idle, probably wondering why that nice ubuntu system never sends it any print jobs.

(I also tried to post this on the Apple Users forum, but it insists that I'm not logged in.  When I log into it, it welcomes me, then changes back to the forum page that says "Hello, Unregistered, ..." and tells me that I can't do anything but read because I'm not logged in. Wonder what's wrong there.  Anyway, if there's a better forum than this to ask on, let me know, and I'll try it.)

---

### Post by DonnieP on 2008-07-13
I can't solve your problem but I can confirm it, if I'm reading your post correctly:  you've connected a USB printer directly to your Airport and then trying to print using an Ubuntu machine networked to the same Airport?  I futzed around with this for hours (some months ago) and finally gave up.  The only method I could get to work was to connect the printer to a computer running CUPS and networked to the Airport.  As long as that computer is on I can successfully use the printer from my laptop on the same network.  This is actually distro agnostic.  I've tried it with several other distros and came to the same conclusion.

---

### Post by John Chambers on 2008-07-13
[Yet another try to get this forum to accept a reply, and not just tell me that I need to click on a "Quick Reply" icon, but clicking on those icons doesn't seem to do anything at all ;-]

Your comment does remind me of something else weird about the airport-printer set up that we've noticed:  We have two Mac PowerBooks, call them PB1 and PB2.  Both can use the airport's printer, but only if PB1 is present and awake.  If I close PB1's lid or carry it out of range, PB2 loses the ability to print to the airport's printer.  When we had the knoppix system talking to the printer, we found the same thing:  It could only print when PB1 was present and awake.

It didn't occur to me to mention this, because I've had PB1 awake nearby while experimenting with ubuntu.  I used it mostly as an extra screen to do things like google for info and read ubuntuforums.com, since that way I wouldn't lose my place in the docs when I rebooted ubuntu.

But maybe it has something to do with the problem.  I'm beginning to suspect that the Apple software doesn't actually support "network printing" on the airport.  Rather, its printer is only accessible from PB1, and other systems have to print via a queue in PB1.  

But I'm not sure how to go about testing this.  Anyone know?  It does seem to be an annoying misfeature.  The main reason to get a laptop is for portability.  Losing all access to a network printer if a certain laptop is carried away seems like a rather ridiculous design.  But it seems to be the way our airport's printer works (or doesn't work in some cases).

Is this just a red herring, or is it a useful clue?

[Now let's see if ubuntuforums will let me post this one ...]

---

### Post by DonnieP on 2008-07-13
Is PB1 running OSX or Linux?  OSX is able to see and print to an Airport-connected printer.  OSX also does CUPS.  So any other machine - Linux or OSX - is going to be able to print to the PB1 CUPS server even though they may not be able to print directly to the printer itself without PB1's CUPS intervention.

By the way, when you click on the Quick Reply Icon (looks like a Return key) all it does is move the cursor down to the Quick Reply box.  If you're not watching for it you'll miss it.

---

### Post by John Chambers on 2008-07-14
PB1 is running OSX 10.4.11.  And I'm guessing that OSX speaks a proprietary protocol to the Airport.  If I'm right, the Airport doesn't actually provide a "network printer".  Rather, it provides an "OSX printer", and other computers have to have an OSX machine handy to intercede with the Airport.  But there's weak contrary evidence: CUPS on ubuntu thinks it has linked to a printer at the Airport's IP address.  That printer is always "busy" and never prints anything.  But CUPS on ubuntu thinks it sees the printer and is able to make some sort of connection/association/whatever with it.  So the Airport isn't completely opaque to a non-OSX system.

I'm not sure I follow the Quick Reply thing.  Yes, when I click on one of those little icons, a cursor appears in the Quick Reply box.  But most of yesterday, that also happened, and I could then type in a message.  But when I hit the "Post Quick Reply" button, I'd get a popup (popdown?) panel at the top of the browser's window saying that I had to click on a Quick Reply icon.  I did, and nothing happened.  The cursor in the Quick Reply box (at the end of my message) would stay right where it was.  Eventually, after poking around at a few random icons, the window would change to something else, erasing my message, and the Back button would bring me back here with an empty Quick Reply box.  

Let's see if it's working now ...

---

### Post by DonnieP on 2008-07-14
I'm guessing that CUPS is the key here.  Yes, your Ubuntu machine knows the printer's IP, but it's accessing that printer through the CUPS server on the OSX machine.  One reason I surmise this is that in my setup I'm running Ubuntu on both machines.  If I attach the printer to the Airport, neither Ubuntu machine can print to that printer.  If I instead attach the printer to one of the Ubuntu machines directly (my desktop machine sits right next to the Airport) then both both Ubuntu machines can now print to it.  CUPS makes this happen.

---

### Post by John Chambers on 2008-07-14
Hmmm ... So it looks like I should abandon the use of the airport as a network print server, and give the job to ubuntu.  Then I could have the fun of learning how to make OSX use a linux machine's printer. ;-)

Actually, I tried this a while back, at a site where they had a mixture of Windows, OSX and linux (RedHat I think) machines.  We never did succeed in making any of the three kinds of machines use any of the others' printers.  We ended up with three printers, one per OS type, and all the machines with the same OS type had a network printer.  But no amount of fiddling made them see each others' machines.  

I was impressed a few weeks back when I tried knoppix, and it found the printer on the airport very easily, and used it.  But it did depend on the one OSX laptop being present and awake.  We'd occasionally notice that the printer had hung, so we'd walk over to the desk with the Mac laptop, hit a few keys to wake it up, and the printer across the room would come to life.  Somehow this didn't seem like total success ...

[Another ubuntuforums flakiness:  An hour ago, it wouldn't let me in.  It accepted my name and password, produced the usual Welcome page, which after a few seconds bounced me to the previous page asking for my name and password, and suggesting that I register.  Then just now it suddenly popped up a page saying I was logged in, when I hadn't logged in for nearly an hour.  Weird.  This is with firefox 3.0 on my Mac.  I wonder if there's a forum about ubuntuforums? ;-]

---

### Post by DonnieP on 2008-07-15
Your ubuntuforums problems sound more like Firefox on OSX problems to me.  You might want to try it on Ubuntu just to compare.  To the printing issue - the nice thing about CUPS is that's it's actually Apple-owned and works beautifully cross-platform.  As long as one machine of whatever platform can see your printer, any other machine on the network of whatever platform can print to it using CUPS.  Good luck!

---

### Post by John Chambers on 2008-07-15
> **DonnieP said:**
> The nice thing about CUPS is that's it's actually Apple-owned and works beautifully cross-platform.  As long as one machine of whatever platform can see your printer, any other machine on the network of whatever platform can print to it using CUPS.  Good luck!

Well, maybe ubuntu can "see" the airport's printer, but it can't print to it.  The printer is always "busy".  The earlier knoppix linux could print to it (though only if the Powerbook was nearby and awake), but ubuntu can't.  Or, if it can, I haven't yet stumbled across the config setup that makes it work.  I've tried lots of combinations of the various settings, all of them make ubuntu's CUPS think it sees the printer.  But it always fails the same way, with the "busy" message.

---

