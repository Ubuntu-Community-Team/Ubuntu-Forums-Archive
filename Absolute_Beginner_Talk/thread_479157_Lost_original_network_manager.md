---
title: "Lost original network manager"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2007-06-20
This is kind of embarrassing. I have lost the oringal network manager notifier. The one that was up in the upper right corner, on the panel. I meant to move it, but osmehow I slipped on the touchpad and removed it from the panel, and now I can't get it back.

I want it back, I need it there. Help, please?

:oops:

/Mimsy

---

### Post by cookies on 2007-06-20
Right Click the panel, Add To Panel, Network Manager.

---

### Post by Mimsy on 2007-06-20
I did that, but that Network Manager is different. It doesn't have the bar that shows signal strength, for example, and when I right-click on it to move it to where I want it on the panel, I only get a list of connections, and that's it.

Or do I just need to reconfigure it a bit?

---

### Post by EagleRock on 2007-06-20
I see what you're saying.  The applet it comes with loaded by default is "NetworkManager", while the "Add to Panel" one is "Network Monitor".

NetworkManager is a different animal.  Do this:

System > Preferences > Sessions

Under Startup Programs, check for Network Manager.  If it's there, make sure it's checked off.  If it's not there, you may need to re-add the entry:

1) Click New
2) Make name "Network Manager"
3) Make command "nm-applet --sm-disable"
4) Click OK
5) Hit Ctrl + Alt + Bksp to restart GNOME

Let me know how it goes.

---

### Post by RomeReactor on 2007-06-20
Hi. **Mimsy**, most likely what you lost was the Notification Area. Right-click on an empty space on the top panel, select "Add to Panel..." and choose "Notification Area"; if it still doesn't show up, press **ALT+F2** and enter **nm-applet**. Should show up then.

---

### Post by Mimsy on 2007-06-21
I think I have the notification area already,it was one of the first things I added... it shows my Pidgin icon, the big red Opera O, and my battery meter, among other things.  

And now I have two network managers! I attached a part of a screenshot, just to show them off. :)

/Mimsy

---

### Post by RomeReactor on 2007-06-21
> **Mimsy said:**
> I think I have the notification area already,it was one of the first things I added... it shows my Pidgin icon, the big red Opera O, and my battery meter, among other things.  

And now I have two network managers! I attached a part of a screenshot, just to show them off. :)

/Mimsy

**Mimsy**, that may have happened if you called the Network Manager applet (nm-applet) from the terminal (as I suggested). Sometimes (rarely, though) the Network Manager applet disappears when performing some tasks that affect the panels. Just reboot; you should get just one Network Manager applet.

---

### Post by Mimsy on 2007-06-21
That worked, nowI only have one Network Manager again. It still looks like the wrong one though... weird.

---

### Post by EagleRock on 2007-06-21
When you say the "wrong one," you mean the network monitor in the "add to panel" list?

Did you try what I said above?  I tried deleting my networkmanager icon and was able to restore it with those steps.

---

### Post by Mimsy on 2007-06-21
> **EagleRock said:**
> When you say the "wrong one," you mean the network monitor in the "add to panel" list?

Yes. Sorry if I am being unclear. The steps you posted above are what led to the duplicate managers in the notification area.

I guess what i want is to be able to remove the network monitor in the "add to panel" list and use the one that was installed when I first installed Feisty. The original one brings up a menu when I right-click on it with, among other things, Preferences, that lets me go into Network Preferences when needed. If I right-click on the one that I find in "add to panel" it only lets me choose between enabling and disabling wired networking. It doesn't give me the option to disable wireless networking though, although I clearly have that function on my laptop.

/Mimsy

---

### Post by RomeReactor on 2007-06-22
**Mimsy**, I think we've got a little misunderstanding here; the Network Manager applet (that comes with the default setup, see second attached screenshot) is the one showing up twice in the picture you posted. The one you can add to the panels has a green bar on the right which shows the signal strength (see first attached screenshot).

---

### Post by Mimsy on 2007-06-22
Maybe my "add to panel" menu only would add half the icon then...? :???: I have tried that one several times, and I get the icon without the bar.

Later:
No, this time I didnt. How very odd. :???: Ah well. Textbook example of confusion, anyone...?:D:D

Thank you for patiently offering help anyway, both of you. Much appreciated.

---

### Post by musky on 2007-07-22
I can't find the original. :confused:  Shows to be installed. Help pls feisty..
Spent way to much time on this ..:redface:..over 2 hrs..
Tried out add to panel..don't see it there :(
EDIT - Ok, think I figured it out from lookin at the applet screenshot on top here.
Thought it was supposed to look like this? (scroll down a bit)
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
This is the one that seems to be in my add remove thingy..Do I have it? Or how to check?
How does one set up e-mail notification?..EDIT -think I figured it out..

---

### Post by RomeReactor on 2007-07-22
Hi. It looks like this first attachment when it's set to roam; if you set it to static ip it looks like the second attachment.

---

### Post by musky on 2007-07-22
Ahh..thx. Don wanna mess with the wifi right now cuz its workin :) but just to be sure, u can't use roam I think if usin wep?

I'm usin auto dhcp & get the pix on the right.:confused:

---

### Post by musky on 2007-07-23
:confused: aahh double.. -delete//

---

### Post by RomeReactor on 2007-07-23
Don't worry if you get the image on the right; that means you either disabled roaming or you manually configured your connection, as far as I know. I also get that, and my connection works perfectly.

---

### Post by musky on 2007-07-23
> **RomeReactor said:**
> Don't worry if you get the image on the right; that means you either disabled roaming or you manually configured your connection, as far as I know. I also get that, and my connection works perfectly.

Ok thx. Afaik, ya can't use roam (& mine's off) with closed wep, which I use. I think i'm usin the manual config. 

At any rate, still sortin out a solid wifi & not to pursue it in this thread but what wifi card (I'm assuming) you have ona desktop and or ya know one that's plug & play in feisty?

---

### Post by RomeReactor on 2007-07-23
My card is a Global Sun Technology wireless with a Marvell W8300 chipset; only way to get it to work was to use NdisWrapper and the XP driver in the included CD. Very easy to set up once you know how to use NdisWrapper, but not recommended as it has no native support yet (I remember Dapper including a Marvell driver, but did not work).

[This]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") is a list of cards and their corresponding installation instructions. [The Free Software Foundation]("https://www.fsf.org/resources/hw/net/wireless/cards.html") recommends the Ralink 2500/RT2400 and the Realtek RTL8180 chpisets.

---

