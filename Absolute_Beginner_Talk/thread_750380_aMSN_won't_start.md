---
title: "aMSN won't start"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-04-09
Hi,

So I try to open aMSN today, and in the panel at the bottom it says "Starting aMSN" for a few seconds, and then dissapears.

I've tried uninstalling aMSN, and reinstalling it (with Synaptic Package Manager), but it still won't start.

Help please,

Thanks

---

### Post by anemptygun on 2008-04-09
Try opening the terminal and typing this command.

```

sudo apt-get autoremove amsn

sudo apt-get install amsn

```

---

### Post by dwally89 on 2008-04-09
Tried that and still doesn't work.

Any other ideas?

---

### Post by anemptygun on 2008-04-09
If you open amsn in the terminal do you get any errors?

---

### Post by dwally89 on 2008-04-09
I typed amsn in on the terminal, pressed enter, and the cursor just blinks, no messages, nothing appears.

Any idea whats going on?

---

### Post by anemptygun on 2008-04-09
Not sure mate.. what do you think of pidgin?

---

### Post by dwally89 on 2008-04-09
Have tried using it in the past, wasn't too fond of it.

Really need aMSN back.

Thanks

---

### Post by Crafty Kisses on 2008-04-09
> **dwally89 said:**
> Have tried using it in the past, wasn't too fond of it.

Really need aMSN back.

Thanks

Have you tried running aMSN through the Terminal?

---

### Post by dwally89 on 2008-04-09
<quote>
I typed amsn in on the terminal, pressed enter, and the cursor just blinks, no messages, nothing appears.
</quote>

---

### Post by Crafty Kisses on 2008-04-09
> **dwally89 said:**
> <quote>
I typed amsn in on the terminal, pressed enter, and the cursor just blinks, no messages, nothing appears.
</quote>

That's really weird, I'm pretty sure aMSN needs a codec to run, not sure which one though because I remember I was using it awhile back and it was asking me to install some codecs. I'll look into it and when I find the proper information, I'll post it up.

---

### Post by anemptygun on 2008-04-09
Maybe if pidgin doesn't suit you, you might find kopete, Emesene, or Kmess suitible.

---

### Post by dwally89 on 2008-04-09
Would prefer not to move to another IM, after all:
1. It doesn't solve the problem as to why aMSN isn't working
2. And I'm used to aMSN etc.

I don't know if this matters (being a beginner and all), but i'm running the Hardy Beta.

Thanks

---

### Post by Crafty Kisses on 2008-04-09
> **dwally89 said:**
> Would prefer not to move to another IM, after all:
1. It doesn't solve the problem as to why aMSN isn't working
2. And I'm used to aMSN etc.

I don't know if this matters (being a beginner and all), but i'm running the Hardy Beta.

Thanks

That could be a possible issue, you might want to wait to the official release then retry aMSN, but for now, you can use Kopete or Pidgin, both real simple clients, with great interfaces I think, but again, the official release is only 2 weeks away.

---

### Post by dwally89 on 2008-04-09
Kk i'll try Kopete.

If anyone else has any ideas as to why aMSN won't open, then please let me know.

Thanks

---

### Post by dwally89 on 2008-04-09
Ok i've installed Kopete, and that doesn't open either :-(
I think there must be some bug in Hardy.
Hopef it'll be fixed when the final release arrives (or before then).

If anyone has any ideas, then please let me know

Thanks

---

### Post by dwally89 on 2008-04-09
Ok listen to this.

So I had another problem, which I thought was totally unrelated.
My main partition was getting full, so on the forums someone just told me to run the following commands:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

So I ran them, then I try to open aMSN, and tada, it works, I then try to open kopete, and that works too.

Why should be being low on diskspace prevent me from opening certain programs?

Thanks

---

