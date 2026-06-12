---
title: "[SOLVED] Ubuntu Updates -&amp;gt; can't be authenticated"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by penguinv on 2008-01-27
The last batch of 8 Ubuntu updates "can't be authenticated"

What's up? A Linux virus? I have gotten this same error message 2 days running.

Naturally I have no installed them. And no one else has posted about this.


 Is my system special? 

Am I the only one awake?

Please help this Absolute Beginner.

---

### Post by emarkd on 2008-01-27
Are you installing software using a third-party repository?  If you add more repositories to your Synaptic configuration, you'll also have to have the gpg key for the repo in order to avoid that message.

---

### Post by argraff on 2008-02-03
I'm having occasional bouts of this too - the last one was called app-data-commercial or something. I didn't download it, but thought to ask today about it, clicked on it and it no longer gave me that warning. Doesn't make sense!

Help!

---

### Post by SunnyRabbiera on 2008-02-03
this is usually nothing to worry about, just remember the more third party repositories you add the more of a chance this warning message will pop up.
But relax, most of the third party repositories offered here are reliable.

---

### Post by casperlingus on 2008-02-07
This is NOT a third-party repo issue.  The items are listed under "Important security updates."

I have attached an screenshot of the window:  it includes 
"linux-headers-2.6.22-14"
"linux-libc-dev"
"linux-source-2.6.22"
"linux-image-2.6.22-14-generic"

There's NO reason these should not be authenticated.  I'm very suspicious.

---

### Post by philinux on 2008-02-07
Open a terminal and use

sudo apt-get update 

then try the update manager

---

### Post by Golem XIV on 2008-02-07
It probably just means that the connection with the server was interrupted before the GPG keys could be verified, maybe because everyone is downloading those same updates :-)

If you're paranoid (which is a good thing to be) just refresh the updates list (either on the terminal with **sudo apt-get update** or directly from synaptic) to verify the GPG keys and the warning should go away.

<edit> Philinux beat me to it.  I'm a slow typer :-) </edit>

---

### Post by dstew on 2008-02-07
Same problem here with an attempted Edgy update. **sudo apt-get update** stalls at the security archive step.

---

### Post by zvacet on 2008-02-07
If you are geting updates from official Ubuntu repos,just download them.

---

### Post by argraff on 2008-02-09
Scary thought: someone hacks into Official Ubuntu Repos and adds mean malicious thing into updates. :shock: Is that possible? That's what I'm worried about. (I always had that fear with M$ too, though, so it's just my nature...)

---

### Post by sandysandy on 2008-02-09
have faced similar issue with security updates to 7.10

regards

---

### Post by casperlingus on 2008-02-14
> Scary thought: someone hacks into Official Ubuntu Repos and adds mean malicious thing into updates.  Is that possible? That's what I'm worried about. (I always had that fear with M$ too, though, so it's just my nature...) 

Unlikely for someone to hack the signatures on the packages, even if they get onto the Ubuntu servers.  Every important signing certificate is not only well-guarded, but protected with a password.  And these are encryption passwords, for which there are no real backdoors, unlike OSes for which there are multiple ways of bypassing a password.

If I was going to inject malicious updates into the system, I would just sign them with a random key and let users will click through the "NOT AUTHENTICATED" dialog, as most users would.  Much easier than trying to hack the actual repos :-)

Hence, why I was suspicious of these updates.  

-Casperlingus

---

### Post by penguinv on 2008-02-18
Thanks all for sharing. Good to know I am not alone.
The problem lasted for days, then vanished.

IMHO someone fixed something upstairs.
Heh.

Thank you Ubuntu Gods.
Self-Solved.

---

### Post by Boelcke on 2008-02-18
Yep, I hit the "check" button once on the Update Manager, and then it stopped warning me about that.  I wonder why it did that hiccough?  Someone here on the thread suggested that it was because the server was busy with everyone updating it at the same time.  Here I am a week later, though.  I wonder why it didn't validate it?

---

