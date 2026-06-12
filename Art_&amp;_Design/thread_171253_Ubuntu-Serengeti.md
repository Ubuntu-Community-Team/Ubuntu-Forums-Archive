---
title: "Ubuntu-Serengeti"
date: 2006-05-06
forum: Art &amp; Design
---

### Post by j_baer on 2006-05-06
Competing colors can be an issue on the desktop and there have been some complaints  about the new Ubuntu Human theme in this regard. Ubuntu-Serengeti is my attempt to bring the colors of the background and icons into harmony without losing the  excitement.

How-to install

1. Download the attached files.

2. Open System>Preferences>Themes

3. Choose the Human Theme

4. Click the Theme Details Button

5. Drag & drop the Ubuntu-Serengeti bz2 file into the control window. You should get a message of successful installation.

6. Scroll down and select Ubuntu-Serengeti as your control, save, and exit.

The above method will install this theme into the ~/.themes folder. This is probably the best method to evaluate it. If you desire to use it system wide the attached inst-serengeti.doc (rename from doc to sh to run) script will install it into the /usr/share/themes folder and present a mini howto (inst-docs.txt) on modifying the gdm.conf file.

BTW, I attempted to document the gtkrc file as best as I could for others who would like to travel this path and I have tested with a variety of backgrounds.

Enjoy ...

---

### Post by kpolice on 2006-05-07
Thanks, I was lookinf for something like this.

BTW What font are you using in your screesnshots??

---

### Post by commodore on 2006-05-07
OFFTOPIC: .doc ?!?

---

### Post by Rotarychainsaw on 2006-05-11
Hey this is cool. Are you going to still tweak this, or are you done? I have no experience really with this kind of stuff, but I started editing the gtkrc. 
I made the menus use the burnt orange instead of grey, and changed that dark blue to something a little lighter. Those 2 changes look nice I think.

---

### Post by Rotarychainsaw on 2006-05-12
also, stuff run as root has ugly gtk1 looking theme. Anyway to fix?

---

### Post by jstueve on 2006-05-15
heads up, running this theme will cause azureus to crash.  I have no idea why.

---

### Post by Omnios on 2006-05-15
[QUOTE=Rotarychainsaw]also, stuff run as root has ugly gtk1 looking theme. Anyway to fix?[/QUOTE]

 In Breezy simply copy your theme files from Home/Your_name/.themes to /usr/share/themes. Basicly this makes the theme available for root.

---

### Post by Rotarychainsaw on 2006-05-15
Azureus works for me. 
Ominos, thanks.

---

### Post by funkenstein on 2006-05-23
we likes eet.

eez dark like everything else around here....


*switches on the light* 

oww oww oww !! the light, it hurts my eyes!! :cry:

for a minute I thought of making a cross between the two - have a dark version of the dapper human theme... and then I realised that'd be brown, like the old human theme.... :rolleyes: 

ack vell, dark eet eez.

ta.

---

### Post by j_baer on 2006-05-25
[QUOTE=Rotarychainsaw]Hey this is cool. Are you going to still tweak this, or are you done? I have no experience really with this kind of stuff, but I started editing the gtkrc. 
I made the menus use the burnt orange instead of grey, and changed that dark blue to something a little lighter. Those 2 changes look nice I think.[/QUOTE]

I think I'm pretty much done with it. I may tweek it for the final release but feel free to modify as you like.

One of my goals was to comment the gtk file in a way that would easy the path for others ...

Cheers

---

