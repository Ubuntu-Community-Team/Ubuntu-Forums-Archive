---
title: "Was away for 3 months; just installed 3 months of updates; now boots but won't login"
date: 2019-03-25
forum: Apple Hardware Users
---

### Post by swarup on 2019-03-25
Using Ubuntu 14.04. Was away for 3 months, so computer was not used during that period. Just returned, booted up computer and installed 3 months of updates. After installing all, the usual message came that need to shut down and reboot to complete install of all updates. When I shut the computer down and tried to reboot, it rebooted fine and came to the login screen. It accepts the password, but then does not come to the desktop. It just again gives me the login screen. I tried putting in a wrong password, and it recognizes that pw as wrong. When I put in the correct password, it recognizes that as correct, but as mentioned just comes back to the login screen rather than coming to the desktop. Will be very grateful for help with the solution.

---

### Post by oldfred on 2019-03-25
Can you boot older kernel in grub menu?
Or boot recovery mode?

What video card/chip?
What brand/model system?

Note that 14.04 is EOL in April 2019. So you may want to backup & do new install for current version.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by swarup on 2019-03-25
I tried the kernel just previous, and the same thing happened. I then tried the kernel five previous, and again the same thing happened. I tried boot recovery mode, selected "fix packages", then when that was done reverted to normal boot, and the same thing happened. I then tried recovery mode, selected failsafe mode, then when that was done reverted to normal boot, and again the same thing happened. The computer is an Apple MacBook Pro from 2009, which has been running Ubuntu 14.04 beautifully since it came out in 2014. The graphics card is NVIDIA GeForce 9400M 256 MB, and the chip is a 2.8 GHz Intel Core 2 Duo.

---

### Post by CatKiller on 2019-03-25
There's been an issue with proprietary drivers from the graphics-drivers PPA and 14.04 kernels, which people have managed to fix by removing the UEFI shim package.

It is time to upgrade, though.

---

### Post by swarup on 2019-03-25
1. I can't upgrade until I boot up fully into the desktop so that I can backup my hard drive.
2. Did the issue you report re proprietary drives from the graphics drivers PPA and 14.04 kernels arise only in the last three months? I had no issues through the end of december 2018. 
3. If the issue arose in the last three months, then perhaps this is the problem I am facing now. How would I go about removing the UEFi shim package?

---

### Post by swarup on 2019-03-25
When one arrives to the login screen, it gives the option to select among three different desktop styles. Till now I was going with the default style, which I always use. Just for kicks, I tried one of the two "classic" options, and it worked! I am logged back into the desktop, albeit with a classic design setup. What about getting the usual desktop style back though. Is that not going to work any more?

I can get to the desktop only in Gnome Metacity mode. It refuses to login using either of the other two modes-- the ubuntu mode or the other Gnome mode. I would prefer the newest mode, the "Ubuntu" mode, which I've been using for the last five years, if it is possible.

Also: the suspend function has been working fine for the last five years. But now with this last series of updates, the suspend function is no longer working.

---

### Post by SeijiSensei on 2019-03-25
If you boot a disc image of Ubuntu, you'll be offered the option to Try or Install.  If you pick Try, you'll see your existing filesystems appear in the file browser.  If you have network connectivity, you can copy what you need to save over the network, or use an external USB drive of sufficient capacity.

---

### Post by CatKiller on 2019-03-25
It is a recent issue, yes. I'm also under the impression that it was an issue for everyone using 14.04 with the Nvidia drivers, but then the drivers in the repositories were patched to fix it and the PPA ones weren't. It's to do with loading kernel modules, I believe. 

A few people who were having the issue reported that removing the shim package fixed it for them. It's not something I've experienced myself. I can't remember the name of the package, but I'll try to look through the posts when I'm at my desktop if you haven't found it yourself by then.

The reason you can use Metacity but not the others is because Metacity doesn't require accelerated graphics but the others do. Once you've got your graphics drivers working again you should be able to log into the other environments.

Since you can log in now, you should be able to run your backups. Otherwise you can back things up from a live environment as SeijiSensei says. Support for 14.04 ends in a couple of weeks, so you'll need to be backing up and upgrading to 16.04 or 18.04 anyway.

---

### Post by swarup on 2019-03-25
Thanks to all of you for your valuable and tremendously helpful suggestions.

The computer is indeed working now in Metacity. Suspend is not working though, so every time I want to put the computer to sleep, I have to instead shut it down. Suspend was working fine for the last 5 years. Any suggestions for a solution on this, kindly let me know.

@ CatKiller: If you are able to let me know about how to get the graphics drivers working again, I will be deeply grateful.

Yes, I will certainly run a backup now, and I do plan to upgrade to 18.04. I would prefer to do so when I get a chunk of free time to do so though. It is inevitably a big job to get the new OS working according to one's specific needs, and get all the needed associated software installed and running again. Having just returned from being away for three months, I have many other works to attend to as well. If I could get my 14.04 working properly, and do the upgrade when I get some time instead of under pressure of immediate need, that would be best.

---

### Post by swarup on 2019-03-26
I do still need help with:
1. Getting the suspend function to work; it has been working perfectly for the last 5 years until these last three months of updates.
2. Getting the graphics drivers to work so that I can boot up into the usual desktop style.

The computer is currently running quite hot even with just minimal activity of email etc. Don't know whether this may be due to the graphics drivers not working?

---

### Post by CatKiller on 2019-03-26
Apparently the package whose removal helped some other people was called *shim-signed*.

---

### Post by swarup on 2019-03-26
Which of the four below options should I use?

1. Uninstall shim-signed

To remove just shim-signed package itself from Ubuntu 14.04 (Trusty Tahr) execute on terminal:

sudo apt-get remove shim-signed

2. Uninstall shim-signed and it's dependent packages

To remove the shim-signed package and any other dependant package which are no longer needed from Ubuntu Trusty.

sudo apt-get remove --auto-remove shim-signed

3. Purging shim-signed

If you also want to delete configuration and/or data files of shim-signed from Ubuntu Trusty then this will work:

sudo apt-get purge shim-signed

4. To delete configuration and/or data files of shim-signed and it's dependencies from Ubuntu Trusty then execute:

sudo apt-get purge --auto-remove shim-signed

---

### Post by oldfred on 2019-03-26
Moved to the Apple hardware users since Mac.

Best to post each as new questions with those issues & your model Mac in title in the Apple sub-forum so those with Mac may be able to help.

---

### Post by swarup on 2019-03-26
This question is unrelated to Mac; it is related only with the NVIDIA card, which people have on all kinds of computers.

---

### Post by CatKiller on 2019-03-26
You only need to remove the package. Any other packages that depend on that package to function will also be automatically removed. That's what depends on means. There's not a lot of practical difference between remove and purge.

---

### Post by swarup on 2019-03-27
I removed shim-signed, but it doesn't seem to have made any difference. Earlier I used to see a big NVIDIA insignia on the screen during boot up. Now I don't get that. Does this mean the NVIDA driver is still not functioning? I checked synaptic, and the NVIDA drivers seem to be installed. Is it that some or another ubuntu software update in the past couple months is blocking the video driver from functioning?

---

### Post by oldfred on 2019-03-27
Please start a new thread on nVidia issue.
Those that know nVidia will not look at a thread with this title.
If your system needs the very old nVidia driver 304.xx or older, it may not work with newer Ubuntu. Open source driver should support those old cards anyway, unless hardware is unique.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

