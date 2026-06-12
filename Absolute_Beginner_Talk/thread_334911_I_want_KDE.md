---
title: "I want KDE"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Fireware on 2007-01-09
How can I get KDE on my desktop (it has no internet connection)?

Where do I download the KDE for Ubuntu? Can I burn it like a normal CD? and then just insert it in my desktop and type in this command: sudo aptitude remove xubuntu-desktop, then type sudo aptitude install kubuntu-desktop ?

---

### Post by obsidion on 2007-01-09
> **Fireware said:**
> How can I get KDE on my desktop (it has no internet connection)?

Where do I download the KDE for Ubuntu? Can I burn it like a normal CD? and then just insert it in my desktop and type in this command: sudo aptitude remove xubuntu-desktop, then type sudo aptitude install kubuntu-desktop ?


  Not something I've tried but downloading and burning the kubuntu cd and apt-cdron add with the cd may work.

---

### Post by Fireware on 2007-01-09
I don't want to burn an ISO though. I cannot on this computer.

---

### Post by Bachstelze on 2007-01-09
Yes, this is the easiest way. Just download and burn a Kubuntu Alternate CD, then do *sudo apt-cdrom add*. You will be prompted for the CD, instert it if you haven't already and when Apt is finished scanning it, do *sudo apt-get install kubuntu-desktop*.

---

### Post by Fireware on 2007-01-09
So I would have to burn a ISO?

---

### Post by scj on 2007-01-09
Just me wondering, would it be possible to mount an iso, and run the kubuntu installer in xubuntu?  Or possibly make a partition that acts like a CD-ROM?

---

### Post by obsidion on 2007-01-09
> **Fireware said:**
> So I would have to burn a ISO?

 The other more convoluted way is to do the apt-get install kubuntu-desktop on another computer, then copy the contents of /var/cache/apt/archives to a cdrom and then copy that to the same place on the other computer and do an apt-get update apt-get install kubuntu desktop on it. Seems like a pretty silly way to do things and assumes the computers are at a similar state. Why not just get a couple of ethernet cards and connect the other computer to the net. What are you actually trying to achieve ?

---

### Post by DaneDog on 2007-01-09
You can request a FREE cd of Kubuntu from [www.kubuntu.org](www.kubuntu.org)  it's says 5-6 weeks shipping but I had mine in about 10 days... but it's not Edgy it's Dapper... or how about

apt-get install kubuntu-desktop -d which should download it to your pc and not install it then you might be able to burn that to a normal cd and copy it then install it...

Good point with the ISO also...

---

### Post by Bachstelze on 2007-01-09
Yes, of course it's possible to just mount the ISO. Whether it's an ISO file or an actual CD changes nothing.

---

### Post by Riyonuk on 2007-01-09
I too am curious, the -d I would do, but Im on windows. Anyway to get it on a usb and take it to my non-internet pc?

---

### Post by Fireware on 2007-01-09
I'll try setting up my internet. I have wireless here at my house. 

When I get a mouse, yes I need one lol, I'll need help setting my desktop to my wireless network. It has the card thing already in the harddrive.

---

### Post by Sef on 2007-01-09
> I don't want to burn an ISO though. I cannot on this computer.

