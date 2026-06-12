---
title: "Firestarter"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Dino05 on 2008-01-01
How to make firestarter run automatically whenever I bootup . Currently I run the program manually whenever I start my computer.

---

### Post by satipera on 2008-01-01
go to system prefferences sessions and add the programme to the list

---

### Post by Dr Small on 2008-01-01
I do believe you have a misconception of Firestarter.

Firestarter is not your firewall. It is merely the graphical tool to configure iptables, your firewall. There is no need to have Firestarter running at bootup, as it is not your firewall, but iptables is, which starts at bootup.

Dr Small

---

### Post by Tyche on 2008-01-01
> **Dino05 said:**
> How to make firestarter run automatically whenever I bootup . Currently I run the program manually whenever I start my computer.

Go to System -> Preferences -> Sessions.  On the "Startup Programs" tab, click "+Add".  In the box, enter the name of the program (Firestarter), the command "gksu /usr/sbin/firestarter" (without the quotes), and a Comment, like "Desktop Firewall Tool" (again, without the quotes).  When you boot up, after you sign in, there will be an additional request for your password to enable Firestarter to start.  That's it - that's all there is to it.

Hope this helps.

---

### Post by hyper_ch on 2008-01-01
Tyche:

What's the point in running Firestarter at bootup?

---

### Post by PeterJS on 2008-01-01
If your worried about having your machine firewalled at boot, don't worry about it, it's done atomically with or without firestarter. The firewall is broken in to two components IPtables which is the actual firewall, which is started atuomatically at boot before the system even enables the network interfaces, and then what ever tool you use to configure the firewall in this case firestarter. But firestarter does have some cool logging and monitoring stuff, long story short, see the above post.

---

### Post by MrFSL on 2008-01-01
> There is no need to have Firestarter running at bootup, as it is not your firewall, but iptables is, which starts at bootup.

Dr Small
> What's the point in running Firestarter at bootup?
>  If your worried about having your machine firewalled at boot, don't worry about it, it's done atomically with or without firestarter.

This same question has come up before - over and over again - so let me reiterate that having firestarter startup with the laptop can be very helpful!

Yes iptables in the firewall - however - firestarter gives a graphical representation of when traffic is blocked. It also logs this information. The user can then - dynamically - open up or close ports/services/etc. If a person feels as though they are having problems - firestarter gives an INSTANT notification that might help them discover intrusion attempts. 

Its just interesting that every time this question is asked multiple people jump on the poster saying "you have it all wrong." ... ... just odd ya know?

Anyhow - there is a problem autoloading firestarter. You will always have to enter your sudo password. A work around is available (search the forums I've lost it) but it never worked for me.

---

### Post by Dr Small on 2008-01-01
[quote=MrFSL]A work around is available (search the forums I've lost it) but it never worked for me.[/quote]

Open up visudo:
```
sudo visudo
```


And add this to the bottom:
```
user hostname = NOPASSWD: /usr/sbin/firestarter
```

But, the user and hostname can NOT be the same.
If when you save and close visudo, you get a syntax error DO NOT IGNORE IT, othewise you will be sudoless.

[http://php.8ez.com/drsmall/blog/?p=157](http://php.8ez.com/drsmall/blog/?p=157)

Dr Small

---

### Post by Tyche on 2008-01-08
> **hyper_ch said:**
> Tyche:

What's the point in running Firestarter at bootup?

hyper_ch:  The point to adding Firestarter to Sessions is that it will bring it up automatically when you enter your password.  It isn't that it brings it up on boot, as much as it is that it brings it up with the GUI.  Firestarter is a reasonable visual reference to the security of the system.  

Wireshark may be good.  I certainly won't dispute it, as I haven't had that much experience with it.  But I notice that both Firestarter and Wireshark require that they be initialized by root to function properly.  The information i get from Firestarter is sufficient to my needs, and doesn't appear to significantly affect the performance of my computer, so I'm satisfied with it.  Wireshark takes more time, effort and knowledge to set up (THIS IS NOT A FAULT), and I haven't gotten around to actually learning it, yet.  Perhaps someday I will.

In all, I would accept that it is not necessary to run Firestarter all the time, since once the IP tables are set, they stay set.  As I said, it's simply a visual reference.  And when the icon turns red, with a lightning bolt through it, I can easily find the potentially offending IP address and check with Whois to see who's trying to access my machine.  Having come from Windows (a number of years ago), I'm used to having a visual referent to the firewall handy.  And Firestarter fulfills that function.

I hope I explained my thinking well enough.  It's not meant to be a definitive answer, simply one that works for this old, perpetual n00bie.  :)  I'm still learning as I go, and Wireshark is somewhere on my horizon.  I just haven't gotten into it yet.

---

### Post by Dr Small on 2008-01-08
You could just setup a conky script which would run this command:
```
tail -n10 /var/log/auth.log | fold -w50
```

And you would always have an up to date visual of your auth.log on your desktop ;)

---

### Post by Tyche on 2008-01-08
> **Dr Small said:**
> You could just setup a conky script which would run this command:
```
tail -n10 /var/log/auth.log | fold -w50
```

And you would always have an up to date visual of your auth.log on your desktop ;)

Interesting.  But I never really got into conky.  Don't get me wrong, I see the point to conky, and I've tried it.  But I have a tendency to maximize windows, which rather defeats the purpose of conky.  I suppose it comes from being an old man (62) that's developing a cataract in one eye.  That, coupled with the fact that I used to be an AutoCAD draftsman, and always maximized windows for the best view of the drawings.

Isn't it amazing how habits can direct the way a person interacts with a computer?  :)

I hope your suggestion helps others, though.  It looks like it could be valuable to some.

---

### Post by Dr Small on 2008-01-08
I maximize my windows too ;)
But I thought that might be useful if someone wanted to glance at the desktop to see their auth.log :D

Dr Small

---

