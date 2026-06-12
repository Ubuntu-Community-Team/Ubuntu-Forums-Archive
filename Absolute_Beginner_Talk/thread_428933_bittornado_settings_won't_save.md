---
title: "bittornado settings won't save"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by hencethus on 2007-04-30
I installed BitTornado through synaptic, but when I change the settings (such as the port range) they won't save. When I restart the program they've always reverted to defaults.

Any suggestions?

---

### Post by supersonicdarky on 2007-04-30
same problem here. try ktorrent instead. much better ;)

---

### Post by frokki on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bittornado/+bug/109799](https://bugs.launchpad.net/ubuntu/+source/bittornado/+bug/109799) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Guess we have just to switch torrent client until this nasty bug is fixed...

edit: just tested KTorrent, which is in Kubuntu by default - and I'm definitely not going back to BitTornado :)

---

### Post by katch22 on 2007-05-02
Or get a new BitTorrent client like Azureus! I have tried many on both the old OS and Linux, and Azureus really is best!

---

### Post by Hallvor on 2007-05-02
That is very strange. I use bittornado all the time, and have never had any problems with the settings. 

What client is the *best* is subjective. I like lean, fast and stable clients. Bittornado is absolutely bloat-free, it is very fast (at least for me) and has never crashed on my computer. It is just what I need.

I tried ktorrent and was very impressed by it until it crashed. Azureus was IMO incredibly bloated.

---

### Post by Chii on 2007-05-08
Im having the same problem with bit tornado, and sadly to say atm it seems its one of the only clients that Ive been able to get to work with this private tracker group as the other ones seem to be banned. :> 

So I am wondering, is there any way that I can find the configuration file and change it by hand?  Because all I need to do is change the port so that it allows me to use a specified one rather than just a random port.

Thanks!
-Chii

---

### Post by Hallvor on 2007-05-08
Just browse to the .bittornado folder (hidden in your home directory). There should be a file named config.gui.ini

Open that file with a text editor, scroll down a bit and try changing these lines: 

> maxport = yourportnumberhere
min_peers = 20
min_uploads = 4
minport = yourportnumberhere
random_port = 0

Save and close. Restart bittornado.

I have no problems with bittornado, but please let us know if it works. :)

---

### Post by Chii on 2007-05-08
I was able to go in and change it, and after loading Bittornado I checked the preferences I can verify that this did indeed work :)

Thanks for your help :)
-Chii

*edit*
A random thought just occured to me.  Not sure if it had anything to do with it, but could having beryl running have made it so that the changes didnt save or something like that?  I may test that to see if this is the case once I get this torret seeded to 1:1 ratio :>

---

### Post by amaroKer on 2007-05-08
Thanks for the manual fix.

I don't run Beryl at all, and it still wasn't working for me.  Must be a bug in the new version of BitTornado or something...

---

### Post by IgnattiousRavenhurst on 2007-05-09
I'm having the same problem. I can't even get Azureus to run, either.  It tells me [X is not a file] and shuts down. I'm gonna try the manual fix for bittornado and see if that works. Heck, I can't even set up a static IP addy. It completely locks me out of my wireless network when I try. Any advise for this?

Iggy

*edit* It worked fine. I still can't set up a static IP addy, though, so I'm stuck on "Yellow" :(   (But I have something, anyway.)

---

### Post by Hallvor on 2007-05-09
Glad it worked. Hope they manage to fix the bug soon. :)

---

### Post by Mr.Linc on 2007-05-15
I just installed BitTornado a few days ago (tried Azureus first, but it starts and shuts down right away, because of some JRE error -JRE is installed and running fine-) and got the same "settings not saved" problem. It's fixed now and fully working thanks to this manual fix. :)

Thank you.

---

### Post by sgbirch on 2007-05-31
[QUOTE=Hallvor;2614964]Just browse to the .bittornado folder (hidden in your home directory). There should be a file named config.gui.ini

Thanks for the tip, this worked for me although directory was .BitTornado on my machine, note the capitalization.

---

