---
title: "Kismet Help (Setting Up)"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-11
Hi, I just install Kismet through the Synaptic Package Manager and do not
see an icon anywhere in my menu. I have been told that you have to set
up the .conf file but I am unsure how to do this or even where it's located.
I'm not even sure how to start it.

I am using a Linksys WPC11 802.11b card.

Any help on this would be great.... Thank you.  :KS

I tried looking for the path of the config file but either
the path is wrong or I can't see it because I'm not root.
Is there a command I can use like I do in Gnome to
Navigate windows a root.  Example: gksudo nautilus

I'm using Xubuntu 6.06 LTS because that's all the power
this laptop will push.  From the looks of it there is no
root account.

---

### Post by MattJ100 on 2007-09-12
Kismet is a somewhat advanced application. If you are not the technical type, it won't mean much.

However since it is a text-based application, you should start it from Terminal. Just type 'kismet' and hit enter.

To run a program as root, type: sudo <program name>, and then enter your password if prompted. The root account in Ubuntu is disabled for security: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Yes, you need to edit the config file first to set the capture source. It is located in /etc/kistmet/ if I remember rightly. Exactly how you need to edit I am not sure... I don't have your kind of card, sorry :|

Find more info about setting the capture source in part 12 of the documentation here: [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

---

### Post by Orbital75 on 2007-09-12
Got it all set up.... It wasn't to hard just had to search a good bit for
what type of card type I needed.

In order to change the kismet.conf, I need to
sudo mousepad /etc/kismet/kismet.conf

that opened up my conf file
I then added myself as the dropback suid  ( My User Name )

After this I need to add the info about my card.

**'source=type,interface,name[,channel]'.  **  ( channel is optional )

'source=hostap,etho,Prism2

Saved that then was ready to run the program.

sudo Kismet

All set up ready to go.....

---

