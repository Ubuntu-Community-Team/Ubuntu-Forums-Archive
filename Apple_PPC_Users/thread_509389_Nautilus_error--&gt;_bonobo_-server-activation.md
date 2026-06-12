---
title: "Nautilus error--&gt; bonobo -server-activation"
date: 2007-07-25
forum: Apple PPC Users
---

### Post by thecommodore on 2007-07-25
I wanted to install Dapper Drake on a friend's Powerbook G4 but as it boots from the CD, Nautilus gives me an error and recommends killing bonobo-activation-server.

I am quite a noob with terminal, HOW do I kill it? And I can't install Ubuntu on the G4 cause there is not install icon on the desktop...

PLEASE HELP!!

And is there a way I can avoid this problem if it happens after I've installed Dapper Drake?

---

### Post by radicalspud on 2007-07-25
this same thing happened to me on my powerbook g3 with feisty live CD. the only two times i managed to get it to boot all the way to the desktop, i had bunches of module failures, starting with the ones you've listed.

i was guessing, from what i could glean from these forums, that it had something to do with the system clock (or date, more likely) being set wrong, but i was never able to verify that as a definite.

the general recommendation seems to be trying to boot from alternate (text-based) install CD or netboot ("mini.iso", downloads nearly everything from the internet), to perform a hard-drive installation if you are having trouble getting the live CD to boot correctly. i've not had complete success with either, yet, but i suspect i have a failing hard drive and the debian-installer doesn't like it.

also look at [http://wiki.ubuntu.com/PowerPCFAQ](http://wiki.ubuntu.com/PowerPCFAQ) for some possible solutions.

good luck, these powerbooks seem to be tricky.

---

### Post by Arbiter on 2007-08-16
did anyone solve this problem with bonobo-activation-server killing nautilus?  I'm plauged by the same problem and I've tried installing from both the Feisty live cd and the alternate and it gives me the same problem and I can't find a solution anywhere.

I've got a 500Mhz G4 desktop if that helps...

---

### Post by Chaotic Thought on 2007-08-16
A workaround may be to temporarily disable the "desktop icons" feature of Nautilus... in my expereince it is this feature which tends to cause the most problems. To disable it run **gconftool** and look for "nautilus" inside "apps" and there's a setting called "desktop" or something similar. Sorry I don't remember the setting at this moment but if you browse through the options you'll find it.

After you turn it off, logout of your session and log back in. See if that gives you less problems. Of course, you can still access the files in your "Desktop" using the "Places" menu, and the items will appear in a new window on your screen.

---

### Post by Chaotic Thought on 2007-08-16
Oops--I typed the wrong thing earlier. It should be in your "desktop" key in gconf editor, not the "apps" key

---

### Post by jkbpower on 2007-09-08
> **Arbiter said:**
> did anyone solve this problem with bonobo-activation-server killing nautilus?  I'm plauged by the same problem and I've tried installing from both the Feisty live cd and the alternate and it gives me the same problem and I can't find a solution anywhere.

I've got a 500Mhz G4 desktop if that helps...

I also got this problem.
I manage to start the 7.04 ppc version and in settings I hit "Install" and i got throgh the whole installation.
But after installation when I boot from harddrive I still get the message that I cant use Nautilus.
And it doesn´t load some modules like trash can,clock,updater etc.

Is there anyone who have a solution to this.
/Jkbpower

---

### Post by maximi89 on 2007-12-13
Hi, this problem with Bonobo-Server is when you have a bad hour. the best thing you can do, it's use NTPDate, and use a web like [www.horaoficial.cl](www.horaoficial.cl) this web is for chilean users only.
Bonobo fail with bad settings of the hour...

---

