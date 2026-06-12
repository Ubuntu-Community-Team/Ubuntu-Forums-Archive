---
title: "I can't even get the live cd working!"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ergonomicben on 2007-11-10
The live CD itself is fine it works on a friends pc ok, the problem i've got is i start up in safe graphics mode but after the loading bar, my monitor says "cannot display input". My monitor is a bog standard 15inch tft with a vga input, my graphics a 7600GT . I've tried setting the resolution in the loadup with F4, but it doesn't have any effect. Any ideas? (i have other questions, but lets cross that road when i get the live cd running!)

thanks in advance,
ergonomicben

---

### Post by insineratehymn on 2007-11-10
Wow, kind of sucks that you hit a problem so early...

Any luck since you've posted this?

If not, do you have another monitor to hook up to your PC?

---

### Post by HermanAB on 2007-11-10
There are many different PC configurations out there.  All distributions test against a large number of machines, but nobody has everything.  The LiveCDs provide a simple way to figure out whether a particular distribution will work on your machine.  So, shop around a bit and try Mandriva 2008, Fedora, Suse and so on till you find one that works.

---

### Post by ergonomicben on 2007-11-10
Thanks for the replies.

Still no success so i think i'll have to borrow a different monitor and try it out, (i'll ask my flatmate nicely!).
I would prefer to get ubuntu working than other distros, i don't want to give up at the first hurdle! :)

If anyone finds this thread and can think of anything i'm not doing right please do say, remember i'm completely new linux so i might be doing something stupid!

thanks

---

### Post by infurnus on 2007-11-10
I had similar problems i also have a small (15") monitor if you can get to terminal run 
```

sudo dpkg-reconfigure xserver-xorg

```
When you go through the process use the vesa driver and when it comes to the monitor do simple and choose 15" this has always worked for me but this only helps when getting to terminal.

---

### Post by gn2 on 2007-11-10
> **ergonomicben said:**
> The live CD itself is fine it works on a friends pc ok, the problem i've got is i start up in safe graphics mode but after the loading bar, my monitor says "cannot display input". My monitor is a bog standard 15inch tft with a vga input, my graphics a 7600GT . I've tried setting the resolution in the loadup with F4, but it doesn't have any effect. Any ideas? (i have other questions, but lets cross that road when i get the live cd running!)

thanks in advance,
ergonomicben

If you have a 7.10 Live CD and it will not run, preventing you from installing, when you get the boot splash screen, press F6 and type "only-ubiquity" (without the quotes) 
This will run the installer without booting a Live session.

---

### Post by ergonomicben on 2007-11-10
Thanks guys, i'll give it a go

---

### Post by ergonomicben on 2007-11-11
Just to let you know where i'm at, i borrowed a monitor and that let me use the live cd! I installed ubuntu then it was then just a case of downloading the drivers from nvidia for my graphics card through the synaptic, to get it to work with my screen.

Now the next problem i've got is getting the wireless internet working. i did a bit of research and apparently my pci wireless card is supported out of the box, belkin V1799 D7000 rev4.6, can anyone confirm this? I go to enter the ssid and the password for the WPA but it seems to try and connect forever with no success and then i can't go back to using the wired ethernet without restarting. Any ideas what's wrong?

Thanks

---

### Post by insineratehymn on 2007-11-11
Are you entering the passcode or the hex value that your router gives you?

On everything in my house (before gutsy!) I entered in the hex code, here I entered in the passcode.

Try reversing the two.

---

### Post by ergonomicben on 2007-11-11
i have a "passphrase" to enter, which didnt work... i have no idea about where to find or what is a hexcode?!

---

### Post by gn2 on 2007-11-11
Some routers/wireless adapters use a "passphrase" to generate the key in their Windows utility (my Netgear does anyway) in Ubuntu it is this key you need to enter.

If you can't find it then if possible set a key manually.

A "hexcode" is a hexadecimal code, i.e. one made up of the ten numbers 0-9 and the six letters A-F

---

### Post by insineratehymn on 2007-11-11
To find the hexcode (at least on most routers I've messed with), find your WEP settings on your router by logging to the router (unless you've changed it, 192.168.1.1).

Where you enter in the key it should generate 1 - 5 hex-key-codes, try 1 of them.

If that doesn't work, try changing your passcode to something else; the system may not like the passcode or something.

If that doesn't get you anywhere... we are always still here. =)

---

### Post by ergonomicben on 2007-11-12
It turns out it was me being a muppet! i didn't load the restricted drivers for the card because it had a different name than i was expecting, doh! it all works fine now just using the passphrase. Thanks for the help though!
Another question i have now.... is it posssible to turn on v-sync somewhere because i notice quite a bit of screen tearing with all the effects on?
Also, probably more important, i think i've done something stupid...I have two hdd the 1st has windows on, the 2nd ubuntu when booting up i have to select the primary master with F12 for Grub to load up, is there anyway of getting it to load Grub without F12? (i've read some threads about this but i'm not quite sure if i can use their solutions)

---

### Post by insineratehymn on 2007-11-13
I would suggest making this a different post in the appropriate section.

I haven't really messed with grub alot, so I'm not being a jerk... I just think you would get more attention there. =)

---

### Post by ergonomicben on 2007-11-13
yeah you're right, i'll make a new post, cheers

---

