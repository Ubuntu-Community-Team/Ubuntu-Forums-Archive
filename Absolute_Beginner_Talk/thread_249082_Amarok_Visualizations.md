---
title: "Amarok Visualizations"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by snapcase16 on 2006-09-02
I've installed libvisual-0.4.0 as well as libvisual-plugins-0.4.0 to be used with Amarok. I configured them and went through the whole make, make install business. I also installed a few other plugins. XMMS sees all of them while Amarok claims that I must not have libvisual or any plugins installed. I've searched through a few posts on this topic and I haven't seen any resolution   thus far. Any help would be greatly appreciated and I apologize if this is a topic which has come up in the past.

---

### Post by snapcase16 on 2006-09-02
Any ideas? Even if you can't help, I'd be interested to hear from anyone who has any visualizations working for Amarok. Thanks.

---

### Post by Bloch on 2006-09-02
Me too.

I've wasted a good few hours trying to get visualisations to work on amarok.

---

### Post by Jucato on 2006-09-02
Amarok 1.4.2, which is now available in Kubuntu.org, fixes this visualization problem. You might want to upgrade. 

[http://kubuntu.org/announcements/amarok-1.4.2.php](http://kubuntu.org/announcements/amarok-1.4.2.php)

---

### Post by snapcase16 on 2006-09-02
The version of Amarok that I've been trying to use is 1.4.2, but I still can't get anywhere. Have you been able to use visualizations in 1.4.2?

---

### Post by Jucato on 2006-09-02
Yes I have. make sure that you have these 2 installed:

libvisual-0.4-0
libvisual-0.4-plugins

Both of which are part of the updates made available by Kubuntu.org. I'm not sure why they aren't working for you, though, if you have them installed.

---

### Post by snapcase16 on 2006-09-02
Sorry about that, I was using 1.4.1 actually. Thanks for the tip.

---

### Post by fakie_flip on 2006-09-04
Thanks for the tips. I am now able to use most of the visual plugins, but there are a few that show up in the list that I can't use. Have you solved that problem? Is it a bug?

---

### Post by Lord Illidan on 2006-09-07
Hi.
I have Amarok 1.42 installed.

I also have Libvisual 0.4 and plugins installed from apt-get, yet somehow, visuals still don't work. Libvisual not found, etc.

I then tried installing libvisual from source, no go, either.

What can I do?

---

### Post by Dinerty on 2006-09-07
I have the same problem, got all the correct libvisual's installed but keep getting the same error :(

---

### Post by Lord Illidan on 2006-09-07
I solved this problem finally.

I removed amarok from apt-get, then I downloaded the source and compiled it.

I needed to install a bunch of deps but it was quite straightforward. Now I have everything working fine.. Oh, and I also got Amarok 1.43 instead of 1.42

---

### Post by Eddie Wilson on 2006-09-07
Hello,
That seems like a lot of trouble to go through to get something working that should already be working. Is this a bug in Amarok? Has the problem really been solved? I've got the same problems.
Thanks,
Eddie

---

### Post by Dinerty on 2006-09-07
Compiled it from source and installed all the neccessary dependecies, still don't work, I'm not bothered now, still a great player :)

---

### Post by Lord Illidan on 2006-09-07
> **Dinerty said:**
> Compiled it from source and installed all the neccessary dependecies, still don't work, I'm not bothered now, still a great player :)

Strange... Did you install libvisual-dev?

---

### Post by Jucato on 2006-09-07
It's really weird that I got both 1.4.2 and 1.4.3 visualizations to work... And I haven't done anything special AFAIK...

---

### Post by Dinerty on 2006-09-07
> **Lord Illidan said:**
> Strange... Did you install libvisual-dev?

I have:

          libvisual0.2
          libvisual0.2-dev
          libvisual0.2-plugins
          libvisual0.4-0
          libvisual0.4-dev

> **Fenyx said:**
> It's really weird that I got both 1.4.2 and 1.4.3 visualizations to work... And I haven't done anything special AFAIK...

I know it seems quite a common bug though this, seen countless posts with people having the same problem. I don't know if it's to do with me using gnome and am missing some crucial KDE packages?

---

### Post by Lord Illidan on 2006-09-07
> **Dinerty said:**
> I have:

          libvisual0.2
          libvisual0.2-dev
          libvisual0.2-plugins
          libvisual0.4-0
          libvisual0.4-dev



I know it seems quite a common bug though this, seen countless posts with people having the same problem. I don't know if it's to do with me using gnome and am missing some crucial KDE packages?

I also installed libvisual from source..perhaps that might help.

---

### Post by Dinerty on 2006-09-07
> **Lord Illidan said:**
> I also installed libvisual from source..perhaps that might help.

Thanks mate, I really don't mind now.

---

### Post by puppy on 2006-09-07
I downloaded and compiled Amarok from source (1.4.3) but downloaded the libvisuals with synaptic and I'm still not having any luck - I'll try to do the libraries from source too and see if it fixes the probs and report back

---

### Post by Dinerty on 2006-09-07
> **puppy said:**
> I downloaded and compiled Amarok from source (1.4.3) but downloaded the libvisuals with synaptic and I'm still not having any luck - I'll try to do the libraries from source too and see if it fixes the probs and report back

Do you use gnome or kde, just wondered if gnome users where being affected from this kde app?

---

### Post by K_Boomer on 2008-01-12
ok, i installed the plugins and all that and i restarted amarok. i can test the visualizations, but shortly after my computer restarts. Same happens when i go into xscreensaver. theres gotta be something funky going on that is causing both these, but i dont know what.

---

### Post by aonegodman on 2008-02-04
> **Dinerty said:**
> Do you use gnome or kde, just wondered if gnome users where being affected from this kde app?

Hello Amarok users.  Following  this thread to solve visuals in Amarok myself I was able to solve my problem by Synaptic checking for the recommended plug-ins.

I noticed I had one but not the other. Marked it for install and asked Synaptic to do it.

Synaptic installed and I noticed it gathered some additional files from depositories.

The one that caught my eye was ***kcontrol***.  Not sure of others, but it worked for me.

My Amarok is 1.4.8  using KDE 3.5.8  on a Gnome Desktop.   :)

---

