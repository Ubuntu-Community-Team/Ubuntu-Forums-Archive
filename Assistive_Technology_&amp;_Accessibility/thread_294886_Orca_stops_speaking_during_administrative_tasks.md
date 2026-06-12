---
title: "Orca stops speaking during administrative tasks"
date: 2006-11-07
forum: Assistive Technology &amp; Accessibility
---

### Post by frequency660 on 2006-11-07
Hi all. I'm new to linux, and have just installed ubuntu. When I need to run a program as root, orca stops speaking. When I alt f4/escape out of it, speech is back. Are there ways around this?

---

### Post by frequency660 on 2006-11-08
I did some googling, and came up with this:

Gaining access to gui based administration tools

If you attempt to access any gnome based administration utilities such as gdm setup or synaptic, you will notice that by default, in order to do so, you
will need to enter your sudo password. Although the use of sudo provides an extra layer of security, it also presents a challenge in terms of accessibility
when it comes to the gui. In a nutshell, the issue is that programs which require sudo are being launched from an account different than that of the user
who is running Orca. At present, accessibility information can not be communicated across accounts. Therefore, when an application is run in this manner,
Orca is unable to provide useful feedback.

One way around this issue is to enable the root account, and to allow the root user to login to gnome. This can be accomplished as follows: set a password
on the root account: 'sudo passwd root'. Next, edit /etc/gdm/gdm.conf-custom and add the following line under the [security] section: AllowRoot=true

Reboot your system. Now, log in as root via a text console, and run orca --setup.You're all done. You can now login to gnome as root, run Orca and administer
your system to your heart's content.

The only disadvantage to this approach is that although they are accessible via the command line, none of the administration tools appear in the start menu
for the root user.

So now my question is, is it possible to make these items appear in the administration menu? Either that, or a way to find out the command line equivalents to run them?

---

### Post by Henrik on 2006-11-10
You can add the menu items in manually with the menu editor (not great, I know).

The good news is that this will all be fixed properly in Ubuntu 7.04, currently being developed. That will also make the installer easier to use.

---

