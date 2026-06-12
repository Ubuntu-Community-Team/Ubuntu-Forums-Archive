---
title: "Elementary OS Luna upgraded!"
date: 2012-11-16
forum: Any Other OS
---

### Post by Chdslv on 2012-11-16
I've been using Luna daily build for sometime, so I knew what to expect, when Beta 1 was released, except the beautiful greeter and the default wallpaper. 

Once, I downloaded and installed the Luna Beta 1, I did my usual thing--upgraded it to Raring direct from Precise, by passing the transit Quantal.

I installed Calibre, so I could read a book, while Apt did its work.  I noticed that the Elementary devs were using their own ppa, so I didn't change that, before upgrade, so I have their Precise ppa applications, while the base became Raring. I also go rid of Plank, because it cannot intellihide and cannot be configured.

**All applications work very smoothly.**:)

I believe, the Elementary devs are somewhat afraid of their own creation, worrying a lot about bugs and delaying its release. Which "new final" release of any distro that's not buggy?!

I'll make a live CD out of my upgraded Luna and then change the Luna ppas to Raring, where applicable. 

Good day!

Happy experimenting!

---

### Post by NormanFLinux on 2012-11-16
I don't get what's wrong with the 12.04 LTS version.

I recommend you try out the noolabs Mac OSX Lion theme and cursors.

Matched with the Leopard OSX Space wallpaper, you couldn't tell this is Linux!

It would be the envy of your Mac friends! :popcorn:

---

### Post by Chdslv on 2012-11-16
> **NormanFLinux said:**
> I don't get what's wrong with the 12.04 LTS version.

I recommend you try out the noolabs Mac OSX Lion theme and cursors.

Matched with the Leopard OSX Space wallpaper, you couldn't tell this is Linux!

It would be the envy of your Mac friends! :popcorn:

Linux is good, so I don't have to envy my Mac friends, but show them the right way, the Linux way.
MacOsX Lion theme doesn't have the umpteen amount of themes Linux has. Anyway, I don't care much about the Mac, and am not ready to pay lot of money for hardware, which gets old the day you by it, but the software. Its not that hard to install Mac OSX in a PC/laptop. I opt for Linux.

**Anyway, this is not about Mac, but about upgrading Luna to Raring**.:)

The Elementary OS is nice, but the Elementary OS devs are afraid of their own creation and won't release a final one. I've been pushing them for few months to release this Beta 1.:)

I'm sure that beautiful greeter and the default wallpaper came from Russian ideas.

Good day!

---

### Post by PhantomTurtle on 2012-11-17
I think they aren't going to use Raring because 12.04 is the LTS release so for Luna its probably going to stay at Precise.

I know that some people are getting impatient because Luna is so awesome but it looks like its never going to be released and by that time it is released, everything will be out of date. But I think its a good idea to take the time to work on the OS rather than release 'half-baked' software. It's coming guys, we just have to wait.

---

### Post by Chdslv on 2012-11-17
> **PhantomTurtle said:**
> I think they aren't going to use Raring  because 12.04 is the LTS release so for Luna its probably going to stay  at Precise.

I know that some people are getting impatient because Luna is so awesome  but it looks like its never going to be released and by that time it is  released, everything will be out of date. But I think its a good idea  to take the time to work on the OS rather than release 'half-baked'  software. It's coming guys, we just have to wait.

Raring is just a base, like Precise. The problem is with their  applications and connecting each other. The Pantheon Files looks nice,  but Nautilus has more functionality. Noise, well, I am going for Vlc.  Plank is out as it cannot be configured, so Docky would come instead, or  Awn or Cairo dock. Or, even the Gnome-panel. Mail would be  Thunderbird--no time to learn another one. Midori, well, its good to  play with, but not for the long day.

The "Elementary experience" is the same. The snappiness is there. Luna  eats a lot of memory, but I have enough, you too, I believe.:smile:

I got rid of the ugly black (Gnome-shell) top panel. Had to let go of  the Wingpanel. Can't help it, even though it looks nice, they should  allow it to autohide. 

But still, I like my EasyPeasy installation upgraded to Precise! Less  memory eating and snappier than any other distro I've used.:smile: 

If the Luna guys keep on postponing the final release, the bus would be gone...

---

### Post by converted on 2012-11-17
I've only been using Elementary for about 12 hours (love it) but one of the first things I did was config plank for intellihide.  It's right there in the desktop section of system settings.

Does that not work for you?

I'm generally curious though -- how do you go about upgrading the ubuntu base to a new release?  Any breakage?  (I didn't see you mention any) I'd love to get it up to quantal...

[IMG]http://i.imgur.com/B6Obd.png[/IMG]

---

### Post by Chdslv on 2012-11-17
> **converted said:**
> I've only been using Elementary for about 12 hours (love it) but one of the first things I did was config plank for intellihide.  It's right there in the desktop section of system settings.

Does that not work for you?

I'm generally curious though -- how do you go about upgrading the ubuntu base to a new release?  Any breakage?  (I didn't see you mention any) I'd love to get it up to quantal...



Plank intellihides, but it doesn't allow you to change settings like Docky.

To get to Quantal;

>   
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list
sudo apt-get update; sudo apt-get dist-upgrade 

Keep an eye on what's happening--Apt would ask you questions, read what's there and get it done as you like it. Usually, Apt gives a hint.

Nothing broke yet. :)

Try this on a free partition, so you get used to it. You can do this with Ubuntu and Ubuntu based. I did a lot of upgrading of Ubuntu and its derivatives and all kind of clones too. Check my posts.

Good day! :)

---

### Post by converted on 2012-11-17
Thanks for the info!

---

### Post by NormanFLinux on 2012-11-17
> **PhantomTurtle said:**
> I think they aren't going to use Raring because 12.04 is the LTS release so for Luna its probably going to stay at Precise.

I know that some people are getting impatient because Luna is so awesome but it looks like its never going to be released and by that time it is released, everything will be out of date. But I think its a good idea to take the time to work on the OS rather than release 'half-baked' software. It's coming guys, we just have to wait.


They've decided to go along with Precise because the elementary devs don't want to change from a reliable and tested base. They want it to be a long term support distro and don't want to be bound to Ubuntu's rapid release schedules. This on the whole, I think is good. And 12.04 is supported by Canonical at least until 2017.

---

### Post by Chdslv on 2012-11-17
> **converted said:**
> Thanks for the info!

Here is a screenshot of Luna 64 bit moved to Quantal.

---

### Post by Chdslv on 2012-11-17
> **NormanFLinux said:**
> They've decided to go along with Precise because the elementary devs don't want to change from a reliable and tested base. They want it to be a long term support distro and don't want to be bound to Ubuntu's rapid release schedules. This on the whole, I think is good. And 12.04 is supported by Canonical at least until 2017.

The problem with the Elementary OS Team is that they are not sure about their own applications...So, by the time Luna final would come out Precise's LTS period would be over...:)

---

### Post by NormanFLinux on 2012-11-17
> **Chdslv said:**
> The problem with the Elementary OS Team is that they are not sure about their own applications...So, by the time Luna final would come out Precise's LTS period would be over...:)

Its possible to upgrade it then to the next LTS release. It is after all Ubuntu at its core. ;-)

---

### Post by Chdslv on 2012-11-17
> **converted said:**
> Thanks for the info!

How did it go?:)

---

### Post by converted on 2012-11-18
I haven't done it -- I just want to know *how* to do it.  :-)

Eventually I probably will, but so far being on Precise is not causing me any difficulty.

---

