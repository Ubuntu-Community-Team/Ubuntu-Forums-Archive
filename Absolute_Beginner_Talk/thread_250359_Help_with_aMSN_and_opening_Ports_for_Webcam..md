---
title: "Help with aMSN and opening Ports for Webcam."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Catewilliams on 2006-09-04
Hi, I don't really know how to work with ports, and from what I hear, when you want to use a webcam with aMSN you need to open ports...

 I don't know how to really do this, if someone could explain what I need to do to make my webcam run, I'd be really happy. I read one of the Tutorials they had, but it made no sence to me. D:

Thank you in advance!

---

### Post by kidders on 2006-09-04
My understanding of webcam apps is that, under the bonnet, you're quietly running a server that whoever you're chatting with connects to. Basically, you're problem is firewall-related.

Ordinarily, people run firewalls to deny unauthorised incoming connections based on a set of "rules", used to decide what is (or isn't) legitimate use of their internet connection. You need to tweak yours. In order to tell you how, you need to figure out where your firewall is. One could be running on your DSL modem, your Ubuntu box, another PC, or all of the above ... how is your network organised?

Once you've gotten that far, you need to find out which ports you need to open. Again, my understanding of MSN's protocols leads me to believe that this is *far* more complicated than, for instance, Yahoo is.

Take a look on aMSN's website and see if it supports a thing called UPnP (Universal Plug n Play), a gizmo that could handle most of this nasty port-related business *for* you.

Let us know what you find out, and I'll post some more specific help for you :)

---

### Post by Catewilliams on 2006-09-04
> **kidders said:**
> My understanding of webcam apps is that, under the bonnet, you're quietly running a server that whoever you're chatting with connects to. Basically, you're problem is firewall-related.

Ordinarily, people run firewalls to deny unauthorised incoming connections based on a set of "rules", used to decide what is (or isn't) legitimate use of their internet connection. You need to tweak yours. In order to tell you how, you need to figure out where your firewall is. One could be running on your DSL modem, your Ubuntu box, another PC, or all of the above ... how is your network organised?

Once you've gotten that far, you need to find out which ports you need to open. Again, my understanding of MSN's protocols leads me to believe that this is *far* more complicated than, for instance, Yahoo is.

Take a look on aMSN's website and see if it supports a thing called UPnP (Universal Plug n Play), a gizmo that could handle most of this nasty port-related business *for* you.

Let us know what you find out, and I'll post some more specific help for you :)


Okay, Thanks!

Well, I'm on my laptop, so I use the Wireless in my house.
I believe it's another computer.. I know my dad controls most of the wireless controls. Which makes me wary, becaue he wouldn't open ports without knowing exactly why.

I don't think it supports UPnP, but I have Firestarter, if that helps.. ](*,)  Sorry, I'm really bad with the internet security thing.

---

### Post by kidders on 2006-09-04
You should ask your dad what he's got set up ... if *he's* firewalling your internet connection, you could probably kill firestarter, which would make your life decidedly simpler :P

MSN's port usage seems to start at 6891, but can theoretically extend quite a bit, depending on how many connections it needs to make. It could be tricky to get it to work reliably without UPnP support, and you'd need to understand exactly how traffic is being managed on your LAN to know where to make changes.

Many people consider UPnP an unacceptable security risk, since it allows fairly arbitrary redirection of traffic on a network. See what he says!

---

### Post by Catewilliams on 2006-09-05
> **kidders said:**
> You should ask your dad what he's got set up ... if *he's* firewalling your internet connection, you could probably kill firestarter, which would make your life decidedly simpler :P

MSN's port usage seems to start at 6891, but can theoretically extend quite a bit, depending on how many connections it needs to make. It could be tricky to get it to work reliably without UPnP support, and you'd need to understand exactly how traffic is being managed on your LAN to know where to make changes.

Many people consider UPnP an unacceptable security risk, since it allows fairly arbitrary redirection of traffic on a network. See what he says!



Hmm.. Well, when you said I could kill firestarter, is there a way to control ports in firestarter?

---

### Post by kidders on 2006-09-05
Doesn't firestarter have a pretty little GUI to help you reconfigure it? I'm really an iptables user, but I took a look at [http://firestarter.sourceforge.net/manual/](http://firestarter.sourceforge.net/manual/) ... firestarter seems way friendlier :P

If there are other firewalls running elsewhere on your LAN, doing so won't help you though ... MSN will still be blocked ... which is why I suggested simply shutting it off.

---

### Post by Catewilliams on 2006-09-05
> **kidders said:**
> Doesn't firestarter have a pretty little GUI to help you reconfigure it? I'm really an iptables user, but I took a look at [http://firestarter.sourceforge.net/manual/](http://firestarter.sourceforge.net/manual/) ... firestarter seems way friendlier :P

If there are other firewalls running elsewhere on your LAN, doing so won't help you though ... MSN will still be blocked ... which is why I suggested simply shutting it off.



Okay! Thank you for helping me. ^^; I'm new to this so my problems are probably part of that. Ahwell. Thank you!

---

### Post by kidders on 2006-09-05
No problem :)

Perhaps your trouble is that you don't understand enough about firewalls to know where to start, even if there IS a pretty-looking user interface. If so, maybe this will help:

Basically, you start with a blank slate, blocking all networked communications to and from your PC. For most peoples' purposes, the following tweaks are sufficient:

[LIST]
[*]Permit outgoing connections destined for a number of commonly used ports
[*]Permit incoming connections seen as "related" to a recent outgoing connection.
[/LIST]

In general, a connection's port number identifies its purpose ... a system which is quite obviously easy to abuse ... so port numbering is more of a convention than a rule. Here are some common ones:

25 - SMTP (Email exchanges)
80 - Web servers
110 - POP (Downloading email)
143 - IMAP (Downloading email)
443 - Secure web servers (SSL)

So, unblocking these ports for the purposes of *outgoing* connections allows you to access these services from your PC.

Your question concerns allowing other people access to a service actually running on your PC however, so you need to unblock the right port; otherwise your firewall will treat any connections as if they were malicious attacks.

Most network applications have some level of support for operating normally in an environment as restricted as the one you probably have set up now ... MSN Messenger is not one of them :-( So you need to:

[LIST]
[*]Identify the port(s) you need to open
[*]Tweak your firewall
[/LIST]

Since the MSN protocol uses quite a number of ports, my understanding is that item (1) isn't as easy as it sounds. You might need to unblock several hundred to be sure nothing will break. To tweak your firewall, open whatever GUI-based app you've installed and see if you can find the right option. Usually, you won't need to restart the firewall to get it to work with the updated rules.

Now, we get to the next problem ... other firewalls on your LAN. Just because your computer is tweaked to permit connections to MSN webcam servers doesn't mean MSN webcam traffic can make it onto your network in the first place. It may be being blocked by another firewall, sitting between you and the internet. This means, of course, that your firewall may be redundant, in that it could simply be duplicating the behaviour of your Dad's firewall. This is why I suggested disabling yours.

To get MSN to cooperate for you:

[LIST=1]
[*]Turn off *all* your firewalls and test MSN's webcam feature. (Do this quickly to avoid attacks!!)
[*]Turn on one firewall and fiddle with it until MSN works again.
[*]Repeat the procedure for any other firewalls.
[/LIST]

Hopefully, this is a little more helpful! Post back if your run into difficulty!

---

### Post by BlacKat_K on 2006-09-07
I cant send my webcam no matter what! Tried it in Kopete and i can see it working in the properties window but it wont send.Also tried aMSN and Skype with no result. I cant even test Ekiga cause nobody can setup netmeeting so i'm very much STUCK!

---

### Post by kidders on 2006-09-08
Have you been able to figure out where the problem is at? Have you ruled out firewalls (on both ends) and hardware trouble as potential causes?

---

