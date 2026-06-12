---
title: "My Experiences and a Couple of Questions."
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by ~nix on 2005-06-01
I have been using linux for quite a few years now, approximately between 4 and 5 years. During that time I have used a variety of systems including Mandrake, SuSE, Fedora, Slackware, Knoppix, Arch, Lycoris as well as a large number more.

I first started using Ubuntu when the free discs offer went floating around the internet. To be honest my intentions were to install it then throw it out again, at the time i was very much attached to Slackware. I first installed it onto my older laptop which used a PCMCIA 3Com 802.11g wireless card. I didnt think for a minute that i would be able to utilise it with Warty but installed it nonetheless. To my surprise, Warty found the wireless network adapter and all that was needed was slight configuration of the ssid and wep key. Very impressive.

I am now using Hoary on both that laptop and my desktop, Ubuntu is now my primary operating system and I don't use anything else. Up until now the systems had mainly been running a completely default install with very little customisation, but the time has come for me to take a look under the hood a little and get my hands dirty i think.

Now for the questions; 
The laptop is a Celeron 677MHz with only 192MB of SDRAM, so naturally it isnt the speediest computer to use. I think I can put the majority of this down to running a default kernel. So I was wondering, is there any steps I can take to speed up the use of Ubuntu on this laptop? Is customising the kernel a relatively easy task (I have only previously done this is Slackware)? 

On the desktop (2.0GHz Sempron, 1GB RAM, 64MB Shared Gfx) I feel that some things just dont act like they should, very small lag which could do with tweaking etc. I put this down to Ubuntu just needing to mature a little and hope that the majority of these will work their way out, does anyone else feel this way?

A final question, this one regarding Fluxbox. Fluxbox is a lightweight window manager. But, when I have installed 'fluxbox' 'menu' and 'fluxconf' from synaptic, then logged out re-loggin in under the fluxbox session. It seems very "floaty". It definetly isnt as lightweight as its meant to be. For example its using the "gnome cursor" making the mouse look just as it did in Gnome. Also the menu doesnt seem as quick as it should, to me it looks like it is still running Gnome, only with a lightweight skin. Is there anyway to retrieve the old original Fluxbox to use like it should?  :-| 

Thanks in advance for any responses :)

---

### Post by mostwanted on 2005-06-01
XFCE is nice. It's eye-candy and light-weight at the same time :)

---

### Post by ~nix on 2005-06-01
[QUOTE=mostwanted]XFCE is nice. It's eye-candy and light-weight at the same time :)[/QUOTE]
 Thanks, i am aware of all of the lightweight managers. But your "recommendation" really doesnt help my problem. 

I like fluxbox and would prefer to use that over Gnome, XFCE, Ratpoison, Openbox or any other manager. ;)

---

### Post by poofyhairguy on 2005-06-01
[QUOTE=~nix]
Now for the questions; 
The laptop is a Celeron 677MHz with only 192MB of SDRAM, so naturally it isnt the speediest computer to use. I think I can put the majority of this down to running a default kernel. So I was wondering, is there any steps I can take to speed up the use of Ubuntu on this laptop? Is customising the kernel a relatively easy task (I have only previously done this is Slackware)? [/QUOTE]

Do you run the 686 kernel? Another speed increase can be gained by starting XFCE and adding Gnome stuff to it ( the panel, desktop, etc).

---

### Post by az on 2005-06-01
"Is there anyway to retrieve the old original Fluxbox to use like it should?  "

There is no gnome fluxbox.  There is only one fluxbox.  If it is sluggish, you are experiencing something particular.  Is there a process running that is consuming a lot of cpu?

You are running gdm as our display manager and that is why your cursor looks like that.  GDm does not load all of gnome.  It is quite lightweight.

---

### Post by ~nix on 2005-06-01
[QUOTE=azz]"Is there anyway to retrieve the old original Fluxbox to use like it should?  "

There is no gnome fluxbox.  There is only one fluxbox.  If it is sluggish, you are experiencing something particular.  Is there a process running that is consuming a lot of cpu?

You are running gdm as our display manager and that is why your cursor looks like that.  GDm does not load all of gnome.  It is quite lightweight.[/QUOTE]
 not only the mouse cursor but also windows borders etc. It might be the gdm or it may just be XOrg, i am unsure. However it is something i will need to look into. Thanks :)

---

