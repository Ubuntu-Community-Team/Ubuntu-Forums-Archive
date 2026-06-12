---
title: "Upgrade your Precise based distro &quot;X&quot; and stay with Precise LTS"
date: 2012-11-12
forum: Any Other OS
---

### Post by Chdslv on 2012-11-12
You have your Precise based 5 year LTS "X" distro, but you don't want to go the new "X" with the Quantal base with only less than 1.5 years already. Some of these "X" distros a spewing out "release candidates," "development releases" with the Quantal, long after Quantal was released--20 days ago.

Examples; 

1) Mint 13 Maya to Nadia. There is no absolute need to wait for Mint 14 as the only things that change would be found in the Nadia repo. All you have to do is change one word in your sources list--Maya to Nadia--and update and upgrade your installation. What would you have? New Cinnamon or Mate with Precise 5 year LTS. If there is another new repo in the future, within this 5 year time, all you have to do is, change the name nadia to the new name and update/upgrade.

2) Snowlinux "cream" to "white"; the same action as above, and you'd have "white" packages, but with the Precise 5 year LTS.

3) Zorin OS - they are not changing their few (five?) "modifications" for few years, even though you can see the "updated" word in Launchpad. Anyway, those are pretty insignificant applications.

4) Pinguy, Luninux, Pear, etc don't have their own repos or packages, so if the users of them likes to stay in the safety of 5 year LTS, thay can do that.

Well, if you want to be in the Quantal,and feel the Quantal expereince, you can do that by downloading and installing the new "X" distros, only you won't have the 1.5 year Ubuntu support, because already 20 days had gone, and by the time the rest of "X" Quantal based distros would be released, there maybe only 17 months or less of *that* support.

Controversial? Maybe...

---

### Post by Chdslv on 2012-11-12
Just to prove what i wrote above.
Here is a screenshot of Linux Mint 13 with Cinnamon 1.6.6+nadia.
You'd notice the lsb-release state thatit is Linux Mint 14 Nadia, while the Installation has Precise Pangolin base!

Now, you'd understand what makes a new "X" distro gets its name, even though in this case, the whole thing was done by Cinnamon Maya changing itself to Cinnamon 1.66+nadia, which rewrote the lsb-release and other files.

That's what happens with Ubuntu based "X" distros, and all they do is change names of repos and upgrade them, only sometimes their applications fail. This Mint 14 Nadia RC is an example. The Cinnamon 1.6.6+nadia is buggy yet. And now, I know what's buggy. Most probably they'd have to do some work with the Nadia apps, before Mint 14 would be released.

Now, if you take Snowlinux 2 "Cream" with Precise and change "wream" to "white" in the sources list, you'd get Snowlinux 3 "White", but with the Precise Pangolin base. **And, with 5 year LTS! **

In Pinguy and Zorin, there is nothing to change to keep the 5 year LTS. Only update and upgrade as it is. Pinguy doesn't have repos/packages, while Zorin's are pretty old!

So much for new releases of Ubuntu based "X" distros!

---

### Post by Chdslv on 2012-11-12
And here is another screenshot of the results of apt-get update of my Precise-Nadia Linux Mint 14!:)

If I want to use Mint, I can keep this updating for next 4.5 years, while Mint 14 Nadia would stop being supported in one year and 5 months!

**So, I shall have the longest supported Mint 14 in the world!**:)

That's why I am more interested in Ubuntu and its derivatives, than all these Ubuntu-clone makers. Actually, they are application makers and sometime desktop environment makers.

The only** fresh wind** is Bodhi, who went in a pioneer way and keep on making packages for it. And, Bodhi won't make another distro until the next LTS. (I hope!)

---

### Post by deadflowr on 2012-11-12
> So, I shall have the longest supported Mint 14 in the world!

Congratulations?

---

### Post by dannyboy79 on 2012-11-12
mixing repos like that is a great way to BORK your system

---

