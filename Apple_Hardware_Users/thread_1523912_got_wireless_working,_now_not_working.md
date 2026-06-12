---
title: "got wireless working, now not working"
date: 2010-07-04
forum: Apple Hardware Users
---

### Post by mwilkinson on 2010-07-04
I am new to ubuntu, but was able to load it on my iBook g4, and use terminal to put the fwcutter command in to make the wireless work. I continued enjoying ubuntu, and loaded the application ubuntu tweaks. I think whlie messing with the settings that this program allows, I made the wifi radar begin at startup. now my wifi no longer works. lurking around the forums, I saw it mentioned that this might be a problem... Tried to reinstall the fwcutter command, but no change. Wifi radar, when turned on, still finds my network, but will not connect. any help would be appriciated, esp. any help that gives detailed instructions for the non code writing type..

---

### Post by quixote on 2010-07-05
Just a few wild guesses here.  Have you tried uninstalling ubuntu-tweaks and reinstalling network-manager-gnome and maybe after that fwcutter?

---

### Post by mwilkinson on 2010-07-07
thanks for answering my cry for help post, Quixote. okay, tried that, even did wifi radar too (all uninstalled and reinstalled thru synaptic package manager) with no luck.. wifi radar shows my wifi, but when I click on it to connect, it brings up a box saying, acquiring IP address (DHCP) and just sits there trying to acquire it. I really dont know what this means; is there a way I can force feed it the IP address? would this even help?

---

### Post by svtguy88 on 2010-07-08
Which wireless card do you have?  What is the output of ```
lspci
``` when you run it in a terminal.  Look for something associated to the wireless card.  I think the iBook uses a Broadcom card IIRC.

Each computer that I've installed Ubuntu on that uses the Broadcom wifi chipset seems finicky.  I think there is a problem initializing the device, as it seems to fail most often after the system comes out of sleep mode or first boots up.  

Anyway, if you have the Broadcom card, usually simply unloading/reloading the module fixes it for me.  Run

```
lsmod
```

and look to see if the Broadcom module is currently loaded (think it's called b43).  If it's there (and assuming b43 is the name of it), do 

```
sudo rmmod b43
```

to unload the module, and then

```
sudo modprobe b43
```

to reload it.

---

### Post by quixote on 2010-07-08
Well, I'm not that good with wireless or networking, but sooner or later somebody who actually knows the answer will jump in. :D  Meanwhile, some more guesses.  Wifi radar, (which I wasn't familiar with so I looked up), sounds like another network manager applet.  Having two network managers running at once often results in clashes of various kinds.  Gnome's network manager generally works well and doesn't conflict with other parts of gnome, so unless there's a reason you'd like to use wifi radar, I'd try uninstalling it, and probably reinstall network-manager-gnome.  Even if the system says nm-gnome is okay, it might have some misconfigurations from conflicts with wifi radar.  (Again, I'm totally guessing on all of this.)

There's umpteen steps network gurus go through to troubleshoot connections.  I remember a couple:  Open a terminal (Applications > Accessories > Terminal) and type "iwconfig" (without quotes).  That'll list all your wireless connections.  You could copy and paste the output here if it looks wrong to you.

Also in a terminal, you can trying pinging your router by internal IP. That's usually 192.168.0.1, but your number might be different.  The command "ping 192.168.0.1" should return line after line telling you how many milliseconds it took a signal to come back, until you hit ctrl-c to stop it.  If it comes back, then you know the problem is somewhere in the wireless configuration.  If it doesn't come back, then the problem is deeper, although it could be something very simple like a loose cable.

You can also ping a server, for instance "ping www.google.com".  If that comes back, then you're not having name resolution issues either.  

As for direct wireless configuration, this is the link I've always used: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)  That and the original thread linked at the bottom.  It's about wireless security, but it goes into configuration in huge detail.

Anyway, you get the picture.  It kind of hairy.  Hopefully it'll just start working without any real troubleshooting!

---

### Post by mwilkinson on 2010-07-10
okay garf, using your suggestions, I saw I have the b43 broadcom driver, so I tried the uninstall and reinstall, restarted the computer & got the same results. (damn, I was hoping for a simple solution!) Thanks for the suggestion just the same (now I guess it gets more tricky.. I may need to try & get my brain to remember back to all those BASIC commands I learned for my apple ][c in the 4th grade..) ;)

---

