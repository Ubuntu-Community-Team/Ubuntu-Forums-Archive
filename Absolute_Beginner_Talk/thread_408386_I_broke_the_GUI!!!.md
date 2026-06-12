---
title: "I broke the GUI!!!"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Fenrirwulf on 2007-04-13
Help! I replaced the motherboard and processor in my pc and now Fiesty will not boot up the gui. It says something about the x server couldn't start or something like that. I can get to the shell and that works fine but I am such a newb to Ubuntu and Linux that I would be hard pressed to navigate that for long. I went into recovery mode and got the same thing. I put the cd in thinking that maybe it would have a repair option like in windows but I didn't find anything. Is there anyway to get this back or should I just re-install again? At least I now understand how to get my wifi card working with ndiswrapper now so it wouldn't be that big of a deal.

---

### Post by Fascination on 2007-04-13
[quote="ubuntu geek"]If you decide to use Feisty then you are doing it on your own risk and with the risk of major breakage and possibly losing data.

Don't use Feisty as your primary desktop/OS. Feisty is Ubuntu in development. It's not ready for the general public! If you want new stuff you can use backports instead of Feisty.

Feisty should only be used if you want to help testing bugs. Important stuff can and will get broken. **Probably X is going to break this means that during that time (maybe even for weeks) you can't easily log into X anymore.**

If you want to help testing you are welcome to try Feisty. You should backup your stuff such as personal files and data. Also install Feisty on a different partition than Dapper/Edgy and use a different username if you use the same /home partition.[/quote]

The trick here would be to use Edgy till Feisty is officialy released and 'safe' to use. ;)

---

### Post by aberry5555 on 2007-04-13
Did you change your Graphics card at the same time?

---

### Post by eentonig on 2007-04-13
I don't think hes problem is related to him using Feisty. As he clearly states, he installed a new motherboard and processor.

What you can try before reinstalling, is reconfigure your X server from the command prompt. I'd have to look for the exact command. But most likely, you'll be able to find it yourself, using the search function. But I'll have a look for you.

---

### Post by Seisen on 2007-04-13
Most likely the reason the gui doesn't work is because the on board graphics is different on the new motherboard  than the one that was one the old motherboard.

Do this in the terminal

```
sudo vim /etc/X11/xorg.conf
``` 

This will open up your the file and you need to scroll down till you see where it says

```
Section 	"Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
```

change the driver to vesa like mine says and then save the file by doing this
```
:wq
```

After that you need to restart your computer and it should fix the gui and then you can find out what vga chipset is and see if it is supported.

Then resta

---

### Post by aberry5555 on 2007-04-13
Either way, even if you didn't, this is worth a shot to get it working:

In the shell type in the following:

```
sudo dpkg-reconfigure xserver-xorg
```

This will take you through some options to reconfigure your xorg.conf (gui configuration file), rather than doing it by hand, fill them out as best you can then restart ubuntu in to normal startup and see what happens, good luck!

---

### Post by Fascination on 2007-04-13
> **eentonig said:**
> I don't think hes problem is related to him using Feisty. As he clearly states, he installed a new motherboard and processor.

He's also clearly shown hes not exactly going to be testing out Feisty constructively either, so whats the need for him to use a beta when he can use a more reliable version?
Problems do, and are, occuring with the beta and so it doesnt harm to eliminate that being the issue behind his problem. Its quite possible the issue is down to a difference in his xorg.conf due to the new mb/processor, meaning running a quick reconfigure would resolve it - but it still doesnt mean that switching to a stable release isnt a sensible idea. ;)

---

### Post by Fenrirwulf on 2007-04-13
Wow, that was fast. Thanks for the responses. Yeah it wasn't because I was using Fiesty. Everything was working beautifully before I upgraded. I had an Athlon 64 3400+ and a Gigabyte K8NPro motherboard with the Nforce3 chipset and now I have a Intel Duo Core 2 E6400 with a ASRock 775lga VSTA board with a VIA chipset so that would make sense that it doesn't recognize it anymore. I will try those commands when I get home and see if that helps. Thanks again!! :D

---

### Post by Fenrirwulf on 2007-04-13
> **Fascination said:**
> He's also clearly shown hes not exactly going to be testing out Feisty constructively either, so whats the need for him to use a beta when he can use a more reliable version?
Problems do, and are, occuring with the beta and so it doesnt harm to eliminate that being the issue behind his problem. Its quite possible the issue is down to a difference in his xorg.conf due to the new mb/processor, meaning running a quick reconfigure would resolve it - but it still doesnt mean that switching to a stable release isnt a sensible idea. ;)

That's probably a good point and I may just re-install Edgy if that doesn't fix the problem.

---

### Post by Seisen on 2007-04-13
Here is the link to get your via chipset to work, I have a via chipset so I know it works.

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

I followed the 2D directions so I at least know they work.

---

### Post by eentonig on 2007-04-13
> **Fascination said:**
> He's also clearly shown hes not exactly going to be testing out Feisty constructively either, so whats the need for him to use a beta when he can use a more reliable version?
Problems do, and are, occuring with the beta and so it doesnt harm to eliminate that being the issue behind his problem. Its quite possible the issue is down to a difference in his xorg.conf due to the new mb/processor, meaning running a quick reconfigure would resolve it - but it still doesnt mean that switching to a stable release isnt a sensible idea. ;)


I agree that it's unlikely that he will be contributing actively in bugtesting and develloping Feisty. But I have the tendency to only shoot when it's needed. In this case and after reading his first post, it was the most logical thing to assume a changed graphics driver. I didn't even had to know which release he's using.

If the problem is indeed caused by a Feisty bug... Well, sorry guy. You knew it's béta, you knew the thight schedule they force themselves on.... Things are likely to break. But there's no law against n00b's or whomever to use the béta releases. Even they can contribute by posting their experiences. Just as long as they don't expect things to be 100% stable and accept the flaws.

---

### Post by Fascination on 2007-04-13
> **eentonig said:**
> But there's no law against n00b's or whomever to use the béta releases.

As soon as I read that line I grinned and said, "Pity." before I could stop myself, sorry. :-P

Anyway, Fenrirwulf - best of luck to you in getting it sorted. :)

---

### Post by eentonig on 2007-04-13
:mrgreen: :biggrin: Yeah, I couldn't resist putting it like this.

I don't mean to say that the Topic starter is a n00b, just to point out that beta is there for everyone ready to accept **** going on. And willing to contribute what he experiences or learns.

I think... If there's one thing that Bill really envies the linux community for.... it's the vast amount on active and participating béta-testers it's got. They might not all be devellopers. 

But I'm pretty sure that they catch, report and help troubleshoot more bugs in new soft in linux apps and distro's, then any beta released by Redmond. 


A lot off people jump on the Ms bétas to try the new and nifty stuff. But I estimate that there is only a minority actively testing and reporting back.

---

