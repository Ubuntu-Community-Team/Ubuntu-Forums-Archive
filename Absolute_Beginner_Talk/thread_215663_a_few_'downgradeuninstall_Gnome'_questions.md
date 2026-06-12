---
title: "a few 'downgrade/uninstall Gnome' questions"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-14
Hi everybody -- my question is in the final paragraph.

I'm going to need to install Ubuntu (alternate install cd with text installer) onto the following machine:  Celeron 433MHz (433/128/66) and 256MB of PC-100 CL3 RAM clocking down to PC-66 speed.  

It also has an 8MB AGP (AGP 2x) video card.

Having already done a test install of both Ubuntu and Xubuntu onto this machine, I want to go for Ubuntu but a dumbed down GUI desktop.

Therefore, to 'get rid of GNOME' and replace it with Xfce, I was just wondering if there are any special steps I need to do.  I'm familiar with using Synaptic, but I would think there is more to this than merely 'uninstalling GNOME' and 'install Xfce'.  Any tips greatly appreciated and thank you so much for reading this.

---

### Post by K.Mandla on 2006-07-14
Hi. If I understand you right, it seems like you have a couple of options.

First, install Ubuntu (which is to say, the Gnome desktop) completely. When it finishes, install Xubuntu with *sudo apt-get install xubuntu-desktop*. You'll have all the software that comes with both installations, and when you log in you'll have the option of using either Gnome or XFCE.

The downside of that is time. You're essentially installing Ubuntu twice, and unless you're on a fast network connection it's going to take a while. And given the specs of your computer, it'll be quite lengthy.

The second option is to install a server (it's an option on the alternate CD menu) then add Xubuntu with the same command as above. It'll take less time, but you're left with just the XFCE software. That might be good enough, given your computer.

Another option is to install a server, then follow some of the directions for [low memory systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). In this case, you're starting from scratch and installing only the software you want. It takes a little more experience, but the results are much lighter than the standard installations. I use this method on machines that have similar specs to yours.

I guess you have the option of installing straight from an Xubuntu CD, too. If you know you want Xubuntu without the rest of the Ubuntu Gnome stuff, this would be the easiest.

Does that help at all? :rolleyes:

Good luck! Ask again if you have more questions! :D

---

### Post by Sonofmoog on 2006-07-14
I believe the packages you want are ubuntu-desktop and xfce-desktop.  Select xfce-desktop and it will pull in all the necessary dependencies.  Select ubuntu-desktop and remove, and it will do the same.  It really is that simple, though I'd mention a couple of caveats.

At the login screen, the first time you login to xfce, you'll have to select it from the session options.  If you have autologin enabled, you'll want to log into xfce at least once before uninstalling GNOME.  

I have not tried this myself, but was given assurances on the Kubuntu board that I could add GNOME in exactly this way, so it should work for you.

---

### Post by Susan.Desanco on 2006-07-14
To K.Mandla --
To Sonofmoog --

Wow, thanks to you both!  Those are particularly helpful posts there.  I have used both Ubuntu and Xubuntu previously, and I'd like to grab the software that comes with both distributions.  Ultimately, the machine will end up in the hands of a user who has only dial-up connection and I'd like to hand it over to her in fairly home/office functional form.

As I read your posts and think about my ultimate goals for the computer user (who won't be me), I really feel that I should:

1) install Ubuntu (alternate CD + text installer)
2) then install Xubuntu with the sudo command given above
3) I understand that at that point, I will be given two desktop login options at startup of linux
4) I log into Xfce once
5) Then I can set up an autologin enable, which I do desire
6) Next, I can uninstall GNOME (not sure how to do that yet though)


Please check me over and any further suggestions based on your expertise are very much appreciated!

---

### Post by K.Mandla on 2006-07-14
I think that will do the trick for you. The session option on the GDM login screen is where you pick XFCE or Gnome. It will ask to set it as the default for all sessions, or as a one-time-only selection. 

Keep in mind that installing xubuntu-desktop is going to double-up on some software, in a manner of speaking. For example, the default Gnome setup will install OpenOffice, and adding xubuntu-desktop will also add Abiword. 

Since the two desktop systems (xubuntu-desktop and ubuntu-desktop -- the Gnome default) are going to take up quite a bit of disk space, you might want to take the time to uninstall things like Abiword and Gnumeric, and anything else that seems repeated. It's just a space consideration.

I guess that depends on the space you have on the drive. ;) 

Cheers and good luck!

---

