---
title: "Pidgin won't load"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by rgraves on 2008-04-03
I can't get Pidgin to load. When I go to load it tries to start but stops loading. Nothing happens. 

I've tries removing and reinstalling but same results.

It ran fine a few days ago but now nothing..

Any ideas.

---

### Post by Shakey_Jake33 on 2008-04-03
I had that problem.  I uninstalled it, but it failed to remove the pidgin-data package when uninstalling, so any attempt to reinstall just gave the same symptoms.  Removed that package in Synaptic, reinstalled from fresh and all was good.

---

### Post by privaterolf on 2008-04-03
> **rgraves said:**
> I can't get Pidgin to load. When I go to load it tries to start but stops loading. Nothing happens. 

I've tries removing and reinstalling but same results.

It ran fine a few days ago but now nothing..

Any ideas.

There's no icon that appears in the system tray in the upper right hand corner of the screen?
[looks like a green circle in front of a white square]

Sometimes Pidgin will start up there.

---

### Post by rgraves on 2008-04-03
I've tries uninstalling, reinstalling, rebooting, reeverything and still the same result.

No icon in upper right hand corner of screen.

It begins trying to install and just quits.

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> I've tries uninstalling, reinstalling, rebooting, reeverything and still the same result.

Have you tried running Pidgin from the Terminal, open up Terminal and type the following: ```
pidgin
```

---

### Post by tdrusk on 2008-04-03
Do you happen to be using the myspace im protocol?

---

### Post by rgraves on 2008-04-03
Okay, I can get it to run using terminal.

Why is it when I close the terminal window all my buddies disappear?

Somethings not right. I shud be able to start the program from the applications menu.

Any other ideas?

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> Okay, I can get it to run using terminal.

Why is it when I close the terminal window all my buddies disappear?

Somethings not right. I shud be able to start the program from the applications menu.

Any other ideas?

When you close the Terminal window, it closes the program also.

---

### Post by privaterolf on 2008-04-03
> **rgraves said:**
> Okay, I can get it to run using terminal.

Why is it when I close the terminal window all my buddies disappear?

Somethings not right. I shud be able to start the program from the applications menu.

Any other ideas?

Usually when you open a program using Terminal, you have to keep that terminal open to keep the program open.

Try deleting Pidgin from your applications list [via the top panel], then re adding it. NOT  uninstalling.

---

### Post by Crafty Kisses on 2008-04-03
> **privaterolf said:**
> Usually when you open a program using Terminal, you have to keep that terminal open to keep the program open.

Try deleting Pidgin from your applications list [via the top panel], then re adding it. NOT  uninstalling.

Yeah, that may solve the issue, and you might want to post some of your logs up, so I can take a look at them, Pidgin might possibly be crashing for some reason.

---

### Post by rgraves on 2008-04-03
Okay, understand about terminal window shutting it down.

What's preventing me from starting it from the applications menu? It worked fine last week. All my other applications work fine from apps menu. Just this one giving me fits.

---

### Post by privaterolf on 2008-04-03
> **rgraves said:**
> Okay, understand about terminal window shutting it down.

What's preventing me from starting it from the applications menu? It worked fine last week. All my other applications work fine from apps menu. Just this one giving me fits.

Just taking a wild stab at it, but perhaps in the apps menu, it's running some different command other than 'pidgin'

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> Okay, understand about terminal window shutting it down.

What's preventing me from starting it from the applications menu? It worked fine last week. All my other applications work fine from apps menu. Just this one giving me fits.

Not sure, try removing it and adding it back, and see if that solves the issue.

---

### Post by rgraves on 2008-04-03
I apologize for being a noob but can you explain how I do this? 

Try deleting Pidgin from your applications list [via the top panel], then re adding it. NOT uninstalling.


There is no option to delete it from the apps/internet menu.

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> I apologize for being a noob but can you explain how I do this? 

Try deleting Pidgin from your applications list [via the top panel], then re adding it. NOT uninstalling.


There is no option to delete it from the apps/internet menu.

There should be an Add/Remove option in your Applications panel.

---

### Post by rgraves on 2008-04-03
I've used add/remove same results. Ball spins fro about 15-20 seconds and it just stops.

How do I post the logs that Codename suggested?

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> I've used add/remove same results. Ball spins fro about 15-20 seconds and it just stops.

How do I post the logs that Codename suggested?

So when it stops you mean it just stops responding?

---

### Post by rgraves on 2008-04-03
Codename,

Yes, it tries to start for about 15-20 seconds. Ball spins, then stops and then back to cursor.

Nothing in upper right hand panel, nothing.

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> Codename,

Yes, it tries to start for about 15-20 seconds. Ball spins, then stops and then back to cursor.

Nothing in upper right hand panel, nothing.

You sure you don't have another Pidgin running on another desktop, that's highly possible?

---

### Post by rgraves on 2008-04-03
No, just checked, nothing running on the other desktops.

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> No, just checked, nothing running on the other desktops.

Have you rebooted and retried?

---

### Post by rgraves on 2008-04-03
I just rebooted. nothing's changed.

What's the alternative to Pidgin?

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> I just rebooted. nothing's changed.

What's the alternative to Pidgin?

You can try Kopete.
```
sudo apt-get install kopete
```

---

### Post by rgraves on 2008-04-03
Thanx for your time. 

I've got Kopete up and running.Will use that instead.

---

### Post by Crafty Kisses on 2008-04-03
> **rgraves said:**
> Thanx for your time. 

I've got Kopete up and running.Will use that instead.

No problem man, anytime. :)

---

### Post by NightwishFan on 2008-04-03
If you ever wish to try again do this command.
```
sudo apt-get update && sudo apt-get purge pidgin && sudo apt-get install pidgin
```

---

### Post by tdrusk on 2008-04-04
Do you happen to be using the myspace im protocol?

---

### Post by rgraves on 2008-04-05
No I'm not using the myspace im protocol

---

### Post by jabraham on 2008-05-11
the same sort of thing seems to be happening for me and i'd rather not switch programs.

i tried purging pidgin and reinstalling it but i still get the same error i got in the terminal window as before:

"Segmentation fault"

help?
is there a configuration file that pidgin creates in my home folder that i can delete?

thanks

---

### Post by EastKY_DO on 2008-07-14
I've just recently tried to run Pidgin and I'm encountering the same problems previously described.  Has anyone found a solution for this?

---

### Post by bjorkiii on 2008-07-15
I had exact same problem followed post 26 and now it seems to have solved it thanks :)

---

