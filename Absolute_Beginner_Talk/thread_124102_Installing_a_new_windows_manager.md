---
title: "Installing a new windows manager"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by NewGroove on 2006-01-31
Hi there,

I'm new to Ubuntu (Breezy Badger) but not new to computers. So far I'm loving the Linux life **much **more than the *Winbloze *world. I've noticed that my older Dell 8000 w/ 256mb Ram and an 850mhz Pentium III is running a little sluggish with Gnome. I've read about alternate windows managers like Xfce and IceWM... wondering if these would help save memory resources for other programs to use? And how in the world would I go about installing Xfce and then uninstalling Gnome?? Another silly question: If I uninstall Gnome and use another windows manager, gosh does that mean it's not technically Ubuntu anymore? Thanks *very much* for your help!

---

### Post by mcduck on 2006-01-31
If you like Gnome, you can try this trick to make it lighter:

1. Open Applications/System Tools/Configuration Editor
2. Browse to apps/metacity/general
3. Select 'reduced_resources'

If that's not enough, installing XFCE is very easy.

1. Make sure you have universe and multiverse repositories enabled. [http://makuchaku.info/amnesty/#extrarepositories]("http://makuchaku.info/amnesty/#extrarepositories")
2. Open terminal (/Applications/Accessories/Terminal)
3. Run 'sudo apt-get install xubuntu-desktop'

Then log out of Gnome, click 'session', select 'XFCE' and log in. You will be asked if you want to make it your default or just use it this time.

It's technicaly still Ubuntu, but you can call it Xubuntu if you like ;)

---

### Post by NewGroove on 2006-01-31
Thanks! I know these are lists of possible packages you can install but wasn't sure how to use them, so I appreciate the link. I'll try it when I get home.

---

### Post by mcduck on 2006-01-31
[QUOTE=NewGroove]Thanks! Umm, how do you make sure you have universe and multiverse repositories enabled? I know these are lists of possible packages you can install, but not sure where to find them or how to use them... appreciate your help.[/QUOTE]
I just tought that you might need help with repositories, and edited the post. I guess I wasn't quick enough :D

You might also want to have a look at [Source-O-Matic]("http://www.ubuntulinux.nl/source-o-matic").
It will create you a nice sources.list that you can copy to your /etc/apt/sourcest.list file. Include security updates, of course, and then packages for both Ubuntu Supported and Ubuntu Community Supported.

You may also add some extra repositories available, for example Open Office 2 or PLF repository that has codecs and other useful stuff. 

Then run 'sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup' and 'sudo gedit /etc/apt/sources.list', replace everything with the text Source-O-Matic gave you and save.

Run 'sudo apt-get update' after changing your sources.list. This will tell apt to check what packets are available in repositories.

---

