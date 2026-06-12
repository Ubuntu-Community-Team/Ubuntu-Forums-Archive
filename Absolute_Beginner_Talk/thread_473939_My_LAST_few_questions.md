---
title: "My LAST few questions"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-14
Hi all - still getting used to Ubuntu.

Last few questions:
1. What is sudo?
2. My laptop KEEPS chrashing. How can I stop this?  (when it crashes, on my laptop, the Caps Lock, and the Vertical Size of the monitor light comes on blinking)
3. I tried desktop effects, my PC went to a white screen... does it not work? can I make it work?
4. Can anyone reccomend some cool backgrounds for Ubuntu?
5. So I got my internet connected - what are some usual updates/upgrades that I should do?]
6. What are some programs that are a "must have" for linux?
7. What is synaptic?
8. EXACLTLY how do I uninstall Gaim? (I already installed pidgin)
9. What can I do to speed up my Laptop? It is almost slower than windows :(
10. Will Linux slow down after a little while like windows does?
11. Do I need ad-ware/spyware protection? Where do I get some?
12. """"""""""virus protecton? Where do I get some free?
13. Do apps already start up like in windows? - I hate that!
14. How do I not make every other app need my password? (for ex: everytime my PC starts WiFi - it asks for my password )
15. What are some cool things you can do on Linux?
16. What does formatting do? Will it make everything faster? Will it erase Ubuntu?



Thanks for all the help :) :popcorn::popcorn::popcorn:

---

### Post by phr0ze on 2007-06-14
> **ajskhan said:**
> Hi all - still getting used to Ubuntu.

Last few questions:
1. What is sudo?
2. My laptop KEEPS chrashing. How can I stop this?  (when it crashes, on my laptop, the Caps Lock, and the Vertical Size of the monitor light comes on blinking)
3. I tried desktop effects, my PC went to a white screen... does it not work? can I make it work?
4. Can anyone reccomend some cool backgrounds for Ubuntu?
5. So I got my internet connected - what are some usual updates/upgrades that I should do?]
6. What are some programs that are a "must have" for linux?
7. What is synaptic?
8. EXACLTLY how do I uninstall Gaim? (I already installed pidgin)
9. What can I do to speed up my Laptop? It is almost slower than windows :(
10. Will Linux slow down after a little while like windows does?
11. Do I need ad-ware/spyware protection? Where do I get some?
12. """"""""""virus protecton? Where do I get some free?
13. Do apps already start up like in windows? - I hate that!
14. How do I not make every other app need my password? (for ex: everytime my PC starts WiFi - it asks for my password )
15. What are some cool things you can do on Linux?
16. What does formatting do? Will it make everything faster? Will it erase Ubuntu?



Thanks for all the help :) :popcorn::popcorn::popcorn:

1. Sudo is a command which tells the computer to do something with administrative privileges. It stands for Super User Do.
2. We will need more details.
3. This can be difficult. First you need to set the right video drivers. Sometimes its even harder on a laptop but I've done it. Do you know the graphics card?
4. art.gnome.org, gnome-look.org
5. The update reminder will appear as an orange icon near the clock. I run it as soon as I see it. Other than that, most people sort out video codecs, mp3, flash on firefox. Most codecs can be had by trying to run the particular file, then ubuntu will ask you if you want the codec.
6. sorta the same as 5. Ubuntu comes fairly loaded so it just depends on what you want to focus on.
7. Synaptic is a very cool utility to find all sorts of applications, drivers and utilities for ubuntu. Go ahead and run it. Go into the settings and put check marks next to Universe and Multiverse. This will give you the biggest list possible. Then type your serach terms and find any software. Synaptic can be found in System->Administration
8. Find GAIM in synaptic and uncheck it. Then click update. You may have to reinstall PIDGIN after this.
9. Open the system monitor and look for swap usage. If you are using the swap, try some more ram. There are also guides to increase boot time.
10. Not really. You can install more and more programs that always run which will slow it down, but thats not the same as windows registry getting cluttered.
11. No, probably synaptic if you insist.
12. No, probably synaptic if you insist.
13. What do you mean?
14. There is a guide for making the keyring not ask for a password. The keyring password doesn't bother me enough where I have bothered though. You really shouldn't avoid the Sudo password prompt. Its protecting you.
15. There are lots you can do with linux, but I don't think you'll see anything radical that windows and mac don't really have. But you will find many things work better or are designed better, and some things are not.
16. Format 'erases' a partition. Don't do it if you don't need to. No it generally is not used for a speed enhancement.

---

### Post by linux noooob on 2007-06-14
overall most of your problems are because you have a low ram or you graphics uses your ram.
also sudo is the administrative comand. gaim should already be installed but if not go to add/remove in the first menu at the top of the screen (the one with the ubuntu symbol). you do not need adware spyware or anti virues all you need is a firewall because there is only like 5 diffrent viruses for linux and only a handfull of spyware and adware. the synaptic update manager is what updates your system like windows and synaptic is the same updater used for norton. and last linux can do anything you want it is all up to you you can play games work on homework/work you can watch and edit videos make games and surf the web linux is the best thing in the world linux is an os on the edge!!

