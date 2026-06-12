---
title: "Is this is a Bug ???"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by avender on 2006-01-21
Hi,

I'm using Kubuntu 5.10, and when I want use system settings in kubuntu I'm getting some thing like below.

If look at it, you'll come to know that "Administrator Mode" button is not visible. Is this is a bug ?? Are you people getting the same thing ? If it is a bug then where to report ?

Since I'm not getting "Administrator Mode" button I used **$sudo ifconfig** to configure my Ethernet Card.

---

### Post by avender on 2006-01-21
Hey, I think I've written this post in the wrong section, How to move this message to Kubuntu support forum ?

Sorry for the mistake. :(

---

### Post by dueY on 2006-01-21
[QUOTE=avender]Hey, I think I've written this post in the wrong section, How to move this message to Kubuntu support forum ?

Sorry for the mistake. :([/QUOTE]

Maybe someone with Kubuntu can help you here.  Other than that a moderator will have to move it if you want it moved.

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=avender]Hi,

I'm using Kubuntu 5.10, and when I want use system settings in kubuntu I'm getting some thing like below.

If look at it, you'll come to know that "Administrator Mode" button is not visible. Is this is a bug ?? Are you people getting the same thing ? If it is a bug then where to report ?

Since I'm not getting "Administrator Mode" button I used **$sudo ifconfig** to configure my Ethernet Card.[/QUOTE]
I think you need to run it with "kdesu".

---

### Post by GoldBuggie on 2006-01-21
System Settings has a bug with resolution 1024. The windows is to big. To go around it either use the alt button to drag the window and show the administrator button or start using kcontrol which is the kde control center which doesn't have this problem.

As mentioned above, running it with kdesu is also a solution, maybe putting a kmenu entry for "system settings(root)".

---

### Post by JNowka on 2006-01-21
yes it is a bug, had a problem with this myself.

use run command from the menu button at the bottom left side of the screen.

then run the command kcontrol.

this should bring up a system settings menu but in a smaller format.

this is the only way around this bug that I have found.

---

### Post by TheForumTroll on 2006-01-22
If its hidden behind the panel why not just hide it?

---

