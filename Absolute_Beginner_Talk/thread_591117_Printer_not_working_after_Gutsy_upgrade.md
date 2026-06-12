---
title: "Printer not working after Gutsy upgrade"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-10-25
I did the upgrade to Gutsy last night via the update manager. All went smoothly and it seems everything is working O.K. except my old HP 722c printer. After checking all that I could find to check, here is a summary of what I found:

Printer Configuration:
Device URI: hp:/par/DESKJET_720C?device=/dev/parport0
HP Deskjet 722c Foomatic/pnm2ppa (recommended)
Policies: Enabled, Accepting Jobs, Shared,
Error Policy: retry job
Operation Policy: default

Looking at the job that failed to print I found under status: /usr/lib/cups/filter/foomatic-rip failed

I noticed in another posting that drs305 had a similar problem, "And in answer to your original question, I had a couple of minor issues with an HP printer and networking but both were resolved."

He didn't say how he resolved them. Maybe he'll see this and offer his solution.:)

A couple of other questions: Does 'Printer State:idle' mean the same as 'ready'? Is there a place to go and cancel the failed print jobs ?

One last thing, I tried printing to a printer shared on the lan and got a message that the cache ticket was not received. What is a cache ticket?

---

### Post by Sef on 2007-10-25
It is not supported by [HPLIP]("http://hplip.sourceforge.net/supported_devices/unsupported.html").

Read [OpenPrinting]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_722C").

---

### Post by rsnow on 2007-10-25
I see what you're saying but the thing is that the printer was working fine with feisty.  So I guess what I need is help determining what configuration I had then and seeing if I can use it with Gutsy. I hope Gutsy isn't like Vista in that one has to upgrade a bunch of hardware just to use it.

---

### Post by rsnow on 2007-10-25
I found in another post the suggestion to install gnome-cups manager. If I do this, will I/should I uninstall the foomatic or whatever was installed initially? I don't really understand why the upgrade would make the printer not work. If it doesn't support that printer then it should have skipped that part and left what was working.

---

### Post by drs305 on 2007-10-26
You mentioned an earlier post of mine. On my previous computer, it just started working and I couldn't figure out why other than multiple installs/deletes. Since then I have switched computers and cannot get my hp lj1000 to work with 64-bit gutsy. It worked fine with feisty. 

As of today (26 Oct) I haven't found any thread on the ubuntu forums that solves it for me. This is really frustrating, as you know!

---

### Post by drs305 on 2007-10-26
I've got my HP LJ1000 usb printer running again. As before, I kept installing and deleting the printer via the new gutsy interface.

One thing I did notice this time was that when I set it up the Device URI kept looking incorrect. I didn't write down what the line was, but I remember it always ended with something like ....serial# even though I was selecting the usb-recognized printer. It installed like this several times.

I thought this was strange since the usb printer was automatically detected and the installation selections were all pre-selected as I stepped through the installation. I recycled the printer power several times and the final (successful) installation had a URI of:
usb://HP/Laserjet%201000

That looked correct and in fact the printer started working.

Edited:  I succesfully got my HP printer working on another machine using a different method. I detailed it in post #4 in [http://ubuntuforums.org/showthread.php?t=583143](http://ubuntuforums.org/showthread.php?t=583143).

---

### Post by squirebug on 2007-10-27
I have the same problem with gutsy, but apparently no way to even diagnose it.  My hp720c worked fine with feisty, but as soon as I upgraded to gutsy it fails.  I also have tried multiple reinstalls, but I get no response.  I can't even get an error message.  The printer interface says it is there, but now I can't even display the printer jobs.

For all practical purposes it appears that Canononical disabled printing.

---

### Post by dptxp on 2007-10-27
Printing has been a pain for me on HP5160 after one of the updates in Feisty. After a lot of efforts it prints at snail's pace. I have not tried Gutsy yet on my desktop, Feisty is otherwise fine.

I do not understand why something running fine should conk out after updates or upgrades.

---

### Post by philinux on 2007-10-27
I had a problem with my epson too.

With the upgrade is a new system print manager. But the upgrade leaves the gnome-cups-manager  installed. For me the solution was to uninstall the gnome-cups-manager. 

For hp printers it might be the case to uninstall the system-config-printer

In my case I had to remove the printer and install it again. At the end of the day having two managers causes conflict I reported it as a bug in launchpad.

---

### Post by Daveth on 2007-10-27
do you think it appropriate to uninstall the HP system-config before upgrading,  as a proactive solution then? - a little cross-thready I know

---

