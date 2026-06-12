---
title: "Thinking of trying Ubuntu: couple questions"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by JeffV on 2006-02-01
I've had some mild experience playing with Linux in the past and am thinking about trying Ubuntu since I've been hearing good things about it.  

This is my situation:  Several months ago I installed Fedora Core 4 for dual booting with Win XP.  I only wanted to try it out and experiment with Linux to see if I liked it, and it turns out I did like it a lot for the most part.  However, over time I found myself booting into linux less and less and now I always just use windows again.  

Now I'm thinking I'd really like to go back and play with linux some more, but thought maybe I should try a different distribution.  What I want to know is what sort of things are different between distributions?  Are there any major differences I should notice trying ubuntu after playing with Fedora Core 4?

---

### Post by m.musashi on 2006-02-01
Since Ubuntu is my first Linux distro I can't speak much to how it compares to other distros (I actually did play with Suse a bit too). However, and maybe you already know this, you can play around with the live CD and see what it's like without having to install it. You will have to download a 600+MB ISO file and burn it. I did that and after playing with the live CD for about 20 minutes went ahead and installed it as a dual boot.

---

### Post by Lord Illidan on 2006-02-01
I have used different distros in the past, and have always gone back to Ubuntu/Kubuntu.

Ubuntu has the best community of any distro I have used. These forums are awesome, and the mods helpful.

The wikis are excellent, too.

Ubuntu is based on Debian (another older distro), and uses the apt-get package manager. The long and short of it is that to install most packages, all you have to do is type: ```
sudo apt-get install *name of package*
```, or use Synaptic, a GUI for apt-get.

The disadvantages over Fedora Core 4, I don't know, since I haven't used Fedora Core 4, only 1 and 3. But tell us what you liked in Fedora, and we'll see if you can get them under Ubuntu.

---

### Post by JeffV on 2006-02-01
Yeah, I was thinking about trying the live CD later tonight. I just wanted to be a little prepared for what to expect compared to my short experience with Fedora.  And I figured there might be differences I wouldn't realized unless someone else pointed them out to me.

---

### Post by JeffV on 2006-02-01
[QUOTE=Lord Illidan]
The disadvantages over Fedora Core 4, I don't know, since I haven't used Fedora Core 4, only 1 and 3. But tell us what you liked in Fedora, and we'll see if you can get them under Ubuntu.[/QUOTE]

Well, I'm sure I didn't explore Fedora Core 4 to its full potential.  Almost everything I liked.  The only things I found awkward were trying to set up the driver for my video card.  And I was trying to get an extended desktop between two monitors, but it wouldn't do it the way I wanted.  And I got a little lost and confused regarding repositories for software.  It seemed awkward that there were all these repositories, but I kept reading different guidelines over which ones to use and which ones to stay away from.

---

### Post by steve.horsley on 2006-02-01
My guess is that the biggest difference is that Ubuntu uses Gnome (I believe that Fedora uses KDE). You can install kubuntu instead if you know you want KDE, but with either, you can install the other desktop too, and choose which desktop to use as you login.

Unlike Fedora, Ubuntu installs from just one CD, but has a massive software repository online that you can download more from post-install.

Brown.

In general, things just seem to work.

Oh, the way you do sysadmin work is different. The root account is locked by default, and you do all you admin tasks using sudo to gain root privilege. This takes a little getting used to.

---

