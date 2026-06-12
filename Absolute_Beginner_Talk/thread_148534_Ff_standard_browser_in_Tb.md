---
title: "Ff standard browser in Tb"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by FISHERMAN on 2006-03-22
Iuse Firefox and Thunderbird as my standrad browser-/mail-client application.
But when I click on a link in Thunderbord it opens in Galeon.
How can I change this to make it open in Firefox.

---

### Post by Super King on 2006-03-22
Try setting FF as your actual default by going to System->Preferences->Preferred Applications and choosing Firefox from the drop-down menu.

---

### Post by FISHERMAN on 2006-03-22
[QUOTE=Super King]Try setting FF as your actual default by going to System->Preferences->Preferred Applications and choosing Firefox from the drop-down menu.[/QUOTE]
I probably should have mentioned this in my first post.
But Ff is already set as my preferred application for webbrowsing in Ubuntu(like you suggested). But still Tb uses Galeon.:confused: :confused: :confused:

---

### Post by Super King on 2006-03-22
Oh, that's strange. I switched my preferred browser app from FF to Ephiphany and it TB correctly opened links in the preferred browser. Might be an issue with Galeon (I don't have it installed ATM).

---

### Post by dixonstalbert on 2006-03-22
Hi Fisherman

not sure if you are still working on this...
I had a similar problem with Thunderbird wanting to use Konquerer, even though I had set Firefox as my default browser in System>Preferances and Kcontrol

I found a forum thread on the command "update-alternatives --list x-www-browser" and sure enough Konquerer was listed as my default, despite what the GUI settings were saying.

I followed the instructions in that thread and ran 
```
sudo update-alternatives --config x-www-browser 
```
and selected firefox

Unfortunately I got an error message about missing /opt/mozilla-firefox.

I tried figuring out x-www-browser script but I dont speak C++ 

I ended up bypassing x-www-browser by going into Thunderbird > Edit > Preferences > Config Editor , scrolling down hundreds of entries to **network.protocol-handler.app.http** and modifying string (r. click over entry and choose Modify) from x-www-browser to firefox.

Now Thunderbird links open in firefox

I hope to eventually figure out x-www-browser but it may take a while to learn C++ !

---

### Post by TuxCrafter on 2006-10-10
```
sudo update-alternatives --config x-www-browser
```

Thanks, this workt for me on xubuntu \\:D/

---

