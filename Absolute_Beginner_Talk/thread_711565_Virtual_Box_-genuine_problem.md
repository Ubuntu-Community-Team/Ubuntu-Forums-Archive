---
title: "Virtual Box -genuine problem"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2008-02-29
Please note from my sig that this refers to Kubuntu.

I've just used Adept manager to install VirtualBox and I've been left with three strange problems:

1) My log-in screen which used to show five different accounts, has been replaced with a different screen that shows only my account. All the other accounts still exist, they just don't show up on the log-in screen

2) Even though I can find the VirtualBox executables, in /usr/lib/virtualbox, nothing happens when I try to run any of them.

3)I get a notification in my task bar saying that the mixer cannot be found.

I noticed in a couple of magazines that I would need libxalan110 and libxerces27 as dependencies, so I installed them before I installed VirtualBox

---

### Post by sumguy231 on 2008-02-29
1.) You should be able to fix that from System Settings, in 'login manager' under the advanced tab. Make sure to enter Administrator Mode once you're there.
2.) Do you have a /usr/bin/VirtualBox? That launches it for me.
3.) I think that's probably unrelated to VirtualBox, but what happens when you start kmix manually?

I should mention that I'm using the Virtualbox repository from the Innotek website without problems. You might try that.

---

### Post by tonymoloney on 2008-02-29
1) I tried that to no avail before I came to the forum. All the users are ticked!
2) No, I don't have a /usr/bin/VirtualBox
3) If I start Kmix manually, I get nothing showing in the current mixer drop down box.

---

### Post by tonymoloney on 2008-02-29
Bump

---

### Post by tonymoloney on 2008-02-29
Well, it looks like I'll just have to uninstall what I've installed and if that works, I'll try the innotek website.

---

### Post by SOULRiDER on 2008-02-29
Open Konsole and type (yes, with captial V and B)
```
VirtualBox
```
See if it gives you any errors.

---

### Post by tonymoloney on 2008-03-01
Sorry SOULRiDER. By the time I got your response, I had already un-installed VirtualBox and then International time zones caused a problem.
If i can get my two other problems sorted out (which hasn't happened yet) I may try re-installing and following your advice.

---

### Post by SOULRiDER on 2008-03-01
Have you posted about your other issues? Maybe I can help. If you havnt posted yet, post and pm me the links, ill see what i can do.

---

### Post by tonymoloney on 2008-03-01
Yes, they were in my original post, but just so you can try to help me, here they are again:

"Please note from my sig that this refers to Kubuntu.

I've just used Adept manager to install VirtualBox and I've been left with three strange problems:

1) My log-in screen which used to show five different accounts, has been replaced with a different screen that shows only my account. All the other accounts still exist, they just don't show up on the log-in screen

2) Even though I can find the VirtualBox executables, in /usr/lib/virtualbox, nothing happens when I try to run any of them.

3)I get a notification in my task bar saying that the mixer cannot be found.

I noticed in a couple of magazines that I would need libxalan110 and libxerces27 as dependencies, so I installed them before I installed VirtualBox

---

### Post by anewguy on 2008-03-01
I don't know the answers to your other questions, but for a virtual machine do you have a reason that you HAVE to use virtualbox?  I only ask because I long ago tried virtuabox, got it running after some headaches, then tried vmware server (free download from them) and I seem to like it better.

Good luck!  :)

---

### Post by tonymoloney on 2008-03-01
Only reason I tried VirtualBox was that I had read several magazine reviews that seemed to show that VB was easier than the alternatives.

---