### Post by mwilkinson on 2010-07-10
Quixote, <<snip>>There's umpteen steps network gurus go through to troubleshoot  connections.  I remember a couple:  Open a terminal (Applications >  Accessories > Terminal) and type "iwconfig" (without quotes).   That'll list all your wireless connections.  You could copy and paste  the output here if it looks wrong to you.
Ok, Here is what I got back..

michael@michael-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

So it looks to me like its off, or there is no extensions. (I don't know what that means)
So I tried the ping, and got it to come back as you described, with the line after line of code. (good news?) the google ping worked as well, so it now seems less hopeless to me! thanks so much, I'm gonna now check out the post you suggested and see if I can get anything going from that.

---

### Post by mwilkinson on 2010-07-10
okay, looked at the thread, but I couldent tell where the security stuff ended and the connection tips began :(  I hope I'm close on this, as I need my wireless back up and running by next Tuesday!)

---

### Post by mwilkinson on 2010-07-10
found this thru looking around more on the forum
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)
I dont know if installing (or reinstalling) all this would help or not; Im willing to try
but I dont understand how to do the stuff beond the first few steps.. I apologize for being pesky about this, but no wireless on this machine is a dealbreaker for me, and I really enjoy Ubuntu and its philosophy so far..

---

### Post by mwilkinson on 2010-07-10
tried to reinstall fwcutter using terminal, thinking maybe I had forgotten to do this, and got this for a reply:
michael@michael-laptop:~$ apt-get install b43-fwcutter
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

does this mean anything to my current situ?

---

### Post by rogerdg on 2010-07-10
Use this: 

                   sudo apt-get install b43-fwcutter

and see what happens!  Your last post indicates that you were trying to run the command as a "normal" user but you need "super user" or "root" permissions to run the command.  This should resolve the issue with reinstalling fwcutter.

---

### Post by mwilkinson on 2010-07-10
Okay Rogerdg, tried that and got this back:

b43-fwcutter is already the newest version.

so, I guess I'm okay there..

---

### Post by quixote on 2010-07-10
mwilkinson, you're not being the least pesky!  Not having wireless is super-annoying. When I first started with Linux (this was using RedHat) it took me *months* to get wireless working, and then I didn't dare touch a single setting on my system for a couple of years just in case wireless blew up. 

Just for comparison to your wlan results from iwconfig, here are mine: ```
wlan1     IEEE 802.11abgn  ESSID:"quixote"  
Mode:Managed  Frequency:2.412 GHz  Access Point: 00:99:8B:EF:D5:10   
Bit Rate=54 Mb/s   Tx-Power=15 dBm   
Retry  long limit:7   RTS thr:off   Fragment thr:off
Encryption key:off
Power Management:off
Link Quality=57/70  Signal level=-53 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Yours is saying ```
wlan0 IEEE 802.11bg ESSID:off/any
Mode:Managed **Access Point: Not-Associated** 
Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
```
To me that looks like the driver is working.  Otherwise it would say "wlan0:      no wireless extensions" and nothing else, I think.  That it reports ESSID as "off" and no Access Point suggests the wireless setup is somehow not getting through.  

You could try a manual setup, but that will only help for a specific router.  It would lose the ability to search for and talk to any other network which, if you're due to be traveling Tuesday, won't do you any good.

... Well, this is a whole lot later as I tried to remember how you do this stuff.  Lots of things have changed in Lucid, so what I did in the Good Old Dapper Days may be useless. (That's how long ago it was.)  

Your router, under the wireless administration, can tell you what your access point (aka MAC address) is for this purpose, as well as what channel it expects to use, and the expected ESSID.  "iwlist scan" command should do that too, but sometimes it returns errors about scanning not being supported.  

If you wanted to just test the settings out you can enter an interminable command.  Check "man iwconfig" for the full list. Substitute your specific data where I have italics and turn off security by using "key open" just to remove one more variable during testing.```
sudo iwconfig *wlan0* essid *mywireless* channel *1* ap *50:00:67:DE:19:6D* key open 
```and see if that gets you anywhere.  If it works, I seem to remember you're then connected without further commands, but I could be wrong.

I'm very pessimistic about that working, so I'll stop right there.  There'd be no point adding those parameters to /etc/network/interfaces if you wanted a normally functioning wireless.  It would only connect you to one router and that without security.

---

### Post by mwilkinson on 2010-07-11
Okay Quixote, thanks for your diligence on this. hopefully a Grand Wizard of wifi will look a this post and know what to do next. it seems like it is so close to connecting; like its just one little hiccup away..(but how many times has that been said about issues like this?)

---

### Post by linuxopjemac on 2010-07-12
Just to make sure we are talking about the right card. Give me the output of:
```
lspci -vnn | grep 14e4
```

---

### Post by mwilkinson on 2010-07-12
here it is...

michael@michael-laptop:~$ lspci -vnn | grep 14e4
0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by mwilkinson on 2010-07-12
Okay, now it gets weird.. I unplugged my ethernet cable and went outside on the porch with my computer. on my porch, my computer picks up my wireless network and my neighbors as well. So, I pull up network manager, and try to log on to my neighbors wifi signal. AND IT LOGGED ON.. So, It seems like its not my computer, but my wifi network here in the house. my network, however, is easily picked up by my wife's computer, my Wii, my Son's ps3, etc. just not by my iBook! Any thoughts?

---

### Post by mwilkinson on 2010-07-12
actually, to clarify, network manager says it logs on to my network as well, but it won't pull up any pages on the internets. it just gives me the standard "can't connect to the internets" page. on my neighbors network, however, I was fully able to surf the information superhighway..

---

### Post by yaaarrrgg on 2010-07-13
Do you have any security settings in the wireless router?   Like locking it down by mac address, or WPA?  If so, you might try turning off all security and cranking it up slowly to see where it breaks at.  It's sounding more like a router issue than a driver issue.

I'm assuming the router support the same standards as the card (like b/g)?

---

### Post by linuxopjemac on 2010-07-13
> here it is...

michael@michael-laptop:~$ lspci -vnn | grep 14e4
0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

This confirms the support for it by b43:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

As you already found out with the network of your neighbour :)

---

### Post by svtguy88 on 2010-07-13
I'm a bit confused.  So you CAN connect to your network now, and you just can't get web sites to load?  Or can you only connect to your/neighbor's network outside?

Can you see any other computers on either network while connected?  Go to Places - Network on the menu bar at the top of the screen and see if you can see other clients (like your wife or neighbor's comptuers).  

I agree that it's starting to sound like more of a config problem now than the driver.

---

### Post by mwilkinson on 2010-07-13
When I am at home, trying to get on my own wifi network, if I hover over the network manager wifi icon in the panel, it says "wireless conection 'name' active: name (92%). but if I then try to go online, it gives me the "firefox cannot connect" page load error page. Im at my office now, and it had no trouble finding and connecting to the wifi here, and pages loaded right up, just like it does when I crib my neighbors signal. so network manager is telling me that it can see my home network, & its a strong signal, but it just cant make the connection to it. but other networks seem to work just fine...

---

### Post by mwilkinson on 2010-07-13
> **yaaarrrgg said:**
> Do you have any security settings in the wireless router?   Like locking it down by mac address, or WPA?  If so, you might try turning off all security and cranking it up slowly to see where it breaks at.  It's sounding more like a router issue than a driver issue.

I'm assuming the router support the same standards as the card (like b/g)?

I dont have any security settings at all on my router. it is fully open. and it did work on this computer with the Lucid OS 2 weeks ago, and I havent made any changes (at least knowingly).. it just stopped.

---

### Post by svtguy88 on 2010-07-13
Hmm...well, the fact that it's working elsewhere means the driver is good for sure.  Now it's a matter of configuring...but I'm afraid I don't know what to configure.  I'm doing a Debian install on my Powerbook right now, and I'll see what I can figure out.

You don't have any security on your network at all?  No WEP/WPA/WPA2...fully open?  

Can you see other clients on your network when you are connected to it?

---

### Post by linuxopjemac on 2010-07-13
Maybe it has to do with protocols. The router may only send in a protocol your card can't do, like n or g or b, if you understand what I mean.

---

### Post by svtguy88 on 2010-07-13
According to the iBook wiki, all iBook G4s came with Airport Extreme cards, which all support A/B/G.  

You could also try connecting to your network, and then log into the router from another computer (192.168.x.x -- if you have a Windows computer go to the command prompt and run "ipconfig" and check the Default Gateway...that's the IP address of your router).  Then page through the settings until you find a Clients table.  I think most routers have it.  Check to see if one of the IP addresses in the table is your iBook.  In other words, check to see if you have an IP address on your iBook.  The router client table is one way, otherwise post the output of 
```
iwconfig
```

If you have an IP address, it's probably something silly in the router that the iBook doesn't support.  What kind of router is it?  Model?  Age?  

Everything I've read says that b43 (or b43legacy if you have the older Broadcom Airport card, which you don't) should get wireless up and running on just about all of the Airport cards (with the exception of the newer cards outlined [here]("http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy")).

---

### Post by yaaarrrgg on 2010-07-13
> **mwilkinson said:**
> I dont have any security settings at all on my router. it is fully open. and it did work on this computer with the Lucid OS 2 weeks ago, and I havent made any changes (at least knowingly).. it just stopped.

To me, it sounds like the router is becoming flakey (might be starting to fail) or a configuration issue on the machine.  The good news is the driver works, and that's usually were people get stuck. :)  

I would try rebooting all routers if you haven't already.  Power them down for 30 seconds.  That fixes most my issues like this for me.  I have a wireless router now that refuses to let my XP laptop connect at all.  Occasionally it will lock out a linux laptop.  One of my routers went bad completely (I suppose too many storms zapped it).

Also I use the default gnome nm-applet.  Hadn't tried wifi radar.  I wonder if you turn off that app (from startup), reboot, and use the default wireless manager if that would make a difference.  Maybe wifi radar has a bug?  I would think anything out of the default configuration could be a culprit.  Or it could be conflicting with something else installed on the machine.

If you go to System -> Administration you should find a log viewer.  Do you see anything in the logs (like dmesg, message, kernel) that looks like it could be related to wireless?

---

### Post by mwilkinson on 2010-07-15
> **pkmgarf said:**
> Hmm...well, the fact that it's working elsewhere means the driver is good for sure.  Now it's a matter of configuring...but I'm afraid I don't know what to configure.  I'm doing a Debian install on my Powerbook right now, and I'll see what I can figure out.

You don't have any security on your network at all?  No WEP/WPA/WPA2...fully open?  

Can you see other clients on your network when you are connected to it?

thanks for the input PK. as far as I know, there is no security. I just plugged it in when I got it and there it has stayed. there is no password or anything like that to access it, and if you came over to my house (btw, your welcome to drop by, its going to be a balmy 115 degrees here in Phoenix today:twisted:) with your laptop, you could just go right online.

---

### Post by mwilkinson on 2010-07-15
PK, I dont know how to find a clients table, but I did get the default gateway on my router using my wife's PC, it is 192.168.0.1 here is the output of iwconfig on my computer: (my router is named "default")

michael@michael-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:49:AD:2A   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by svtguy88 on 2010-07-15
Looks like the router isn't assigning you an IP.  I think the computer is setup correctly, and the router is not.  How old is it?  I've had routers randomly start failing after a few years...

Try resetting the router if you have not already (either the reset button on the back, or unplug it for 10 minutes).

---

### Post by mwilkinson on 2010-07-15
> **yaaarrrgg said:**
> To me, it sounds like the router is becoming flakey (might be starting to fail) or a configuration issue on the machine.  The good news is the driver works, and that's usually were people get stuck. :)  

I would try rebooting all routers if you haven't already.  Power them down for 30 seconds.  That fixes most my issues like this for me.  I have a wireless router now that refuses to let my XP laptop connect at all.  Occasionally it will lock out a linux laptop.  One of my routers went bad completely (I suppose too many storms zapped it).

Also I use the default gnome nm-applet.  Hadn't tried wifi radar.  I wonder if you turn off that app (from startup), reboot, and use the default wireless manager if that would make a difference.  Maybe wifi radar has a bug?  I would think anything out of the default configuration could be a culprit.  Or it could be conflicting with something else installed on the machine.

If you go to System -> Administration you should find a log viewer.  Do you see anything in the logs (like dmesg, message, kernel) that looks like it could be related to wireless?
Tried the reboot, with no changes.

 I uninstalled wifi radar a while back, and I am only using network manager now.

looked at log viewer, but didn't see anything that caught my attention. (but I don't really know what I am looking for!)

---

### Post by svtguy88 on 2010-07-15
You could try assigning the laptop an IP address manually on the router.  But it really sounds like a router going bad.  How old is it and what kind?

---

### Post by mwilkinson on 2010-07-16
I got the router used, AT  :mrgreen:GOODWILL:mrgreen: about 2 years ago. it's vexing to me because it worked on this computer, with this OS, 2 weeks ago, but not anymore.... maybe my $3 thriftshop find is petering out... but everything else wireless in my house can connect to it okay...

---

### Post by mwilkinson on 2010-07-16
Oh, sorry, its a D-Link..

---

