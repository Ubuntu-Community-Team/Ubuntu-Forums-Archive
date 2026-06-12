---
title: "Mint 14 Nadia with Gala and Slingshot, and without Cinnamon"
date: 2012-12-03
forum: Any Other OS
---

### Post by Chdslv on 2012-12-03
Yesterday, I wrote about Mint 14 becoming, Mint Elementary, but the thread had been moved to "December screenshots." 
[http://ubuntuforums.org/showthread.php?p=12386212#post12386212](http://ubuntuforums.org/showthread.php?p=12386212#post12386212)

I thought the photos would say more than words, so the screenshots. 

I had made SolusOS 2 Alpha, a Debian distro to take in Ubuntu ppas and work with Gala and old Slingshot. I like SolusOSvery much, and that's why I did that.

This time, I took Mint 14 and made it work with Gala and new Slingshot of eOS and while still working in "Cinnamon session" work without Cinnamon. I am not very keen on Mint. Now, it is nothing, but Cinnamon and Mate. The engine is Ubuntu Quantal. It is a simple Ubuntu based distro.

So, this Mint 14 is **not** Cinnamon, **not** Mate, but Elementarished Mint. 
And, if I drop all the Mint applications, it becomes another Ubuntu-Elementary distribution.
If I install all the new applications of eOS, it becomes Elementary Luna, even with the shiny greeter of eOS Luna.

Elementary Luna has a lot of potential, at least their applications, base and especially the window manager - Gala!

Note the memory usage, **without** Cinnamon! 

Of course, I didn't want to go through the hassle, as I wouldn't use Linux Mint for daily work. 

Good day!

---

### Post by zeusalmighty on 2012-12-05
Could you go about explaining how you did something like that?

As far as I've tried, using the elementary OS daily ppa and installing pantheon-desktop results in really nasty effects(switchboard plugs don't show up, crashes, theme is all weird).

Is there any way to get a Gala WM with the latest slingshot/plank/switchboard in Lunix Mint 14/Ubuntu 12.10?

---

### Post by Chdslv on 2012-12-05
> **zeusalmighty said:**
> Could you go about explaining how you did something like that?

As far as I've tried, using the elementary OS daily ppa and installing pantheon-desktop results in really nasty effects(switchboard plugs don't show up, crashes, theme is all weird).

Is there any way to get a Gala WM with the latest slingshot/plank/switchboard in Lunix Mint 14/Ubuntu 12.10?

True enough, it gives nasty effects, if you install the whole thing.

If you are interested having only the "Elementary experience", then you need only Gala. You don't need to install the Pantheon desktop.

1) Add the Elementary daily ppa to your sources.list and update.
2) Install Gala; sudo apt-get install gala
3) Download the Slingshot launcher and Plank as deb packages and 
dpkg -i "the deb package" or,
sudo apt-get install slingshot-launcher plank

Then, install Gnome-panel, if you want the right clicking, to use it as the panel.

Then, change the cinnamon to gala in the cinnamon.session, and/or gnome-wm to gala in gnome-classic.session. Add gala, panel to required components.
Changing Cinnamon to Gala is little tricky but can be done.

In Mint, in the xsessions, in the cinnamon.desktop, Cinnamon is directed to /usr/bin/cinnamon, and that could be changed to /usr/bin/gala

Check these places; /usr/share/xsessions and /usr/share/gnome-session/sessions and you'd see what to do.

For example;
[GNOME Session]
Name=Display Manager
RequiredComponents=gnome-panel;gala;gnome-settings-daemon;
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=gala

Both Cinnamon and Pantheon are memory hogs, but in this case, Mint with Gala brought down the memory usage. Mint Cinnamon is 3 times more.

I did this for fun. I am not using Mint at all.  

You can achieve this Gala experience much better in Ubuntu Precise or Quantal, and even in Raring

---

### Post by Chdslv on 2012-12-05
I'm bit tired today. I'd give you a step by step instructions to build your Gala experience for Quantal tomorrow, oaky?

---

