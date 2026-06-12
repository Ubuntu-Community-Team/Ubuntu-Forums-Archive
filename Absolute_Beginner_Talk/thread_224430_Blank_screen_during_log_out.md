---
title: "Blank screen during log out"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Kieferkat on 2006-07-27
Hello, I installed Ubuntu on a computer at my house today for the first time, and I have never used linux before, so I am very inexperienced.  I decided to install KDE alongside Ubuntu so that I could experience both.  When I was logging out of Ubuntu for the first time to start a new session in Kubuntu the screen went blank.  Only after pushing the power button on the computer would a message appear asking for a username.  After I entered my username Kubuntu shut itself and the computer off.  I have tried again logging out of Ubuntu and Kubuntu and the same thing happens every time.  How can I fix this problem?

---

### Post by richardward101 on 2006-07-28
Do you know if you are running KDM or GDM (do you get a kubuntu logo before you type your password, or a ubuntu one?). The fist thing I'd suggest is to change from the one you're using to the other one, see if you still get the problem

---

### Post by Kieferkat on 2006-07-28
OK, so I removed Kubuntu using the sudo aptitude remove kubuntu-desktop command (which I could luckily use since I installed it with aptitude over ubuntu).  However, even with just ubuntu/gnome left when I log out it still gives me a blank screen.  The message I get when I press the power off button on my computer after the blank screen occurs is this:

Ubuntu 6.06 LTS JohnDesk tty1
Username:

When I try to type a username no text can be entered, and eventually it changes over to the ubuntu shut down screen whether I press anything or not.  Strangely pressing the power off button seems to be the only way to "unlock" the computer display and imput.  It's not too big of a hassle right now since I am the only user using the computer, but soon other people in my family will be using it too, which could cause a lot of inconvienience when they try to log out.  Any ideas as to what it might be?

---

### Post by richardward101 on 2006-07-28
```
sudo aptitude remove kubuntu-desktop
```

will not actualy remove KDE. The package manager works by dependancies, so if one package needs anothe package, it will be figured out by aptitude. the kubuntu-desktop package actually is empty, but it relies on ALL the things that come with kubunu, so removing kubuntu-desktop will not have changed anything on you're system.

As for the power button, that shuts down the system whenever you press it. the message you see is one of the non-graphical logins that ubunutu loads by default, it is shown because the graphical environment is the first thing to stop in a shutdown.

Its actually quite difficult (afaik) to remove kubuntu-desktop, but 
sudo apt-get remove kdm
sudo apt-get --purge remove libartsc0
should get most of it. try that and see if it works again

alternatively you could just switch to the other login manager (as thats what seems to be messing up).
sudo dpkg-reconfigure kdm
will give you the option of which login manager you want to use, (gdm or kdm, these are distinct from gnome and kde, either login manager can use either desktop). Try one, then if you still have the problem, try the other.

---

### Post by Kieferkat on 2006-07-28
Thank you for your help, I will try those things right away.  But as for fully removing KDE, is it too difficult for me to attempt?  Would it be easier to just do a clean install of ubuntu?  I suppose I don't really need to have it off my system, as long as its not slowing anything down or messing anything up.

For now I'll give what you said a try though.

---

### Post by Kieferkat on 2006-07-28
Alright, So I used sudo apt-get remove kdm as well as sudo apt-get --purge remove libartsc0 but neither command said I had anything to remove, so I guess they had already been removed.  

However, when I tried to imput sudo dpkg-reconfigure kdm it gave me this message:
/usr/sbin/dpkg-reconfigure: kdm is broken or not fully installed

Where should I go from here?

---

### Post by richardward101 on 2006-07-29
Ok, try```
sudo dpkg-reconfigure gdm
```
select gdm if asked, and see if that fixes it.

If not make the blank screen thiung happen, then press CTRL+ALT+F1. this should hopefully drop you into a text login screen. login and type```
dmesg | tail 1>dmesg.txt
```
then restart and log back in, you should have a file in you're home folder called dmesg.txt, post its contents here (then you can delete it).

---

