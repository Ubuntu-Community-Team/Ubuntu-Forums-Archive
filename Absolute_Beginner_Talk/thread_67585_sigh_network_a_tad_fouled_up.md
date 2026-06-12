---
title: "*sigh* network a tad fouled up"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by NaOH on 2005-09-20
Hello all.  I've got a bit of a problem here, maybe someone can help.  Someone had switched around my LAN cables on my router (I suspect a younger sibling).  Long story short, I once again have internet, but everytime i start up I get the little warning that there is no network connection present which can cause gnome to malfunction, and malfunctioning it is.  It seems I no longer have access to the synaptic package manager, updates, and System>Administration>Networking   ](*,)   .  Thank you!

---

### Post by matthew on 2005-09-20
I wish I had a better answer for you, but short of coming to your house and tracing every cable and making sure it is plugged in correctly in the correct places I don't know how I could help you.

EDIT: I guess I could give you the basic plan, anyway.
1) cable comes from the wall to the modem in
2) then a cable should go from the modem out to the router in and from the router out jacks to each individual computer

---

### Post by mlomker on 2005-09-20
Can you be more specific?  What is the error when you try to go into those things?  If you can surf the web then everything else should be fine.

---

### Post by NaOH on 2005-09-20
The cable configuration isn't an issue at all, i've got that squared away.  When I try to access the listed things i get no error at all.  In fact, i get absolutely no reaction.  For instance, the update icon is in my task area now, and no matter how i try to open it, i get no reaction.  Same with the network config and the synaptic package manager, simply no reaction.  Unfortunately that is as specific as it gets.  No reaction

---

### Post by mlomker on 2005-09-20
>   No reaction

That's a tough problem.  One strategy is to open a terminal window and then type **sudo synaptic**.  Sometimes you'll then get some errors in the terminal window that you wouldn't otherwise see.

---

### Post by NaOH on 2005-09-20
wow, that brought it up.  But still, I wish to get to the problem at hand.  Here's another interesting tid bit.  Everytime I use the sudo command i get the following message before the password prompt:   "unable to lookup ubuntu via gethostbyname()"

anymore ideas?

is there a command to bring up the network settings window and the update window?

---

### Post by mlomker on 2005-09-20
>    "unable to lookup ubuntu via gethostbyname()"

Check the contents of your /etc/hostname and /etc/hosts files.  The name of your computer probably isn't in there.

Here's what mine looks like:

```

root@mlomkernote:/etc # cat hostname
mlomkernote
root@mlomkernote:/etc # cat hosts
127.0.0.1       localhost.localdomain   localhost       mlomkernote

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@mlomkernote:/etc #  

```

> 
is there a command to bring up the network settings window and the update window?

network-admin
update-manager

---

### Post by SilentCacophony on 2005-09-20
I once had what seems to be a similar problem after a power outage. With mine, the router had fouled up and given my computer's ip to the other on the network, and left mine in limbo.

Just in case you haven't tried it, what I needed to do was power everything off, and restart them in the proper order (modem -> router -> computer in my case, making sure each finished it's init process before starting the next.)

---

### Post by matthew on 2005-09-20
[QUOTE=SilentCacophony]Just in case you haven't tried it, what I needed to do was power everything off, and restart them in the proper order (modem -> router -> computer in my case, making sure each finished it's init process before starting the next.)[/QUOTE]
That is a great idea and was going to be my next recommendation, but you beat me to it.

---

### Post by NaOH on 2005-09-21
[QUOTE=mlomker]Check the contents of your /etc/hostname and /etc/hosts files.  The name of your computer probably isn't in there.

Here's what mine looks like:

```

root@mlomkernote:/etc # cat hostname
mlomkernote
root@mlomkernote:/etc # cat hosts
127.0.0.1       localhost.localdomain   localhost       mlomkernote

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@mlomkernote:/etc #  

```



network-admin
update-manager[/QUOTE]

When i try to open network-admin through the terminal the application comes to a complete hault...

So i checked out both of these files, and hostname simply says    ubuntu    and hosts simply says    # The following lines are desirable for IPv6 capable hosts


is there someway i can reconfigure these?

---

### Post by mlomker on 2005-09-21
> is there someway i can reconfigure these?

Just edit them so that they're similar to the ones that I posted (my hostname is mlomkernote).

```

sudo nano /etc/hostname

```

Nano is a fairly friendly editor that you can use from a terminal.  There are a million ways to edit files.  You could also run **gksudo gedit** if you prefer a graphical editor.

---

### Post by NaOH on 2005-09-22
drat, the topic dies
r.i.p.

---

