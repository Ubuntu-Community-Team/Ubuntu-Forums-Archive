---
title: "Mouse cursor is not showing after logout and login."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-07-17
At the moment, I'm using using the Ubuntu Feisty Live-CD.

Here is the scenario:

1. I boot using the noapic code. Afterwards, everything loads ok.
2. It logs into the desktop, and things look alright.
3. There are some resolution problems, but that is because I'm using an nVidia graphics card.

When I saw the desktop when I first loaded from the Live-CD, everything was fine: The cursor was showing.

4. However, there is a problem when I logout.

After I logout and log back in, the mouse cursor is gone. 

Why is it gone?

I tried the following:

trial 1:
1. Edit /etc/X11/xorg.conf
2. Insert Option "HWcursor" "off"
3. ctrl+alt+backspace
4. relogin

That didn't work
So, I rebooted with noapic once more.

trial 2: (maybe it was nVidia?)
1. Installed nVidia drivers ([http://ubuntuforums.org/showpost.php?p=2742573&postcount=224](http://ubuntuforums.org/showpost.php?p=2742573&postcount=224))
2. Edited xorg.conf
3. ctrl+alt+backspace
4. relogin

That didn't work.

I figure those were the biggest options available.
I don't know why the mouse cursor does not show after I logout and log back in.

I do know I will eventually use the computer for administrative purposes with multiple users. So, I don't see a way out of this.

I'm using a Compaq sr2020nx computer with a simple ps/2 ball mouse.

---

### Post by Al3xK3aton on 2007-07-17
Several possibilities occur to me, off the top of my head.
1. You could restart the computer. 
2. You could avoid logging out.
3. You could buy a new mouse. (You could definitely find better than a simple ps/2 ball mouse.)
4. Is the cursor invisible, or not present? How important is it to be able to see the cursor?

---

### Post by Genecks on 2007-07-17
> **Al3xK3aton said:**
> Several possibilities occur to me, off the top of my head.
1. You could restart the computer. 
2. You could avoid logging out.
3. You could buy a new mouse. (You could definitely find better than a simple ps/2 ball mouse.)
4. Is the cursor invisible, or not present? How important is it to be able to see the cursor?

> 1. You could restart the computer.

I'm using a Live-CD. It cannot be restarted.

> 2. You could avoid logging out.
I could. But I want to setup multiple users. I want to create a system of administration.

> 3. You could buy [or try] a new mouse.

I think I shall try this next.

> 4. Is the cursor invisible, or not present? How important is it to be able to see the cursor?

I consider it highly important. I don't think the users would be happy to control the computer without a mouse. Unless you know of a daemon that can constantly automate and loop the cursor-find option, then I'm going to need a mouse cursor to display.

---

### Post by Al3xK3aton on 2007-07-17
In that case, I would go with trying a new mouse. A wireless optical scroll mouse ought to work. Good luck!
I hope this helps.

---

### Post by Genecks on 2007-07-19
Using a new, optical mouse did not improve my situation. I still cannot see the cursor after logging out and logging back in.

---

### Post by silhouette on 2007-09-04
Sorry to bring up an old thread. I'm having this same issue. Upon booting everything's fine and I can see the mouse cursor. However, if I log out (or simply restart X), the cursor disappears, forcing me to reboot. Does anyone know if this would be a software issue or hardware issue?

---

