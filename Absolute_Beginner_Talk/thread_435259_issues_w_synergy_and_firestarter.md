---
title: "issues w/ synergy and firestarter"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by wookaru on 2007-05-06
!First post!

I just installed Ubuntu 7.04 and I have synergy setup as a server on my Ubuntu box (XP pro laptop as client).   

I downloaded Firestarter to manage my Ubuntu firewall.

I when I start synergy while the firewall is turned on (command: synergys), my laptop is unable to connect to the synergy server.  But if i start synergy while the firewall is off, my laptop is able to connect fine.  After synergy is up, I can turn on the firewall and synergy seems to run just fine (although it seems to fail occasionally with the firewall turned on - rarely fails with firewall off).

My question is this:  How can I configure my firewall to allow synergy to establish a connection without having to toggle it on and off?

---

### Post by Billy McCann on 2007-05-06
Find out what port synergy uses by monitoring your connections from within Firestarter. Then, in Firestarter, create a new policy for that port, allowing whatever service type synergy uses.

By the way, welcome to Ubuntu.  :)

---

### Post by wookaru on 2007-05-06
I actually already tried the port thing - sorry I should have mentioned it.  I found that synergy uses port 24800.  I found this out by looking in Firestarter on the status tab, then looking under active connections.  The service is listed as "Unknown", but the source IP address is my laptop, so im pretty sure thats the port synergy is using.  

In the policy tab, under "Inbound Traffic Policy" I have:

```
Allow Service     port       For
Synergy           24800   everyone

```
Does this configuration look right?

I see no difference in behavior when i add/delete this rule.  I still cant establish the synergy connection with the firewall on, but I can maintain the synergy connection with the firewall on, if I started it w/ the firewall off.

And thanks for the warm welcome!

---

### Post by Billy McCann on 2007-05-06
Did you create both an incoming *and* an outgoing policy for synergy?

---

### Post by wookaru on 2007-05-06
No, I did not create an outgoing synergy policy.  For the outbound traffic policies, I have the radio button "Permissive by default, blacklist traffic" selected.  So I assume there is no blocking of any outbound traffic.  Is this correct?  I have no polices setup for outbound traffic of any kind.

---

### Post by Billy McCann on 2007-05-07
>  	No, I did not create an outgoing synergy policy. For the outbound traffic policies, I have the radio button "Permissive by default, blacklist traffic" selected. So I assume there is no blocking of any outbound traffic. Is this correct?
Two things.

1.  The fact that your firewall behaves differently when the Firestarter GUI isn't running and when it is running tells me that Firestarter is NOT loading your firewall rules on boot.  This is a bug within either Firestarter or the Firestarter package build.  

Whatever changes you make to your firewall via the Firestarter GUI are NOT implented on boot.  This is very, very bad.  

[COLOR="Red"]You need to totally ditch Firestarter.[/COLOR]  

The alternative is Guarddog, which is not nearly as user-friendly as Firestarter.  You must enable certain protocol manually.  Do not simply starter the program, click "OK", and then close it.  You'll have to just re-open it to let yourself surf the web, chat on IRC, instant message, etc.  It's all manual, which, honestly, is cool.  Just be sure to enable the protocol you need.  

2.  I believe you are correct about the permissive outbound policy within Firestarter.  It wouldn't hurt, though, to specify a policy, just to see what happens.  But ... the larger picture is ...

[COLOR="Red"]You need to totally ditch Firestarter.[/COLOR]  


:KS

---

### Post by wookaru on 2007-05-07
K, I can definitely do without Firestarter.  Im behind a router anyways, so its not absolutely necessary. 

Another question - and this might be a dumb one:  If I uninstall Firestarter, is there any kind of built in Firewall in Ubuntu that will take over automatically or anything like that?  Or will i just be completely sans-firewall when I remove firestarter?

---

### Post by Billy McCann on 2007-05-08
Firestarter is merely a nice frontend to the true Ubuntu firewall, iptables. Firestarter can be safely removed.  

On another note, I just set up my home network.  How does being behind a router help?

---