### Post by exploder on 2012-11-12
Technically, this type of upgrading will not give you the same thing as installing a new release. If you look in Synaptic at the installed packages you will find some differences. The dependencies change from Cinnamon 1.4 to 1.6. For example, there are some compiz packages installed in Mint 13 that are not installed in Mint 14. Just changing repos could lead to an unstable system

It is better to wait and install newer versions of Cinnamon and Nemo from the backports repo because the packages are built to work in that particular release. 

Also, if you compare a system that has been upgraded by changing repos you will notice that the system has a lot more packages installed than a clean install. I would rather spend 10 or 15 minutes to install a new release rather than hours cleaning up a mess and fixing things. I just back up my data and copy it into the new install.

These are of course my opinions. If I do not want to reinstall the system for a long period of time I use a distro like PCLinuxOS because it is a rolling release by design. Doing a lot of changing to an LTS release defeats the whole purpose of it's design.

---

### Post by Chdslv on 2012-11-12
> **exploder said:**
> Technically, this type of upgrading will not give you the same thing as installing a new release. If you look in Synaptic at the installed packages you will find some differences. The dependencies change from Cinnamon 1.4 to 1.6. 

Did you look at the screenshots? What Cinnamon do you see there?

> It is better to wait and install newer versions of Cinnamon and Nemo from the backports repo because the packages are built to work in that particular release. Nemo is there, pal. I am not that keen about Nemo. I prefer Nautilus 3.6.1.
The packages built for Cinnamon-1.6.6+nadia are in the repos, and **that's all** you get in the "new" Mint 14, other than 12.10 Quantal. *Did I say anything about Quantal, or 5 year LTS with Precise? *

> Also, if you compare a system that has been upgraded by changing repos you will notice that the system has a lot more packages installed than a clean install. Did you read the topic subject? I am talking about 5 year LTS with Precise and also with Cinnamon-1.6.6+nadia! Did you see the name change to Linux Mint 14 Nadia done by the Cinnamon-1.6.6+nadia?

> I would rather spend 10 or 15 minutes to install a new release rather than hours cleaning up a mess and fixing things. I just back up my data and copy it into the new install.Please read the topic subject! This is not about installing the "new release" with Quantal, okay?:)

> These are of course my opinions. If I do not want to reinstall the system for a long period of time I use a distro like PCLinuxOS because it is a rolling release by design. Doing a lot of changing to an LTS release defeats the whole purpose of it's design.Well, I am talking only about Ubuntu clones! The Precise LTS was there and I didn't change that, I only changed the name maya to nadia....Apt did the rest of the work.:) 

While, Mint would release the next Mint 15 and still won't cover the 5 year LTS, my installation would be supported by Ubuntu! 

Do you think, the Mint devs are upgrading the Maya repo, or only working on the Nadia repo? Do you think they are interested in the 5 year LTS for Mint 13 Maya, or in churning out new numbers 14, 15, 16 etc? Its all about profit, pal! 

They need Ubuntu to come out with new releases every six months, all these Ubuntu clone makers!:)

I'm not going to use this Precise-Mint 14 Nadia, but make a live distro out of it and keep it away until the Mint 15 -girl name- repo would show up. *I have no other use for Mint releases at all. *I can take Quantal and make myself a Mint 14 any time, just adding the Nadia repo and update, upgrade. By the way, I have done that, all the way to Raring. My post is somewhere in Ubuntu Forums, most probably in the Ubuntu+1.

By the way, my install doesn't differ at all from the future Mint 14 Nadia, except mine is based still on Precise Pangolin.

Here's another screenshot.

I am not saying only about Mint, but about all Ubuntu based "X" distros/OSs. I have done an upgrade on Peppermint 3, Zorin 6, Snowlinux, Pinguy, Luninux to Raring. Now, I have done Mint 13 with Precise to Mint 14, but without Quantal.

By the way, I don't how to program in Python, or any such language, so I am not geeky.

See, Linux is all about files!

Good day!
Wish you guys nice experiences!

