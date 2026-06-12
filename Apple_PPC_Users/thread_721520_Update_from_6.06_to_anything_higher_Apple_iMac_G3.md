---
title: "Update from 6.06 to anything higher? Apple iMac G3"
date: 2008-03-11
forum: Apple PPC Users
---

### Post by steveyos666 on 2008-03-11
No distro updates show up in the default update manager, and doing the -c -d trick got me an upgrade, but it failed. I believe if I installed 6.06 on a regular PC (which I currently do not have access to or else I wouldn't be on this grey/green dinosaur) it would just show me the upgrades by default that aren't betas or whatever.

It's been a while since I've used Ubuntu, so if you're gonna recommend some repo edits and such, please also tell me how to get to them from the terminal.

I don't need the latest Ubuntu or anything, just whatever the newest version is I can get to without any problems. Something that'd hopefully let me get flash and java (or alternatives to them from what I've read on this forum) going. Or if 6.06 is good for getting all the essentials, I can just stick with this. Whatever's easiest, but I've used newer versions of Ubuntu when I had a real PC and they were obviously easier to get things going with. I still don't quite understand having LTS distros when every ugprade is so much better.

I'd also like to be able to torrent :guitar: and use .rar's. I'd prefer Utorrent if Wine can work with this ancient relic, but if not any recommendations would be welcome.

Mandatory apologizes if this is already discussed on the forum, but I've searched the best I could to find it. And this machine is amazingly slow; I feel like I'm back in 1999 with dial up.

---

### Post by stream303 on 2008-03-11
> **steveyos666 said:**
> I don't need the latest Ubuntu or anything, just whatever the newest version is I can get to without any problems.

I'd recommend Xubuntu Feisty 7.04 **ALTERNATE** for that machine:
[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/)

If you want the very latest that's not alpha, Gutsy for Xubuntu is here:
[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.10/release/)

Of course if you have a lot of ram you can run the regular Ubuntu, Feisty 7.04 is here:
[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

If you want something else, you can navigate around the directories.  Stick to the "alternate" images.

> Something that'd hopefully let me get flash and java (or alternatives to them from what I've read on this forum) going.

An alternative to flash is gnash, which is undergoing development, but you should be able to download and install it.  That's the big problem with ppc, manufacturers aren't exactly going overboard to help out the developers.

> I still don't quite understand having LTS distros when every ugprade is so much better.

They aren't exactly better, they are just places where the new ideas get worked on for the next LTS release.  A rough analogy would be to compare to Debian - you have a Debian "stable" release (Ubuntu's LTS), and a period of a "testing" release, (Ubuntu's interim releases between LTS) which are for the most part stable, but aren't as finicky as the experimental Debian Sid (Ubuntu Alpha's).  As desktop users, we can usually afford to be in testing or interim-release phase.

> And this machine is amazingly slow; I feel like I'm back in 1999 with dial up.

This could be indicative of just a network issue with our windows-centric soho networking equipment.

Some of the more usual suspects are DNS and IPV6 issues.

I'm fond of using outside DNS servers, such as those found at the bottom right hand page of

[http://www.opendns.com/](http://www.opendns.com/)

If you are using a router, I tend to put these addresses inside the router's setup page, and let the machines pick them up from there, rather than manually try to edit the config in the machine.  This way, you can bypass some of the older router's windows-centric dns issues.  They don't always play by the rules.  You can use your ISP's primary and backup dns servers of course if you know them.  Since dns addresses are a security-related issue, I don't list them here, but refer others to see it for themselves.  The addresses aren't secret, they are just easily altered.

Older routers sometimes don't quite work well with IPV6, and in that case I tend to either globally blacklist IPV6, (add "blacklist ipv6" without quotes and no hyphen to the end of /etc/modprobe.d/blacklist), restart networking or reboot, or as a quick workaround with Firefox, just disable IPV6 by typing *about:config* in the url bar, search for IPV6, and double click on *network.dns.disableIPv6* to make the boolean value "true" and restart firefox.

See if these tips help you out on your current installation, and let us know if you decide to try the others!

---

### Post by steveyos666 on 2008-03-12
I managed to get 7.04 working, but of course not perfectly. I'm having problems with Gnash, but I'm probably doing it wrong. I'm not even sure which download I get. I'm mainly just used to Automatix, kinda screwed me over on learning how to ./install tar files and all that. Gonna take a guess and say Automatix won't work on this machine? I don't see any downloads for PPC, but Ubuntu likes to hide them too so maybe they're out there. If not, some help with Gnash would be nice.

Any chance on Wine so I can get Utorrent? MP3 support? I'm just trying to get this thing to browse the net the best it can, and play MP3's and let me torrent.

Thanks a ton so far.

---

### Post by DirtDawg on 2008-03-12
I actually put Debian Etch onto my g3. It works great and, although some things are a little trickier to get set up, you'll feel right at home as it's very similar to Ubuntu.

---

### Post by steveyos666 on 2008-03-12
> **DirtDawg said:**
> I actually put Debian Etch onto my g3. It works great and, although some things are a little trickier to get set up, you'll feel right at home as it's very similar to Ubuntu.

How much trickier are things? Things are hard enough with Ubuntu.. heh. Does it run faster? I could definitely use something that'd run better on old hardware, but at the same time I need to be able to set it up to actually have a purpose. Internet, music, torrents- I need 'em. It's been like a month since I've actually gotten to listen to music, I won't live much longer like this.

---

### Post by stream303 on 2008-03-12
I recently put Debian Etch 4.0r3 on my G5 iMac and documented how it went here:

[http://ubuntuforums.org/showthread.php?t=701875](http://ubuntuforums.org/showthread.php?t=701875)

It runs fast, in fact faster on my external firewire than Gutsy runs on my internal drive.  Not only that, but when you call up Rhythmbox, you'll find many mp3 streams available for listening right away.  To be fair, I haven't tried the latest 6.06x dapper to compare it with.

The thing to remember is that all ppc distros face the problem of the lack of proprietary video drivers (not a problem in my book!) so don't expect any fancy 3-d graphics.  And just because the Gnome desktop environment is fast, it doesn't mean that the applications will run any faster - something you'll find out if you try to manipulate huge graphics in Gimp for example on a low-spec ppc box, no matter what distro or window manager you use.

You might be better off running Tiger or Panther on that box for the things you want to do.

The thing is, as ppc users, we are already doing things in a very "debian way" already, since ppc doesn't "just work" all the time.  We can't blame Ubuntu nor Debian, since some of the problems come even further upstream in xorg or the kernel for instance.

---

### Post by steveyos666 on 2008-03-12
I'm not a fan of torrenting operating systems, so I won't get tiger or panther.

Plus I loves me some Linux, and if I see one more Dock I'm gonna just smash this thing and wait until I get my new laptop with Vista.

I'm gonna download Debian and see where that takes me. As long as I've got a good tutorial on setting stuff up I should be all set. I've gotten everything working on an Ubuntu install plenty of times, I'm just not used to PPC and its lack of support.

---

### Post by konungursvia on 2008-03-12
Upgrades are finicky. I'd backup your /home/ folder to an ntfs or other drive, by copying the /home/ folder or by using flyback to do the same thing. This will save your settings and personal files. Then, I'd suggest downloading and burning the ISO for a new install of 7.04 or, next month, 8.04. Then make a new install.

---

### Post by DirtDawg on 2008-03-12
> **steveyos666 said:**
> I'm not a fan of torrenting operating systems, so I won't get tiger or panther.

Plus I loves me some Linux, and if I see one more Dock I'm gonna just smash this thing and wait until I get my new laptop with Vista.

I'm gonna download Debian and see where that takes me. As long as I've got a good tutorial on setting stuff up I should be all set. I've gotten everything working on an Ubuntu install plenty of times, I'm just not used to PPC and its lack of support.

Yeah, give it a shot. If you've gotten Ubuntu running several times, you'll have no problems. I was nervous too when I switched, but the hardest part is figuring out which image to download! 

I also agree that debian runs noticeably faster on the g3. Let us know how it goes!

---

### Post by steveyos666 on 2008-03-12
Thank you everyone, a lot, for the help so far.

I don't wanna say mission accomplished yet but so far Debian is rocking.

However, of course, now I still need MP3 support etc etc etc etc. But from what I gather, this is the newest distro, so things shouldn't be that bad. Am I correct? Ubuntu = given up on PPC for the most part, as where Debian = their main download page has [all] [sorts] [of] [things] [including] [PowerPC]? I don't even know most of the things it supports, damn.

I've still got the 7.04 disk just in case though.

I'll head over to the Debian forums in a bit to see if I can't find some stuff on MP3's _(EDIT: Oh! MP3 seems to be working like stream said, so hopefully it'll just work with all my stuff. Another point for Debian)_ , torrents, flash/java/firefox etc etc etc, but if you wanna contribute in this thread that's fine by me.

If I can get all that working, Debian stays. But, I'll be getting my sister's old laptop when she buys a new one, and that'll get Ubuntu no doubt. I love it too much to leave it.


But now I've got another problem: no right mouse button and f12 doesn't count as a right click. There's gotta be a way to assign a key as the right mouse, I'll search for it myself in a bit. Need a break after all this installing.

---

### Post by DirtDawg on 2008-03-13
> **steveyos666 said:**
> Thank you everyone, a lot, for the help so far.

I don't wanna say mission accomplished yet but so far Debian is rocking.

However, of course, now I still need MP3 support etc etc etc etc. But from what I gather, this is the newest distro, so things shouldn't be that bad. Am I correct? Ubuntu = given up on PPC for the most part, as where Debian = their main download page has [all] [sorts] [of] [things] [including] [PowerPC]? I don't even know most of the things it supports, damn.

I've still got the 7.04 disk just in case though.

I'll head over to the Debian forums in a bit to see if I can't find some stuff on MP3's _(EDIT: Oh! MP3 seems to be working like stream said, so hopefully it'll just work with all my stuff. Another point for Debian)_ , torrents, flash/java/firefox etc etc etc, but if you wanna contribute in this thread that's fine by me.

If I can get all that working, Debian stays. But, I'll be getting my sister's old laptop when she buys a new one, and that'll get Ubuntu no doubt. I love it too much to leave it.


But now I've got another problem: no right mouse button and f12 doesn't count as a right click. There's gotta be a way to assign a key as the right mouse, I'll search for it myself in a bit. Need a break after all this installing.

Excellent, glad to hear it.

As far as the mouse button, there is a way to assign it to a key because I did it before, but it's been awhile so I don't remember how. I'll take a look through my notes later. Honestly though, I would highly recommend picking up a cheap usb mouse(I found some at my local second hand store). It will save you lots of grief in the long run.

Also, you should be aware that there is no Flash on linux ppc. This is not a specific distro issue, it just doesn't exist. I've heard about gnash and one or two other open source alternatives, but never got them to work right.

I also stuck with Ubuntu for my x86 comp. But for the ppc, I think Debian is the way to go.

---

### Post by steveyos666 on 2008-03-13
Yeah I'll be getting a better mouse, just can't right now.

So are you going at it with no flash or java? I guess I could live without them, or at least I hope.

Got any suggestions on a browser and IM client? I'm hoping to get firefox and GAIM, since they're what I know and what works best for me. I'll browse through synaptic and see if I get lucky. I'll report back when I make some progress.

---

### Post by stream303 on 2008-03-13
Firefox should already be on the install - in Debian it is known as "IceWeasel" due to licensing issues.

The browser icon on the top bar is actually the Epiphany browser, which uses the same gecko engine as Firefox, er Iceweasel. :)  So you get two browsers right off the bat.

You may want to be sure to make your fonts look good with

```
dpkg-reconfigure fontconfig-config
```

and at the last prompt, just say NO to bitmapped fonts.  I've got a feeling you'll be wanting to add some truetype fonts such as msttcorefonts.

---

### Post by DirtDawg on 2008-03-13
> **steveyos666 said:**
> Yeah I'll be getting a better mouse, just can't right now.

So are you going at it with no flash or java? I guess I could live without them, or at least I hope.

Got any suggestions on a browser and IM client? I'm hoping to get firefox and GAIM, since they're what I know and what works best for me. I'll browse through synaptic and see if I get lucky. I'll report back when I make some progress.

Java works fine, although it's slightly tricky to set up. I have notes on that too that I can take a look at. I'll try to get back to you tomorrow on that and the key-bindings stuff. 

Flash, though, is a no go. It sucks, I totally feel your pain, but until you get that laptop, I'm afraid you're out of luck on the YouTube.

Gaim works fine for me as an instant messenger. Pidgin is the updated version of Gaim, but I haven't bothered trying to install it on the imac as Gaim suits my needs fine. 

I've personally found Firefox(or Iceweasel, as it's called on Debian) to be pretty bogged down. I use Epiphany, which can be found in the repos. It's based on the same engine as Firefox(gecko), but is tailored for gnome and I've found that it runs a bit faster. Epiphany is good, but not ideal. An ideal, light web browser is the one thing I haven't been able to find to my satisfaction. Opera has a ppc linux version, but when I tried it, I only got errors.

---

### Post by DirtDawg on 2008-03-13
Ah, found the Java link I was looking for: [http://peter.makholm.net/2007/04/16/java-on-linuxppc/](http://peter.makholm.net/2007/04/16/java-on-linuxppc/)

I had a rough time getting Java to install and I remember this was the only thing I found that worked. In fact, I was so happy I left a comment! It had something to do with the way a file was named. I think step 4 and the blurb after step 5 are key.

So, just follow the steps carefully and hopefully everything will work fine for you. Welcome to the wonderful world of Linux on ppc ;)

---

### Post by DirtDawg on 2008-03-13
Okay, since I'm awake, I'll try to help with the mouse buttons as well. Aparantly, I didn't take the notes I thought I did concerning this, so what I'm suggesting you try here, I have not actually tried myself.

**EDIT**: To any wayward travelers who may have found their way here. Simply install 'mouseemu' with
```
sudo apt-get install mouseemu
```
This package will make F10 the MMB and F11 the RMB by default and is a hell of a lot easier than anything suggested below. [/EDIT]

According to the [debian ppc installation manual]("http://www.debian.org/releases/stable/powerpc/install.txt.en"), you can emulate a 3 button mouse like this:
```
Modern kernels give you the capability to emulate a three-button mouse when
your mouse only has one button. Just add the following lines to /etc/
sysctl.conf file.

# 3-button mouse emulation
# turn on emulation
/dev/mac_hid/mouse_button_emulation = 1
# Send middle mouse button signal with the F11 key
/dev/mac_hid/mouse_button2_keycode = 87
# Send right mouse button signal with the F12 key
/dev/mac_hid/mouse_button3_keycode = 88
# For different keys, use showkey to tell you what the code is.
```
Only problem is, on my g3 at least, 87 and 88 are not the F11 and F12 keys. To find out the keycode of a key, you can use the '**xev**' command. Then, when you press a key, it will give you a keycode(amongst some other spewage). Try replacing the keycodes above with the keycodes of whatever keys you decide you'd like to use to emulate RMB and MMB.

Actually, if this works, it would be a lot easier than whatever I did before. Again, please let us know if it works(and buy a 2 button mouse asap)!

---

### Post by steveyos666 on 2008-03-13
dpkg-reconfigure fontconfig-config is *awesome*.

I got GAIM working, perfectly simple with synaptic.

And I'll use Epiphany, fine with me.  "GNOME Web Browser 2.14.3" under help/about, so it's made for it. I don't like the default setup though with just a giant search bar, but I'll just tweak it and be happy.

As far as Java goes, I probably don't even need it. If I do though I'll keep that link in mind.

Thank you, thank you, thank you a lot for all the help. If you still have any more suggestions, go for it. As of now I think I've got this setup as good as it's gonna get (except the mouse heh), and at least it'll do the basics decently.

---

### Post by steveyos666 on 2008-03-13
WAIT TIME OUT FORGOT XEV

EDIT again: Well actually that didn't seem to work either. 

```

KeyPress event, serial 26, synthetic NO, window 0x3c00001,
    root 0x44, subw 0x0, time 2801662028, (828,38), root:(833,116),
    state 0x0, keycode 95 (keysym 0xffc8, F11), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3c00001,
    root 0x44, subw 0x0, time 2801662108, (828,38), root:(833,116),
    state 0x0, keycode 95 (keysym 0xffc8, F11), same_screen YES,
    XLookupString gives 0 bytes:

KeyPress event, serial 29, synthetic NO, window 0x3c00001,
    root 0x44, subw 0x0, time 2801663670, (828,38), root:(833,116),
    state 0x0, keycode 96 (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3c00001,
    root 0x44, subw 0x0, time 2801663727, (828,38), root:(833,116),
    state 0x0, keycode 96 (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes:


```

I put in 95 and 96. Are those the right numbers? No luck if so. Maybe I gotta restart or something?


^^^^^^newest edit to this post woo 3:16 AM^^^^^^^^^^^^

> **DirtDawg said:**
> Okay, since I'm awake, I'll try to help with the mouse buttons as well. Aparantly, I didn't take the notes I thought I did concerning this, so what I'm suggesting you try here, I have not actually tried myself. 

According to the [debian ppc installation manual]("http://www.debian.org/releases/stable/powerpc/install.txt.en"), you can emulate a 3 button mouse like this:
```
Modern kernels give you the capability to emulate a three-button mouse when
your mouse only has one button. Just add the following lines to /etc/
sysctl.conf file.

# 3-button mouse emulation
# turn on emulation
/dev/mac_hid/mouse_button_emulation = 1
# Send middle mouse button signal with the F11 key
/dev/mac_hid/mouse_button2_keycode = 87
# Send right mouse button signal with the F12 key
/dev/mac_hid/mouse_button3_keycode = 88
# For different keys, use showkey to tell you what the code is.
```
Only problem is, on my g3 at least, 87 and 88 are not the F11 and F12 keys. To find out the keycode of a key, you can use the '**xev**' command. Then, when you press a key, it will give you a keycode(amongst some other spewage). Try replacing the keycodes above with the keycodes of whatever keys you decide you'd like to use to emulate RMB and MMB.

Actually, if this works, it would be a lot easier than whatever I did before. Again, please let us know if it works(and buy a 2 button mouse asap)!




So do I sudo gedit /etc/sysctl.conf ? I did that, then I added your code to the bottom of this but it didn't seem to do anything...


```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1


# 3-button mouse emulation
# turn on emulation
/dev/mac_hid/mouse_button_emulation = 1
# Send middle mouse button signal with the F11 key
/dev/mac_hid/mouse_button2_keycode = 87
# Send right mouse button signal with the F12 key
/dev/mac_hid/mouse_button3_keycode = 88
# For different keys, use showkey to tell you what the code is.

```

Do I need to put it somewhere else in the text file? Maybe restart the pc? Disable F12 from doing anything else for any other programs?

---

### Post by DirtDawg on 2008-03-13
> **steveyos666 said:**
> So do I sudo gedit /etc/sysctl.conf ? I did that, then I added your code to the bottom of this but it didn't seem to do anything...
Do I need to put it somewhere else in the text file? Maybe restart the pc? Disable F12 from doing anything else for any other programs?

Did you use the 'xev' command as I suggested? It might help if you did not. Also, after you finish editing the file, you will probably have to log out and back in. Maybe even reboot, though I doubt it.

Even then, like I said, I've never tried this particular method. I'm trusting the debian install guide. If it doesn't work, I'll see if I can't figure out whatever it was I did before. I'm sure it also involved the 'xev' command.

EDIT: Just to be clear, on my computer, for example, when I run xev and press the F12 button, I get this(I added the highlights):
```
KeyPress event, serial 29, synthetic NO, window 0x3600001,
    root 0x4d, subw 0x0, time 1774862647, (486,128), root:(496,225),
    state 0x10, **keycode 96** (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3600001,
    root 0x4d, subw 0x0, time 1774862729, (486,128), root:(496,225),
    state 0x10, **keycode 96** (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
The first is when I press the key, the second is when I let go. They're both essentially identical for our purposes. Anyways, if you look you will see a snippit in there that says: 'keycode 96', so I would add this line to my /etc/sysctl.conf:
```
...
# Send right mouse button signal with the F12 key
/dev/mac_hid/mouse_button3_keycode = **96**
...
```
Notice I changed the default '88' with my 'actual' keycode of '96'.

Hope this helps clear up any confusion.

---

### Post by steveyos666 on 2008-03-13
I'll try logging out and back in and if that doesn't work I'll restart, back in a few years!

Well at first it didn't work, so I did what any professional would do: push buttons


I ended up trying the apple key + f12, control, alt + f12, then I pushed all four buttons and my screen went blank except at the top left with a little blinking _

So I held down the power button, and now I'm back. While f12 doesn't work, enter on the numpad counts as a right click. I wonder if it did that by default? Much better spot than f12 anyway.

Sometimes you gotta just push buttons.

I don't need the middle mouse button, so I'd say this was a success!

---

### Post by DirtDawg on 2008-03-13
Wow! Talk about making things harder than they need to be! I just found a package called 'mouseemu'. You can install it with:
```
 sudo apt-get install mouseemu
```
This maps the MMB to F10 and the RMB to F11 by default. You don't even have to log out! I'm sure you can change the default keys if you want, but don't ask me how :D Maybe 'man mouseemu' will help.

EDIT: I just read about your button mashing experiment. I appreciate your spirit, but I would suggest erasing those lines you placed in the config file and using the method above. Sorry I didn't tell you about this super easy method before, but I didn't know about it! What can I say :)

---

### Post by steveyos666 on 2008-03-13
Well I deleted that stuff in /etc/ and the enter key's still workin, so I'm not gonna bother with mouseemu unless it stops. Hopefully this thread helps some other newcomers though, you guys did an awesome job. Even the link to 7.04 helped me understand the alternate install and stuff, so that'd be good for someone who can't make the switch to Debian (hint: it's exactly the same but with a tiny bit less polish).


But since we're on a roll here, how about I throw out another problem? Power options don't seem to do anything. I want the monitor to shut off after about seven minutes and the computer to go into standby after about twelve. I couldn't get that to happen. I set everything to "never" but the monitor turned itself off after a bit anyway. Is it confused since the entire computer's all in one case? Including the awesome... awesome speakers oh man I need better speakers..


Oh and some stuff with Epiphany. I get a lot of "forms are unfinished" errors when I go to close tabs, and things are opening in a new browser instead of in a new tab. Any way to fix that stuff? How about a real address bar instead of a giant search bar? Maybe the google toolbar? Spell check? Can I get ctrl t to go to a blank tab and not the home page? Anything?

---

### Post by stream303 on 2008-03-13
> **steveyos666 said:**
>  Power options don't seem to do anything. I want the monitor to shut off after about seven minutes and the computer to go into standby after about twelve.

Welcome to the club.  Unfortunately, for many models, monitor power-down and shutoff are still dependent on the manufacturer's secrets.  I have to resort to the old "If I'm away for 8 hours or more, shut the whole thing down."  

>  Including the awesome... awesome speakers oh man I need better speakers..

For my money, the JBL Duet speakers offer the best bang-for-the-buck.  You'll get a million opinions about speakers, but to my ears the flat response with a bit of low-end enhancement is perfect on a budget.

[http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?mco=57009F69&fnode=home/shop_ipod/ipod_accessories/speakers&nplm=TB998LL/A](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?mco=57009F69&fnode=home/shop_ipod/ipod_accessories/speakers&nplm=TB998LL/A)

---

### Post by steveyos666 on 2008-03-13
Well my sister will be giving me her old laptop, hopefully sometime soon, and when that happens this won't ever be used unless my cousin comes over, so power isn't that big of a problem at least.

As far as speakers go, I can't afford 'em right now. Plus I wouldn't give Apple any money (someone was throwing this iMac out, *score*), they already got some from when I bought my iPod but I smashed that thing and my next purchase will be something better. I don't need to overpay. Plus, I'm one of those people who can appreciate low quality, makes you a better person or something. Or actually, I got some speakers now that I think of it, I just need to get adapters for them, but for some reason I enjoy low quality things and am rocking out with these little tin cans.

---

### Post by doorknob60 on 2008-03-14
If you want flash, you could try Gnash. The newest version supports Youtube, and it should work on PPC. It's in the Debian repository, but depending on your version that you installed, it might not be a new enough version to support youtube. If you want to try it though:

If you're using Etch:
[http://packages.debian.org/etch-backports/gnash](http://packages.debian.org/etch-backports/gnash)
[http://packages.debian.org/etch-backports/mozilla-plugin-gnash](http://packages.debian.org/etch-backports/mozilla-plugin-gnash)
(Get Both)
You could probably get these ones from the repository also, but you might have to enable backports or something, not totally familiar with Debian's default repository setup.

Also, if that version doesn't work with Youtube, which I'm not sure if it does, you could cheat and try to install packages from Sid (Unstable). Use at your own risk, but you can always uninstall the packages if they cause problems.

[http://packages.debian.org/sid/mozilla-plugin-gnash](http://packages.debian.org/sid/mozilla-plugin-gnash)
[http://packages.debian.org/sid/gnash](http://packages.debian.org/sid/gnash)

It might require more packages linked from those links, so download those too if it asks you, but so that at your own risk. Alternativly, you could compile Gnash. Good luck :)

---

### Post by steveyos666 on 2008-03-14
Well I thought I'd give Gnash a shot on my own, but I can't figure out how to install it. I don't know how to install anything that isn't automatic (I miss automatix heh). A little help please?

and thennnn...

stevey is not in the sudoers file.  This incident will be reported.

I've been getting this while trying to install things from the terminal. I switch into root and it works fine, but I know I shouldn't have to. Help with that please?


On another subject, I got another problem. I've installed a few things like Transmission for torrents and Camera (I just searched for camera and got that) in hopes of being able to import pictures from my camera (obviously). After they're installed, they don't show up in the Applications menu. I try right clicking and going to open with (I had to use that mouseemu, I can't find that eiter as a program but it just works as f11), but they're not in that list either. Those ones I tried with synaptic, and then I tried with terminal but it said they were installed. I'm guessing I need to use Alacarte or something to put them in the applications menu? I'd need some directions with that please.

---

### Post by stream303 on 2008-03-14
> **doorknob60 said:**
> You could probably get these ones from the repository also, but you might have to enable backports or something, not totally familiar with Debian's default repository setup.


I just checked the backports for Ubuntu Feisty, and it appears that Gnash 0.8 and youtube-dl are both available in the backports repository.  If you go into "software Sources" and enable the backports repository, you should be able to pick up both of these.  I'm sure it is similar for Debian.

---

### Post by DirtDawg on 2008-03-15
> **stream303 said:**
> I just checked the backports for Ubuntu Feisty, and it appears that Gnash 0.8 and youtube-dl are both available in the backports repository.  If you go into "software Sources" and enable the backports repository, you should be able to pick up both of these.  I'm sure it is similar for Debian.

It's not quite as easy for Debian Etch, but it's not terribly hard. You just follow [these instructions]("http://www.backports.org/dokuwiki/doku.php?id=instructions") to add the backport repositories to your sources list.

Unfortunatly, the newest version for Etch appears to be 7.2. I installed and tested it out and the results were pretty bad. Iceweasel doesn't seem to register the plugin at all, even though I have the mozilla-plugin-gnash package. Epiphany was worse. When I tried to run a youtube video, my g3 crashed and crashed hard. Reboot was necessary.

I also tried the testing suggestion on [this page]("http://wiki.gnashdev.org/wiki/index.php/YouTube#Full_off-line_testing") and, although I did get a youtube-like window, the video did not play. On the upside, it didn't crash the computer either.

It looks like the only version 8.2 in the backports are for Sid(unstable). I'm tempted to go ahead and attempt the upgrade if Gnash will actually run youtube videos. Anyone have any experience using it as a replacement for the official Flash player?

Also, if anyone knows how to get 7.2 in working order, I would love that too.

---

### Post by DirtDawg on 2008-03-15
> **steveyos666 said:**
> Well I thought I'd give Gnash a shot on my own, but I can't figure out how to install it. I don't know how to install anything that isn't automatic (I miss automatix heh). A little help please?

and thennnn...

stevey is not in the sudoers file.  This incident will be reported.

I've been getting this while trying to install things from the terminal. I switch into root and it works fine, but I know I shouldn't have to. Help with that please?


On another subject, I got another problem. I've installed a few things like Transmission for torrents and Camera (I just searched for camera and got that) in hopes of being able to import pictures from my camera (obviously). After they're installed, they don't show up in the Applications menu. I try right clicking and going to open with (I had to use that mouseemu, I can't find that eiter as a program but it just works as f11), but they're not in that list either. Those ones I tried with synaptic, and then I tried with terminal but it said they were installed. I'm guessing I need to use Alacarte or something to put them in the applications menu? I'd need some directions with that please.

You may need to install the sudo package as it does not come preinstalled with Debian:
```
su
apt-get install sudo
exit
```

As far as your camera, have you tried just plugging it in? It might work. If not, look through these forums and see what people recommend since Debian and Ubuntu are identical in many ways. Some applications don't start until you plug in hardware(like your camera) so there's not really any way to "start" the app before that. Others you can start in the terminal, usually by typing in the name of the program. Try typing 'transmission', for example, although I've never used nor heard of that app(I like rtorrent. Lots of people prefer deluge). 

And yes, alacarte is great too. Install it if you haven't already:
```
sudo apt-get install alacarte
```

EDIT: A note on sudo. You have two passwords with Debian vanilla. You're administrative password(the one you use with su), and your user password(the one you will use with sudo). You entered them both upon installation. This is actually one thing I don't like because I'd rather just have one password to have to remember. But I really only use the administrative password for updates, so I guess it's no biggie.

---

### Post by steveyos666 on 2008-03-15
Well if you're having problems with Flash, I honestly doubt I'd get it. Not sure if I said it yet but even when I had OS X on here, videos went like this for the most part: still image of first frame of video while all the audio plays choppily, then a slideshow of the video. I think this thing's happier without it.


As far as sudo goes, I type just sudo in and get:

```

usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

```

So I'm guessing I already got it, and just need to add myself to some list like it says? -u myname|#whatever_number_this_is ?

With Alacarte, I have it, but I have no idea how to use it. How do I know where things are installed? I'm only used to digging around Windows, I don't know where the Program Files for Linux is. Once I'm able to add things to the "start menu", I'll try those torrent programs you mentioned. 
I type transmission into the terminal and get "bash: transmission: command not found", but either away I'll give your reccommendations **(where's the global spell check like Ubuntu has? I *need* that)** a try in case they just work.

When I plugged the camera in it asked if I wanted to import, I clicked yes, then never saw from that program again. So maybe my stuff's actaully on my hard drive somewhere?

And as far as the two passwords go, they're both just "f". I don't really have a need for local security, and if they're meant to stop hackers getting into this machine... well I say if they wanna wait a year for a single folder to open, they've earned it.

---

### Post by ubuntubrian on 2008-03-16
I have installed gnash from source and it is not easy at all. The INSTALL file in the gnash package helps and you'll need lots of forum help too (gnash forum that is)! There are lots of config options and some work, some don't and they are all command line. You'll need SVN installed and do a check out in terminal and then do the install. Google gnash and go to the home page and check out the install instructions. Like I said, not easy. Gansh works with some youtube and sometimes as a capable plugin for firefox but it's not great yet. Better to install the firfox extension, download helper and watch on VLC.The 6.06 version of VLC doesn't play flash but the most recent source version does and it's not hard to install. Download the package from VLC home page and follow the INSTALL file instructions.

---

### Post by steveyos666 on 2008-03-16
Before I try that though, do you think I'd even be able to run videos?

400mhz G3
256mb
8mb graphics

Like I said, they didn't run with OS X, and on Debian I'm lucky to get a smooth running .gif let alone a real video. I just really don't think I could get my hopes up, plus apparently Debian took up about 80% of my hard drive since I only have a couple free gigs left from this ten gig drive. I'd rather just clear up some space so I could get more music, and worry about flash when I actaully get a computer that could handle it.

---

### Post by ubuntubrian on 2008-03-16
If you install the firefox extension "download helper" and you have VLC (a video player in the repositories and easily installed) then yes you would be able to play videos. VLC plays almost everything. Download Helper is easy to install too-just open firefox, go to Tools>add-ons and you'll be directed to the mozilla add-on page where you can find "DownloadHelper". Install as per instructions. You can install VLC from Applications>add/remove. Download a video and open it with VLC and it should work fine even with your set up..

---

### Post by steveyos666 on 2008-03-18
Hey it works good enough, thanks. I toally forgot about VLC, best program ever!

Now I'm seriously running out of hard drive space though... it's like ten gigs, and Debian took up about seven or so gigs... Anyone got an idea of any of the junk I can uninstall that came with Debian?

---

