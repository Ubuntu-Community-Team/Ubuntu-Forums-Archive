---
title: "extremely new to ubuntu, wireless usb problem"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by mikey555 on 2006-03-10
hello! i installed ubuntu last weekend, and i havent found out how to get the drivers installed until today with the help of this forum. the adapter i have is the airlink+ 101 wireless usb 802.11b. i installed the drivers (i'm pretty sure) with the ndiswrapper but now i don't have a clue what to do. could anyone help me out? thanks!

---

### Post by Pragmatist on 2006-03-10
Try reading this and when you get stuck ask us specific questions:
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by mikey555 on 2006-03-10
ok ,thanks for that. ill try doing what it says. i found out my usb adapter isnt on the lst. (i also found out airlink+ and airlink101 might be different companies... two different sites, logos, but somehow they still seem related). i got the drivers, and im going to try installing the right ones this time.

---

### Post by mikey555 on 2006-03-11
hmm still not working. what i did now was 

sudo ndiswrapper -i <name>.inf 

but what it said was that is couldnt be installed. i then did

ndiswrapper -l    to list them, it said 2 of em werent installed properly or something, and 2 of em were. i tried deleting all of them with -e to start it over again but it said they dont exist... anyone have any suggestions?

---

### Post by Pragmatist on 2006-03-11
> it said 2 of em werent installed properly or something

You need to paste the output in your post so we can see exactly what it says.

---

### Post by mikey555 on 2006-03-11
ok i've gotten past that now, i got the correct driver installed and i deleted the wrong ones with ndisgtk. now when i try to go to set up a network, there is no spot to add a wireless network (this is contrary to what the help file for this menu says: it says there should be ann add button where i can add a network but there isn't). it does see the hardware now by the way.

---

### Post by Pragmatist on 2006-03-11
Have you read these yet?:
[https://wiki.ubuntu.com/WirelessNetworking?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessNetworking?highlight=%28wireless%29)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)

---