PS: ZevenOS had been discontinued, so I made this;
[http://ubuntuforums.org/showthread.php?t=2082728](http://ubuntuforums.org/showthread.php?t=2082728) 
and it is done as a tribute to *that* unique distro and its developer Leszek Leszner!

---

### Post by Chdslv on 2012-11-12
Installed Linux kernel 3.7 to my Precise-Nadia Mint 14.
Every application works well. No crashes yet...:)

So, when Mint 14 finally comes out, I'd have a more modern installation than the Mint devs. And, if someone says that I don't have Quantal base as it would be in the upcoming Mint 14, I'd need about few minutes to make it Quantal. Of course, after I make a live iso.

I am waiting for the last day before the release to make that live iso. It would be updated until then.:)

You can experiment with other Ubuntu clones, if you like. I don't want to do that as I won't be using any of them. This one I did for fun!:)

I think, I proved a point--Linux is all about files.

Good day!

---

### Post by wojox on 2012-11-12
Have you only been doing this with Ubuntu based distros?

---

### Post by Chdslv on 2012-11-12
> **wojox said:**
> Have you only been doing this with Ubuntu based distros?

Yes, of course!:)

Mint is Ubuntu based...

---

### Post by Chdslv on 2012-11-13
Okay, I made a live iso out of the installation, and then moved the repos to Quantal and updated and upgraded it. Here is the screenshot of that distro updated to Quantal. I have already upgraded it.

This is just to show you that you don't really need to download an Ubuntu based new "X" distro. If you have one, and you want to use it without losing all the apps and tweaks you had mede, you could just change the name of the repos and update and upgrade it to the new state, even better than the new "X" distro release. :)

Sometime later, I'll move this to Raring, of course after making a live iso. So, I'd have Precise-Nadia LTS, Quantal-Nadia and Raring-Nadia live isos. It is pretty simple!:) 

Of course, if you are worried that you might make some mistake--Apt does all the work out of the way--you should try on a free partition and/or back up. If you are observant enough, there won't be any hiccups. 

Don't believe, just because I say this, or the devs say something else, but you should decide for yourself, what's best. 
What fun, if you don't make mistakes and then solve the problem!:)

Apt is a great application, which solves a lot for you, but as it can't think as humans do, the thinking part is yours!

Have a great day!:)

---

### Post by kansasnoob on 2012-11-13
> **dannyboy79 said:**
> mixing repos like that is a great way to bork your system

+1!

---

### Post by Chdslv on 2012-11-13
> **kansasnoob said:**
> +1!

If you are not observant enough!
And, if you are fearful...

---

### Post by guimaster on 2012-11-14
I want to subscribe to this thread, as I find this topic very interesting. :popcorn:

So, you keep the Precise repos, but update to the latest Linux Mint repos? Will this really work for release after release after release without "borking" a system? Opinions? It would sure be very cool if it worked because Cinnamon keeps improving constantly, and who really wants to reinstall every 6 months?

---

### Post by Chdslv on 2012-11-14
> **guimaster said:**
> I want to subscribe to this thread, as I find this topic very interesting. :popcorn:

So, you keep the Precise repos, but update to the latest Linux Mint repos? Will this really work for release after release after release without "borking" a system? Opinions? It would sure be very cool if it worked because Cinnamon keeps improving constantly, and who really wants to reinstall every 6 months?

Well, it worked for me.:) I'm not that keen about Cinnamon anyway. I did that for fun.

If you've downloaded the Mint 14 Rc, you'd notice in uname -a that the day the Mint devs downloaded the Quantal daily or whatever is before the release of Quantal. It is just the same thing as I did. When you have Quantal and add the Nadia repos, and update and dist-upgrade, you'd get Mint 14. Then, if you want, you can add the wallpapers etc, which comes down with Cinnamon-1.6.6+nadia from Mint Nadia repos.

This Cinnamon-1.6.6+nadia takes over your Quantal installation and rewrite the lsb-release etc. That's all in this Mint 14, or the one before--Precise+maya repos.

There is a bug in Cinnamon-1.6.6+nadia, and that's why it is still RC and most probably, when they release Mint 14 final, it'd have that bug(s). 

