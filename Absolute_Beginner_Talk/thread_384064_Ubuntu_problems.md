---
title: "Ubuntu problems"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-14
The ubuntu installation was flawless---and I had my hopes up. Maybe this would be the day of M$ freedom --- YAAAY!!! My dreams really *had* come true. Then . . .

Can't untar folders even though all appropriate software was applied --- folders remain tarred, can't install.

Unsupported hardware --- yes I downloaded the appropriate drivers, but my printer is connected via NIC to NIC without a domain. That's not an option in the available driver installation. They want USB, LPT1, serial 1, serial 2. No option for NIC to NIC without a FQDN. I have the MAC address for the printer, but ...

Yes, over the past few days I've done a little reading, but have yet to be able to navigate the directory tree from the prompt. I'm familiar with DOS and can actually get around readily in that OS, however in ubuntu cd.. does not regress up the tree as described in the Linux tutorials. Yes, I can navigate to other folders using cd [full path], but the other commands (pwd, and etc) don't seem to function as described.

I understand the "free" software concept, and appreciate the work done in the community to maintain that. I have always paid $$ for "free" downloads, shareware, etc. It's my moral obligation. However, it would seem that there should be an easier, standardized way for *all* applications to install. Whether a clickable icon or from the prompt -- just type "install.run" or whatever, and the OS would be smart enough to unzip, untar, and install the app to the correct folder with all libraries intact. Backward compatability should not be a problem if all libraries are packed with the app.

If there are licensing issues preventing distrubution of various plugins intact with the OS that's fine, but make all currently popular (like Lame and the ubiquitous MP3 and other audio/video plugins) readily available and installable with a link on the Ubuntu page that says something like "Due to licensing issues product XYZ cannot be bundled with this OS. You will need this package to make everything work right."

Yes, keep the app source open and available for development, but have a compiled, ready-to-use version also readily available. I downloaded WINE --- the only way to get it is in the uncompiled source format. Since I know nothing about compiling it will be a long time before I can use that app --- or any of the Windows apps for which I have not yet found a suitable Linux replacement that will read my existing files (ie. Quickbooks).

This is not the end of my search for something non-M$. With the ease of initial Ubuntu installation and perfect recognition of all my hardware devices I had really hoped this would be the day. That does not seem to be the case. I suppose the old adage "You get what you pay for" remains true.

Thanks again for all the attempts to correct my problems. Everyone here has been great and helpful. I'm sure I'll try again another time.

---

### Post by charles.g.moore on 2007-03-14
I am a big fan of using VMWare for all of those crappy little windows apps that I can't seem to part with like quickbooks, etc...

You can find it at [www.vmware.com](www.vmware.com)

As far as installations are concerned I know that you can write (or d-load) scripts which can do all of the tar-make-make installs for you, getting them to dump into the right directories im not sure of.

When you are untarring folders are you doing it from the command line?

I hope that you keep chipping away at your problems with ubuntu, when you finally do get it running you will be happy you're free from windoze

Good luck and happy posting...

---

### Post by brettg on 2007-03-14
<snipped almost trollish rubbish>

    "Can't untar folders even though all appropriate software was 
      applied --- folders remain tarred, can't install."

You need to provide more info than that if you want help, that is if you actually want help.

Vague assertions of "it doesn't work" do not cut it.

I'm gonna ignore the rest of your post because it is basically just a rant. 

Just remember, you are entitled to a FULL REFUND of your money at any time. You don't even need to ask for it.

If you decide to continue using Ubuntu or any other Linux, I suggest you ask your questions in a less hostile manner and provide more relevant details so we VOLUNTEERS can attempt to solve your problem for you.

---

### Post by maniacmusician on 2007-03-14
lwalper; you're creating too many threads :) I've answered your "Too bad Ubuntu doesn't work" thread, and a couple of other ones as well. Please read them.