### Post by philinux on 2007-10-27
> **Daveth said:**
> do you think it appropriate to uninstall the HP system-config before upgrading,  as a proactive solution then? - a little cross-thready I know

no idea but it cant do any damage. You can always install it after

---

### Post by go_beep_yourself on 2007-10-27
My printer also quit working after upgrading to Gutsy with the update-manager. I have tried removing the printer from the web interface and adding it again. The printer is detected automatically when plugged in. I have also tried deleting the printer and then adding it again by running hp-setup as root. I still had the same problem. I've tried to use a ppd from openprinting.org to see if that would fix the problem, and it didn't.
[IMG]http://img507.imageshack.us/img507/3980/screenshotprinterscups1rq7.png[/IMG]

---

### Post by rsnow on 2007-10-29
Sorry to be so long in responding. I had to go out of town for a few days. Can someone tell me how to uninstall the printer-config that uses the HPLIP? I want to try installing the printer using just gnome-cups and see if that will work. Since HPLIP does not support the 722c I don't see any sense in trying to use it.

---

### Post by rsnow on 2007-10-30
O.K., I figured out how to uninstall the HPLIP. I did and then installed the printer with gnome-cups but it still doesn't work. Everything looks OK except the job gets stopped. Also I'm still not sure if the Printer State: idle shown in the Printer Configuration means the same as Deskjet 722c Ready shown in the Printers window. Does 'idle' mean 'ready'? Or does this indicate that the Printer Configuration doesn't recognize the printer as being ready?

---

### Post by joemacnz on 2007-10-30
ok, I have been having trouble with my Epson cx3100. Also, it didn't work after installing Gutsy. I ended up deleting all the printers on there(the print manager GUI) and reinstalling the printer using the offered "foomatic" driver and not the recomended "gutenprint" one

---

### Post by go_beep_yourself on 2007-10-30
My printer is working now. I went to the website for the HPLIP driver, downloaded it, compiled it, followed some directions, and my printer works.

---

### Post by rsnow on 2007-10-31
I'm glad you got your printer working. I also appreciate all the responses. However, since I can't seem to get the specific help I need, I guess it means uninstalling Gutsy and reinstalling Feisty. I had a feeling that I should have waited awhile before jumping into Gutsy.

---

### Post by drs305 on 2007-10-31
Uninstalling an OS can be painful. I just did a clean install of another machine a couple of days ago and my HP is now working (although it's a usb printer). I edited my post above instead of making a new entry and referenced another thread. Did you try that before giving up?  

If so or if you decided not to, I'm sorry we weren't able to resolve your problem.
Ref: [http://ubuntuforums.org/showthread.php?t=583143#4](http://ubuntuforums.org/showthread.php?t=583143#4)

---

### Post by rsnow on 2007-10-31
I went to the thread in your edited post. Of course I couldn't do exactly as shown because the only driver I know of for the 722c is the pnm2ppa. I thought perhaps I could download the pnm2ppa driver directly from sourceforge and install it just in case the one that came with Gutsy was faulty. But I was never able to get my attempts to install the downloaded file to work. I'm still not all that familiar with using the command line. I thought I had notes on how to do it but they didn't work so I guess I'll have to find better notes.

After reading about the pnm2ppa driver, where it says its purpose is to put the print job into PC memory instead of the printer's memory, that seemed to be where things are going wrong. Each time I try to print a test page I get the message that the print job is sent to the printer. When I look at the print job status it says the print job was stopped. So, it looks like the job is sent directly to the printer which doesn't have enough memory to handle it and it stops the job. Just a guess.

As you say, going back to Feisty won't be a pleasant task but right now I can either do that or just wait (not use my printer) and see if a fix comes down. I haven't totally decided yet which I'll do.

Thanks for the effort to help.

---

### Post by y6FgBn)~v on 2007-10-31
I had a similar problem and after a bit of digging found this post on the forum;

[http://ubuntuforums.org/showthread.php?t=579519&highlight=sudo+aa+complain+cupsd](http://ubuntuforums.org/showthread.php?t=579519&highlight=sudo+aa+complain+cupsd)

After following the steps regarding the "sudo aa-complain cupsd" in terminal, I now have a functional printer.

Hope this helps.

---

### Post by rsnow on 2007-10-31
Hey! It worked! Thanks pcybill. This info should be posted in prominent place and hopefully the folks at ubuntu will correct whatever is making this necessary.

Thanks again to all.

---

### Post by Gumper on 2007-11-01
Yeah baby!!! It works for me too! :)  This has been bugging me for weeks now. I was hoping that when I went from Ubuntu to Kubuntu it would have been fixed, but no luck. Now I can finally print things.

This rocks! :guitar:

---