### Post by zeusalmighty on 2012-12-05
Hmm, no time for me to test it now but I'll get to it tomorrow.

A couple of questions:

- Why would ubuntu Quantal give better results instead of Mint?
- Why not install Wingpanel while you're at it?
- Does Switchboard work?
- Does the GTK theme work correctly? As far as I know there are some incompatibilities with Gnome 3.6 (so I was told).


I'll also try to find a way to create a custom new session rather than mess up the one I'm currectly running.


PS. I see how you got about to get that working. What I'm trying to see is if there's a way to use the nice and fast pantheon suite (switchboard/plank/slingshot/wingpanel/gala) on a distro that is kept updated all the time (such as Ubuntu). I'm just not that happy with how eOS is kept an ubuntu version back for providing what appears to be *just* a DE.

---

### Post by Chdslv on 2012-12-05
> **zeusalmighty said:**
> Hmm, no time for me to test it now but I'll get to it tomorrow.

A couple of questions:

- Why would ubuntu Quantal give better results instead of Mint?
- Why not install Wingpanel while you're at it?
- Does Switchboard work?
- Does the GTK theme work correctly? As far as I know there are some incompatibilities with Gnome 3.6 (so I was told)

PS. I'm just not that happy with how eOS is kept an ubuntu version back for providing what appears to be *just* a DE.

1) Ubuntu Quantal is faster than Mint. Cinnamon in Mint is just adding bloat to it. Download Quantal mini.iso and install xinit and add Mint nadia repos, update and upgrade, and you are in "Mint 14 Cinnamon." You can then add any app you like. Anyway, Cinnamon is a memory hog.

2) Wingpanel is unconfigurable. It is a copy of Gnome-shell panel, whether it was written in Vala or not. The Slinghsot luancher points upwards and to the left top corner, whatever dock/panel you use. You can link the /usr/bin/slingshot-launcher to any place and click from there and it comes up in the same place.  

3) I didn't try Switchboard. I had no need to, as I wanted only to get the Slingshot launcher working. The rest, even Gala WM is of no use to me. I don't want the "new" Slingshot, if it won't have transparency. 

4) GTK themes work superbly.

**Both** Cinnamon and Pantheon are DEs. You can install them or parts of them in any distro. All these developers do is to "glue" the other applications to these DEs, which some of us don't want. I dissect them to get what I want. I don't want neither Plank or Wingpanel as they are unconfigurable. docky is more responsive than Plank. The Wingpanel is just a waste of the screen area--has no value other than the "applications" button. I have placed the old and the new Slingshot in many distros, even in a Debian one. I like the old Slingshot. 

If I am to choose between Cinnamon and Gala, I'd choose Gala. You saw the memory usage.
I'd always choose Ubuntu Precise, Quantal or Raring, and *never* use Mint as a base. What for? Ubuntu is the base and Cinnamon is the DE out of lot out there.

Good day!

Ch

---

### Post by Chdslv on 2012-12-06
By the way, if you need only the Slingshot, there is no need to install Gala, but if you install Gala, you'd get transparency, that is for the old Slingshot.
Otherwise, just add;

