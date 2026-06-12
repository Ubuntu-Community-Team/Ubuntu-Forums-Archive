---
title: "Suddenly no sound from my machine."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by mmasroorali on 2008-03-19
Recently I migrated from Fedora 8 to Ubuntu 7.10 in my home machine. After fresh installation, sound was working alright. Then I upgraded the system and installed more than three hundred packages. Now, sound is not coming out. 

I have checked. The sound level is set at 100%. Speakers are not muted. When the same machine is booted from live CD, sound comes back. 

This is so frustrating. Could you please tell me how can I get the sound back? My initial hunch is that may be some process has taken hold of the sound system. But may be it is something else. 

I tried alsamixer and then set everything to 100% without any result,

Your input will be highly appreciated. Feeling desperate.

Regards.

---

### Post by superprash2003 on 2008-03-19
hope this helps u [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by mmasroorali on 2008-03-19
I already tried setting the Device in Sound Preference. It did not work for me.

Thanks for your post.

---

### Post by bubonic1347 on 2008-03-19
I realize that this won't help you much, but I had the exact same problem. I was going great with 7.10 then I did an update and then...no sound. 

You're also not going to like how I fixed it.

I installed the Alpha 4 of Hardy Heron.

My sound now works.

---

### Post by mmasroorali on 2008-03-19
It works!

It is difficult to pin it down. I did so many installations and uninstallations. At one point in alsamixergui I set PCM to 100%. But I believe that I did this before without any avail.

---

### Post by Rome.konig on 2008-03-19
yeah when i installed hardy i had sound, and after a few updates my sound went away just like you. I gave it a day or two and new updates showed up, so i installed them and it fixed my sound problem. Glad we can all hear now YAY!

---

### Post by mmasroorali on 2008-03-19
A reboot further reveals the nature of the problem. 

PCM gets muted at each boot. To correct, you boot the machine, go to alsamixer and then press M at PCM to unmute it. Use alsamixergui if you want a mouse click.

How to make PCM not going dumb at each reboot?

---

### Post by Rome.konig on 2008-03-19
try going in system/preferences/sessions and save your current running session when your sound is on, then reboot, "its a long shot but hey if it works, then it works."

---

### Post by mmasroorali on 2008-03-19
Now another problem is detected. For non administrator users, no sound is coming out of applications. The same applications work well for the administrator.

Yes, I did check. These users belong to the audio group. They can also use the System, Preference, Sound and play those test tunes (which are actually heard).

How to solve this?

---

