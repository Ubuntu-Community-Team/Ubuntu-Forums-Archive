---
title: "Almost there! Keyboard, Mouse, Apps and DVD problems"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Jdoki on 2007-04-11
Hello all,

I have been using Ubuntu for about a week now, and am getting close to forgetting about XP for everything except gaming!  I've even managed to get a friend to consider trying it. Unfortunately I have a few problems that are causing me issues, so I really hope someone can help me out...

1. I use Ubuntu on a laptop with no PS2 sockets. I have a PS2 keyboard which I'd like to connect when at home.  I have a PS2 to USB adapter, but when I plug it all in the keyboard does not work (Caps Lock light flashes when it is first connected, but does not toggle when the key is pressed; the F-Lock button does toggle the keyboard light  - F-Lock is a special key on this keyboard for locking the Function keys).

The Keyboard is a Microsoft Multimedia device.  I have enabled USB Legacy support in BIOS. Is there any way to get this keyboard working, or would I be better of just buying a new USB keyboard?

2. I added DVD and MP3 playback.  DVD's play great using VLC, however the default player - Totem - does not reproduced colours correctly leaving everyone looking like Smurfs - skin tones have a blue tinge among many other oddities!! :)  Any ideas why this happens, and how I can solve it?

3. It would be great to be able to activate the extra buttons on my Logitech MX518 mouse.  In particular one of the side buttons to go 'Back' in Firefox or when moving through folder trees.  I'm thinking of having a bash using this  link as a guide, but are there any easier (i.e GUI apps) to help with this?  [http://ubuntuforums.org/showthread.php?t=382962&highlight=mouse+back+in+firefox](http://ubuntuforums.org/showthread.php?t=382962&highlight=mouse+back+in+firefox)

4. How do I change the default launch programs? For example when I insert a DVD I want VLC to start up, not Totem. When I click an MP3 I'd like Amarok to fire up, etc

5. If I want to remove some apps (like Rhythm Box) using Synaptic, it mentions that Ubuntu-desktop needs to be removed... not a good idea I think!?! I like to keep a tidy hard drive and remove unwanted apps.  Can this be done?

Apologies for so many questions.  I've hunted the forums and web for answers but no luck finding straight forward solutions.

Any help would be much appreciated.

---

### Post by chewearn on 2007-04-11
> **Jdoki said:**
> 4. How do I change the default launch programs? For example when I insert a DVD I want VLC to start up, not Totem. When I click an MP3 I'd like Amarok to fire up, etc


Only able to answer this one. :)

For removable media (DVD, usb, etc), you can change it by:
Top panel menu > System > Preferences > Removable Drives and Media Preferences

For media files:
Right-click on the file in Nautilus > Properties > Open With > Add
select you favorite application, then select the radio button to set it as default.

---

### Post by mand0 on 2007-04-11
> **Jdoki said:**
> 
3. It would be great to be able to activate the extra buttons on my Logitech MX518 mouse.  In particular one of the side buttons to go 'Back' in Firefox or when moving through folder trees.  I'm thinking of having a bash using this  link as a guide, but are there any easier (i.e GUI apps) to help with this?  [http://ubuntuforums.org/showthread.php?t=382962&highlight=mouse+back+in+firefox](http://ubuntuforums.org/showthread.php?t=382962&highlight=mouse+back+in+firefox)

Take a look [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox"). I got my MX518 working perfectly. Sorry, I don't think there are any GUI applications that do this as of now.

---

### Post by 3rdalbum on 2007-04-11
4. System > Preferences > Removable Drives and Media

5. Removing ubuntu-desktop isn't so bad; removing it only removes an almost-useless 6 kilobyte file, not all the programs that were installed when you installed Ubuntu. So, if you want to remove The Gimp, it will remove The Gimp and Xsane, but no other programs.

If you want to upgrade to the next release, you should probably reinstall the ubuntu-desktop package before upgrading. Then you can get rid of it again if necessary.

---

### Post by mand0 on 2007-04-11
::edit::
Internet is being slow and I double posted by accident.

---

