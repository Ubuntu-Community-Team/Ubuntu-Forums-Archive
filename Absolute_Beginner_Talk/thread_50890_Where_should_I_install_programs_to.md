---
title: "Where should I install programs to?"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by cueshot on 2005-07-21
Hi!

Okay, this is my first post to this forum or, for that matter, to any forum regarding Linux. I'm a Linux Newbie. I installed Ubuntu 5.04 Hoary about 5 days ago. And I must say I love it! This is my second go at trying out Linux, but my first one with the full willpower to really learn it. I've learned a lot in the last 5 days.

I have a few issues/questions I want to get resolved/answered, but I will not present all of them at once in this thread. I will post a separate thread for each over time. I'll start simple with a question. It's a general Linux question as opposed to an Ubuntu-specific question, but I would imagine that is okay on this forum.

Where should I install programs to?

I know I should use Synaptic whenever possible, and I have. I've already got all my development stuff (php4, mysql, php4-mysql, apache2, screem, etc.), among other things, installed through it. I'm sure there will be times when what I want is not in Synaptic. BTW, I do have the "Universe" repository added to Synaptic.

I'm not sure where the most sensible place is to install programs. During my research I've seen different things mentioned.

Install to my Home directory!?
Install to /usr/share!?
Install to /usr/local!?

I suppose it's whatever I prefer, but I'm wondering what would make most sense. What is the typical place most Linux users install programs to?

Thanks,
cueshot

---

### Post by grofaz on 2005-07-21
Good question, I'd like to know as well.

---

### Post by musicman2059 on 2005-07-21
ense to install to /usr/share IIRC

---

### Post by fishfork on 2005-07-21
I wouldn't choose /usr/share/, the system puts lots of things here. Sometimes people install things to /usr/local, but I would recommend using /opt. This keeps them seperate from files installed by the package manager. Give each program it's own directory like /opt/firefox, /opt/Azureus.

---

### Post by dataw0lf on 2005-07-21
Both /usr/local and /opt are viable solutions.  /usr/local is traditionally where the 'local' system administrator places whatever software he wishes into.  /opt has oft been used for more 'commercial' packages.  Either/or.  I use /usr/local

---

### Post by poofyhairguy on 2005-07-21
As you can tell...there is no consensus. I like the home directory personally.

---

### Post by cueshot on 2005-07-21
Thanks for your input everyone. After seeing your responses, I'm leaning more toward using the /opt folder. Also seeing that it comes empty by default, that should make for cleaner organization.

L8r

---

### Post by stig on 2005-07-22
The well-known "Linux for Dummies" book lists the main directories on page 287 and has the following:
"opt: The location that many people decide to use for installing new software packages, such as word processors and office suites."

Also:
"usr: The programs that machines can share between them."

---

### Post by doclivingston on 2005-07-22
I tend to put them in my home directory (usually ~/opt/AppName), because that way I don't have to worry about messing something up while installing as root. But either /opt or /usr/local work fine too.

---

