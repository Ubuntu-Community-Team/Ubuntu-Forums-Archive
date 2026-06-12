---
title: "NetworkManager problems after suspend"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Endless Bard on 2007-04-06
Hi everyone,

Just installed 7.04 on my Gateway M275.  Everything works just fine, including the wireless card (which was a pleasant surprise) -- Intel PRO 2200BG.  The problem I'm having is, sometimes, when I come out of suspend, NetworkManager either refuses to connect to a wireless network, or refuses to recognize that I have any network interfaces at all.

I've tried, so far, restarting GDM and stopping and restarting NetworkManager using nm-client.  Neither has had any effect.  Rebooting fixes the problem, and I can still configure the card manually using iwconfig and dhclient3, so it isn't like this is crippling.

What I would like to know is one of these two things:

1) How can I force NetworkManager to re-scan my network hardware?

2) Is there another wireless manager program that will put a nice little icon in my notification area?  I tried wifi-radar but that looks like a proper application, not an applet.

Thanks in advance.

---

### Post by mac.ryan on 2007-04-06
> **Endless Bard said:**
> 2) Is there another wireless manager program that will put a nice little icon in my notification area?

I am not sure I got your question. You mean a little something showing if there is signal and if you are connected? If this is the case, there is. (It is the same than the icon for ethernet: you simply have to click on it and select eth1 instead of eth0... you will see a bar (either green or orange) beside the little monitors...

If you don't have the icon already you can add it via right-clicking on the pane and selecting "add"...

Hope this helps! :)

PS: This is the way it works in Edgy... I hope Feisty is the same!

---

### Post by Endless Bard on 2007-04-06
> **mac.ryan said:**
> I am not sure I got your question. You mean a little something showing if there is signal and if you are connected? If this is the case, there is. (It is the same than the icon for ethernet: you simply have to click on it and select eth1 instead of eth0... you will see a bar (either green or orange) beside the little monitors...

If you don't have the icon already you can add it via right-clicking on the pane and selecting "add"...

Hope this helps! :)

PS: This is the way it works in Edgy... I hope Feisty is the same!

Mm.  No.  What I mean is, NetworkManager puts a little widget showing connection status/signal strength in what would, on a Windows machine, be the Systray (not sure what Gnome calls it).  I know I can click on it to change the interface or the wireless network it's connected to.  My problem is that sometimes, after I come out of suspend, it refuses to connect to the wireless networks.  It shows them just fine, it just won't connect.  Either that, or it doesn't show the computer as having any network interfaces at all.

When this happens, I can still configure the network interfaces using the command line.  What I'm asking is, is there a way to force NetworkManager to re-scan my network interfaces?  Or, is there a program that I can use instead of NetworkManager that will also put the widget in the Gnome-Systray?

Hope this helps to clarify.  Thanks for the response. :)

---

### Post by srt4play on 2007-04-08
When network manager is acting up, try:

```
sudo /etc/dbus-1/event.d/22dhcdbd restart
```

and then select a network to join.

If that fixes it you can create a script and put a shortcut to it in your menus. I haven't yet found the right spot to put it in the acpi resume scripts so it gets executed automatically when resuming from suspend.

---

### Post by Neikius on 2007-04-14
Similar problems here, the same (2200bg) card.

Exact description: waking up after suspend, there just aint any network interfaces available. If I use wired, I have to go to properties and unclick and click again on the interface to make it do dhcp again, while on wireless, well I just can't do squat with the interface. Wireless just disappears. Seems like a bug to me. Oh and btw, it usually freezes after that anyway, so reboot it is.

---

### Post by hotani on 2007-04-16
Same problem here, and I'm only using a wired network. Sometimes when it is revived from suspend, it will not connect to anything. IM, web, weather, all are dead. However, I can still connect to another machine on the network via ssh. 

Sometimes it actually shows that the network is fine! Usually a reboot fixes it, but last time it did not. Something is borked in there... I'm using 7.04 as well.

---

### Post by beathan on 2007-04-20
Same issue here, just installed 7.04 and I have a ipw3945 on an HP dv6000t.

---

### Post by sharan4o on 2007-04-21
Same problem with HP dv6121.After "sudo rmmod ipw3945" & "sudo modprobe ipw3945" is everything OK. Realy dirty.
[COLOR="Red"]Solution for me :[/COLOR]
edit MODULES="" to MODULES="ipw3945" in /etc/defaul/acpi-support

---

### Post by viterico on 2007-04-21
I found the solution!

edit this archive:  /etc/network/interfaces with kate, kwrite or your editor.
for example in kde: run... " kdesu kwrite  /etc/network/interfaces " and delete the wlan0 lines, save, reboot and ready!!!

The reply before (add the line in etc/defaul/acpi-support ) is too recommended.

Sorry, my english is very bad...

---

### Post by climbingrose on 2007-04-21
I got the same problem on Asus W7J. When waking up from Hibernate wireless and sometime wired network don't work.

---

### Post by bignickel on 2007-04-22
I tried Viterico's solution, and it sort of worked.  Previously, when coming back from suspend or hibernate I couldn't get the wired or wireless to work.  Now when it comes back, network manager does its circle for a minute or so, and then says it's connected, but it really isn't.  However, if I click on network-manager and click on wired network again, it will connect.  I THINK this is because of commenting out that line in /etc/network/interfaces but I can't be totally sure.

