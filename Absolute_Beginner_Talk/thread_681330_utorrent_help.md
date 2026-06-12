---
title: "utorrent help"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Jake90 on 2008-01-28
Hi, I'm relatively new to linux so nothing advanced please. I installed deluge as my torrent client, but it was slow and stopped working so I decided to run utorrent with wine. Everyhting is working fine and it is very fast. My problem is that when I try to download a torrent I get this message. "*****.torrent could not be opened because your associated helper application does not exist. Change the association in your preferences." I clicked ok and downloaded it to my desktop and it came up as a .xml file. I changed it to a .torrent file and then when to utorrent and clicked add file and selected it. It is downloading fast it is not finished so I can't tell you if it's working. Is there a way to do this automatically so I don't have to do it manually every time I want to download a torrent? Thanks in advance
If any information is needed tell me and I'll post it as soon as possible

---

### Post by amaroKer on 2008-01-28
Doesn't sound like anything to do with uTorrent.  Just save the torrent (not 'Open...') to the desktop or wherever.  It should save with the extension it has on the server you got it from.  Open the file from within the torrent program.

On a second note, using Wine seems like an awfully arduous route to use to merely download a torrent.  I use Transmission available from the repositories (0.93 in gutsy-backports), and it seems to work quite well.  All I had to do was tell it what port to run on.

Good luck

---

### Post by Jake90 on 2008-01-28
> **amaroKer said:**
> Doesn't sound like anything to do with uTorrent.  Just save the torrent (not 'Open...') to the desktop or wherever.  It should save with the extension it has on the server you got it from.  Open the file from within the torrent program.

On a second note, using Wine seems like an awfully arduous route to use to merely download a torrent.  I use Transmission available from the repositories (0.93 in gutsy-backports), and it seems to work quite well.  All I had to do was tell it what port to run on.

Good luck
Thanks but I don't have an option to save I think I selected do this by all downloads or something so it always opens. I tried transmission and deluge and both of them are considerably slower. I think it is because I don't know how to set everything up correctly but I googled for it and it is so complicated I just switched to utorrent which is very easy to set up and use except for this problem.

---

### Post by RomeReactor on 2008-01-28
Hi. Try right-clicking on a **.torrent** file and go to 'Properties'; there, go to the 'Open With' tab and make sure Deluge is not the default program.

EDIT: The problem  seems to be a file association in Firefox; go to 'Edit->Preferences->Content' and press the "Manage" button in File Types. Find TORRENT there, press the 'Change Action' button and select the 'Save them to my computer' radio button, or 'Open them with this application:'.

---

### Post by Jake90 on 2008-01-28
> **RomeReactor said:**
> Hi. Try right-clicking on a **.torrent** file and go to 'Properties'; there, go to the 'Open With' tab and make sure Deluge is not the default program.

EDIT: The problem  seems to be a file association in Firefox; go to 'Edit->Preferences->Content' and press the "Manage" button in File Types. Find TORRENT there, press the 'Change Action' button and select the 'Save them to my computer' radio button, or 'Open them with this application:'.
Thanks it gets saved to disk the default was set to windows wine emulator and I still have to do everything manually. This is a lot of trouble for a torrent program. Does anyone have a suggestion on which program I should switch to. I need three things, I don't need any fancy plugins. I need it to be fast, be able to do more than one torrent at once and preferably be light. Thanks in advance

---

### Post by Amstell on 2008-01-28
I didn't like utorrent.  had to many problems.  I have used deluge for a while now, love it.

---

### Post by RomeReactor on 2008-01-28
> **Jake90 said:**
> Does anyone have a suggestion on which program I should switch to. I need three things, I don't need any fancy plugins. I need it to be fast, be able to do more than one torrent at once and preferably be light. Thanks in advance

As amaroKer suggested, try [Transmission]("http://www.transmissionbt.com/"); you can find in Add/Remove or Synaptic; or to install it from the terminal:
```
sudo aptitude install transmission transmission-gtk
```
Have you tried the default BitTorrent client? Or, if you're not afraid of the terminal--or if you're comfortable using it--try [running the default client from the command line]("http://ubuntuforums.org/showpost.php?p=4203019&postcount=27").

---

### Post by Amstell on 2008-01-28
Deluge is crazy.  I get like 1.2mb/s sometimes with it.  I am on cable and pay $30 a month.  TOtally worth it.

---

### Post by Jake90 on 2008-01-28
> **Amstell said:**
> Deluge is crazy.  I get like 1.2mb/s sometimes with it.  I am on cable and pay $30 a month.  TOtally worth it.

I had deluge but it was very slow, It may be because I didn't know how to set it, what ports etc.

---

### Post by Amstell on 2008-01-28
I installed it just like it is.  Its one of the best ones i've used.  I get faster connection off of that than any of my friends do on windows, mac, or linux.

---

### Post by Jake90 on 2008-01-28
> **RomeReactor said:**
> As amaroKer suggested, try [Transmission]("http://www.transmissionbt.com/"); you can find in Add/Remove or Synaptic; or to install it from the terminal:
```
sudo aptitude install Transmission transmission-gtk
```
Have you tried the default BitTorrent client? Or, if you're not afraid of the terminal--or if you're comfortable using it--try [running the default client from the command line]("http://ubuntuforums.org/showpost.php?p=4203019&postcount=27").
Ok I'll try it do I need to set up the ports and everything or is it set automatically. Also how do I uninstall utorrent?
bittorrent can only do one torrent at a time but thanks

