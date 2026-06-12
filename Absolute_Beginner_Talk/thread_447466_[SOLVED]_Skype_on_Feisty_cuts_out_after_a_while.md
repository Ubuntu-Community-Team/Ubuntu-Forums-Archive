---
title: "[SOLVED] Skype on Feisty cuts out after a while"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-05-18
When having a conversation on skype after 15-30 minutes the audio breaks up for the other person.  I can hear them fine.  It seems like the problem is with my mic.  I downloaded the package from the repository.  Has anybody else noticed this?  Any ideas on a resolution or is this a bug I should file?

---

### Post by viciouslime on 2007-05-18
Unfortunately I have found this to just be the way skype works, it seems to depend on the amount of bandwidth of the supernode you're connected to. Try hanging up and redialling until you get router through one without problems.

---

### Post by wormser on 2007-05-18
> **viciouslime said:**
> Unfortunately I have found this to just be the way skype works, it seems to depend on the amount of bandwidth of the supernode you're connected to. Try hanging up and redialling until you get router through one without problems.

I never had this issue using skype in windows.

---

### Post by Killtown on 2007-05-18
I just got Skype working tonight.  I noticed the audio wasn't as good, but didn't seem to change in audio quality as my conversation got longer.  Conversation lasted about 25min.

---

### Post by viciouslime on 2007-05-18
> **wormser said:**
> I never had this issue using skype in windows.

I did, but it is a while since i used it. Unfortunately, because it is closed source no one but skype can fix it and they don't seem very bothered about development of their linux client, so reporting a bug may not be much help. Worth a try though...

---

### Post by Killtown on 2007-05-18
What's a good Skype alternative for Ubuntu?

---

### Post by quandary on 2008-01-13
Gizmo – A free phone for your computer
Gizmo Project provides low cost international calling and free calls to users on Yahoo Messenger, Google Talk, Windows Live users and SIP networks.
[www.gizmoproject.com/](www.gizmoproject.com/)

---

### Post by kostkon on 2008-01-13
> **wormser said:**
> When having a conversation on skype after 15-30 minutes the audio breaks up for the other person.  I can hear them fine.  It seems like the problem is with my mic.  I downloaded the package from the repository.  Has anybody else noticed this?  Any ideas on a resolution or is this a bug I should file?

I believe *Skype* is changing the codec used during a conversation from a high quality one to a lower, if it is needed. It is continuously probing the connection quality/speed and the CPU use and alters the audio codec used appropriately.

You can check if this is happening for yourself by going to the application's Options, then select *Advanced -> Other* and tick the *Display technical call info*.

Then, during a conversation, if you hover your mouse pointer over it, a pop-up will show info (including the codec being used) about the connection.

Thus, in your case, something is causing *Skype* to select a very low quality codec after some time in your conversation.

---

### Post by wormser on 2008-01-14
I believe this issue has been resolved.  It was a bug in Skype and I have not had any issues lately.  If you are having a problem make sure you upgrade to the latest version.

---

