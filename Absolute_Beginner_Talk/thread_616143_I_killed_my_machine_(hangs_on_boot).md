---
title: "I killed my machine (hangs on boot)"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-11-17
I found many, many threads about machines hanging on boot.  Too many to read, and none that I could find an answer in.

My problem is this...  I recently installed an Edimax RaLink 2651 (or 2561, can't remember exactly).  I chose it specifically because many sites claimed that Linux had no problems with it.  Well...  It was a bitch to get the thing working right--had to run through hoops just to get it all set up.

I wake up this afternoon (yeah, it was Friday night, heh, so I wake up in the afternoon), and my Internet isn't working.  My girlfriend's Windows computer, two feet away, is working just fine.  The various wireless LAN Managers I had set up in pursuit of getting the wireless working on this computer all tell me I am connected to the "albanese" network (our home network), but I cannot ping anywhere by domain name or IP address, not even my own router at 192.168.1.254.  (Of course I can ping myself at 192.168.1.72 and 127.0.0.1.)

Anyways, after exhausting my own (very limited) knowledge of getting the connection working, I kick my girlfriend off of her computer and come to the Internet for aid.  I saw someone having a very similar problem, and they had fixed it by editing their /etc/network/interfaces file and restarting the network.  Cool!  So I give it a try...  ... ...er, being a relative Linux dumbarse, I don't know how to restart the network except for restarting the computer.  So that's what I do....

...

And now I am talking to you from my Windows Vista, because I cannot boot into Kubuntu at all.  I tried using the "recovery mode" that GRUB offers, and it told me there was a "soft lockup" or something like that on CPU#0, while it was trying to load the network configuration.



Obviously, this is because I decided to change my /etc/network/interfaces file, right?  Well, I think so, anyway...  and I did find an old archived thread somewhere that said as much.



Anyways, is there some way I can make things right again, without having to completely re-install the system I've been using for months?  I don't have my Kubuntu install disc handy, anyways.

(using 7.04)

---

### Post by mellowd on 2007-11-17
I assume you made no backup of this file before making the edit?

---

### Post by Sarteck on 2007-11-17
No, I just commented out the lines that I took out, and added the new lines at the bottom.  If I could get to the file, I could easily change it back.

Windows won't recognize my Linux partition, though, so I can't even see the files from here.

---

### Post by MegaJim on 2007-11-17
Get hold of a Live CD mate, you'll be able to edit the file back to sanity from there.

---

### Post by sports fan Matt on 2007-11-17
I second that ..just because you said you arent all that knowledgeable like you stated it just seems like even though it will take longer to get the cd depending on were you are once you get it, you can start from scratch

---

### Post by Sarteck on 2007-11-18
MegaJim, sox fan Matt,

I was able to locate one of my previously burned discs... my latest one, too!

Unfortunately, it wasn't much help in booting my system, because it too would hang on booting.  Finally, after pulling out what precious few hairs I have left, I decided that I'd just have to re-install.  Quite often, I don't have the foresight to even make backups of my most precious of files, but this time around, I dedicated an entire partition to them.  :)  So it wasn't going to be TOO painful...

...or so I thought.  I was thinking, "sure, the regular bit of the disc fails to boot, but I can use the text mode and see if that works."  It did... but each time, no matter what text-mode I chose (regular, server install, etc) it would always hang at Installing Software at 85% (which was different packages depending on the type of install).

Worse yet, it mangled GRUB up good, giving me an "Error 15", so I couldn't even boot into Windows.  ;_;

So my girlfriend says, "why not just take out the wireless card, hon?"  I tell her, of course, that taking out the wireless card wouldn't matter, that it's a software problem, not hardware, that it was booting fine before.  Just to show her how right I was, though, I took our the wireless card...

...and stuck my foot in my mouth.  That's what I get for acting like I knew everything.

So now I'm sitting here (with the card back in), and downloading all the updates for Fiesty.  In about half an hour (I'm on a slow DSL), when that's done, I'll be upgrading to Gutsy (I hear they have better luck on Gutsy with NVidia cards, and I went through hell the first time around trying to get this one done right).



The moral of the story: no matter how much more you think you know about computers than your girlfriend. listen to her anyway.

---

### Post by Pinger05 on 2007-11-18
The same goes for wifes, listen to them to :)

Glad it all worked out for you.

---

