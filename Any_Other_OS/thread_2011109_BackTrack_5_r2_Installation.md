---
title: "Back|Track 5 r2 Installation"
date: 2012-06-26
forum: Any Other OS
---

### Post by meathdeath on 2012-06-26
I have successfully installed back track 5 r2 gnome in virtual box. I love it and i want to install it to my hard drive, but the problem is after i choose the first option and type "startx" the screen goes black and the caps lock and num lock start flashing on my keyboard. Any ideas on how to get it going? Ive tried both the gnome and KDE versions and neither of them work. Ive even tried booting from USB and it failed.

---

### Post by haqking on 2012-06-26
> **meathdeath said:**
> I have successfully installed back track 5 r2 gnome in virtual box. I love it and i want to install it to my hard drive, but the problem is after i choose the first option and type "startx" the screen goes black and the caps lock and num lock start flashing on my keyboard. Any ideas on how to get it going? Ive tried both the gnome and KDE versions and neither of them work. Ive even tried booting from USB and it failed.


Backtrack forums are here [http://www.backtrack-linux.org/forums/forum.php?](http://www.backtrack-linux.org/forums/forum.php?)

BT wiki including HOW TO's are here [http://www.backtrack-linux.org/wiki/index.php/Main_Page](http://www.backtrack-linux.org/wiki/index.php/Main_Page)

BT is a specialised distro for security auditing and not for general desktop use, the majority of it is done from the /pentest directory and a GUI is not a priority, so its either you get it working or you dont ;-)

Peace

---

### Post by Cheesemill on 2012-06-26
What graphics card does your machine have?

On my workstation which uses onboard Intel graphics I have to boot with the i915.modeset=1 option set in Grub.

---

### Post by nothingspecial on 2012-06-26
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by haqking on 2012-06-26
Also to the OP, reiterating my point that the GUI is  not a priority for BT

here is a guide about X [http://www.backtrack-linux.org/wiki/index.php/Basic_Usage#Starting_a_GUI_Environment](http://www.backtrack-linux.org/wiki/index.php/Basic_Usage#Starting_a_GUI_Environment)

---

### Post by meathdeath on 2012-06-26
i have intel hd graphics... i dont think any of you guys really helped me at all because your comments were either over my head or were too general. Dumb them down for me please...

---

### Post by haqking on 2012-06-26
> **meathdeath said:**
> i have intel hd graphics... i dont think any of you guys really helped me at all because your comments were either over my head or were too general. Dumb them down for me please...

If following links was too general or too complicated then i expect you will struggle using BT effectively for its intended purpose.

GUI support is not a priority with BT as it is not meant for general desktop usage.

Good Luck

Peace

---

### Post by meathdeath on 2012-06-26
If its not meant for general desktop usage then what the hell is it used for? Also im a noob when it comes to linux and have to have a GUI to take advantage of an OS and use it effectively.

---

### Post by haqking on 2012-06-26
> **meathdeath said:**
> If its not meant for general desktop usage then what the hell is it used for? Also im a noob when it comes to linux and have to have a GUI to take advantage of an OS and use it effectively.


Well you obviously got it from somewhere, why didnt you read what it said where you downloaded it from.

it is a Linux distro built around security auditing and penetration testing for use by pen testers/auditors/ethical hackers and more for the purposes of testing and auditing system security.

From their website:

> BackTrack is a Linux-based penetration testing arsenal that aids  security professionals in the ability to perform assessments in a purely  native environment dedicated to hacking. Regardless if you&#8217;re making  BackTrack you [Install BackTrack]("http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/"), boot it from a Live DVD or [thumbdrive]("http://www.backtrack-linux.org/tutorials/usb-live-install/"),  the penetration distribution has been customized down to every package,  kernel configuration, script and patch solely for the purpose of the  penetration tester.Source: [http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

Though in theory any security professional newcomer or advanced should be able to use it, in my experience there are far more people who have it than can actually use it ;-)

As a noob i suggest you use or try **Ubuntu**. from here [http://www.ubuntu.com/](http://www.ubuntu.com/) and ask questions in this forum about it if you get stuck in either General Help or beginner talk

---

### Post by Cheesemill on 2012-06-26
> **meathdeath said:**
> If its not meant for general desktop usage then what the hell is it used for? Also im a noob when it comes to linux and have to have a GUI to take advantage of an OS and use it effectively.

It's meant for security professionals who need to conduct penetration tests and software security auditing.

If you can't use Linux without a GUI than BackTrack really isn't the distribution for you, nearly all of the included applications are run from the command line and don't have GUI's anyway.

---

### Post by Cheesemill on 2012-06-26
> **haqking said:**
> in my experience there are far more people who have it than can actually use it ;-)

+1

I know people who have tried to use BackTrack as their main OS because they thought it would make their computer more secure !!

---

### Post by haqking on 2012-06-26
> **Cheesemill said:**
> +1

I know people who have tried to use BackTrack as their main OS because they thought it would make their computer more secure !!

 I know, epic fail.

I know at least 4 people who have done just that.

I know one guy who has BT stickers all over his laptop and a custom made BT T- shirt, who couldn't figure out how to start networking.

I weep for our civilization

---

### Post by meathdeath on 2012-06-26
cheesemill,
i think youre on to something. i want to be able to install it so i can access wifi networks even if they are WPA encrypted.... any other easier meathods you can mention? Thanks

---

### Post by haqking on 2012-06-26
> **meathdeath said:**
> cheesemill,
i think youre on to something. i want to be able to install it so i can access wifi networks even if they are WPA encrypted.... any other easier meathods you can mention? Thanks

1. You dont need BT necessarily to do that.

2. If you cant get graphics working it is highly unlikely you can crack WPA.

3. Cracking and circumventing system security is not supported here

4. As for easier methods, i already linked you to the appropriate forums, ask the questions there

Peace

---

### Post by cariboo on 2012-06-26
If you are having problems installing backtrack, you may get better and quicker support on the backtrack forums:

backtrack-linux.org/forums

We don't support the activities that you are asking about here. Thread closed.

---

