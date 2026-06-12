---
title: "Firestarter is broken."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by chrispche on 2008-01-01
On boot up Firestarter will not start. I can' t even run it from the administration menu. Any Ideas?

Thanks.

---

### Post by kestrel1 on 2008-01-01
Can you run it from a teminal?
:~$ sudo firestarter
If not re-install
:~$ sudo apt-get install firestarter

---

### Post by chrispche on 2008-01-01
Done that. Still fails on boot up.

---

### Post by chrispche on 2008-01-01
Although I can run it from a GUI.

---

### Post by jken146 on 2008-01-01
Are you sure you need firestarter to run at startup?  It is not a firewall, just a GUI tool for configuring iptables, which is your firewall.

---

### Post by Ripfox on 2008-01-01
Really? I thought firestarter ran in the background and the gui was for settings...when you boot it starts "firestarter" at boot up with no gui. Am I wrong?

---

### Post by kestrel1 on 2008-01-01
Firestarter looks like a firewall to me:
[http://www.fs-security.com/docs/introduction.php](http://www.fs-security.com/docs/introduction.php)
But maybe I am wrong also.

---

### Post by jken146 on 2008-01-01
> **ripfox said:**
> Really? I thought firestarter ran in the background and the gui was for settings...when you boot it starts "firestarter" at boot up with no gui. Am I wrong?

The firewall itself is called **iptables**.  Firestarter is just a GUI tool.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=gutsy&release=all)

---

### Post by (((X))) on 2008-01-01
Firestarter works invisible, like iptables, will you keep reinstalling iptables until there is an systemtray, showing 'firewall is active'?
Leave it the way it is, test your firewall with an online test to see if firestarter does it's job:
[http://www.hackerwatch.org/probe](http://www.hackerwatch.org/probe)
[http://www.nmap-online.com](http://www.nmap-online.com)

---

### Post by hyper_ch on 2008-01-01
> **(((X))) said:**
> Firestarter works invisible

No, firestarter does nothing but configure IPTables through a GUI.... no need to run firestarter if you don't have a need to alter your firewall rules.

---

### Post by (((X))) on 2008-01-01
thanx for correcting me:)

---

### Post by kestrel1 on 2008-01-01
& me. I knew Linux was cool.

---

### Post by Ripfox on 2008-01-01
> **jken146 said:**
> The firewall itself is called **iptables**.  Firestarter is just a GUI tool.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=gutsy&release=all)

So it was doing what I thought it was doing, which is activating a "firewall" at boot after you install it, the gui is just for tweaking it then.

---

### Post by thelatinist on 2008-01-01
> **ripfox said:**
> So it was doing what I thought it was doing, which is activating a "firewall" at boot after you install it, the gui is just for tweaking it then.

Actually, the firewall is activated automatically any time ubuntu is started.  Firestarter doesn't activate it, it only sets specific rules for handling connections (by default IP tables allows all connections).

Are you sure you really need to define firewall rules, though?  There shouldn't be anything in a default Ubuntu installation that's even listening for incoming connections.  Your computer should therefore be invisible to the Internet by default.  Unless you've installed some sort of server software, you may not even need to worry about rules.  This is just another of the many reasons Linux is great.

---

### Post by Ripfox on 2008-01-02
> **thelatinist said:**
>  Firewall doesn't activate it, it only sets specific rules for handling connections (by default IP tables allows all connections)t.

You mean **Firestarter**.  One of the things that makes Linux great is that I **can** set specific rules with a great gui like Firestarter. :)

---

### Post by thelatinist on 2008-01-02
> **ripfox said:**
> You mean Firestarter

Yes, thank you.  I've fixed that.

---

### Post by chrispche on 2008-01-02
Yes but why does it say "fail" on boot up with firestarter? What am I missing. It used to say OK. Why the sudden change I have done nothing to change it.

---

### Post by Fungal Fractoids on 2008-01-02
^^ Coooool... That explains a lot. Thanks!

---

### Post by Fungal Fractoids on 2008-01-02
> **chrispche said:**
> Yes but why does it say "fail" on boot up with firestarter? What am I missing. It used to say OK. Why the sudden change I have done nothing to change it.

Cooooool. That explains a lot. Thanks!

---

### Post by chrispche on 2008-01-02
I just reinstalled the system. I'm still getting this problem what the hell is going on? Firestarter fails on boot up. Is there nothing I can edit to sort this out?

Please, Please Help. This was working before.

---

### Post by thelatinist on 2008-01-02
> **chrispche said:**
> I just reinstalled the system. I'm still getting this problem what the hell is going on? Firestarter fails on boot up. Is there nothing I can edit to sort this out?

