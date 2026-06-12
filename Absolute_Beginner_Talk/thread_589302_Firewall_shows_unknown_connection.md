---
title: "Firewall shows unknown connection"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-10-24
I've just installed firestarter and now I have a couple of questions.

1. If I start the firestarter GUI, it runs normally. However if I leave it alone for a while, the GUI closes. Is this normal behaviour? Or is it crashing on me?

2. Under 'active connections' there is one incoming connection (it is coming from something that says it is an nzserver, whatever that is...). It is also the one connection I do not understand. How do I determine what this connection is? How do I terminate it?

3. Related to the incoming connection: I have no incoming policy. I thought this meant all incoming connections are blocked. If this is so, how is it possible that there even is an incoming connection?

---

### Post by ofb on 2007-10-24
1. It shouldn't close itself. That's odd. Try starting it by entering 'sudo firestarter' in a terminal, then see if you get any useful error messages when it does the closing trick.

2. Do you mean nxserver perhaps? That would be this
[http://en.wikipedia.org/wiki/NX_technology](http://en.wikipedia.org/wiki/NX_technology)

---

### Post by hyper_ch on 2007-10-24
Firestarter is not a firewall but a frontend for iptables. I think it's normal behaviour that it closes itself upon a longer time of no interactinol

---

### Post by ofb on 2007-10-24
You've seen this? I have not observed that behavior, and cannot find a reference to it. That would be strange behavior for an interface that displays events like active & blocked connections. 

... and mine's been sitting un-disappeared on a far workspace for an hour now. Time for me to get some sleep. Good luck with it chaps.

---

### Post by hyper_ch on 2007-10-24
I don't use firestarter... no need for it ;)

---

### Post by EvilBro on 2007-10-24
> **ofb said:**
> 1. It shouldn't close itself. That's odd. Try starting it by entering 'sudo firestarter' in a terminal, then see if you get any useful error messages when it does the closing trick.
Well, I've tried this and I did indeed get an error. Whether it is useful, I don't know. I'll just post it here so you might be able to determine its usefulness.

***MEMORY-ERROR***: firestarter[6242]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

---

### Post by ofb on 2007-10-24
Bug reports
[http://www.google.com/search?hl=en&client=opera&rls=en&hs=Jrn&q=+site:bugs.launchpad.net++MEMORY-ERROR+firestarter+GSlice+](http://www.google.com/search?hl=en&client=opera&rls=en&hs=Jrn&q=+site:bugs.launchpad.net++MEMORY-ERROR+firestarter+GSlice+)

I'll have to see if my 7.10 test-box does that. 

Meanwhile you probably want a quick fix, so I suggest Guarddog instead. It's not as simple because at default everything is locked off, so you need to know what protocols to allow. But their documenation about that is very good. It's simply a matter of sitting down with it and reading through once.

With the exception of SMTPS, I should say. If you need that, you do this
[http://ubuntuforums.org/showpost.php?p=3506111&postcount=4](http://ubuntuforums.org/showpost.php?p=3506111&postcount=4)

What was the story with nzserver/nxserver?

---

### Post by EvilBro on 2007-10-26
But the crash of my firestarter gui doesn't affect the actual working of the firewall, right? If this is the case, I'll live with it for now.

> What was the story with nzserver/nxserver?
I think it was a connection that was already present when I first ran firestarter. I haven't seen it since (I've restarted since then :) ). Still, I do find it a bit weird as I thought that the firewall was already present blocking all incoming connections before I ran firestarter (and that firestarter was just a GUI configuration tool).

If this situation happens again, I will look into it further.

---

### Post by ofb on 2007-10-26
In theory the GUI crashing shouldn't alter the iptables on the way down. However crashing is not precisely choreographed behavior, and that GUI does have the permission and ability to alter the iptables, so it /could/ mess them up on the way out, though I'd doubt it.

But since I'm an old paranoid what I'd do is restart Firestarter and close it normally. Further, I'd restart it via terminal and then watch terminal for error messages while closing to see that it did closed normally, & not crash when I selected close.

If it exits cleanly, then you'd be absolutely assured the desired iptable configuration is in place. 

Anyway... back to nz/nx -- what shows up in 'active connections' is just your connections. That entry is very likely a response to a request you made, not something instigated as an outside request. Those are blocked, as you say.

If you feel like it, go to the Shields Up site and run the tests to see how well you're locked down. (He's a bit of a crank, but the tests are very nice service.) Firestarter's defaults are quite good.

So to emphasize: you're probably fine.

However you do have a crashing firewall GUI, and IF you're getting **nx**server connections as well, then I'd start looking at the outside chance your machine has been hacked.

---

### Post by EvilBro on 2007-11-02
I've just noticed this: during booting my machine it says "*starting firestarter. failed..." and something about an exit code 2. I've tried to locate this message in some sort of log, but I haven't found it yet. 

So... 1) where can I find the exact message? and 2) what does it mean? and 3) how do I fix it?

---

### Post by ofb on 2007-11-03
I believe what you want is /etc/default/bootlogd

Change the variable from No to Yes, the after next boot look at /var/log/boot

Then try a search with the Firestarter error, and/or post it here of course.

What you might also do is in Synaptic do a complete removal of firestarter, then install again.

---

### Post by EvilBro on 2007-11-04
I've tried doing what you told me to do, but /var/log/boot stays empty (actually it says "(Nothing has been logged yet.)").

I have seen the error enough times to read it though. It says "Firestarter has exited with code 2". Later in the boot sequence (I think when it shows which services it is starting), it says [fail] when Firestarter comes by. However when I do "/etc/init.d/firestarter status", I get the message that Firestarter is running (which sort of surprised me as I though it would only configure ip-tables).

> **ofb said:**
> What you might also do is in Synaptic do a complete removal of firestarter, then install again.
I've done this at least twice already, but that didn't help.

---

### Post by ofb on 2007-11-04
Firestarter is primarily a GUI for configuring IP tables, but some people like to run it at startup. Partly that's from a misconception that it is the firewall, but the practical reason it it also shows connection reports.

Unless you want to dig through bug reports to solve this one, I'd say just bin Firestarter and use Guarddog for now. I haven't had a chance to dig into this yet thanks to other little gems 7.10 has brought along.

---

