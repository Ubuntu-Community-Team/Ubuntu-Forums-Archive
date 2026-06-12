---
title: "Need help with wireless card on Thinkpad X41..."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by cloudcover on 2007-11-05
hi there -

i'm totally new to linux and just installed ubuntu (gutsy gibbons) on my thinkpad x41.  the regular ethernet connection works fine, but my wireless networking doesn't seem to work at all.  when i click on the "Network" icon on the top (near the clock) the only entries are "Wired" and "Manual configuration."  if i click on "Manual configuration" i see a dialog box that lists "Wireless Connection" at the top with a check in the box to its left.  it has the correct name of my home network (i.e., its essid) but i can't connect to anything.  when i try to ping [www.google.com](www.google.com), nothing happens.  

i don't know if i'm supposed to have the "Enable roaming mode" box checked or unchecked.    i'm unchecking it, just because that's when i'm able to make any changes to the network info (e.g., selecting security, etc).  and just to avoid any issues with encryption, i've disabled any kind of encryption temporarily on my router.  in that case, how do i indicate to the network utility that there's no encryption set.  is it simply by selecting wep security and leaving the password field blank?

i've looked around elsewhere online before posting here and it seems some people recommend using wlassistant.  but i'm so new to this that i don't even know which package to get and how to install it.  (very frustrating, since i knew this kind of stuff very well on the windows side of things).  i tried downloading it from [https://launchpad.net/ubuntu/gutsy/+source/wlassistant/](https://launchpad.net/ubuntu/gutsy/+source/wlassistant/), but don't even know which file to get...is it the binary package, one of the tar files, or what?  also, i saw on other sites a suggestion to type "sudo apt-get install wlassistant" in a terminal window, but that just returns an error code of some sort (can't remember exactly what it is).

would really appreciate any help i can get on this?  also, though basic operation is the key issue right now, i'm also wondering how to turn the wireless card on/off, for when i want to conserve battery life.

thanks in advance, from a bright shiny new linux "trier",
kr

---

### Post by kevinatkins on 2007-11-05
Hi,

If the wireless card in your X41 is recognised by Ubuntu then you shouldn't need to do anything other than click on the network icon and wireless networks should appear. If that isn't the case, then Ubuntu has either failed to recognise the card, or it's turned off.

I've just done a google and it seems that the WLAN chipset for your laptop is supported; however, you might need to obtain firmware. But before going that far, check that the WLAN is enabled. Normally this is via a function key combination, and I *think* it should be BIOS controlled, so will work regardless of OS... I may be wrong, but it's worth a shot initially..

---

### Post by cloudcover on 2007-11-06
strange, but it now seems to be working.  the only thing i did was select "Enable roaming" in the properties of the wireless connection and then my wireless network showed up in the networks area.  i say "strange" because the same "Enable roaming" box was checked after i first installed ubuntu but the wireless network had not shown up at the time, which is what led me to all of the machinations i mentioned before.  anyway, thanks.

---

