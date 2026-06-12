---
title: "Talk About Frusterating!"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2005-12-29
So, I've got my DSL hooked into Ubuntu through the ethernet cord, and whadda know, it won't pick up.

I go into networking, enable it, tell it it's DHCP or whatever, connect it...

Nothing.

So I restart the whole computer.

AND GUESS WHAT POPS UP? A little box that states:

"Could not look up internet address for ColemanNetwork (my network name).
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
ColemanNetwork to the file /etc/hosts/"

Then is asks me if I want to "Log in anyway" or "Try again".

Try again does nothing.

Log in anyway will not let me use any administraitive things, like the Synaptic package manager or the Network settings (WHICH IS WHAT I WANT TO USE ANYWAY GRRRR)

So. I screwed myself over. Help?

---

### Post by Zimmer on 2005-12-29
[QUOTE=SZF2001]So, I've got my DSL hooked into Ubuntu through the ethernet cord, and whadda know, it won't pick up.

I go into networking, enable it, tell it it's DHCP or whatever, connect it...

Nothing.

So I restart the whole computer.

AND GUESS WHAT POPS UP? A little box that states:

"Could not look up internet address for ColemanNetwork (my network name).
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
ColemanNetwork to the file /etc/hosts/"

[/QUOTE]
Your Network name?  do you mean the computer name for the network?
If so, does your hosts file have the first entry as something like this...
127.0.0.1	localhost.localdomain	localhost ColemanNetwork

and does your hostname file have the entry   ColemanNetwork ?
Regards

---

### Post by ubuntuuser on 2005-12-29
Have you actually tried to add ColemanNetwork to /etc/hosts/?
And what exactly happens after you try to start synaptic or whatever admin program you want to use?

---

### Post by Mustard on 2005-12-29
I would say you will need to get to a root prompt in terminal to edit your /etc/hosts file, as your sudo command is probably fubared as well. To do this you could use the 'Recovery mode' option in your grub menu at startup.  When you get to a root prompt, type nano /etc/hosts and this will open up the /etc/hosts file in a text editor.  Make the necessary changes and then save the file and try logging in again.

The first line of my /etc/hosts file looks like this....

```
127.0.0.1       localhost.localdomain   localhost       slave

```

You would need to substitute your hostname for the part above that says 'slave'.

---

