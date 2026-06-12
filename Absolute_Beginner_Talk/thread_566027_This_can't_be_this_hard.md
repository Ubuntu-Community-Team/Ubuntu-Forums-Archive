---
title: "This can't be this hard"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by ShadowdogKGB on 2007-10-03
Why, oh why, must it be so difficult to install drivers for Via audio drivers, or any drivers for that matter. I downloaded the latest Ubuntu drivers for Via audio. Now, I'm a total noob. Total beginner. I open terminal, and since I'm a total noob I DON'T KNOW HOW TO NAVIGATE OR USE TERMINAL. So I choose the built-in help option. IT TELLS ME NOTHING ABOUT WHAT COMMANDS TO USE TO NAVIGATE, CHANGE DIRECTORIES, ECT. So I try the IRC method to find an  Ubuntu chat room. Well, all I get is this IRC message window with no way to find ANY channels at all. I don't have the time or the patience to sit down and pull needles out of my eyeballs just to get this to work. 

I'm frustrated for sure. But this is a fine example of the HUGE hurdle the Linux community faces. I don't know how on God's green earth anybody expects Linux to become mainstream. It is so convoluted it's not even funny anymore.

---

### Post by thiebaude on 2007-10-03
Which audio driver is it VIA HD Audio Codec VT1708 paired with VT8237A/VT8251/CX700(M)

---

### Post by santiagoward2000 on 2007-10-03
To navigate on the terminar you must use the cd command. For example, if you want to go to the folder /home/user/drivers, you type:
cd /home/user/drivers
By the way, if you type:
-h
you should see a list with commands you can use.
Just ask if you have any other question, I'll try to help (even if I'm a newbie too), or someone else probably will.

---

### Post by ShadowdogKGB on 2007-10-03
That's great. But why isn't this information displayed where it can easily be found. This is the kind of encrypted procedure that just totally turns people away.

---

### Post by llamakc on 2007-10-03
Simply googling for a basic command-line how-to would have helped too.

If your mind is already made up, why are you asking questions?

---

### Post by American_Outcast on 2007-10-03
> **ShadowdogKGB said:**
> That's great. But why isn't this information displayed where it can easily be found. This is the kind of encrypted procedure that just totally turns people away.

I have a VIA audio card and when I installed Ubuntu it got my card working without me doing anything.

1- Going from Windows to Linux there is a slight learning curve. MS wants you to completely rely on them. 

2 - Being specific as possible with hardware, drivers and your problem helps people to help you.

Maybe it is not the same for everyone. But with Ubuntu and Automatix2 I had no problem setting up the basics, including my Nvidia card and driver.

If you don't like Ubuntu or Linux then you can go back to XP. No one here will force you to stay or try to convince you to stay with Ubuntu. It is your choice and thats what Linux is about, in part, is choices.

---

### Post by maniac_X on 2007-10-03
Here's a coupla links to get you started....

This gives a list of useful links.
[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

This is a good place to start for learning the commands to use.
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

I hope this helps you out. Don't give in to the frustration. 
You're not the only one that has experienced it. Good luck 
in your journey and hope to see more of you.

---

### Post by ShadowdogKGB on 2007-10-03
> **llamakc said:**
> Simply googling for a basic command-line how-to would have helped too.

If your mind is already made up, why are you asking questions?

This is just the response I was expecting at some point. Kudos to you.

 Now, back to my frustration. I'd love to have an alternative to Bill Gates' empire. But going through the contortions of hell is not the way I had envisioned it. I simply want to get the sound to work on the machine in question. Googling, researching, trial and error, reading and more reading, and more trial and error. This is what we had to do with WINDOWS 3.1. It's 2007 now and here I am revisiting the same process. 

This is the motherboard in question:
[http://www.newegg.com/Product/Product.asp?Item=N82E16813138262R](http://www.newegg.com/Product/Product.asp?Item=N82E16813138262R)

---

### Post by 3rdalbum on 2007-10-03
Xchat opens up #ubuntu by default on Ubuntu.

It is difficult to install Via drivers because Via doesn't make it easy for Linux users. I guess they figure that "anyone who uses Linux will be able to use the terminal to install the driver".

For very common drivers (ATI and Nvidia), the Ubuntu team creates their own installation procedure which is super-easy, so the difficulty of installing drivers is imposed at the manufacturer's end, and is not due to any deficiencies in Linux.

If you feel strongly about having the Via drivers made easy to install, why not learn some scripting and make an easy installer? It would be a massive help to others in your situation. That's how open-source works - people who feel strongly about things put it down "in writing" and make Linux easier for everyday people to use.

---

### Post by llamakc on 2007-10-03
> **ShadowdogKGB said:**
> This is just the response I was expecting at some point. Kudos to you.

 Now, back to my frustration. I'd love to have an alternative to Bill Gates' empire. But going through the contortions of hell is not the way I had envisioned it. I simply want to get the sound to work on the machine in question. Googling, researching, trial and error, reading and more reading, and more trial and error. This is what we had to do with WINDOWS 3.1. It's 2007 now and here I am revisiting the same process. 

This is the motherboard in question:
[http://www.newegg.com/Product/Product.asp?Item=N82E16813138262R](http://www.newegg.com/Product/Product.asp?Item=N82E16813138262R)

This is the information we needed in the first post in order to help you. Thanks for providing it.

---

### Post by llamakc on 2007-10-03
Open a terminal. 

Type:

lsmod | grep ac97

and post the results.

---

### Post by American_Outcast on 2007-10-03
Correction on my above post. I have a Realtek AC97 not a VIA AC97. Apparently this is a slight difference, never paid attention to that before.

[My Motherboard]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&tool=softwareCategory&product=386640&docname=c00063254#N822")

Ubuntu did get it working without and trouble.

I had to play around with the controls in the volume control. Master, PCM and VIA DXS controls. (Volume Control: VIA 8237 (Alsa Mixer) )

---

### Post by adamorjames on 2007-10-03
> **ShadowdogKGB said:**
> That's great. But why isn't this information displayed where it can easily be found. This is the kind of encrypted procedure that just totally turns people away.

Command line in Windows uses cd. Though I guess not many people use the command line anymore.

---