There are a few things that may not work, but you've got to decide how much you can sacrifice and how much you can't.  As charles.g.moore has said, Virtual Machines are a great solution if you've got a few things that don't work but still want to make it work (though I think VirtualBox is a better program for doing it; [http://www.virtualbox.org](http://www.virtualbox.org) ). As long as you have relatively recent hardware and an abundance of RAM, VM'ing shouldn't be a problem.

For your quickbooks thing (that's a financial app, right?) check this thread: [http://www.ubuntuforums.org/showthread.php?t=350336](http://www.ubuntuforums.org/showthread.php?t=350336) I haven't read it, but it may name an app that you can use. If not, you can try using a Virtual Machine to use windows for things like that. And if not that, then I guess you must go back to Windows :(

---

### Post by Kay The Bantu on 2007-03-14
Hi I know the switch can be hard (brutal in your case) but for the basics

1. filename.tar go to the command line and  tar -xvf <filename>.tar this will extract all contenets to a folder, in that folder (still in command line) do the following
   ./configure
   make
   make install 
   make clean(optional)
and voila

2. as for running windows apps with wine in the configuration gui(command line type winecfg) there's a section for dll overrides if that's too much you could try vmware or crossover(commercial)

Take your time with it goodluck

---

### Post by undertakingyou on 2007-03-14
> **lwalper said:**
> The ubuntu installation was flawless---and I had my hopes up. Maybe this would be the day of M$ freedom --- YAAAY!!! My dreams really *had* come true. Then . . .


Sounds like your mind is already made up.  Even if we could fix all the problems, there would always be a "Then . . ."

---

### Post by silhouette on 2007-03-14
> **lwalper said:**
> Yes, over the past few days I've done a little reading, but have yet to be able to navigate the directory tree from the prompt. I'm familiar with DOS and can actually get around readily in that OS, however in ubuntu cd.. does not regress up the tree as described in the Linux tutorials. Yes, I can navigate to other folders using cd [full path], but the other commands (pwd, and etc) don't seem to function as described.

That's because it's

```
cd ..
```

Notice the space.

I don't know why "pwd" wouldn't work, but as far as I know "etc" isn't a program.

> However, it would seem that there should be an easier, standardized way for *all* applications to install.
There is, it's called the package system. You can use a GUI like Synaptic or the command-line. Dependencies are automatically sorted out and selected for installation if necessary. When you remove a package, all files under that package that were installed are removed.

Oh and compiling really isn't as hard as it sounds. Most of the time any libraries you need are in the package repositories.

> If there are licensing issues preventing distrubution of various plugins intact with the OS that's fine, but make all currently popular (like Lame and the ubiquitous MP3 and other audio/video plugins) readily available and installable with a link on the Ubuntu page that says something like "Due to licensing issues product XYZ cannot be bundled with this OS. You will need this package to make everything work right."
They ARE readily available, and they may not be on the front page but they're [in the wiki](https://help.ubuntu.com/community/RestrictedFormats), which is conspicuous enough. As for more conspicuous ways of letting users know what plugins are needed within Ubuntu, Feisty is supposed to feature a new mechanism to handle that. So stuff like you mention is on the way, it just takes time.

> Yes, keep the app source open and available for development, but have a compiled, ready-to-use version also readily available.
Again, package system...

> I downloaded WINE --- the only way to get it is in the uncompiled source format.
No, I don't think so. There's a dedicated repository that holds the latest version. See the [wiki page on Wine](https://help.ubuntu.com/community/Wine).

> Thanks again for all the attempts to correct my problems. Everyone here has been great and helpful. I'm sure I'll try again another time.
The first time I tried Linux I didn't like it.

The second time I tried it I was more familiar with it, but I still didn't like it.

The third time I tried it I decided I would just take the plunge. I wasted a lot of time at first researching how to get things compiled and drivers installed, and borking my system. It took me about three months to really get going.

So perhaps when you come back you'll feel more open to Linux.

---

### Post by lwalper on 2007-03-14
I'm reading the Wine Community Documentation -- it tells me to add a repository, which I did in the Software Sources/Third Party box using the address given in the documentation (deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main). When I click the "Update" button I get the following error:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by maniacmusician on 2007-03-14
> **lwalper said:**
> I'm reading the Wine Community Documentation -- it tells me to add a repository, which I did in the Software Sources/Third Party box using the address given in the documentation (deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main). When I click the "Update" button I get the following error:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
Yup, that's normal. This is because the WINE repository is a third-party repository, so Ubuntu is smart enough not to trust it by default. To get it to trust the WINE repository, it needs a GPG key that both your computer and the server will have. That way, they know that the computer they're talking to is safe. To find out how to do this, you just had to look around. I just went to winehq, Wine Wiki, Scroll down to User Area, and there it was [http://wiki.winehq.org/GPGKey](http://wiki.winehq.org/GPGKey)

Anyhow, it's fine. You'll get the hang of this sort of stuff after a little while. What the instructions on the page say to do are enter the following commands:

> wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) 
That downloads the GPG key from wine's website
> gpg --import 387EE263.gpg
that imports the gpg key into your system
> sudo apt-key add 387EE263.gpg
that adds the key to "apt", which is the basic package manager for ubuntu. It keeps track of what you have installed, and allows to install stuff. It's the interface that needs to trust the wine servers.

After you do that, you can then update without problems.

There's a graphical way to do this as well, but I don't recall what it is. Trust me, even though you may be repulsed by it, the command line is much faster and more efficient. in **most** cases. There's a few situations when using a GUI is more efficient.

---

### Post by lwalper on 2007-03-14
Thanks maniacmusician. I appreciate your encouragement. Maybe this thing will finally come together. I've just got to get productive -- and quickly -- there's a web page that needs editing TODAY.

---

