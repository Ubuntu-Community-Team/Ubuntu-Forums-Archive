---
title: "Custom settings in ubuntu"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by ochana25 on 2008-01-27
hey everyone im tryin to put in the command so i can get the custom visual effects in the appearance option so i can add in the cube and this was the code i used before and it worked, now its not workin help.

sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins

---

### Post by emarkd on 2008-01-27
What error do you get?

---

### Post by ochana25 on 2008-01-28
im not gettin nuttin im puttin in the command and pressing run and nuttin is happening

---

### Post by Zars on 2008-01-28
Hey there :)

Just some quick questions :D

**What version are you using?**
Gutsy comes with Compiz-Fusion preinstalled so all you need to do is install compizconfig-settings-manager. I would suggest installing this via Synaptic. Just go to System > Administration > Synaptic Package Manager, scroll down to compizconfig-settings-manager, right click and select install. You may be prompted to install other packages (eg Python related ones).

Then, in System > Preferences you will have Advanced Desktop Effects Settings. You can enable the cube in there.

**If not, is Compiz-Fusion installed?**
If not, I would recommend you install it before looking for manager, although many tutorials will include installing the manager.

Let me know if you need any more help.
Zars

PS Dont forget to enable the desktop effect in the System > Preferences > Appearence windows, under the Visual Effect tab :)

---

### Post by ochana25 on 2008-01-28
in visual effect all i get is the extra i dont have the custom and  i dont have the advanced desktop effect setting and im runnin ubuntu 7.10. thanks

---

### Post by Zars on 2008-01-28
Try this:

> Gutsy comes with Compiz-Fusion preinstalled so all you need to do is install compizconfig-settings-manager. I would suggest installing this via Synaptic. Just go to System > Administration > Synaptic Package Manager, scroll down to compizconfig-settings-manager, right click and select install. You may be prompted to install other packages (eg Python related ones).

Then, in System > Preferences you will have Advanced Desktop Effects Settings. You can enable the cube in there.

Then let me know.
Zars

---

### Post by ochana25 on 2008-01-28
got it thanku soooooooo much i appreciate all ur help.

---

### Post by ochana25 on 2008-01-28
hope u dont mind with me bugging u again lol, umm two things how do i put a wallpaper in the background of the cube i was told the skydome i loading a pic but it didnt work and one more thing i saw on the internet when the window was minized or closed the window exploded do u know how to do that

---

### Post by macogw on 2008-01-28
Skydome images have to be a power of 2 in each direction.
Powers of 2:
2
4
8
16
32
64
128
256
512
1024
2048
4096

So if it's 1024x2048, it'll work fine, but not 800x600, because 800 and 600 are not powers of two.  And 1024x800 also won't work because 800's still not a power of 2.  Both dimensions have to be a power of 2.

Exploding windows are in the animations section of ccsm (compizconfig-settings-manager)

---

### Post by Zars on 2008-01-28
The exploding windows options are in the animation bit. Click on the tab for the action you want (eg Open Animation, Minimize Animation), then click on the required window match (you're probably after the 'type=normal' ones). Click edit, then and then select the Effect you want. You can also change the Duration.

With regards to the background image, I found that it would only work with some pictures. For example, [http://evolution.vault.googlepages.com/starcraft-2-wallpaper.jpg]("http://evolution.vault.googlepages.com/starcraft-2-wallpaper.jpg") worked, but some of my personal pictures did not. It is in the Appearances tab of the Desktop Cube, at the bottom. Make sure you tick the box inline with 'Skydome'. Then browse for a picture in the form underneith.

Now, I know I haven't explained it very well. If you cant find the menus and tabs, I'll print screen them for you.

Let me know if you need anymore help. Im more than happy to do so! :D
Zars

---

### Post by ochana25 on 2008-01-28
would i be able to get ur msn or something cuz im having some more problems with ubuntu  like i restarted and all the effects i did arent workin and my screen is like zoome in and im tryin to fix my effects and there not workin now

---

### Post by ochana25 on 2008-01-28
when i go to appearance option then visual effects it stays at none when i click on custom it starts to apply then says desktop effects could not be enabled

---

### Post by Zars on 2008-01-29
If you screen is zoomed in, you may need to change the resolution. Be sure to back up your xorg.conf file first by doing 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup' in the terminal. I find its easiest to change your screen to a generic screen of your resolution (in the Screens and Graphics option).

Once the sceen has returned to normal, then try to enable the effects.

---

### Post by ochana25 on 2008-01-29
ok i restarted now everything is workin except one problem now my screen resolution is only letting me go 640X480 and my windows are huge and i cant go bigger

---

### Post by Zars on 2008-01-30
I think you need to change your screen settings. Go to System > Administraton > Screens and Graphics. Here you can change your screen settings. Click on the model settings (your's may be on Plug 'n' Play?) and I find the easiest way is to select Generic in the left columb and then the right size in the right options. This should then allow you to select up to your resolution.

Zars

---

### Post by ochana25 on 2008-01-30
got it workin thanks again that pic u sent me for the skydome wallpaper loved it but opened  it in the option but its not workin

---

### Post by ochana25 on 2008-01-30
k i got it work lol thanks, how do i keep in touch if i need ur help

---

### Post by oedha on 2008-01-30
have you try autumn, snow, 3d and atlantis.....they are cool effect

question : can someone tell me how to make 4 desktops with 4 pictures ?


~E~

---

### Post by ochana25 on 2008-01-30
how do u do those effects

---

### Post by ochana25 on 2008-01-30
[LISu can do 4 desktops with 4 pictures lol how

---

### Post by oedha on 2008-01-30
follow this : [http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)
you will have autum, snow, atlantis, 3d , etc

there is a way to make 4 desktops have different picture......but i didnt find the way for ubuntu yet........

regards;
~E~

---

### Post by oedha on 2008-01-30
it says for gnome : [http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

but i am not confidence in working with source packages....
~E~

---

