---
title: "Please help me get control of CUPS"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-01-25
arrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrgggggggggggggggggggggggghhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh


OK have installed and re-installed CUPS a dozen times, purged it, deleted subdirs tried it all except for a complete re-install of the OS.

Still cannot get it to even attempt to work, well sort of, sometimes, kind of, maybe just a teaser - but not consistently for all networked machines.

So CUPS is installed, installed printer. Printer prints great from local.

goto localhost:631 - looks good

goto admin select 'Share published printers connected to this system' press Change Setting and it asks for a CUP username and password - yes cupsys is a member of shadow, yes user mikeh (me) is a member of lpadmin and for extra value root is enabled and a member of lpadmin for good measure.

And no, none of the username password combos is allowed.

Now I am suprised that this system is so secure that Root does not have permission to share a printer, NOW that is what I call secure. I realise we want to be safe here, but this is very silly indeed.

DAMN this really pisses me off, I have spent ages getting this machine running with the tools necessary and it falls over on the basics of sharing printer - THIS IS REALLY STUPID.

Looks like I have to start all over again with another distro, SUSE maybe or Red Hat

---

### Post by pearlie on 2007-01-25
Glad you brought this up, mate - I've been banging my head against the wall since my install last week.  I thought at first that it was because my printer is attached to the desktop (running 6.06, i386) and the laptop is running 6.06 AMD64... but now I realize that's probably not it, it's my own inexperience.

Did you try the method given [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Print_Server_.28cupsd.29")? Look at section 21.2 'Print Server'.  I just found it, haven't given it a shot yet.

---

### Post by kosmic on 2007-01-25
Easy Way :

***Install Samba***

then edit the file [I]/etc/samba/smb.conf

[/I]```
sudo gedit /etc/samba/smb.conf
```

and add this :

```
[I]
[hp-printer]
      path = /tmp
      printer name=HP DeskJet 690C (your printer name)
      printable = yes
      print command = lpr -r -h -P %p %s
      create mode = 0700
[/I]
``` 
[I]After that go to your Windows workstations and install your printers drivers,
and choose the printer from the **Add network printer wizzard in windows**

[/I]

---

### Post by budgie9 on 2007-01-25
Why can't we get an answer to this question 

"goto admin select 'Share published printers connected to this system' press Change Setting and it asks for a CUP username and password - yes cupsys is a member of shadow, yes user mikeh (me) is a member of lpadmin and for extra value root is enabled and a member of lpadmin for good measure.

And no, none of the username password combos is allowed.

Now I am suprised that this system is so secure that Root does not have permission to share a printer, NOW that is what I call secure. I realise we want to be safe here, but this is very silly indeed."

I too have been banging my head to get around this situation. I could access CUPS  in Suse, but for some reason not in Ubuntu, and nothing I have found tells me how to actually access CUPS itself.

---

### Post by Busta999 on 2007-01-26
OK I never was able to gain access to manage the CUPS web admin, but still got around the problem.

see

[http://www.ubuntuforums.org/showthread.php?t=345766](http://www.ubuntuforums.org/showthread.php?t=345766)

Thanks for your help/input guys much appreciated.


Mike


----------------------------------------------
Linux ain't your Aunt Mable's OS

---