If you want to move to Quantal or Raring from Precise with Cinnamon-1.6.6+nadia, you'd also get a connection problem, which can be solved by sudo dhclient eth0.

If you want the 5 year LTS of Precise, you don't have to download Mint 14, but take your Mint 13 Cinnamon and change the name of the Mint repo from maya to nadia. 

You update it and then dist-upgrade it. And to be on the safe side apt-get install cinnamon. You can do that with Ubuntu Precise or any other derivative and even over the minimalist Bodhi. Isn't it really strange about Ubuntu clones?

I really like Bodhi, as Jeff had done very good job of stripping Ubuntu and adding Enlightenment, his own way. 

My new EasyPeasy, I am trying to push to Precise, but at this moment there is a slight problem, but I'd overcome that. If one is not a geek, its easy to experiment, right?:)

Just a few days ago, Distrowatch announced a new respin of Peppermint 3, but I had pushed it to Raring some weeks ago, and I sent a email to the developer immediately.

My post on Peppermint-Raring is somewhere here. Its just fun! Real fun!:)

Good day and happy experimenting!

Take care!

---

### Post by critin on 2012-11-14
Hey, Chdslv.

It is fun to experiment with different OS's if you are experienced enough to fix them when they break.  

Just be sure and make yourself available when a bunch of inexperienced users start posting about how 'ubuntu' broke their system when they tried to do this.  I wish you wouldn't make it sound so easy and foolproof, because a lot of people will be trying this.

Can't you put a disclaimer or something in your posts?  :(

---

### Post by kansasnoob on 2012-11-14
> **critin said:**
> Hey, Chdslv.

It is fun to experiment with different OS's if you are experienced enough to fix them when they break.  

Just be sure and make yourself available when a bunch of inexperienced users start posting about how 'ubuntu' broke their system when they tried to do this.  I wish you wouldn't make it sound so easy and foolproof, because a lot of people will be trying this.

Can't you put a disclaimer or something in your posts?  :(

+1!

Personal experiments are great but they shouldn't be presented as safe and sane procedures when they're clearly NOT!

When Precise was still in development there were many questions asked about why Lubuntu only had 18 months of support versus Ubuntu's 5 years, and versus Xubuntu's 3 years of support.

The basic question was, "wouldn't I still have 5 years of support if I just started with Ubuntu and added the DE of choice"?

The overwhelming response from the security team was "NO"!

---

### Post by Chdslv on 2012-11-14
> **critin said:**
> Hey, Chdslv.

It is fun to experiment with different OS's if you are experienced enough to fix them when they break.  

Just be sure and make yourself available when a bunch of inexperienced users start posting about how 'ubuntu' broke their system when they tried to do this.  I wish you wouldn't make it sound so easy and foolproof, because a lot of people will be trying this.

Can't you put a disclaimer or something in your posts?  :(

**This is not an experiment, but a highly thought out venture!**

There won't be a disclaimer, as it is your own computer/laptop and your own free partition you install and "play" with the distro.

I'm experienced **in life**, living a long one. I am not a geek, I can't write in Python. Yet!

One is given a mind, and thoughts are made in the mind, and thoughts made to action, makes things. (Not my words, but Gautama Buddha's 2600 years ago! Dhammapada.)

I moved my Pepermint 3 to Raring and informed this forum, and the developer by email, the result is obvious--a "new" Peppermint 3 was announced on 13th November. I moved Mint 13 to Raring with Nadia, making it 14 and 15 alphabeta, and informed this forum and his forum, and emailed the Mint "root" and the result was obvious--a buggy Mint 14RC was announced on 11th November. The final release day is "when its ready." The Cinnamon-1.6.6+nadia is somewhat buggy, and that's the reason of the delay of the final release.

I can tell you how to make Snowlinux "White" from "Cream" and also how to make Mint 14+, Pinguy 12.10 or 13.04, Luninux 12.10 or 13.04, ZorinOS 7 or 8, etc--the template is the same and its Apt working, and my thoughts. You can make all these from Precise and/or Quantal, without downloading these remixes.

I like Peppermint 1, 2, 3 Ice etc, and I wanted to help the developer. I want Peppermint 4, 5, 6 to come, for it is a very good OS!

Mint is arrogant, and how far the development of Cinnamon would go? Mate would go? No further than the Gnome 2 level and it'd stop. Ubuntu did a very good brainstorming and made Unity, which would grow and grow, and later there would be something new. It didn't go the Gnome 3 way, but used the base. *That brainstorming was brilliant!*

With Ubuntu, I can hold onto 5 year LTS Precise and make a Mint, or a Peppermint or even a unique ZevenOS, and an EasyPeasy. I have already moved EasyPeasy to Oneiric, very stable, and to Precise, a bit buggy with the Precise base, *but not* the EasyPeasy packages. Precise Pangolin had moved few steps towards the Gnome3 way, and the problems. 

No pal, I am not putting a disclaimer, as it works. Its your computer, your free experimenting partition, so why not work on that?

Have a good day!:)

