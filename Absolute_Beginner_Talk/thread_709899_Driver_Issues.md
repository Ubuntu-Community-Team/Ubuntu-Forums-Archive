---
title: "Driver Issues?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by efledderman on 2008-02-27
I recently purchased a **Toshiba A215-25818**, equipped with **Windows Vista**.  This is my _[FONT="Courier New"]first Vista experience[/FONT]_, and though I really don't think it is as bad as it's made out to be, I decided that open source is the way to go.  This would be my _[FONT="Courier New"]first Linux experience[/FONT]_ as well, so I have decided to dual boot.  Everything is going great except my **Ubuntu** _[FONT="Courier New"]will not recognize my[/FONT]_ **Atheros AR5007EG Wireless Network Card**.  I have done many Google searched and seem to find common results for this issue.  _[FONT="Courier New"]Some say[/FONT]_ that I need to download something called **MADWIFI**, which I have and _[FONT="Courier New"]didn't quite understand[/FONT]_ how to install it.  _[FONT="Courier New"]Others say[/FONT]_ to use **ndiswrapper**, which I have also tried and also _[FONT="Courier New"]didn't quite understand[/FONT]_ how to install it.
   
As I mentioned this is my first Linux experience, so I'm sure that this whole command line thing is just over my head until I get the hang of it.  Until I do, does anyone have _[FONT="Courier New"]any suggestions[/FONT]_ on what I could do to fix _[U]my wireless issue_[/U]?  Or perhaps _[FONT="Courier New"]any tips[/FONT]_ on how to get either of the two solution mentioned earlier to work?

I'm a _[FONT="Courier New"]very experienced Windows user[/FONT]_ but am _very interested in trying Linux_ but so far have just _felt dumb_.  Can anyone help?

Thanks in advance...

---

### Post by ryanhaigh on 2008-02-27
You might want to look at ndisgtk which is a nice gui frontend to ndiswrapper and may make things easier for you. You will need to have the universe repository enabled, refer to [this page]("https://help.ubuntu.com/community/Repositories/Ubuntu") for details on doing that. Then you can use whatever method you like to install the software, refer to [this page]("https://help.ubuntu.com/community/InstallingSoftware") for more info on that. Or once you have enabled universe and refreshed just click this link: [apt://ndisgtk]("apt://ndisgtk").

For more info on ndiswrapper and what you will need refer [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by neurostu on 2008-02-27
the easiest way to install madwifi is:

to open a terminal then type exactly:
```

sudo apt-get install madwifi-tools

```
it will prompt you for your password, just type it in. It will then go to the ubuntu servers, download mad wifi and install it along with any other packages it needs to work.

To install ndiswrapper type:
```

sudo apt-get install ndiswrapper*

```

I have never used either mad wifi or ndiswrapper so I can't be more help but these two commands will install both of the utilities that you mentioned above.

---

### Post by ryanhaigh on 2008-02-27
You will also need to enable the universe repositories for neurostus instructions to work.

---

### Post by efledderman on 2008-02-27
I appreciate that feed back, those links help out a ton.  It seems like there are quite a few steps and a lot of ifs and maybe's.  I'm starting to think that this whole thing might not be worth the hassle.  Is this a good taste of what's to come if I choose to continue with Ubuntu?

---

### Post by ryanhaigh on 2008-02-27
Wireless networking is a special case, I myself have NEVER had a single pci/pcmcia/usb wireless card not recognised and working out of the box since I started using ubuntu. Once you get things set up there is a lot less hassle associated with maintenance, you can spend more time being productive or just trying new things.

Im at work at the moment so I can't go through this with you step by step but from what I remember ndiswrapper was actually quite easy and I imagine the GUI makes it even moreso. Enable the universe repo, install ndiswrapper and ndisgtk, find the windows driver files (inf files generally extracted during driver install on windows) and install them using ndisgtk at which point you should have networking. You then want to edit the file that tells linux which modules(same as drivers in windows) to load at startup using the command gksudo gedit /etc/modules and add the word ndiswrapper to the end of the file. You should then be able to reboot to check that wireless is working.

---

### Post by efledderman on 2008-02-27
See, this is why I want to use Linux to begin with.  I can never find people this willing to help for Windows...  I'll give it a shot thanks.

---

### Post by ryanhaigh on 2008-02-27
The instructions in the ndiswrapper site I referred you too are more extensive and include using ndistk, I just tried to summarise what I remember from my prebuntu days and what is there fore ndisgtk. None the less happy to be of assistance.

---

