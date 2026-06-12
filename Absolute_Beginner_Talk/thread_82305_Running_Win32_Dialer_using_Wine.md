---
title: "Running Win32 Dialer using Wine"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by blue_shift on 2005-10-26
I am trying to connect to the internet in ubuntu using a dialup modem. I have a dialup account but I cannot run the dialer program under ubuntu even using wine. The dialer application claims "registry error".

I cannot use a linux dialer as I don't know the phone number for the ISP and getting this number looks unlikely as they clearly do not want to hand it out.

The one point I can think of is that I just copied the files from the dialer's folder across. Could I run the installer under wine? Does wine emulate a registry?

Any other ideas?

Thank you in advance.

---

### Post by blastus on 2005-10-26
What's your ISP? I would call them and ask for the phone number and your account information. I would refuse to do business with any ISP that did not provide this information and/or required me to use Windows software for connectivity. I haven't encountered these so-called WinISPs, but I know they exist. 

The Internet is supposed to be an open place where anyone can connect to it and use it regardless of the platform they use. I've been getting dialup service from the same ISP for about 9 years now. My advice to you would be to call your ISP, get your account information, and if they can't help you then cancel your service and find a real ISP.

Also, I haven't had much success running anything other than Solitaire on Wine. Even if you got it working, anything that runs under Wine is fragile because a future release of Wine can break it. Your dialer probably relies on some kind of ActiveX environment. I would not even consider running a Windows dialer on Wine--furthermore you don't even know the phone number it dials! What if your dialer gets hijacked, and dials the Cook islands, you wouldn't even know until you got a $500 phone bill. Part of reason why I'm so irritated with Windows is because it offers no protection against rogue ActiveX dialers and I contracted one of them many years ago.

---

### Post by zerhacke on 2005-10-26
Many of these WinISP's are modifying your TCP/IP stack on install.  AOL is rather famous for doing this.  Netscape's internet service does this too.

These ISP's, even if you did somehow manage to get the dialer to work, would not connect as they rely upon sleight of hand to get your account online.  For instance, I know that AOL changes from one type of script to another mid-login.  I don't remember if it's PAP to CHAP or SLIP to whatever, but they change styles mid login.

It may be possible to configure your modem to change mid login like this, but that would require knowing what the trickery your ISP is using.  Since they're using a custom dialer to connect, it's extremely likely they won't tell you this over the phone.  You'd have to reverse engineer it, something you're probably not willing or able to do if you're trying to run the dialer under WINE.

I suggest as blastus suggested.  Get another ISP, and when you sign up ask if they use a simple dialer such as pppd or kppp would be able to handle.  If they require you to use their special dialer don't get service with them.

---

### Post by blue_shift on 2005-10-26
I think I have located the phone numer, so I'm attempting to get pppt to work. Thanks for your input.

---

### Post by wmcbrine on 2005-10-26
[QUOTE=zerhacke]For instance, I know that AOL changes from one type of script to another mid-login.  I don't remember if it's PAP to CHAP or SLIP to whatever, but they change styles mid login.[/QUOTE]

[http://ubuntuforums.org/showthread.php?p=358508#post358508](http://ubuntuforums.org/showthread.php?p=358508#post358508)

---

### Post by zerhacke on 2005-10-27
Oh hey, thanks Brine.  Roger's right.

One has to wonder if AOL's claiming to be a good, fast dialup provider simply because they're using CSLIP and a funky way to connect.

---

