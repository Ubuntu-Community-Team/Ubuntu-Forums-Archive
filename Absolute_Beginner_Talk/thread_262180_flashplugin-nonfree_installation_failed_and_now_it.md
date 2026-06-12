---
title: "flashplugin-nonfree installation failed and now it's annoying"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-21
Hi helpers,

I tried to install the flash plugin according to [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) but something went wrong. And now every time I use Synaptic to install something I'm asked if I agree with the flash plugin terms and the same error occurs. It seems like it's trying to install the flash plague-in over and over again. Flash actually works with sound though, I can play games in my Firefox just fine.

I can't copy from the "changes applied" window of synaptic, where I can open the "terminal" part and see the messages. I think the essence is this:

dpkg: error processing flashplugin-nonfree (--configure):
subprocess post-installation script returned error exit status 1

How can I get rid of nuisance?

Thank you
Cruz

---

### Post by Metacarpal on 2006-09-21
When did you try to install it?  There was an update that I downloaded, and mine failed, too.

...Just did a search of the boards, and it looks like this is a known problem with a fix:

> **Limulus said:**
> Looks like there's a working package in the archives, but its not downloading via Synaptic just yet.  Gdebi will install it just fine though :)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb)

Be sure to click the Terminal arrow so you can agree to the EULA.

So you should download that package, save to desktop, then double-click it.  Click on the Install button (it'll ask for your password and re-open).  There will be a small arrow next to the word "Terminal" - click the arrow and a text screen will appear in the existing window.  When prompted, choose "Yes" and all should be well.

Can't wait to get home from work to fix mine, too...

---

### Post by Cruz on 2006-09-21
I just installed it about a half an hour before I started the thread. I followed your instructions and it solved the problem thanks a lot.

---

### Post by Metacarpal on 2006-09-21
> **Cruz said:**
> I just installed it about a half an hour before I started the thread. I followed your instructions and it solved the problem thanks a lot.

YAY!  Glad I could help

---

### Post by Peetke on 2006-09-21
This fixed it for me too.

---

### Post by Mimsy on 2006-09-21
It's not working for me. :(

I downloaded the package, saved it ot desktop and double-clicked. I click "install pacckage" and put in my password, and then I get an error message that says:
> Only one software management tool is allowed to run at the same time. Please close the other application e.g 'Update Manager', 'aptitude' or 'Synaptic' first.

So I tried to find them in the System Monitor. No luck.

Fine, I thought, opened a terminal window, and did "killall" on the processes name in the error message. Still no luck.

I logged out and logged back on. No luck.

I rebooted. No luck.

What is the obvious solution that I'm missing? Help, please.

/Mimsy

---

### Post by Metacarpal on 2006-09-21
If you have Synaptic, Update Manager, apt-get, aptitude, Automatix, EasyUbuntu, or anything like that running, then you can't have another instance of any of the above going at the same time.

If you can't see one running, reboot.

---

### Post by xyverz on 2006-09-21
> **Metacarpal said:**
> ...Just did a search of the boards, and it looks like this is a known problem with a fix:

w00t!  Thanks for finding this.  This makes me haapy. :-)

---

### Post by Mimsy on 2006-09-21
> **Metacarpal said:**
> If you have Synaptic, Update Manager, apt-get, aptitude, Automatix, EasyUbuntu, or anything like that running, then you can't have another instance of any of the above going at the same time.

If you can't see one running, reboot.

I tried that, but I still get the same error message. I'm confused. :confused: 

/Mimsy

---

### Post by Metacarpal on 2006-09-21
What was the last thing you installed (before Flash), and how did you do it?

---

### Post by Mimsy on 2006-09-21
Hmmm... let me think. As far as I remember, I had installed the KDE desktop environment, to see if it was better at power management than Gnome. I noticed no difference, so I uninstalled all KDE packages, via a tutorial called "pure gnome" or something similar, that I found on Psychocats.net

I had to reinstall Kopete and Amarok and Skype after that, and I got tired of the constant update notifications so I also did all the system updates and the kernel updates. The flah error message started appearing while I ran the updates, so I tried the solution you posted in this thread, to see if I could get flash back.

So whatever causes the problem is probably related to all the changes I made last night.

/Mimsy

---

### Post by Mimsy on 2006-09-21
I found it! I did another forum search, with other keywords, and came across a thread about another problem, with another error message. Since I got this other message when I tried to install through Synaptic, I tried the solution presented in this second thread, and it worked.

I opened a terminal window and put in 
> sudo sed -e 's/multiuser/defaults/' -i /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo dpkg --configure -a

It uninstalled a ton of things, and now flash works! Wohoo! Thanks everyone who figured this out. :)

/Mimsy

---

### Post by Metacarpal on 2006-09-21
Glad you're back up and running, Mimsy!

---

### Post by SubWolf on 2006-09-22
Worked, thanks!

---

