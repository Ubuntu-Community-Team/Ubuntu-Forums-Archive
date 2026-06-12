---
title: "Unity panel autohide not working in Precise"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by Diskdoc on 2012-04-26
Installed 12.04 (beta) with updates on an iBook G4. If I switch on the autohide feature, the Unity-panel disappears but doesn´t come back when I move the mouse to the left side of the screen, or into the upper left corner.

Any solution/workaround for this?

---

### Post by MaxxABillion on 2012-04-26
I just downloaded the official version of 12.04 and I am having the same problem.

---

### Post by Diskdoc on 2012-04-27
Submitted a [ bug report ]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/989477")

---

### Post by greyback1 on 2012-04-27
Hi guys,
a big change in Unity & Unity 2D is that the launcher reveal works differently. 

In Oneiric you just moved your cursor to the left edge and paused for a second for the Launcher to appear.

However in Precise this has now changed, and you need to push the mouse  cursor into the left side of the screen. Just keep moving your mouse left even though it's at the screen edge. Don't move it slowly :)

How much you need to push  before the launcher gets the hint to reveal is adjustable in System  Settings -> Appearance in the Behaviours tab.

This is to help prevent accidental reveals of the Launcher & I find it works well.

Please let me know if that helps
-Gerry

---

### Post by canhoto on 2012-04-29
> **greyback1 said:**
> Hi guys,
  need to push the mouse  cursor into the left side of the screen. Just keep moving your mouse left even though it's at the screen edge. Don't move it slowly :)

How much you need to push  before the launcher gets the hint to reveal is adjustable in System  Settings -> Appearance in the Behaviours tab.

(...)

Please let me know if that helps
-Gerry

It didn't help. I tied it. I pushed, I pushed, and nothing happened.

---

### Post by Enigmapond on 2012-04-29
This is an ongoing bug that should get fixed soon. What happens when you do:
```
unity --replace
```

This fixes it until the next time. Be patient they are working on it.

---

### Post by canhoto on 2012-04-29
> **Enigmapond said:**
> This is an ongoing bug that should get fixed soon. What happens when you do:
```
unity --replace
```This fixes it until the next time. Be patient they are working on it.

I have a black screen and then the Unity 3D dash, with most of the icons completely white (that's why I use 2D).

But I'll wait.

---

### Post by rsavage on 2012-04-30
> **Enigmapond said:**
> This is an ongoing bug that should get fixed soon. 
....
Be patient they are working on it.
 
This is entirely the wrong attitude.  We're talking unity-2d here not autohide problems with nvidia proprietary drivers under unity-3d that you'll find on other threads.
 
It certainly isn't ongoing because I remember testing it at some point in 12.04 development (probably around first beta).  Unfortunatly I didn't pick up it had stopped working.
 
As far as I can tell diskdoc's is the only bug report on the problem so people need to help the developer on that bug report.  Currently it is marked as 'incomplete' which means without further action by somebody it is unlikely to get looked at.

---

