---
title: "Front Jacks on eMachines"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by HeyGabe on 2006-08-24
I have an eMachines T3256. It has front mike and headphone jacks, but Ubuntu doesn't seem to recognize them. 
Any suggestions?

---

### Post by Scythe!? on 2006-08-24
I have a eMachines too. The front jacks are actually plugged into the motherboard and so the connection must be loose or something. The front jacks (sound & microphone) work fine in Windows & Ubuntu 6.06

---

### Post by HeyGabe on 2006-08-24
> **Scythe!? said:**
> I have a eMachines too. The front jacks are actually plugged into the motherboard and so the connection must be loose or something. The front jacks (sound & microphone) work fine in Windows & Ubuntu 6.06

They work fine in Windows. They work for the headphones, even cut the speakers off if a set is plugged in, but the mic doesn't pick up sound. 

Here's what I get when I do "aplay -l"
[INDENT]
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/INDENT]


EDIT: 
When I launch Audacity, I get an error message: "There was an error initializing the audio i/o layer. You will not be able to play or record adio. 
Error: Host Error.

---

### Post by oliverb on 2006-08-24
I use one at work and the front mic jack just doesn't work.

I've a similar one at home and both front jacks are fine.

---

### Post by aysiu on 2006-08-24
I have two eMachines and the front jacks work just fine in Ubuntu.

I'm with Scythe?! on this one--maybe it's a physically loose connection?

---

### Post by HeyGabe on 2006-08-24
> **aysiu said:**
> I have two eMachines and the front jacks work just fine in Ubuntu.

I'm with Scythe?! on this one--maybe it's a physically loose connection?

I thought this too. So I fired up the ol' livedisk. 

The jacks work perfectly. I'd like to fix whatever broke with my current install, but I'm afraid I don't know enough about hardware to really be able to troubleshoot it myself. Any suggestions?

---

### Post by aysiu on 2006-08-24
Hm.

So it worked in Windows.
It works with the live CD of Ubuntu.
Doesn't work with installed Ubuntu.

Is that correct?

---

### Post by HeyGabe on 2006-08-24
Ring-a-ding.

---

### Post by aysiu on 2006-08-24
One more thing to test.

Create a new user named *testaudio* and make sure the new user belongs to all the same groups as your old user.

Log in as that user and see if that new user has the same problem.

This is really to see whether your entire installation of Ubuntu is messed up or if somehow the particular user modifications you've made since you installed have been messed up somehow.

---

### Post by HeyGabe on 2006-08-24
Yes!
sndtest can use the front jacks!
I take it this is a confirmation of my breaking things.

---

### Post by aysiu on 2006-08-24
It just means something happened to your current user... it could be anything, I guess--maybe a theme you installed or... I don't know, actually.

---

