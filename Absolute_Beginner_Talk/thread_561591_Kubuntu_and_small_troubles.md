---
title: "Kubuntu and small troubles"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-09-27
I'm having a little trouble getting Kubuntu right on my second machine. First machine has been running Ubuntu for about a year and I'm comfortable with it as a user.

Install was as server first via mini.iso, then kde-core, then kubuntu-desktop - I wanted to have a look at different things.

I'm definitely having trouble with Nvidia. Card is GeForce2 MX/MX400 so I'm using the legacy driver. I get the Nvidia splash on boot, but I don't get more options for refresh. Refresh did improve slightly, but it's still only 60hz, which is difficult to view.

Also Kubuntu doesn't detect my monitor, and sets it as Generic. My IBM G78 isn't on its list, so I can't set that manually. Ubuntu doesn't seem to have a list, but the monitor is recognized under nvidia-settings, so that was never a trouble. (Same monitor for both - I use KVM.)

If I set the monitor as Plug'n'Play, restart puts me in 640x480, so back to Generic.

The first time I asked for nvidia-settings, terminal replied that I didn't have it. I installed that, and now I get "ERROR: NV-CONTROL version 1.6 is too old", and nvidia-setting fires up with only options for configuing itself, not the card. I'm guessing that's because I'm using the legacy driver, and not the newer one I'm used to with my GeForce4?

As an Ubuntu user, what I'm looking for is the next step of going to System > Administration > Restricted Drivers Manager, but I can't find anything like that.

The next step appears to be editing xorg.conf as suggested on pages like this one,
[http://www.linuxforums.org/forum/ubuntu-help/77338-kubuntu-6-10-geforce-2-mx-woes.html](http://www.linuxforums.org/forum/ubuntu-help/77338-kubuntu-6-10-geforce-2-mx-woes.html)

...but that seems like dealing with it via the back door. I'm wondering if I'm missing a front-door method for regular users that I should try first?

----

Other oddity is I've lost network by default under kubuntu-desktop. Everything ran fine until restarting X - that's how I was able to install packages. But now I get a broken icon on the toolbar for KNetworkManager. Click it once, then click the network card's name on the little menu to activate, and then fine until next boot. That's strange, and more strange is that's the /only/ way to activate it -- if I try it through Settings->Control Panel->etc, it refuses to work.

The machine has two cards, which shouldn't matter, but perhaps there's a related bug?

----

Finally, a beginner's opinion about Kubuntu for the curious -- it's quite nice, and I already prefer a number of KDE apps on Ubuntu, but Kubuntu just isn't quite as polished for the user as Ubuntu is, and of course there's a mere fraction as much beginner-help online as for Ubuntu.

It's a number of little things that sets that opinion, like the above, and applications like Adept, which is supposed to be Synaptic's "sister" for Ubuntu. It's more like Ubuntu's Add/Remove Applications app, except much slower. The first thing one should do with Adept is use it to install Synaptic, which works fine.

It's also very likely that whatever polish Kubuntu lacks will show up in April when it gets the major upgrade of KDE4 -- so if you're curious, I'd say try it then.

---

### Post by ofb on 2007-09-28
Right then, moving on -- In Synaptic I removed nvidia-glx-legacy and nvidia-settings, and added nvidia-glx, making the Kubuntu setup match what I have on Ubuntu for the newer GeForce4. 

On reboot, I get a different Nvidia splash, and a refresh of 75Hz, but not the 85Hz I have on Ubuntu. Try "nvidia-settings" in terminal, and get the familiar NVIDIA X Server Settings application, which is correctly listing both card and monitor. Hurrah. Set to 85Hz & save.

So I guess a GeForce2 MX/MX400 isn't the sort of "GeForce 2" meant by the info in Synaptic for the legacy driver. Somehow. (Not that Nvidia drivers for Windows aren't full of pitfalls. I learned the hard way to never install newer drivers for either of these cards there.)

No idea what to do about the KNetworkManager glitch yet.

---