---

### Post by RomeReactor on 2008-01-29
To uninstall uTorrent go to your **.wine** folder (it's hidden in your home directory, so press CTRL+H to show the hidden files and folders), and delete it there, or leave it if you wish--it shouldn't make any difference once you set the **.torrent** files to open with another application.

I haven't used Transmission, so I won't be able to help you with the port setup there.

**NOTE**: Deluge might be slow if the ports are not open in your firewall (if you're running one), your modem/router.This also applies to the default BitTorrent client, but there's an extra step: In Gconf there was bug where only one port is set to be used--6881. I don't know if this has been fixed, but to make sure the port range is correct, open a terminal (Applications->Accessories->Terminal), write or paste:
```
gconf-editor
```
and press ENTER. Once it shows up, go to "apps->gnome-btdownload->settings", double-click on **max_port**, and write **6889**. Close Gconf, right-click on a .torrent file, and select "Open with->BitTorrent". See if it downloads faster.

EDIT: Also note that in the command I gave you:
```
sudo aptitude install Transmission transmission-gtk
```
There's an upper case letter T; it should be all lower case letters, so the correct command is:
```
sudo aptitude install transmission transmission-gtk
```

---

### Post by Jake90 on 2008-01-29
All right I got transmission up and running but it is still not as fast as utorrent or deluge. I think deluge is the best program out of the three if set up properly does anyone know of a post or tutorial on the web on how to figure out which ports I need?
(I do have a router)
Thanks

---

### Post by RomeReactor on 2008-01-29
I think Deluge by default uses the standard BitTorrent ports (6881 through 6889). Make sure the ports are open in your router. In Deluge go to 'Edit->Preferences' and then go to the 'Network' tab; there you can also change the ports if you want. Press the 'Test Active Port' button; it will open Firefox with a page telling you if the port is open or closed.

---

### Post by Jake90 on 2008-01-29
> **RomeReactor said:**
> I think Deluge by default uses the standard BitTorrent ports (6881 through 6889). Make sure the ports are open in your router. In Deluge go to 'Edit->Preferences' and then go to the 'Network' tab; there you can also change the ports if you want. Press the 'Test Active Port' button; it will open Firefox with a page telling you if the port is open or closed.
it's closed. how do I open it?

---

### Post by Crumpets and Jam on 2008-01-29
> **Jake90 said:**
> it's closed. how do I open it?

Select your router make and model from [here]("http://portforward.com/english/routers/port_forwarding/routerindex.htm") and follow a guide. I don't think that there is one for Deluge but following on for uTorrent will have the same outcome.

---

### Post by Jake90 on 2008-01-29
Deluge still won't work even though the ports are working fine. At first it would only connect to the peers not the seeds and was downloading 0.0 a sec. Now I was just downloading a couple of stuff and it won't connect to anything. Any suggestion?

---

### Post by RomeReactor on 2008-01-29
Do you have Firestarter installed? If so, make sure the ports are open there also. Did you open the ports in your router? Does the torrent file you want to download have enough peers/seeds?

---

### Post by Jake90 on 2008-01-29
> **RomeReactor said:**
> Do you have Firestarter installed? If so, make sure the ports are open there also. Did you open the ports in your router? Does the torrent file you want to download have enough peers/seeds?

I don't know what firestarter is, is it like firewall? I don't think I have it though. I folowed the guide posted by crumpets and jam and when I tested it it it said it they were open. Yeah it had like 300 seeds and like 250 peers and at first I was able to connect to about 30 peers but it didn't download anything. However it never connected to a seed not matter how many were available.

---

### Post by RomeReactor on 2008-01-29
> **Jake90 said:**
> I don't know what firestarter is, is it like firewall? I don't think I have it though. I folowed the guide posted by crumpets and jam and when I tested it it it said it they were open. Yeah it had like 300 seeds and like 250 peers and at first I was able to connect to about 30 peers but it didn't download anything. However it never connected to a seed not matter how many were available.

Firestarter is a graphical interface for a command line program called IPTables, with which you can make firewall rules. You don't need to install it, but you can do so if you wish and then open the ports there; Firestarter can be found in Synaptic or Add/Remove.

With Deluge open, [go to this page]("http://www.whatsmyip.org/ports/") and press the "Check ports" button on "P2P Port Test". See if ports from 6881 through 6889 are detected as open.

---

### Post by Jake90 on 2008-01-30
> **RomeReactor said:**
> Firestarter is a graphical interface for a command line program called IPTables, with which you can make firewall rules. You don't need to install it, but you can do so if you wish and then open the ports there; Firestarter can be found in Synaptic or Add/Remove.

With Deluge open, [go to this page]("http://www.whatsmyip.org/ports/") and press the "Check ports" button on "P2P Port Test". See if ports from 6881 through 6889 are detected as open.
All of them say "timeout" also in deluge my port is set to 49152-49152 not 6881-6889

---

### Post by RomeReactor on 2008-01-30
> **Jake90 said:**
> All of them say "timeout" also in deluge my port is set to **49152-49152** not 6881-6889

Are the **49152-49152** ports also open in your router? Try assigning **6881-6889** in both Deluge and your router, then test again.

---