> deb [http://ppa.launchpad.net/elementary-os/daily/ubuntu](http://ppa.launchpad.net/elementary-os/daily/ubuntu) quantal main  deb-src [http://ppa.launchpad.net/elementary-os/daily/ubuntu](http://ppa.launchpad.net/elementary-os/daily/ubuntu) quantal mainand, 
> sudo apt-get updateand,
> sudo apt-get download slingshot-launcherthen,
> sudo apt-get install libunique-1.0-0then,
> dpkg -i slingshot-launcher_0.7+r303-0+pkg15~precise1_amd64.debthen navigate to /usr/bin and copy the "slingshot" to you desktop, or use "Add to panel" of your panel, if it is the Gnome-classic-panel and click on that, and you'd have the "new" Slingshot launcher appearing at the top left corner pointing upwards.

If you want the "old" one, you'd have to search the Launchpad for that. I forgot where it was. I have downloaded both the 32 bit and 64 bit deb packages.

When you download the Slingshot-launcher or any other deb package, your present installation would choose the 32 bit or 64 bit by itself.

**If you want Gala WM**, you might find some difficulty in installing dependencies, but you keep on trying to install one dependency at a time in the Terminal. And, at one point, you'd be instructed by Apt to use
> apt-get -f installdo that, and all those dependencies would get installed along with Gala.

Then, do the changes as given in an earlier post above in /usr/share/xsessions and/or in /usr/share/gnome-session/sessions in the appropriate ---.desktop and ---.session

Good day!
Good luck!

Ch

---

### Post by Chdslv on 2012-12-06
I have found away to make the Slingshot launcher work without Gala, Pantheon and even libmutter, so you can just throw away Mutter, libmutter and Cinnamon and get your Compiz to work too.:p

Have look here, if you are interested;

[http://main.solusos.com/showthread.php?3176-Ideas-again-for-SolusOS-2-and-further&p=21947#post21947](http://main.solusos.com/showthread.php?3176-Ideas-again-for-SolusOS-2-and-further&p=21947#post21947)

Good day!

Ch

---

### Post by zeusalmighty on 2012-12-07
Well, I've tried creating the session but nothing works. The gala session fails. Anyways, I'd love to see a tutorial at some point but for now I'm calling it quits. Yes, Cinnamon is a bit heavier but I think it's a good blend between resources requirements and features.

I'll just till this whole DE war thing is over. Hopefully we'll be left with better and faster DEs in the end.

---

### Post by screaminj3sus on 2012-12-08
gala is a very nice window manager. Nice effects, lightweight, and stable. I recently started using it with xfce myself, works much better than compiz. I'm also using plank, isntalled them both from the elementary daily ppa on xubuntu 12.10, working very well.

here's my current desktop:

[[img]http://en.zimagez.com/miniature/galaxfce.png[/img]](http://en.zimagez.com/zimage/galaxfce.php)

---

### Post by zeusalmighty on 2012-12-09
> **screaminj3sus said:**
> gala is a very nice window manager. Nice effects, lightweight, and stable. I recently started using it with xfce myself, works much better than compiz. I'm also using plank, isntalled them both from the elementary daily ppa on xubuntu 12.10, working very well.

here's my current desktop:

[[img]http://en.zimagez.com/miniature/galaxfce.png[/img]](http://en.zimagez.com/zimage/galaxfce.php)

Could you explain how you built your session in xfce? Although from I got, it shouldn't really matter if it's xubuntu or ubuntu or even mint.

---

### Post by screaminj3sus on 2012-12-09
> **zeusalmighty said:**
> Could you explain how you built your session in xfce? Although from I got, it shouldn't really matter if it's xubuntu or ubuntu or even mint.

Should work for any xfce distro (except the ppa part only works on *buntu based distros obviously). Didn't have to do any major tweaking to get gala as the window manager for the session. Just:

**Add the elementary daily ppa and install gala**

sudo apt-add-repository ppa:elementary-os/daily

sudo apt-get update

sudo apt-get install gala dconf-tools

**Set gala as xfce's default window manager**

cp /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

leafpad ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

replace "xfwm4" with "gala"

**Put min/max/close buttons on the right and change decoration theme**

open dconf-editor:

org > pantheon > desktop > gala > appearance

button-layout: :minimize,maximize,close
theme: Greybird

Plank I just added as a startup item in the xfce settings.

---

### Post by Chdslv on 2012-12-09
> **screaminj3sus said:**
> Should work for any xfce distro (except the ppa part only works on *buntu based distros obviously). Didn't have to do any major tweaking to get gala as the window manager for the session. Just:

**Add the elementary daily ppa and install gala**

sudo apt-add-repository ppa:elementary-os/daily

sudo apt-get update

sudo apt-get install gala dconf-tools

**Set gala as xfce's default window manager**

cp /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

leafpad ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

replace "xfwm4" with "gala"

**Put min/max/close buttons on the right and change decoration theme**

open dconf-editor:

org > pantheon > desktop > gala > appearance

button-layout: :minimize,maximize,close
theme: Greybird

Plank I just added as a startup item in the xfce settings.

This is all excellent, but could you do me a favour and start a new thread? I like Xfce, but wouldn't **contaminate** that with Gala or Pantheon, both of which are practically dead areas. That Elementary OS Luna won't come out that quickly and when it does, it'd be **full** of bugs. Xfce, on the other hand does not have bugs!

The applications of Xfce are excellent and they are very well coordinated with the Xfce environment. Xfce allows the user lot of freedom; you can install any other dock/panel and/or any other WM while you are logged in, *for example* you can do compiz --replace. 

When Istarted this thread, I wanted to show how easy to get the so-called, much coveted Elementary experience, but it boils down to **only one **application, the Slinghsot launcher, incidentally wasn't done initially for the elementary OS and the original developer was John Doe.  The developer of the "new" Slingshot is not with the eOS team.

You **don't need** Gala and/or Pantheon to use that launcher. And, there is no need to contaminated the excellent Xfce environment with anything from the elementary OS.

Exactly, about what Elementary distro are you talking about? I have seen/noticed a released distro yet. Oh, there is a Beta? **A beta release after so much hype is nothing!** 
Don't you see it is just advertising, and keeping the hype on?

[B]There is nothing that interesting about Pantheon desktop to contaminate the excellent Xfce environment. 
[/B]
My advice is, if you want this Luna so much, download **the unstable distro** and use it. And, it'd be always unstable!

Both Cinnamon and Pantheon are memory hogs. Plank is just useless too.

Do me a favour and please start a new thread, if you want to contaminated Xfce, okay pal?

---

### Post by screaminj3sus on 2012-12-10
> **Chdslv said:**
> This is all excellent, but could you do me a favour and start a new thread? I like Xfce, but wouldn't **contaminate** that with Gala or Pantheon, both of which are practically dead areas. That Elementary OS Luna won't come out that quickly and when it does, it'd be **full** of bugs. Xfce, on the other hand does not have bugs!

The applications of Xfce are excellent and they are very well coordinated with the Xfce environment. Xfce allows the user lot of freedom; you can install any other dock/panel and/or any other WM while you are logged in, *for example* you can do compiz --replace. 

When Istarted this thread, I wanted to show how easy to get the so-called, much coveted Elementary experience, but it boils down to **only one **application, the Slinghsot launcher, incidentally wasn't done initially for the elementary OS and the original developer was John Doe.  The developer of the "new" Slingshot is not with the eOS team.

You **don't need** Gala and/or Pantheon to use that launcher. And, there is no need to contaminated the excellent Xfce environment with anything from the elementary OS.

Exactly, about what Elementary distro are you talking about? I have seen/noticed a released distro yet. Oh, there is a Beta? **A beta release after so much hype is nothing!** 
Don't you see it is just advertising, and keeping the hype on?

[B]There is nothing that interesting about Pantheon desktop to contaminate the excellent Xfce environment. 
[/B]
My advice is, if you want this Luna so much, download **the unstable distro** and use it. And, it'd be always unstable!

Both Cinnamon and Pantheon are memory hogs. Plank is just useless too.

Do me a favour and please start a new thread, if you want to contaminated Xfce, okay pal?

What the hell are you smoking dude?

1. First of all: I've distro and desktop hopped for many years, all of the desktops have plenty of annoying unfixed bugs, so yes XFCE has bugs too. Off the top of my head: 

thunar randomly doesn't show trash and network locations until you log out and log back in.

Trash will sometimes show as empty on the desktop but full in thunar, or vice/versa.

xfce4-power-manager's automatic screen dimming is totally broken at the moment on 64-bit, I had to build a deb package with a patch to fix that. (and xfce's power manager is just buggy in general)

xfce4-appfinder randomly crashes

etc...

2. pantheon isn't even particularly memory intensive, its actually fairly light.

3. All I'm using is gala and plank, that's hardly all of luna. I'm not using wingpanel, slingshot, or any of the elementary apps. Pantheon and gala are actually quite stable at the moment, its the elementary apps that are quite unstable, and its to be expected, they are all written from scratch and its the first beta release.

4. Using gala is hardly "contaminating" anything. You know why I always use something like gala or compiz in xfce? because xfce's compositor is a piece of crap, because its xrender based and therefore causing video tearing, even in fullscreen video. with gala I can get a tear-free xfce desktop. Don't get me wrong, I like xfce, but xfwm leaves a LOT to be desired. I chose gala because its lightweight and fast compared to compiz and works very well for getting some nice opengl compositing in XFCE. I chose plank because I like how simple it is, I only need a simple dock. Plank is lacking features at the moment, but its stable (the only thing that really annoys me about it at the moment is the broken sorting)

5. I don't give a crap about slingshot, I always use kupfer or synapse. slingshot isn't even a very impressive launcher, its probably my least favorite part of pantheon. slingshot is hardly the "core of the elementary experience" or whatever you are blathering on about.

My post was fairly relevant to this topic, I did something sort of similar to what you did here, except in XFCE.

I'm sorry you are so strangely butthurt about luna taking too long to be released, but there's no reason for your obnoxious unprovoked attack at me, good day.

---

### Post by zeusalmighty on 2012-12-10
Eitherway, I ended up installing the pantheon-session, which works just fine and I realized that any errors in display on wingpanel, only occur because of the GTK 3.4 theme you're supposed to use with wingpanel. If you use anything else, the dialogues (and slingshot) look kinda <snip> up.

As the previous poster said, the two things I'm keeping from elementary are Gala and Plank. Wingpanel/Slingshot have a long way to go.

Thanks for the help!

---

### Post by Losgann Mor on 2012-12-10
> **screaminj3sus said:**
> gala is a very nice window manager. Nice effects, lightweight, and stable. I recently started using it with xfce myself, works much better than compiz. I'm also using plank, isntalled them both from the elementary daily ppa on xubuntu 12.10, working very well.
That looks very nice! Interesting mix of DE's too. I'll be trying this out later myself. Thanks for posting!

> **Chdslv said:**
> I like Xfce, but wouldn't **contaminate** that with Gala or Pantheon, both of which are practically dead areas... there is no need to contaminated the excellent Xfce environment with anything from the elementary OS...**There is nothing that interesting about Pantheon desktop to contaminate the excellent Xfce environment.**...Do me a favour and please start a new thread, if you want to contaminated Xfce, okay pal?
Perhaps you're not a native English speaker, so I would just like to quickly clarify some potentially confusing terminology. The proper term for what the previous poster is sharing with us is "having fun", not "contaminate".

---

### Post by Chdslv on 2012-12-10
> **tmleigh said:**
> That looks very nice! Interesting mix of DE's too. I'll be trying this out later myself. Thanks for posting!


Perhaps you're not a native English speaker, so I would just like to quickly clarify some potentially confusing terminology. The proper term for what the previous poster is sharing with us is "having fun", not "contaminate".

Ha, ha!

I said contaminate, and I meant it.
I like the way this *screaminj3sus* jumping the thread, and the way he is copying and pasting! I am talking about Mint, and he is talking about Xfce. Mint doesn't "produce" a Xfce distro, so why should I be interested? He wants a thread, start one on Xfce.

This *screaminj3sus *had been hopping distros, but I am only dissecting them and making new ones. I am kicking Unity out, Gnome-shell out, Xfce out, Lxde out, and only keeping some parts, mostly a panel to hold the logout/shutoff buttons.

I don't need their panels to, I could do with Awn, Cairo dock or Docky, and the WM could be Compiz, instead of Gnome-wm. Well, I like Openbox, so I might be making a "nimble" distro out of it.

I do hope, this  *screaminj3sus* read the heading--Mint 14 Nadia with....and without Cinnamon. Did I say, Mint 14 without Xfce? I wonder...

Good day, tmleigh!

---

### Post by Chdslv on 2012-12-10
Moderator, could you please close this thread? I don't want it hi-jacked!

---

### Post by nothingspecial on 2012-12-10
Closed.

---

