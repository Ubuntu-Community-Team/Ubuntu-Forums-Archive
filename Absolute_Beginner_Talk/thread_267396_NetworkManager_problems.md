---
title: "NetworkManager problems"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by 00trav on 2006-09-28
I am noob, so if i sound like i don't know what i am doing, its because i don't know what i am doing.  I just installed ubuntu, love it, wireless worked at school right out of the box (unsecured network). when i went home, i had some issues becuase i have a WPA encrypted network.  no problem, found the post on how to get iwp2200 and WPA to work, modified the files and restarted, it worked great. 

my problem is that i want to be able to go from home to school without having to constantly change my /etc/network/interfaces file.  It was suggested to use NetworkManager, so i installed network-manager-gnome, and checked and made sure it also installed network manager.

my problem comes with the interface, compared to the screenshots and what other people say they see, i don't have anything near that.  All I get is a little computer screen looking icon in the upper right with a caution triangle and when i click on it it has a drop down with a radio button and "wired network", which is grayed out because there is no wired network plugged in.

I have tried searching for a network manager config file but i can't find it. any ideas.  i feel like i am missing something simple here.

i am running an HP DV1000, with intel 2200BG card, wpa_supplicant works with Wext driver. newest version of ubuntu off their site.
Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5))

thanks in advance

---

### Post by H.E. Pennypacker on 2006-09-28
I simply use Network Settins (System > Administration > Networking).  If I need to switch to another network, I click on my wireless networking card, and go to "Properties."  From Properties, I get a drop-down list of the networks available in my neighborhood.  The drop-down list also tells me whether those networks are secured or not.  

I then pick a network, and click "OK."  That's it. 

Doesn't this work for you?

You could use Network Manager, but try using Ubuntu's tools first.

---

### Post by 00trav on 2006-09-28
the network config tool that ubuntu comes with doesn't work on WPA networks. 

i did finally get networkmanager to work, i had to delete everything but the auto loopback from the interfaces file.

i am going to test it out a little more... but so far its work, but a lot slower then using the built in tool.

---

### Post by shanepardue on 2006-09-28
> **00trav said:**
> the network config tool that ubuntu comes with doesn't work on WPA networks. 

i did finally get networkmanager to work, i had to delete everything but the auto loopback from the interfaces file.

i am going to test it out a little more... but so far its work, but a lot slower then using the built in tool.
i'm very interested in your conclusion as i've had the same problem. i use ubuntu's network tool for now, but it seems too much of a hassle changing networks as opposed to right-clicking the nm-applet. please let us know how it goes for you!

---

### Post by shanepardue on 2006-09-28
p.s. if you could include a screenshot of how it looks for you, that'd be awesome!! thanks!

---

### Post by 00trav on 2006-10-02
alrighty, Network-Manager works like a charm.  I just got back froma weekend trip, connected to several different networks, both encrypted (WPA) and non encrypted. 

i don't really have anything negative to say about Network manager.  I ended up reinstalling ubuntu after i messed up some config files (unrelated to wireless). after the reinstall, I used the synaptic Package Manager to install network manager and all the components. I deleted everything except the loopback from /etc/network/interfaces . (I suggest making a backup before you do this, or just comment out all the lines).

I restarted and the icon was in the upper right where it should be, i clicked on it, it displayed all the different networks to connect to.  After selected the network, it autodetected the security and prompted for the password (which is saved and used the next time i turned on my computer).

All in all, pretty easy, once i figured out the /etc/network/interfaces thing.

I am on my Windows box right now so i can't take a screen shot, but i found one on the site.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

hope this helped...

---

### Post by malathia on 2006-10-02
Excellent work. I've been wondering about this since I tried using Network Manager the other day. May I ask how exactly you stumbled on this solution? Pure desperation or a moment of divine intervention?  Anyway, thanks for the info. Helped me out quite a bit.

---

### Post by shanepardue on 2006-10-02
i've done as you said, but i only seem to get the icon with "enable networking" and "enable wireless". they're both checked so they are enabled, but there is not a list of networks to join. it must be an issue with my network card or something.

---

### Post by fragos on 2006-10-02
For me, wifi-radar was a better choice.  To run it I needed to uninstall the gnome-network-manager and disable the nm-applet in System-> Preferences-> Sessions-> Startup Programs Tab.  I dragged a wifi-radar icon onto the applet bar and now have instant access.  I also use the Network-Monitor applet, placing them next to each other.

---

### Post by shanepardue on 2006-10-02
wifi-radar didn't work well for me either. i think i'm stuck with the regular networking route. it's not so bad with locations set up and all.

---

