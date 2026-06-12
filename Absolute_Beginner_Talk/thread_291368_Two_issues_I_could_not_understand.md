---
title: "Two issues I could not understand"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Duwady on 2006-11-02
Hi Friends,

I am a newbie, trying to make on my own!!

I am still trying to get everything up and running, and have come a long way, but one thing I have not understood at all.

I have WG111v2 Wireless Adapter through which I connect to the internet in my Ubuntu/ WinXP dual boot.  I got the adapter to work, and it does show me the available Acess Points.  But the problem is that the connection uses WPA, not WEP.  Search on the Forum here confused me more.  Is there a place that I can go to which will guide me (in plain English...  :-D ) steps that I need to take?  

Also, just out of curiosity, how can I change the order on the GRUB menu?  I want XP on top, and default, so that other souls in my home can still work on their XP, without being overwhelmed?  Will just editing the menu.lst so that XP is on top and Ubuntu is down do the trick?

Thanks.

---

### Post by compmodder26 on 2006-11-02
Try downloading network-manager and network-manager-gnome through Synaptic.  You should see a new icon in the gnome-panel.  Click it and you should then be able to select your wireless network and use the wpa key to access it.

As for grub, you'll need to edit your /boot/grub/menu.lst file. BE SURE TO CREATE A BACKUP FIRST!!  Just move the entry for XP, ahead of Ubuntu.

---

### Post by bsussman on 2006-11-02
On grub:

Yes but the problem is that the automatic installer change it when you upgrade you os later.

instead, use the default function.  count the entries and make the line say default x

where x is the number of the xp stanza

Then the win users do nothing and they get windows, you use ESC and change it to ubuntu and everybody is happy

---

### Post by Duwady on 2006-11-02
[QUOTE=compmodder26;1704240]Try downloading network-manager and network-manager-gnome through Synaptic.  You should see a new icon in the gnome-panel.  Click it and you should then be able to select your wireless network and use the wpa key to access it.
QUOTE]

This is my only connection, so can not use Synaptic.  Any downloads will have to be done from Windows, then "installed" in Ubuntu... (I hope that makes sense...  :))

---

### Post by Duwady on 2006-11-02
> **bsussman said:**
> On grub:

Yes but the problem is that the automatic installer change it when you upgrade you os later.

instead, use the default function.  count the entries and make the line say default x

where x is the number of the xp stanza

Then the win users do nothing and they get windows, you use ESC and change it to ubuntu and everybody is happy

This makes sense.  The changes you are suggesting is on menu.lst, I assume...

---

### Post by bsussman on 2006-11-02
> **Duwady said:**
> This makes sense.  The changes you are suggesting is on menu.lst, I assume...
Yes.

do back up your menu.lst first

it is hard to make a fatal mistake with only the default line but worse has happened in the world :)

---

### Post by mahy on 2006-11-02
The kernel upgrade changes entries ONLY within the "Debian Automagic Kernel List" portion of menu.lst. Outside it you should be OK. Just place windows option BEFORE that portion. As for the network-manager-gnome, it's located on the CD, so no need to go online to install it ;)

---

### Post by mattskr on 2006-11-02
> **Duwady said:**
> This makes sense.  The changes you are suggesting is on menu.lst, I assume...

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_BAK

sudo gedit /boot/grub/menu.lst
```

Just cut and paste Windows to be above Ubuntu in the Text File.

---

### Post by Duwady on 2006-11-02
> **mahy said:**
> The kernel upgrade changes entries ONLY within the "Debian Automagic Kernel List" portion of menu.lst. Outside it you should be OK. Just place windows option BEFORE that portion. As for the network-manager-gnome, it's located on the CD, so no need to go online to install it ;)

I believe I tried to install it from CD, but it gave some "not-being-able" error, but that was yesterday night at home.  I will try it at home tonight, and will post the actual error message that I get.

I had read something about a GUI WPA Manager program, (I do not remember the name right now), which I downloaded from Windows, and tried to install, which gave me another "not-able-to" message.

SO, is there any place, threads, anything that I can read so that I can understand it more...

Thanks a bunch.  I will try the suggestions you guys have given tonight, and will be back if I still have problems.

---

### Post by mahy on 2006-11-02
The name of the gui wpa manager is network-manager-gnome. IMHO, that's the only thing you have to install and it's definitely on the CD.

---

### Post by Duwady on 2006-11-03
> **mahy said:**
> The name of the gui wpa manager is network-manager-gnome. IMHO, that's the only thing you have to install and it's definitely on the CD.

I tried installing this, but I got the following message.

"Network-Manager-Gnome' is not available in any software Channel.  The application might not support your system architecture."

And I am stumped again...  :)

Any other things that I need to do?

Thanks.

---

### Post by Duwady on 2006-11-03
> **Duwady said:**
> I tried installing this, but I got the following message.

"Network-Manager-Gnome' is not available in any software Channel.  The application might not support your system architecture."

And I am stumped again...  :)

Any other things that I need to do?

Thanks.

Please somebody help, I am literally banging my head on the wall... ](*,) :)

---