hint sudo -i , or su (username) log you in as admin

---

### Post by ajskhan on 2007-06-14
Thanks, when I try and uninstall Gaim - it says sometihng about synaptic. How do I start it?

Also - my laptop is lagging a lot! I mean a lot!

---

### Post by OldTimeTech on 2007-06-14
firestarter is a good firewall and can be found in Synaptic.

---

### Post by ajskhan on 2007-06-14
Where on earth do I find synaptic?!

---

### Post by meman63 on 2007-06-14
System>Administration>Synaptic Package Manager.

Cheers,
    Meman63

---

### Post by starcraft.man on 2007-06-14
> **ajskhan said:**
> Hi all - still getting used to Ubuntu.

Last few questions:
1. What is sudo? [[COLOR="Red"]Sudo[/COLOR]]("https://help.ubuntu.com/community/RootSudo")
2. My laptop KEEPS crashing. How can I stop this?  (when it crashes, on my laptop, the Caps Lock, and the Vertical Size of the monitor light comes on blinking). - See end.
3. I tried desktop effects, my PC went to a white screen... does it not work? can I make it work? [COLOR="Red"]Have you installed your graphics cards driver? If not, download and install by following instructions on [Envy]("http://albertomilone.com/nvidia_scripts1.html").[/COLOR]
4. Can anyone reccomend some cool backgrounds for Ubuntu? [[COLOR="Red"]Link.[/COLOR]]("http://www.gnome-look.org/index.php?xsortmode=high&page=0")
5. So I got my internet connected - what are some usual updates/upgrades that I should do?] - - [COLOR="Red"]Depends on what you want to do, [Linux app finder ]("http://linuxappfinder.com/")has all the apps there are (mostly) browse via the left tree structure. Do all of the regular updates.[/COLOR]
6. What are some programs that are a "must have" for linux? [COLOR="Red"]Firefox and OO suite are the ones I use and both are installed, banshee is my favourite music player. Its in repos.[/COLOR]
7. What is synaptic? [COLOR="Red"][Synaptic.]("https://help.ubuntu.com/community/SynapticHowto?highlight=%28synaptic%29")[/COLOR]
8. EXACLTLY how do I uninstall Gaim? (I already installed pidgin) [COLOR="Red"]I never bothered with Pidgin, their the same mostly and I use aMSN more often, I don't know.[/COLOR]
9. What can I do to speed up my Laptop? It is almost slower than windows :( [COLOR="Red"]More ram, faster CPU, XFCE desktop environment will all speed improvement. [/COLOR]
10. Will Linux slow down after a little while like windows does? [COLOR="Red"]No, it doesn't have a registry. It will only slow or become unstable if you mess it up.[/COLOR]
11. Do I need ad-ware/spyware protection? Where do I get some? [COLOR="Red"]No.[/COLOR]
12. """"""""""virus protecton? Where do I get some free? [COLOR="Red"]No you don't. The only reason is to scan email attachments before forwarding to windows users. If you don't do that forget about an AV.[/COLOR]
13. Do apps already start up like in windows? - I hate that![COLOR="Red"] Yes, but only if you tell them to. System > Preferences > Sessions. Services can be disabled via System > Administration > Services.[/COLOR]
14. How do I not make every other app need my password? (for ex: everytime my PC starts WiFi - it asks for my password ) [COLOR="Red"]Read sudo above, it is an integral part of Ubuntu and is what makes it secure. Keep it enabled and don't log in as root just because its easier. I don't use wifi, if you use WPA you should only need to input the pass one time.[/COLOR]
15. What are some cool things you can do on Linux? [COLOR="Red"]Beryl/desktop effects, tux racer, GIMP, it depends what you find "cool"[/COLOR]
16. What does formatting do? Will it make everything faster? Will it erase Ubuntu? [COLOR="Red"]Formatting, erases the entire partition. If you format the drive with your data or root system, there goes your data or root system. Don't do it unless you know what your doing.
[/COLOR]


Thanks for all the help :) :popcorn::popcorn::popcorn:

Do I get a cookie or some bonus for answering all of those?

Now as for labtop crashing, how much ram is in your machine? What were you doing when it crashed? Is it always the same thing or random? Lastly, try popping in and running the live CD for 30 minutes and if it doesn't crash that means you must have destabilized your system by doing something.

---

### Post by lee292 on 2007-06-14
As far as cool backgrounds, you can use any image your heart desires.  For example, if you want your desktop to be a photo of your significant other, kids, pets or whatever else, open it with Image Viewer, select "Image" from the menu and then select "Set as wallpaper."

---

### Post by ajskhan on 2007-06-14
> **starcraft.man said:**
> Do I get a cookie or some bonus for answering all of those?

Now as for labtop crashing, how much ram is in your machine? What were you doing when it crashed? Is it always the same thing or random? Lastly, try popping in and running the live CD for 30 minutes and if it doesn't crash that means you must have destabilized your system by doing something.
256mb RAM - intergrated graphix. Envy didnt work :(


By the way... what is so cool about desktop effects (it wont work on my lappy)

---

### Post by starcraft.man on 2007-06-14
> **ajskhan said:**
> 256mb RAM - intergrated graphix. Envy didnt work :(


By the way... what is so cool about desktop effects (it wont work on my lappy)

Never mind desktop effects... you won't get them working on an integrated graphics card I don't think. If its intel you may try the i915 driver I think but I don't know anything about it...

256 RAM is low though, you should consider using the xfce desktop otherwise known as Xubuntu. Thats really the border of running Ubuntu well...

---

### Post by ajskhan on 2007-06-14
Can I go to xubuntu directly from ubuntu?

What does this mean: NOTE: Make sure you have all the repositories enabled (also universe and multiverse) in your /etc/apt/sources.list on Ubuntu

If you do not know how to enable those repositories, please take a look at this page:
enabling_extra_repositories"'

---

### Post by jfinkels on 2007-06-14
> **ajskhan said:**
> Can I go to xubuntu directly from ubuntu?

What does this mean: NOTE: Make sure you have all the repositories enabled (also universe and multiverse) in your /etc/apt/sources.list on Ubuntu

If you do not know how to enable those repositories, please take a look at this page:
enabling_extra_repositories"'

To install xubuntu-desktop, type the following in the terminal:```
sudo aptitude install xubuntu-desktop
``` Then, press Ctrl+Alt+Backspace to log yourself out and restart your X session (the system that controls your window display). When you get to the login screen, go to "Sessions" and select Xubuntu. Then log in and you will be using Xubuntu!

To uninstall the ubuntu-desktop (to clear up some hard drive space) type the following in the terminal:```
sudo aptitude remove ubuntu-desktop
```

To enable software repositories, go to "System > Administration > Software Sources" and check the box next to the multiverse and universe options. Then run the following command in the terminal:```
sudo aptitude update
```

---

### Post by ajskhan on 2007-06-14
I think I'll stick with ubuntu for now. Those boxes were already check?!

EDIT: Nevermind

Will Envy work now that this is updated?

---

### Post by starcraft.man on 2007-06-14
> **ajskhan said:**
> I think I'll stick with ubuntu for now. Those boxes were already check?!

Ok... the reason I recommend xubuntu is it is designed to run on machines with less ram/power like yours and you'll thus see a speed increase.

---

### Post by phr0ze on 2007-06-14
> **starcraft.man said:**
> Never mind desktop effects... you won't get them working on an integrated graphics card I don't think. If its intel you may try the i915 driver I think but I don't know anything about it...

256 RAM is low though, you should consider using the xfce desktop otherwise known as Xubuntu. Thats really the border of running Ubuntu well...

It depends on the card. It works on my 4+ year old laptop with integrated graphics. I did it in edgy and it was a pain to do, but I got it working. I have a feeling feisty would do it without a problem. I have a desktop with integrated graphics and it worked by checking the box on feisty. 

We just need to know what graphics chip you have. Thats what I meant by card. I assumed it was integrated since you said laptop.

---

### Post by phr0ze on 2007-06-14
> **ajskhan said:**
> Can I go to xubuntu directly from ubuntu?

What does this mean: NOTE: Make sure you have all the repositories enabled (also universe and multiverse) in your /etc/apt/sources.list on Ubuntu

If you do not know how to enable those repositories, please take a look at this page:
enabling_extra_repositories"'

In my first post I told you an easier way to enable those using synaptic.

---

### Post by ajskhan on 2007-06-14
the card is:
ATI Technologies Inc Rage Mobility P/M AGP 2x

---

### Post by ajskhan on 2007-06-14
I do intend on upgrading, or downgrading - whatever. but basically, is it the same thing?

---

### Post by cobrn1 on 2007-06-14
upgrade/downgrade what? the vid card?

If im not very much mistaken (and have just stumbled in here to look like the fool) upgrading is getting better, downgrading is getting worse. I assume you mean upgrade. ;-)

As goes low specs, I've got Ubuntu (6.10) installed and happily working on a pc with 128Mb RAM and a ATI Rage vid card (think thats the name - long story short - v. OLD card). While it can be a bit sluggish i think it runs quite fast - however, what I think is quite fast is probably unacceptably slow to most people - I run XP on it as well - PAIN... Ubuntu, even at half min requirements runs much quicker than XP at min req.

Xubuntu _is_ designed for slower systems, but I didn't really like it - in fairness I had internet difficulties, but it almost put me off Ubuntu - however, installing proper ubuntu on the chance it would work restored my faith. If youre happy running ubuntu and you've got 256Mb then you're almost certainly OK.

PS: sorry you can't use the cool graphics (neither can I :-(   ), but if you want to see what they're like then youtube beryl, compiz or XGL.

---

### Post by ajskhan on 2007-06-15
upgrade/downgrade to xubuntu...

---

