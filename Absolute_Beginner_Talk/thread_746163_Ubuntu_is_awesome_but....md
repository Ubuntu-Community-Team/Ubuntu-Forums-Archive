---
title: "Ubuntu is awesome but..."
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Milestones on 2008-04-05
I downloaded and installed ubuntu 7.10 the Gutsy roughly a month ago and I must say I'm deeply impressed. Unlike windows, my router worked the moment I first booted it up and everything's been really smooth for this past month. And with just a command it automatically updates my program(how much neater can it get?!), and lets not forget the level of customisation given to me.  But, as much as I'm getting used not having trojans and whatnot bothering me, I'm starting to feel the lacking aspects of ubuntu. Don't get me wrong, I have no intention of uninstalling it. I thought of listing my problems here so maybe they can be resolved and such. Any help is much appreciated.

[INDENT][LIST=1]
[*]I'm mainly using this computer for work that is of lower end of demand on the specs, like managing documents, excel(or spreadsheet, whatever the case), typing and research on the internet. So in actual fact I do not need a high performance machine but at times I can't help to sway and get the urge of wanting to play games. But most of the games I wanted to play doesn't work, not even on WINE. I guess I have to live with that but here comes the real problem. I'm running on a 761GX-M754 motherboard with everything else pretty much integrated and the drivers aren't supported on linux OSes. Because of that, i find myself even unable to play playable games with low specs, or games which previously ran almost flawlessly on windows on this low end machine. The first solution I got after searching the forums a few times is to dual boot windows and ubuntu but as I have read, windows will erase ubuntu completely and the thought of needing to re-backup my files really turns me off(time is precious!), furthermore I fail to see the point in this as games I wanted to play is supposed to run almost flawlessly on WINE (the ever so prone to nostalgia, Diablo 2). So to sum up, my problem is the lack of driver support. A second solution is to purchase a new machine. That is without a doubt gonna happen but not anytime too soon. Due to some commitments I will not be using that new desktop/laptop too often and thus, its a waste of cash to buy it now.


[*]Point 2, I do typings quite often and i relieve on word processors to do my spellcheck and normally I do the formating of the text on the processor itself as well, and more than often, I would copy and paste the text onto, say a blog or maybe a webpage. When I started using ubuntu, it came together with openoffice wordprocessor. I won't say its a good experience using it. But as easily and helpfully as it is, it didn't take long to find alternatives, and so I settled for AbiWord for now. Here comes the problem, for some odd reason, copying the text format onto blogs or webpages(or basically sites that support vB code or HTML) from microsoft word worked, the alignment and such I didn't give a thought at all. But the thing bout AbiWord and Openoffice is that copying the format doesn't work. The double spacing screw up, the indents doesn't seem to exist at all and such. But I found the solution after searching online for a while. Yes they work but it just makes me life more difficult instead of just blindly copy and pasting.


[*]Point 3, more problems. The rest of ubuntu works too well and I can't get myself to turn it off. Its wasting power and my parents aren't too happy about that. Oh the penguin freaks me out but thats beside the point. :tongue:
[/LIST][/INDENT]

---

### Post by TeoBigusGeekus on 2008-04-05
About your first problem.
If you download the Gparted live cd and boot up with it, you can create a new NTFS partition on your hd and install window$ there.
Window$ will leave Ubuntu intact but it will erase your grub loader. You can recover it with the instructions at this link
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
Furthermore, have you enable the restricted drivers for your system?
Go to system->administration->hardware drivers to see if they are enabled.

---

### Post by bumanie on 2008-04-05
Not sure of the specs of your machine, but a possibility is using windows in virtualisation with a program such as vmware or virtualbox.As you use your computer for work, virtualisation would need to a paid for service. The other option is to make a dual boot system so that you can choose to use windows for work/games and ubuntu for everything else.

---

### Post by Milestones on 2008-04-05
That was certainly helpful and from whatever limited knowledge I have about all these stuff, I actually need to install windows and then use the LIVE CD to recover ubuntu no? I'd try that in due time. One more question, is there like a list or site that I can check what hardware drivers are supported and what are not? One that is similar to the Wine database.

---

### Post by bumanie on 2008-04-05
I don't know of a list, but thaere may be one. I can say that the vast majority of hardware is supported by ubuntu at the kernel level. Probably the two biggest hardware issues people have are with graphics cards (especially with very new cards) and wireless internet, however in most cases these problems can be sorted out. Nvidia graphics cards are better supported than ati at this point in time.
If you are using an older computer, the chances of major hardware/lack of drivers will be much less of an issue than if were running the latest 'cutting edge-type' hardware.
As far as installing windows goes, you would have to partition your hard drive - gparted is good for this. You should be able to partition without wrecking your ubuntu installation, although partitioing has inherent, if only small dangers. Windows prefers the first partiton on master drive and it should not be too much problem reinstalling grub via the live cd. You may need to edit /boot/grub/menu.lst as grub won't know windows is there if windows is installed after ubuntu.

---

### Post by Fixman on 2008-04-05
[This]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") may help you with dual booting.

Before dual booting, be sure that the bugs on your games [can't be resolved]("http://appdb.winehq.org/").

---

