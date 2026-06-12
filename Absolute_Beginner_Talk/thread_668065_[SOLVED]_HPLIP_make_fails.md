---
title: "[SOLVED] HPLIP make fails"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by ckennow on 2008-01-15
Ok i am trying to install the HPLIP drivers for my HP OfficeJet 5510v All-In-One and in the instructions on [http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html) when getting to step 5 Run Make i get ```
make: *** No targets specified and no makefile found.  Stop.
```

What now?!

---

### Post by PeterJS on 2008-01-15
HPLIP is one of the core packages that is always installed with ubuntu, you should be able to jump right to the setting up CUPS step. In fact the HP setup tool is in the menu at Sytem > Preferences > HPLIP toolbox.

---

### Post by ckennow on 2008-01-15
i am running just the server edition of ubuntu

---

### Post by PeterJS on 2008-01-15
Well then the desktop packages certainly wouldn't be installed, eh?

Well then you probably want to install one or both of these:
[http://packages.ubuntu.com/gutsy/utils/hplip](http://packages.ubuntu.com/gutsy/utils/hplip)
[http://packages.ubuntu.com/gutsy/text/hpijs](http://packages.ubuntu.com/gutsy/text/hpijs)

---

### Post by ckennow on 2008-01-15
just do a wget?

---

### Post by PeterJS on 2008-01-15
```

Sudo apt-get install *PackageName*

```

And the command line section to the guide to installing any thing:
[http://monkeyblog.org/ubuntu/installing/#installing_with_terminal](http://monkeyblog.org/ubuntu/installing/#installing_with_terminal)

---

### Post by ckennow on 2008-01-15
ok so now that i installed with ```
sudo apt-get install hplip
``` is there any config to be done?

---

### Post by PeterJS on 2008-01-15
That is a real good question, I think there is, but it should all be stuff that can be done with the CUPS webconfig interface.

---

### Post by ckennow on 2008-01-15
CUPS webconfig interface?

---

### Post by PeterJS on 2008-01-15
Cups Documentation to the rescue:
[http://www.cups.org/doc-1.1/sam.html#4_4](http://www.cups.org/doc-1.1/sam.html#4_4)

Only difference is you probably want to configure it from a machine with a graphical browser, so you'd want to substitute the server's IP for localhost, but keep the port number.

---

### Post by ckennow on 2008-01-15
ok I go to ```
http://<my ip addy>:631/admin
``` and i get ```
Page not found - connection failure.
``` but if i do it in lynx it come up but like you said....not graphical

---

### Post by PeterJS on 2008-01-15
Good security practices in linux, you don't say, I'd never tried to configure cups remotely before, makes sense though. I assume you've got ssh installed on the server to connect to it. If that's the case you could use that to tunnel in a connection from your remote machine. I'm going to go install putty so there should be screenshot's shortly if needed.

---

### Post by ckennow on 2008-01-15
never done tunnelling before I would be interested as to why this is not working even though my server is on dmz thru my router.  I am using putty as i lie here in bed next to my annoyed wife who is learning how to fall asleep to the sound of a laptop keyboard

---

### Post by ckennow on 2008-01-15
BTW THANK YOU SO MUCH for taking the time to help me on this one.  The Ubuntu community seems to be the exception to the rule when speaking of linux community support in general.  The rest of the linux community could take a cue from this community here.

---

### Post by PeterJS on 2008-01-15
The reason it's not connecting is because cups is only accepting local connectings, which make sense, you don't want any old random machine on your network to be able to get to your printer configuration page and do what ever they want.

I warn you these aren't the prettiest screen shots in the world it's the default GTK theme, I take no reponsiblity if they burn your eyes out, I'm sorry. This is the linux version of putty, but it looks enough like the windows version that I haven't noticed any differences in the course of writing this.

[img]http://oregonstate.edu/~sandinp/Ubuntu/putty.png[/img]

[img]http://oregonstate.edu/~sandinp/Ubuntu/putty1.png[/img]

[img]http://oregonstate.edu/~sandinp/Ubuntu/putty2.png[/img]

After that's set up localhost:361 of your laptop should forward to cups as though it were coming from the local machine it is running on.

I can empathize with the annoyed wife, I'm exiled to the living room with the cat because my fiance can't sleep over the tap tap tap of a keyboard.

---

### Post by ckennow on 2008-01-15
THANK YOU THANK YOU THANK YOU THANK YOU. WOW i never knew you could do that.  That will be useful in so many ways. Especially at college when i can't access my router for tweaks and such.  Man You are SOOOO Awesome!!!!!!

---

### Post by ckennow on 2008-01-15
So now how do I add my printer?

---

### Post by PeterJS on 2008-01-15
On the administration tab there's a button labled find new printers, click that, and follow the directions.

Also on the admin tab is a check box to allow remote administration.

After the printer is all set up I suppose you're going to ask about SMB print sharing :)
That's what SWAT is for:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html)

Also I suppose I do also owe you some thanks, without this thread I never would have dragged my printer out of storage and set it up.

---

### Post by ckennow on 2008-01-15
does it matter which ppd file i choose?

---

### Post by PeterJS on 2008-01-15
Yes, the ppd tells cups how to mangle the document so the printer can understand it, pick the wrong one and who knows what kind of wacky printer mishaps you'll get. I know the list is giant, I just looked at it, it's mostly in alphabetical order by series and then model. When you get reasonably close to the one you're looking for they should start having (recommended) after the name, as long as you're with in the right family and +-100 for the model number things shouldn't be too bad.

---

### Post by ckennow on 2008-01-15
i downloaded and used the 5500 series one but it told me:

"Filter "foomatic-rip" for printer "hp_officejet_5500_series_USB_1" not available: No such file or directory"

ALMOST THERE I CAN TASTE IT!!!

---

### Post by PeterJS on 2008-01-15
foomatic-rip is in the foomatic-filters package.
```

sudo apt-get install foomatic-filters

```

You know, I wonder how they came up with that name, its just so fun to say.

---

### Post by ckennow on 2008-01-15
Almost:

"/usr/lib/cups/filter/foomatic-rip failed"

---

### Post by PeterJS on 2008-01-15
Uh... that's no good... like you said so close.
If you've got the bandwidth, disk space, and time, you might just try throwing foomatic packages at it until it works. The desktop comes installed with foomatic-db, foomatic-db-engine, foomatic-db-gutenprint, and foomatic-db-hpijs (which might be a good place to start). Barring that try using one of the PPDs from the big old list of pre-installed ones, the one you need might already be there.

---

### Post by ckennow on 2008-01-15
[http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_5500](http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_5500)

tells me that i should use the HPLIP driver which i installed however the ppd files that are listed are for deskjet and laserjet and color laserjet.  I am not concerned with space i have a 320 gb drive as the main so if those packages will help then my next question is can they be installed via apt-get?

---

### Post by PeterJS on 2008-01-15
Everything* can be installed via apt-get, that's why it's great.

*Everything being 90%+ of everything you'd ever want that isn't a game, dvd decoder, or really obscure and off the wall. For those things there's google and getdeb.net.

---

### Post by ckennow on 2008-01-15
do i need to restart cups or anything after installing those pkgs

---

### Post by PeterJS on 2008-01-15
Only if it tells you to. That's one of the other nice things about the deb post install scripts is that most maintainers write theirs to tell you if there's something you need to restart or configure. So it's pretty safe to assume that unless told otherwise things will just work(tm).

---

### Post by ckennow on 2008-01-15
WOW thank you I don't know which pkg it was that did it but i just added them all into one big apt-get and then it showed up.  I printed a test page and sure enough.  SCARED THE CRAP OUT OF MY WIFE when the printer went on cuz it is a NOISY machine but nonetheless i now need it to be shared in windows so my laptop can get at it. I added my name to the accepted users list and now i see it in the shared folder for my server.  However it asked me to install the proper drivers for it.  I assume the OS is looking for XP drivers so I am installing the basic drivers from HP.  not sure if this is gonna work I will let you know

---

### Post by PeterJS on 2008-01-15
> **ckennow said:**
> WOW thank you I don't know which pkg it was that did it but i just added them all into one big apt-get and then it showed up.  I printed a test page and sure enough.  SCARED THE CRAP OUT OF MY WIFE

And that's the sort of satisfaction you can only get with a job well done.
> 
 when the printer went on cuz it is a NOISY machine but nonetheless i now need it to be shared in windows so my laptop can get at it. I added my name to the accepted users list and now i see it in the shared folder for my server.  However it asked me to install the proper drivers for it.  I assume the OS is looking for XP drivers so I am installing the basic drivers from HP.  not sure if this is gonna work I will let you know
I think that's a reasonable assumption, but I'm just guessing. I'll figure out a definitive answer, when/if you tell, or when/if I get around to setting up print sharing with smb myself (likely never, or more accurately next weekend forever).

---

### Post by ckennow on 2008-01-15
lol....

hmmmm.....

Windows does not seem to like the drivers I am giving it.  Darn those cryptic MS error messages.

---

### Post by ckennow on 2008-01-15
I install the generic driver for MS publisher generic color and now i can print from windows but i was hoping to be able to setup scanning capabilities as well when i went to use the CUPS web manager the tunneling no longer works is there something i changed?

---

### Post by PeterJS on 2008-01-15
CUPS doesn't deal with scanning directly, so if you were trying to share the scanner, it would be smb you need to mess with. As for the tunneling, putty doesn't save it's settings unless you explicitly tell them to save, and then explicitly load them. Otherwise you need to resetup the tunnel each time you connect.

---