Please, Please Help. This was working before.

Why are you trying to run Firestarter on bootup?  You don't need it.  Only run Firestarter when you want to *change* your firewall settings.

---

### Post by chrispche on 2008-01-02
I don't know, it's self installed in to the startup of the machine. Firestater startup failed. Where do I edit out such things? If you install firestarted does it not automatically go in to bootup as it has done for me.

I have just done a fresh install and it's still saying fail. It was working perfectly before. I just don't understand.

1 Why is it automatically on boot up?
2 What options have I for getting it working again?
3 If I don't need it, then how do I get rid of it from the bootup sequence?

---

### Post by llamakc on 2008-01-02
> **chrispche said:**
> I don't know, it's self installed in to the startup of the machine. Firestater startup failed. Where do I edit out such things? If you install firestarted does it not automatically go in to bootup as it has done for me.

I have just done a fresh install and it's still saying fail. It was working perfectly before. I just don't understand.

1 Why is it automatically on boot up?
2 What options have I for getting it working again?
3 If I don't need it, then how do I get rid of it from the bootup sequence?

Firestarter is NOT the firewall.

Firestarter is the apparatus (GUI tool) used to adjust the rules and policies for the built-in, RUNNING BY DEFAULT firewall called **IPTables. **Again, there is no need for Firestarter to run at boot or login, unless one intends to alter their firewall rules every single boot or session.

---

### Post by thelatinist on 2008-01-02
> **chrispche said:**
> I don't know, it's self installed in to the startup of the machine. Firestater startup failed. Where do I edit out such things? If you install firestarted does it not automatically go in to bootup as it has done for me.

I have just done a fresh install and it's still saying fail. It was working perfectly before. I just don't understand.

1 Why is it automatically on boot up?
2 What options have I for getting it working again?
3 If I don't need it, then how do I get rid of it from the bootup sequence?

Try going to System > Preferences > Sessions and seeing if it's listed in the startup list there.  If so, uncheck it or delete it.

And, no, installing Firestarter does not do what you describe.  You must have done something else that caused this.

---

### Post by chrispche on 2008-01-02
I'm not trying to be funny but. I went to synaptic installed firestarter and there it was on the bootup text. I don't have a splash screen I like to see what's going on.

---

### Post by thelatinist on 2008-01-02
Did you try my suggestion?

---

### Post by chrispche on 2008-01-02
> **thelatinist said:**
> Try going to System > Preferences > Sessions and seeing if it's listed in the startup list there.  If so, uncheck it or delete it.

And, no, installing Firestarter does not do what you describe.  You must have done something else that caused this.

Nope it's not in sessions. This is freaking me out. What is going on here.

---

### Post by llamakc on 2008-01-02
> **chrispche said:**
> I'm not trying to be funny but. I went to synaptic installed firestarter and there it was on the bootup text. I don't have a splash screen I like to see what's going on.

Well all that means is that there's an init script. If you look in /etc/init.d/ you'll see a script for firestarter. That init script calls /usr/sbin/firestarter, a binary file that applies the IPTables rules/policies/settings.

So both sides of this "firestarter" discussion are correct: Firestarter is already starting at boot, and the graphical tool used to modify rules does not need to be started at boot. Further, Firestarter is a front-end for the application of IPTables, the built-in firewall. Does this help?

If not, perhaps this will:

[http://www.fs-security.com/docs/persistence.php](http://www.fs-security.com/docs/persistence.php)

---

### Post by chrispche on 2008-01-03
Ok before I go ahead an fiddle with those files. Just let me tell you what comes up on the bootup, I thought it might help incase anyones missed anything.

--
* Stopping the Firestarter firewall...

 [19.288000] ip_tables (C) 2000-2006 Netfilter Core Team
 [19.444006] Netfilter messages via NETLINK v.0.30
 [19.4600000] nf_conntrack version 0.5.0(6143 buckets, 49144 max)
...done
*Starting the Firestarter firewall...                                           ...fail
  run-parts: /etc/network.if.up.d/SOFirestarter exited with return code 2

Then the bootup continues to load.

Finally saying a bit down on the bootup

Starting the Firestarter Firewall...                                              [fail]
--

Thats it, in the bootup screen.

So does that add any light on the sitaution?

---

### Post by mister_pink on 2008-01-04
You weren't going mad or anything, when you say that firestarter isn't working on boot people assume you're trying to get the GUI to load on login, which isn't the case here. This is a known problem that I also experience - [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/132039](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/132039)

---

