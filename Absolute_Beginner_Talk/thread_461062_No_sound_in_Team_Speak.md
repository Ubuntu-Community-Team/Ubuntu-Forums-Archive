---
title: "No sound in Team Speak"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-06-01
I installed Team Speak from add/remove, but I can't hear or say anything. I'm set to mute for both input and output and I can't change the setting. I think I'm missing a setting or some sort of dependency.

---

### Post by Crafty Kisses on 2007-06-01
Hmmm, you might want to install your sound drivers, and install the Multimedia codecs.

---

### Post by Hellcom on 2007-06-01
What sound drivers and what codecs? I'm not sure what you are talking about :S

---

### Post by Crafty Kisses on 2007-06-01
> **Hellcom said:**
> What sound drivers and what codecs? I'm not sure what you are talking about :S

That's completley ok. Here let's try this.

You should try to download "AutoMatix" although I really never recommend it that often I will in this case.
[http://getautomatix.com]("http://getautomatix.com")
That will install all the Multimedia codecs and Drivers you need.
Any questions post back.:D

---

### Post by Hellcom on 2007-06-01
> **Codename said:**
> That's completley ok. Here let's try this.

You should try to download "AutoMatix" although I really never recommend it that often I will in this case.
[http://getautomatix.com]("http://getautomatix.com")
That will install all the Multimedia codecs and Drivers you need.
Any questions post back.:D

Already have those codecs installed :(

---

### Post by Hellcom on 2007-06-01
bump

---

### Post by srt4play on 2007-06-01
Are you using any other audio applications when teamspeak doesn't work such as listening to music? You could try installing 'esound-clients' in Synaptic and running teamspeak with the command 'esddsp teamspeak'.  This will use a wrapper and force sound output from teamspeak to go through esd.

---

### Post by Hellcom on 2007-06-01
> **srt4play said:**
> Are you using any other audio applications when teamspeak doesn't work such as listening to music? You could try installing 'esound-clients' in Synaptic and running teamspeak with the command 'esddsp teamspeak'.  This will use a wrapper and force sound output from teamspeak to go through esd.

Thanks, that worked!

---

### Post by srt4play on 2007-06-01
cool, could you modify the title of the thread to include RESOLVED?

---

### Post by Hellcom on 2007-06-01
> **srt4play said:**
> cool, could you modify the title of the thread to include RESOLVED?

I can't edit the thread title, sorry.

---

