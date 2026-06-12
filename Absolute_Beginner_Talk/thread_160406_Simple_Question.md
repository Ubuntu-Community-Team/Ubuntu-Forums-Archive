---
title: "Simple Question"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by IUFLA on 2006-04-14
I have a dual-boot system with XP residing on its own 120 GB Hard drive and Breezy 64 residing on its own 120 GB HD as well...

If I boot into XP and fire up my SBC Yahoo account (using their software) I always have to log in with my user name and password...

But, if I boot into Breezy, it simply takes me to my home web page without signing in...

:confused: 

Why?

---

### Post by Mustard on 2006-04-14
I assume you have previously informed the Breezy install of the username and password?

---

### Post by RRS on 2006-04-14
What browser are you using in XP? And also do you have Yahoo set as your homepage there?

For auto log-in try "internet preferences" for the settings in IE, not sure with Yahoo's browser, never really used it much.

Also check that you allow cookies from Yahoo, I seem to remember it took several tries to have IE log into Yahoo automatically but even in windows Firefox was much easier, almost default after the first log in.

Since I haven't booted XP for a couple weeks I can't trust my memory of IE settings any further. I use Firefox as my default browser there too.

Since you have no trouble with Ubuntu I doubt there's any problem with your modem/router settings though.

---

### Post by IUFLA on 2006-04-15
[QUOTE=Mustard]I assume you have previously informed the Breezy install of the username and password?[/QUOTE]

It's been about a month since I set it up, but I don't remember putting in any internet info...

Breezy runs really well on this machine, and Firefox is plenty fast...I was just wondering where it gets the info to log onto the SBC network from...

---

### Post by IUFLA on 2006-04-15
[QUOTE=RRS]What browser are you using in XP? And also do you have Yahoo set as your homepage there?

For auto log-in try "internet preferences" for the settings in IE, not sure with Yahoo's browser, never really used it much.

Also check that you allow cookies from Yahoo, I seem to remember it took several tries to have IE log into Yahoo automatically but even in windows Firefox was much easier, almost default after the first log in.

Since I haven't booted XP for a couple weeks I can't trust my memory of IE settings any further. I use Firefox as my default browser there too.

Since you have no trouble with Ubuntu I doubt there's any problem with your modem/router settings though.[/QUOTE]

I use Yahoo's browser...And, yes, I have SBC Yahoo set as the home page...But I'm not sure that matters...

The internet works very well on both OSs, so there isn't really a problem,..I just wondered how it worked...

---

### Post by Mustard on 2006-04-15
Did you use a guide like this when you first setup?

[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

If you ran pppoeconf when you were configuring your connection it would have asked for login details at that stage.

---

### Post by RRS on 2006-04-15
> Breezy runs really well on this machine, and Firefox is plenty fast...I was just wondering where it gets the info to log onto the SBC network from...

I'm running the modem shipped from SBC when I switched to Yahoo DSL. The initial installation (pre-Linux) set things up so that the modem works as a DHCP server and router.

In this way all PPPoE and Yahoo log-in functions are handled by the modem without having to install any other software on your machine.

When you installed Ubuntu it most likely recocgnised and set up the DHCP automatically as mine did, but I do recall having to change some settings in Windows for auto-login several months ago.

Though I haven't gotten around to it yet I don't see a problem with actually removing any Yahoo software from you're windows system that you don't use since I recently set up a second machine with dual boot and was able to access Yahoo simply by plugging into the modem, though again I had to set my homepage manually, but no software installation was needed.

Sorry to get so long winded but I hope this helps you understand the "magic" a little better. Still have A LOT to learn myself. :)

---

### Post by IUFLA on 2006-04-15
[QUOTE=Mustard]Did you use a guide like this when you first setup?

[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

If you ran pppoeconf when you were configuring your connection it would have asked for login details at that stage.[/QUOTE]


Actually, I booted off of the iso I burned onto a disc and it set itself up...Sound, internet, pretty much everything except the video card and printer...And those were easy setups (with a little guidance :D )...I don't remember outting in any internet info...

Anyway I could check and see if my user name and password were entered anywhere?

---

### Post by IUFLA on 2006-04-15
[QUOTE=RRS]I'm running the modem shipped from SBC when I switched to Yahoo DSL. The initial installation (pre-Linux) set things up so that the modem works as a DHCP server and router.

In this way all PPPoE and Yahoo log-in functions are handled by the modem without having to install any other software on your machine.

When you installed Ubuntu it most likely recocgnised and set up the DHCP automatically as mine did, but I do recall having to change some settings in Windows for auto-login several months ago.

Though I haven't gotten around to it yet I don't see a problem with actually removing any Yahoo software from you're windows system that you don't use since I recently set up a second machine with dual boot and was able to access Yahoo simply by plugging into the modem, though again I had to set my homepage manually, but no software installation was needed.

Sorry to get so long winded but I hope this helps you understand the "magic" a little better. Still have A LOT to learn myself. :)[/QUOTE]

I'm running off of the Siemens Speedstream 5100b hooked to a Netgear 614 wireless router that I've set up for 2 other computers (both XP...For my daughter and wife)...The modem is just a bridge as the router handles the PPPoe...Maybe, like you said, it recognized the DHCP when I loaded it...

Thanks to all for the replies...

---