If you can burn an iso and change your mind about burning them on Windows, then read [How_to_write_iso_files_to_cd.htm]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")
and download [Isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by Fireware on 2007-01-09
I have the Ubuntu 6.06.1 Live CD. Could I just put that in the CD while Xubuntu Edgy is on and in the terminal do sudo aptitude update and then sudo aptitude install kubuntu-desktop 


then after it is install, do sudo aptitude update, sudo aptitude remove xubuntu-desktop 


could I do that to get KDE?

---

### Post by Fireware on 2007-01-09
anyone?

---

### Post by obsidion on 2007-01-09
> **Fireware said:**
> anyone?

  Why don't you just try it and find out. Instead of geting your knickers in a twist because no-one has answered you for a while.

---

### Post by Russty of Oz on 2007-01-09
I use KDE on Ubunut, just go to synaptic and I think you will find all the KDE bits there.  Install KDE core and see what happens.  Then log out and click "end current session" then when you go to log in again click "services" (I think it is, or it may be "Options") and select KDE from the list.  

Doing it this way is great as you have both gnome and KDE to use!

Russty.

---

### Post by Fireware on 2007-01-09
I do not have Gnome install. I have XFCE. I'll try....when I have XFCE up and running and I put the Ubuntu Lice CD it the install icon comes up. Maybe if I re-install it from that I can install Ubuntu and then switch the KDE somehow?

---

### Post by Russty of Oz on 2007-01-09
I don't know for sure, but it should be the same.  Just see if KDE core is in your packages.

---

### Post by Fireware on 2007-01-09
How do I do that? If I do have it what commands do I use to install KDE?

---

### Post by Russty of Oz on 2007-01-09
Hmm, I have never used XFCE so I don't know how it works.

I assume you have it actually installed?  If so, you should have a package manager like synaptic so just open it and scroll through the list to KDE-core and select it then click whatever you do to apply the changes.

I will do some searching to see if I can find out more about XFCE.  Let me know if you have any success in the meantime.

---

### Post by Fireware on 2007-01-09
Yes, well did. Its installing again right now. I'll try that and let you know. I am using the Xubuntu Alternate CD btw.

---

### Post by Fireware on 2007-01-09
It only had the Gnome desktop, no KDE

---

### Post by Russty of Oz on 2007-01-09
OH!, I will have to check that out later, as I am about to have lunch.  Will get back as soon as possible.  

Does anyone else out there know anything about XFCE?

---

### Post by Russty of Oz on 2007-01-09
Just a thought, you could try installing gnome desktop then log out and at the log in screen select gnome from the list in "options" or "session", whatever you have on your log in screen, then log in and then follow the instructions here [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Russty of Oz on 2007-01-09
Just found this, give it a try.

sudo aptitude update
sudo aptitude install kubuntu-desktop

---

### Post by Fireware on 2007-01-10
That sudo commands don't work. Tried them.

---

### Post by Fireware on 2007-01-10
The Kubuntu CD won't work on 128 MB of RAM, correct? I would need the Alternate CD?

---

### Post by Russty of Oz on 2007-01-10
have you tried installing gnome from your package manager and then use gnome to install Kubuntu desktop?

---

### Post by Russty of Oz on 2007-01-10
Try **sudo apt-get install kubuntu-desktop**

---

### Post by Fireware on 2007-01-10
> **Russty of Oz said:**
> have you tried installing gnome from your package manager and then use gnome to install Kubuntu desktop?

How do I do that?

---

### Post by Russty of Oz on 2007-01-10
First of all, try the **sudo apt-get install kubuntu-desktop** in a terminal.  I just did it to install xubuntu and it worked.  Let me know what happens

---

### Post by Fireware on 2007-01-10
I thought you couldn't install KDE off of the alternate cd though? I'll go try right now. :)

---

### Post by Russty of Oz on 2007-01-10
You have actually installed xubuntu, haven't you?   You can't do it if you are just using the CD.  You have to have it installed on the computer before you can install another desktop.

---

### Post by Fireware on 2007-01-10
Didn't work.

---

### Post by Russty of Oz on 2007-01-10
So, have you xfce INSTALLED on your computer or are you just using the CD?

---

### Post by Russty of Oz on 2007-01-10
With Xubuntu installed, open the package manager and look through it until you find gnome-core and select it for installation.  Then log out and when you get to the log in screen, click "session" or "options" depending what is on your login screen, and then choose gnome and then log in.  If you are now in gnome, you could try the sudo apt-get install kubuntu-desktop 

Or look through synaptic package manager for KDE-core and if it is there then select it and then install.

---

### Post by Fireware on 2007-01-11
The gnome-core isn't there. I thought it was. I'll just get the Kubuntu Alternate CD I guess. I'll just figure out a way to get it on there. I don't know what to do.

What programs excatly do I need to burn an ISO and I'll download them and install them so I can download and burn the CD myself.

---

### Post by Russty of Oz on 2007-01-11
I use Nero myself on windows.  If you are using your Xubuntu you can do it with K3B

---

### Post by Russty of Oz on 2007-01-11
I am surprised that you haven't been able to install KDE using either synaptic or using the terminal, so using the Kubuntu CD is the best way out.  

Good luck. :)

---

### Post by Fireware on 2007-01-11
What is a good free program, that will always be free, not a trial type thing.

---

### Post by Fireware on 2007-01-11
I decided to download: CDBurnerXP. Is there any other program I need?

---

### Post by Fireware on 2007-01-11
I also got winMd5Sum. 

'bout how long does it take to burn the ISO?

---

### Post by Russty of Oz on 2007-01-12
I just had a look at CDBurnerXP Pro and it seems you don't need anything else, just the iso file to burn.  However, did you consider one called Active ISO Burner?  It seems very simple to use, you just put a CD in, locate the ISO file to burn and click BURN ISO!  see it here [http://www.ntfs.com/iso-burning.htm]("http://www.ntfs.com/iso-burning.htm")

As to how long it takes, well it all depends on your disc speed etc, but it shouldn't take too long, mine takes about 15min.

Let us know when you have success with Kubuntu.  I think it is great!

Russty :)

---

### Post by forkart on 2007-01-27
You can also use magiciso to burn iso file to cd and dvd. It works great for me.
[http://www.magiciso.com/tutorials/miso-burniso.htm](http://www.magiciso.com/tutorials/miso-burniso.htm)

---

