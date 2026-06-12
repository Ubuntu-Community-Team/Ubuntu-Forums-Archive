---
title: "My first Ubuntu Install - Hoary!"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-11
Hi Everybody

I tried to install Ubuntu (5.04 - Hoary) having read so much about it - I wanted to give it a go.

I tried to install it on 2 computers - mine spare one and my dad's. Installed ok but the problem in both cases was that I wasn't able to change my screen resolution from the default 640 x 480 to my preferred 1024 x 720. There was no other option to select.

What went wrong and what do I need to do to fix this.

On both these computers, I have Windows 2000/XP and both have a screen resolution of 1024 x 720.

Can anyone help please!



Best regards


Deepak Agarwal

---

### Post by engla on 2006-02-11
I. You should probably install Ubuntu 5.10 "Breezy Badger" now. It's the latest stable release and has got updates added to it for extra stability.

II. Running 'sudo dpkg-reconfigure xserver-xorg' in a terminal can help your display settings. Input your user's password to authenticate before the program starts.

---

### Post by taurus on 2006-02-11
Why don't you try out the latest version which is Breezy, 5.10!!!  And if you want to modify your screen resolution, you can do it in /etc/X11/xorg.conf.

sudo gedit /etc/X11/xorg.conf

Scroll toward the end of it to where you see something like "640x480", add "1024x768" before it...

---

### Post by aysiu on 2006-02-11
[This page](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has all the answers.

---

### Post by agarwaldvk on 2006-02-12
Guys

Thanks a lot for all your responses.

But going by the responses, it appears that I am at even a further lower level at using this Ubuntu O/S. I need a bit more step by step help.

First thing, how do I get to the command line to enter commands?
Second, how do I go looking for a file, I mean the filepath etc etc.?
Thirdly, how do start this editor "Nano" and lastly what is this "Sudo" thing?

This confirm to you all that I am an absolute Novice when it comes to Ubuntu or Linux or anything other than Windows but the fact remains that I want to be able to use Ubuntu, so please bear with me and help.

I have already requested for the Breezy version CD's - this could take a while to get to me but there is no way I can download 600MB on dial up? So in the interim, is there anything I can do with my current installation of Hoary?


Best regards


Deepak Agarwal

---

### Post by aysiu on 2006-02-12
[QUOTE=agarwaldvk]
First thing, how do I get to the command line to enter commands?[/quote] If you're in Hoary Ubuntu, go to Applications > System Tools > Terminal. If you're in Hoary Kubuntu, go to KMenu > System > Konsole

> 
Second, how do I go looking for a file, I mean the filepath etc etc.? In Ubuntu, go to Places > Filesystem. Unfortunately, Hoary's file browser defaults to "spatial" mode, which doesn't give you back, forward, up, or down arrows, but you can change it to "browser" mode in Edit > Preferences.

In Kubuntu, just open Konqueror and type the path in the title bar: /home/agarwaldvk for your home directory, for example.

> 
Thirdly, how do start this editor "Nano" and lastly what is this "Sudo" thing? Nano is exactly that--an editor. There are graphical editors (Gedit for Gnome, KWrite for KDE), but Nano is a terminal editor. I usually give people Nano commands because I don't know whether they're using KDE or Gnome. For more on "sudo" see the third link of my signature.

> 
I have already requested for the Breezy version CD's - this could take a while to get to me but there is no way I can download 600MB on dial up? So in the interim, is there anything I can do with my current installation of Hoary? Yeah. Just *use* it. Honestly, Breezy doesn't have that much over Hoary--most of the changes are cosmetic. Hoary was a very stable release. Just stick with it for now.

---

### Post by agarwaldvk on 2006-02-12
Dear Aysiu

You are an absolute legend.

Thanks a lot again for your generous response. Greatly appreciated.

I shall give that a go and see how I go.

One last thing before I go - do I log in as the user account that it created for me when I installed Hoary or do I need to log in as a different user to have administration rights?

Best regards


Deepak Agarwal

---

### Post by swguru on 2006-02-12
Log in as the cerated user account, and by using the sudo command, you have root (administrator) rights. Refer to that 3rd link in aysi's sig for more info.

---

### Post by aysiu on 2006-02-12
[QUOTE=agarwaldvk]
One last thing before I go - do I log in as the user account that it created for me when I installed Hoary[/quote] Yes. > or do I need to log in as a different user to have administration rights? No.

The regular user can assume temporary root privileges with something called *sudo*. For more details, see the third link of my signature.

**Edit**: swguru beat me to it.

---

### Post by agarwaldvk on 2006-02-15
Guys

Thanks a lot everyone. With all the help that has been provided I have been able to set my screen resolution to what I wanted - 1024 x 768.




Greatly appreciated.


Best regards

---

