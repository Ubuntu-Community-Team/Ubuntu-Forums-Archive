---
title: "Can't Connect to internet"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-07
I can connect to the internet on Ubuntu but not on Windows, which I just installed. I've tried getting drivers from a few sites and burning them but none of them seem to work.

It's a RealTek RTL 8139 Family PCI Fast Ethernet NIC card,

---

### Post by spankymasterc on 2007-04-07
have u tried these? [http://www.soft32.com/download_180517.html](http://www.soft32.com/download_180517.html)

---

### Post by Biscuitpie on 2007-04-07
I already installed those. Still says my hardware is disconnected.

---

### Post by mikeyphi on 2007-04-07
When in windows look under Control Panel - System Properties - Hardware tab.....select device manager... is your card listed...if yes - highlight select properties then select Enable device....... why use windows!!!!! 
If your card is not listed - you will have to remove it then install the driver then reinstall so that windows can do its autoconfig thing!

---

### Post by Biscuitpie on 2007-04-07
> **mikeyphi said:**
> When in windows look under Control Panel - System Properties - Hardware tab.....select device manager... is your card listed...if yes - highlight select properties then select Enable device....... why use windows!!!!! 
If your card is not listed - you will have to remove it then install the driver then reinstall so that windows can do its autoconfig thing!

I use Winblow$ for gaming. :P I reboot and switch over to XP and try this but it said the device was working properly before. Also, it's in my laptop, don't know if I can take it out, hehe.

---

### Post by mikeyphi on 2007-04-07
> **Biscuitpie said:**
> I use Winblow$ for gaming. :P I reboot and switch over to XP and try this but it said the device was working properly before. Also, it's in my laptop, don't know if I can take it out, hehe.

Sorry - didn't understand.... Confirm the card is not newly installed and that it worked OK until you installed Ubuntu?

---

### Post by Biscuitpie on 2007-04-07
> **mikeyphi said:**
> Sorry - didn't understand.... Confirm the card is not newly installed and that it worked OK until you installed Ubuntu?

It worked before I wiped my hard drive.... and it's working right now for Ubuntu.

---

### Post by mikeyphi on 2007-04-07
> **Biscuitpie said:**
> It worked before I wiped my hard drive.... and it's working right now for Ubuntu.

So...did you install Ubuntu and THEN install windows?

---

### Post by Biscuitpie on 2007-04-07
Yeah, because I had to get a new Windows disc. >.> I fixed the GRUB menu and such, though.

---

### Post by mikeyphi on 2007-04-07
> **Biscuitpie said:**
> Yeah, because I had to get a new Windows disc. >.> I fixed the GRUB menu and such, though.

OK so it's a new windows install.....did you look where I asked?

When in windows look under Control Panel - System Properties - Hardware tab.....select device manager... is your card listed...if yes - highlight select properties then select Enable device

What result?

---

### Post by Biscuitpie on 2007-04-07
It was already enabled, but I restarted it and same thing. =/

---

### Post by mikeyphi on 2007-04-07
> **Biscuitpie said:**
> It was already enabled, but I restarted it and same thing. =/

Did you setup new internet connection under Network connections?

---

### Post by Biscuitpie on 2007-04-07
Eh, I went to a setup network wizard, and it said my "device is disabled".

---

### Post by mikeyphi on 2007-04-07
> **Biscuitpie said:**
> Eh, I went to a setup network wizard, and it said my "device is disabled".

Looks like a windows problem........ you're just going to have to try disabling/enabling that piece of hardware until both parts of windows 'sees' it...... don't think I can suggest anything else...

---

### Post by Biscuitpie on 2007-04-07
> **mikeyphi said:**
> Looks like a windows problem........ you're just going to have to try disabling/enabling that piece of hardware until both parts of windows 'sees' it...... don't think I can suggest anything else...

Well that's really annoying. =/ Why can't things ever just work for me?

---

### Post by Biscuitpie on 2007-04-07
Maybe someone else knows?

---

### Post by Biscuitpie on 2007-04-07
I used a card from another computer and the same thing.. it just won't work.

---

### Post by jerryrw on 2007-04-07
Make sure that TCP/IP installed if so you may have to try reinstalling it.

---

### Post by Biscuitpie on 2007-04-07
Don't even know what that is. =/

On a side note: does anyone know how to stop my GNOME theme from affecting Firefox's theme? I can't even see what I'm typing right now.

---

### Post by freebird54 on 2007-04-07
WHile in the Device Manager, there are a couple of things to try.  One is the menu entry for 'remove'.  Then you 'Search for new hardware' and let the auto configure happen.  It took about 10 tries for Windows to get my video card right!

Another place to look is in the 'conflicts' - under properties I think (not on Win right now).  Sometimes things show up there without much apparent reason.  No other changes were made?

As for themes - as far as I know they will affect everything - but FF does have it own 'skins' and looks available.  They might affect your vision difficulties! (in a positive way, one hopes!)

Good luck!

---

### Post by Biscuitpie on 2007-04-07
I did what you said and it worked in one try, and I couldn't find a conflicts area. It still said it wasn't working... Maybe a screen shot will help.

---

### Post by Biscuitpie on 2007-04-07
Here it is.

Can't see it...

---

### Post by Biscuitpie on 2007-04-07
...

---

### Post by Biscuitpie on 2007-04-07
Ok, this should be bigger: [http://img293.imageshack.us/my.php?image=internetissuebm7.png](http://img293.imageshack.us/my.php?image=internetissuebm7.png)
  and everything is still white even with this new theme...

---

### Post by Biscuitpie on 2007-04-07
Bump for great justice.

---

### Post by freebird54 on 2007-04-07
Sorry- watching the Masters...

OK - so it looks like all is well - but when you try to use it - not?

The conflicts is under 'Resources' on the top left of your screenshot - but it should not have 'working properly' if any of those existed.

WHen I referred to 10 tries - that's 10 tries that 'apparently' worked - before i got one that survived a reboot and still worked....

This is a strange one!  Have you run your network connections wizard again?

---

### Post by Biscuitpie on 2007-04-07
Which one? Hehe, haven't had to do this stuff in a long time!

---

### Post by freebird54 on 2007-04-07
Problem is - neither have I!  I have a dual boot here, and I haven't needed/wanted to see xp in a couple of weeks at least...

Which one?  Only one Network wizard I know of... :)  Sorry can't be more specific right now - the Toronto Maple Leafs need this win - and they can't win if I don't watch (nahh - no superstitions here)

---

### Post by Biscuitpie on 2007-04-07
> **freebird54 said:**
> Problem is - neither have I!  I have a dual boot here, and I haven't needed/wanted to see xp in a couple of weeks at least...

Which one?  Only one Network wizard I know of... :)  Sorry can't be more specific right now - the Toronto Maple Leafs need this win - and they can't win if I don't watch (nahh - no superstitions here)

Well what exactly do you want me to do in the network connections wizard? (Trying to get all the info I can before going to XP where I won't have internet >.> )

---

### Post by Biscuitpie on 2007-04-07
Bump.

---

### Post by Biscuitpie on 2007-04-07
Sorry to keep bumpbing, but this is important.

EDIT: Ah, got it fixed. Thanks, everyone!

---

