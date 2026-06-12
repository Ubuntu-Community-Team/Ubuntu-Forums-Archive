---
title: "Limewire error message"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Biciclettapc on 2008-02-26
I get this message when I try installing Limewire.  I have nothing else running and even shut down and restarted the computer.

Thanks
Paul

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> I get this message when I try installing Limewire.  I have nothing else running and even shut down and restarted the computer.

Thanks
Paul

You might just want to install FrostWire, it's a lot better. :)

---

### Post by Biciclettapc on 2008-02-26
Ok, will do!

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> Ok, will do!

It's also easier to install. :)

---

### Post by Biciclettapc on 2008-02-26
Hmmmm, same error message when I d/l and installed.

Did not find in add/remove

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> Hmmmm, same error message when I d/l and installed.

Did not find in add/remove

What's the error message?

---

### Post by Biciclettapc on 2008-02-26
This one.

Thought I attached it in first but didnt :rolleyes:

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> This one.

Thought I attached it in first but didnt :rolleyes:

Hmmm, that's weird, it looks like you have 2 Synaptic Package Managers open at the same time, go in System Monitor and close one, that should sovle your issue. :)

---

### Post by UK-Wobbie on 2008-02-26
> **Biciclettapc said:**
> I get this message when I try installing Limewire.  I have nothing else running and even shut down and restarted the computer.

Thanks
Paul

I hate Limewire :lolflag:
Install FrostWire like what Codename says :)

---

### Post by Crafty Kisses on 2008-02-26
> **UK-Wobbie said:**
> I hate Limewire :lolflag:
Install FrostWire like what Codename says :)

Yeah, FrostWire is a lot better. :)

---

### Post by Biciclettapc on 2008-02-26
According to system monitor I have none running, still get message.....

All thing running is the system monitor and opera

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> According to system monitor I have none running, still get message.....

All thing running is the system monitor and opera

Did you try rebooting, then try re-installing it?

---

### Post by Biciclettapc on 2008-02-26
Tried that once already and just tried a restart again with the same error message
:confused:

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> Tried that once already and just tried a restart again with the same error message
:confused:

Do you also have Flash and JAVA installed on your machine?

---

### Post by Biciclettapc on 2008-02-26
Yes, I have both.

I also get this error message now.  I have used add/remove before with no issues

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> Yes, I have both.

I also get this error message now.  I have used add/remove before with no issues

Go into the Terminal, and try the following:
```
dpkg --a configure -a
```

---

### Post by Biciclettapc on 2008-02-26
Ok, this is what I get.  I had tried this earlier with no luck (same message)

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> Ok, this is what I get.  I had tried this earlier with no luck (same message)

Try ```
sudo dpkg --a configure -a
```

---

### Post by Biciclettapc on 2008-02-26
ok, seems to say the same thing.

Thanks for helping!
Paul

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> ok, seems to say the same thing.

Thanks for helping!
Paul

Make the desktop screenshot delay 1 instead of 0, I can't see. :)

---

### Post by Biciclettapc on 2008-02-26
Here you go, sorry about that.

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> Here you go, sorry about that.

What happens when you try to install a package?

Try this:
```
sudo apt-get intstall xchat
```

---

### Post by Biciclettapc on 2008-02-26
this...

Mis-spelled install as intstall but caught and corrected.

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> this...

Mis-spelled install as intstall but caught and corrected.

Copy and paste that command it tells you to manually run in the Terminal.

---

### Post by Biciclettapc on 2008-02-26
Think I need a cape :lol:

---

### Post by Biciclettapc on 2008-02-26
FYI

I checked to see if system was up to date and got this message (similar to first)  System was up to date

---

### Post by Crafty Kisses on 2008-02-26
> **Biciclettapc said:**
> FYI

I checked to see if system was up to date and got this message (similar to first)  System was up to date

Try this:
```
sudo -i
```
Then do the command:
```
dpkg --a configure -a
```

---

### Post by Biciclettapc on 2008-02-27
tried that and this is the result.  Got error about --a first and removed and tried again, both are in shot.

---

### Post by 3rdalbum on 2008-02-27
The command should be:

```
sudo dpkg --configure -a
```

Try that and we'll see if it solves your problem. So far you've just been asking Ubuntu to dial the television :-P

---

### Post by Biciclettapc on 2008-02-27
Thanks!  That worked and fixed it.

So, I like MHD channel, what do I key in to get that :guitar:

---

