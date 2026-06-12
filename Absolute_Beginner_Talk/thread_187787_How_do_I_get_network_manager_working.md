---
title: "How do I get network manager working?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by michaeljb2005 on 2006-06-03
I downloaded and installed network manager and it's frontend so how do I run it?

---

### Post by tonyr on 2006-06-03
What is it that you are trying to do?  What packages did you install?  For
**network-manager**, Synaptic says
> 
NetworkManager attempts to keep an active network connection available at
all times.  It is intended primarily for laptops where it allows easy
switching betwen local wireless networks, it's also useful on desktops
with a selection of different interfaces to use.  It is not intended for
usage on servers.


Is that what you're after?

EDIT: A brief search on the forums indicates that **sudo nm-applet** in a terminal seems to
be the ticket.  There are complaints that it shouldn't require **sudo**; maybe
a bug.

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=tonyr]What is it that you are trying to do?  What packages did you install?  For
**network-manager**, Synaptic says


Is that what you're after?[/QUOTE]

Yes that's what i'm after.

---

### Post by tonyr on 2006-06-03
See my EDIT in previous post.

---

### Post by Jason_25 on 2006-06-03
Once you install it, you need to log out and log back in.

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=tonyr]See my EDIT in previous post.[/QUOTE]

All that did was pull up another icon that said no network connection.

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=Jason_25]Once you install it, you need to log out and log back in.[/QUOTE]

My wired connection is disconnected.  I'm only using wireless.  Maybe it's trying to use my wired connection?

---

### Post by Jason_25 on 2006-06-03
Even so, the icon should pop up.  You know that if you have any wireless info listed in your interfaces file that it won't work right?

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=Jason_25]Even so, the icon should pop up.  You know that if you have any wireless info listed in your interfaces file that it won't work right?[/QUOTE]

Ok so what do I do to get it working with wirless then?

---

### Post by tonyr on 2006-06-03
Have you tried to use **System->Administration->Networking**?  If your interface is
recognized at all, there should be something there under **Wireless**.  Choose
Properties to configure the interface.

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=tonyr]Have you tried to use **System->Administration->Networking**?  If your interface is
recognized at all, there should be something there under **Wireless**.  Choose
Properties to configure the interface.[/QUOTE]

The interface is already working but I would like to get Network Manager working so that I can easily find and change wireless networks when I go somewhere else.

---

### Post by tonyr on 2006-06-03
I am stumped.  It ceratinly is not intuitive.  Did you look at
[http://www.gnome.org/projects/NetworkManager](http://www.gnome.org/projects/NetworkManager) ?
Documentation there says that not all wifi cards are supported.

I'm gonna side-step here and suggest that you try **wifi-radar** instead.

---

### Post by michaeljb2005 on 2006-06-03
Dude that so rocks my socks, thank you so much

---