---

### Post by matthias_k on 2007-04-29
Same issue here.

This problem also applies to Edgy. The wlan0 hint is appreciated, but there aren't even wlan0 lines in my interfaces file. Actually there shouldn't be, since NetworkManager ignores the contents of this file anyways if I'm not mistaken.

I'll try the DBUS DHCP script advice, but I doubt it'll solve the problem. Theres more going wrong than just dhcp not working. NetworkManager completely loses all state and configured interfaces.

---

### Post by matthias_k on 2007-04-29
By the way, I'd rather see this thread on another forum. It's not a beginner's question, it's clearly a defect in Ubuntu and should be read by the people with the right expertise.

---

### Post by hotani on 2007-04-29
I haven't had this happen for a while now, so it may have been fixed(?). I'm sure it wasn't anything I did, since I haven't gotten around to messing with it yet.

Recently when I open the laptop lid after a suspend, the network hooks right up.

---

### Post by matthias_k on 2007-04-30
I wouldn't be so sure about that. For example, after hibernating my network used to come up fine, too, but just yesterday it broke just like after a suspend. That's on Edgy though.

---

### Post by json684 on 2007-04-30
Take a look at 

[https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28manager%29%7C%28network%29](https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28manager%29%7C%28network%29)

Discusses the suspend issue and offers a fix. I know it worked for me before upgrading to feisty. And now that I have a clean install of Feisty I just used the fix again, and I hope it works.

---

### Post by phillyburks on 2007-05-04
I was having this same problem in Edgy, where after 2 or 3 suspend/resumes Network Manager would say no network devices found. This is what worked for me, and I have the same Intel wireless chipset. If you are running Beagle for your desktop search, try killing the 'beagled' process. Make sure it doesn't get started back up and see if you still have problems with Network Manager upon resume. This solved my suspend/resume problems with Network Manager. It reconnected flawlessly every time. 

If you're like me and you like having Desktop search, remove Beagle completely and replace it with Tracker ([http://www.gnome.org/projects/tracker/)](http://www.gnome.org/projects/tracker/)). Tracker is in the repositories. It uses less system resources and also integrates with the Deskbar applet. For deskbar integration install the libdeskbar-tracker package. 

Hope this help.

---

### Post by Victor Meldrew on 2007-05-14
I was unable to connect to my wired network following a resume from suspend.

I found that including the network driver module in the WHITE_LIST within /etc/default/acpi-support fixed this problem for me.

Here is what I did :-

[INDENT]1. Identify the network module by starting System.Preferences.Hardware Information.
2. Find info.linux.driver from the Device Manager, mine was sis190.
3. sudo gedit /etc/default/acpi-support
4. Insert the driver/module into the WHITE_LIST ie.

MODULES_WHITELIST="sis190"

5. Restart the computer.
6. Suspend.
7. Resume and hopefully the network will still be running.[/INDENT]

This worked for me, I can't guarantee this will work for you. I'm sure there are better ways of identifying your network module. 

Hope this helps

---

### Post by Ubuntiac on 2007-05-15
Thanks Victor!

This worked perfectly for me first time. One thing I would add for clarity is that you're looking for _"info.linux.driver" in the "advanced" tab of the Device Manager after clicking on your network card / device_.

Took me a while to find that one... ;)

Thanks again for solving my problem Victor!

---

### Post by matthias_k on 2007-05-15
What do you mean by "network driver module"? WLAN and LAN devices use different drivers, but it has to work for both!

---

### Post by bignickel on 2007-05-20
Victor's solution worked for me too.  Thanks!

---

### Post by opus on 2007-07-06
Thanks Victor - it seems you found the solution for me as well!

Aaron Throckmorton

---

### Post by rogun on 2007-07-29
Victor's solution worked for my wired, static connection also.

---

### Post by koveitan on 2007-08-30
Victor thank you very much this solution works great 
on my thinkpad R50E
is there an open bug on this issue ?

---

### Post by Niels Olson on 2007-12-02
The whitelisting method did not work for my bcm43xx wireless card (in a Dell Latitude D820) but the [scripting method]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28manager%29%7C%28network%29") did. One thing: make sure the permissions on your new script files are executable 

```
sudo chmod 755 /etc/acpi/suspend.d/07-network-manager.sh
sudo chmod 755 /etc/acpi/resume.d/63-network-manager.sh
```

Edit: no, that didn't work. It worked a couple of times, and then it decided to cause a kernel panic. I'm back to no scripts, no whitelist, but if I use the dedicated kill switch on the side of the laptop to cycle the wireless card, that will get me back on the network.

Edit: and that seems to work over and over and over.

---

### Post by hhpeter on 2008-01-02
victor's solution worked for me too....thanks...however after suspend it shows that I'm connected but I'm not so I need to click on my wireless icon and then click on my wireless network name to connect again not big deal ....just wondering if there is a better solution ...and when Its time to restart the computer it just hangs at the and with the ubuntu screen all unloaded and I need to press for 5 sec on the power button to shut it down....don't know if its related with suspend but if I never suspend my session it shuts down normally any suggestions?

---

