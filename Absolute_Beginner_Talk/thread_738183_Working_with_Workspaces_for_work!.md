---
title: "Working with Workspaces for work!"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by kneewax on 2008-03-28
Hi folks,  Couldn't find an answer to this in any existing threads so am going out on a limb with a new post.  

Is it possible to limit an application to a specific workspace? For example -  have an app so that no matter which deskspace it is launched from it will always anchor to deskspace 4.

When I used Windoze I used to minimise Thunderbird to the Systray - this about the only thing I miss - I realise from other threads that this isn't possible at the moment (although Amarok does it, but presumably that is in the code rather than via an extension like it was in TB) - so limiting TB to a specific workspace would be a great work around....

cheers
Kneewax

---

### Post by sayakb on 2008-03-28
> **kneewax said:**
> Hi folks,  Couldn't find an answer to this in any existing threads so am going out on a limb with a new post.  

Is it possible to limit an application to a specific workspace? For example -  have an app so that no matter which deskspace it is launched from it will always anchor to deskspace 4.

When I used Windoze I used to minimise Thunderbird to the Systray - this about the only thing I miss - I realise from other threads that this isn't possible at the moment (although Amarok does it, but presumably that is in the code rather than via an extension like it was in TB) - so limiting TB to a specific workspace would be a great work around....

cheers
Kneewax

 Instead of minimizing TB, you might right click on the titlebar -> Move to another workspace -> Desk 4

---

### Post by Joeb454 on 2008-03-28
Try installing alltray :) It sounds like it might be what you're after.

You could use Synaptic/Add Remove, or run the following from a terminal ```
sudo aptitude install alltray
```

---

### Post by kneewax on 2008-03-28
> **LinuxIsInnovation said:**
> Instead of minimizing TB, you might right click on the titlebar -> Move to another workspace -> Desk 4

Yup, that's what I do at the moment.  I just wondered if there was a way of automating that so TB did it on launch - just being lazy really! :)

---

### Post by forrestcupp on 2008-03-28
If you install alltray, you can just edit your menu entry or launcher for Thunderbird so that the command is
```
alltray thunderbird
```
That way it will launch Thunderbird with alltray so when you close it, it will minimize to the notification area and stay open in the background.

---