Its raining here in Sri Lanka and cold as in autumn in Europe!

Take care!

Ch

---

### Post by Chdslv on 2012-11-14
> **kansasnoob said:**
> +1!

Personal experiments are great but they shouldn't be presented as safe and sane procedures when they're clearly NOT!

When Precise was still in development there were many questions asked about why Lubuntu only had 18 months of support versus Ubuntu's 5 years, and versus Xubuntu's 3 years of support.

The basic question was, "wouldn't I still have 5 years of support if I just started with Ubuntu and added the DE of choice"?

The overwhelming response from the security team was "NO"!

That's your opinion, not mine pal!

**This is not an experiment, but a well thought out action.** And, every respin works very well!

Security team?! I don't see a security team in and around my laptop, or in the partitions I use. Its only me and my laptop!

Have a good day!:)

---

### Post by critin on 2012-11-14
>  I wanted to help the developer. I'm not saying it can't be done, I am saying it shouldn't be done unless a user is comfortable with the system and is sure they can fix it when it goes wrong.   Or if they don't care if their system breaks, some don't because testing is helpful over all.

Developer's teams have their own forum, brainstorming has their own forum.  Testing is called 'Testing' so anyone who wants to test knows there may be consequences--and it has its own forum.  
Bottom line is a user should be aware this is not the standard upgrade and they are being used as 'testers'.

Besides, not many 'buntu'ers stick with the same version for 5 years anyway.    How boring!
Look at the forums, users are upgrading to 12.10 before the ink got dry on 12.04.   Many are raring to install 13.04.  6 months is too long.

---

### Post by Chdslv on 2012-11-14
> **critin said:**
> I'm not saying it can't be done, I am saying it shouldn't be done unless a user is comfortable with the system and is sure they can fix it when it goes wrong.   Or if they don't care if their system breaks, some don't because testing is helpful over all.[/Quaote]

It can be done. Period!
You don't break your system, if you go wrong, but your installation in your free experimenting partition. :)

> Developer's teams have their own forum, brainstorming has their own forum.  Testing is called 'Testing' so anyone who wants to test knows there may be consequences--and it has its own forum.

If you have the Mint 14RC, check uname -a and notice the day of their download. Is it before the official release of Quantal or after? 
  
[Quote]Bottom line is a user should be aware this is not the standard upgrade and they are being used as 'testers'.

It is the standard way of upgrading. Check the date in uname -a of you r Mint 14Rc or Snowlinux "White" or any other Ubuntu-remix. 

> Besides, who ever sticks with the same version for 5 years anyway?   How boring!

There are people, who need 5 year LTS. They cannot afford to re-install every few months.

> Look at the forums, users are upgrading to 12.10 before the ink got dry on 12.04.   Many are raring to install 13.04.  6 months is too long.

I am one of them! Read my other posts in this forum. I moved to Raring, even before they announced its availability in the repos. You'd find that in one of my posts.:)

Its only a free partition, so why not "experiment?"
All, I wanted to prove is that you don't need to download every "X"Ubuntu clone, but just change that developer's repo, or packages and update and dist-upgrade.

Good day!

---

