---
title: "firewall and azurues"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Caton420 on 2007-08-28
azurues says its firewalled and will not dl anything

---

### Post by WinterWeaver on 2007-08-28
if you are behind a router you will need to forward the port that azureus is using there.

go to: [www.portforward.com](www.portforward.com)

by default the ports in Ubuntu is open, so you might not need to do the following. However I think it's a good security measure to follow
anyway... install firestarter.
```
sudo apt-get instal firestarter
```

In firestarter, also add the port as a inbound policy.

---

### Post by Caton420 on 2007-08-28
apperintally its installed how do i get to  it to add port?

---

### Post by WinterWeaver on 2007-08-28
system >> administration >> firestarter

next go the policy tab

make sure that **Editing** is on "Inbound"
right-click in the bottom white box and select "Add Rule"
Type in the port (you dont need a name)
make sure "Anyone" is selected
click Add

Now in the Toolbar for Firestarter, click the "Apply Policy" button.

NOTE: this wont do you any good if you have not forwarded your port on the router.
go to, [www.portforward.com](www.portforward.com) , and from there you can find out how to forward ports on your router.

hope it helps.

WW

---

### Post by Caton420 on 2007-08-28
"make sure that Editing is on "Inbound""
how do i do this? b/c add pol. is not lite up

---

### Post by Dirk Lately on 2007-08-28
> **WinterWeaver said:**
> if you are behind a router you will need to forward the port that azureus is using there.


I just intalled Azureus and although I'm behind a firewall, I never told Azureus what port I had forwarded. And yet it seems to work just fine.

Odd.

When I was setting up utorrent in Windows, it was a nightmare to get the thing to seed; this was easy! I would have expected it not to work until I told it what port to use.

---

### Post by Caton420 on 2007-08-28
mines dosent... like i said its not allowing me to click add rule

---

### Post by Caton420 on 2007-08-29
could i please get some help with this it seems like it must be a common problem

---

