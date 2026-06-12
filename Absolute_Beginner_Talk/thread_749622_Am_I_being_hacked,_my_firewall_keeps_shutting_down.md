---
title: "Am I being hacked, my firewall keeps shutting down!"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Linewbie on 2008-04-08
Am I being hacked, my firewall (firestarter) keeps shutting down!
I don't know enough to decipher the auth.log, help would be appreciated.

I'm a little concerned about the "ohiggins.canonical.com" firewall events. (listed at the bottom, they're showing up on this page as :ohiggins)
Are there undocumented backdoors in Ubuntu, because I recently reinstalled Ubuntu because my firewall turned off by itself on the previous install after my firewall blocked a series of events. In other words, was I successfully hacked more than once, with the same set of circumstances both times?? I saved the previous events, I'll post them in a reply if it's warranted.
I've only logged in my system as user gadzooks (multiple times today), but it says user root logged in and out multiple times!
I have completely different usernames and (strong= 18+digits long) passwords too!
Another thing I don't understand, all those timestamps with the "17" in them, is that random?? (I did reboot today more than once, though)
Please tell me that my concern is overblown (preferably more than one opinion).
If I am being hacked, I don't know how it's being done after a fresh install!
Maybe my firestarter is not configured correctly, but it is blocking SOME events.

But I do think I know who did it, I was playing a online game. The last few times I played, there were firewall events concurrent to my game session. If I have been cracked, it was someone there with admin powers!

Thanks.
:confused:
-----------------------------------------------------------------------------------------------------------------------------

My auth.log is as follows:
Apr  8 00:17:01 GenericHostname CRON[7483]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 00:17:02 GenericHostname CRON[7483]: pam_unix(cron:session): session closed for user root
Apr  8 01:17:01 GenericHostname CRON[7512]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 01:17:02 GenericHostname CRON[7512]: pam_unix(cron:session): session closed for user root
Apr  8 02:17:01 GenericHostname CRON[7725]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 02:17:01 GenericHostname CRON[7725]: pam_unix(cron:session): session closed for user root
Apr  8 02:19:14 GenericHostname gdm[5510]: pam_unix(gdm:session): session closed for user gadzooks
Apr  8 02:21:32 GenericHostname gdm[5513]: pam_unix(gdm:session): session opened for user gadzooks by (uid=0)
Apr  8 02:21:33 GenericHostname gdm[5513]: gkr-pam: couldn't unlock 'login' keyring: 1
Apr  8 02:28:14 GenericHostname gdm[5513]: pam_unix(gdm:session): session closed for user gadzooks
Apr  8 02:30:45 GenericHostname gdm[5509]: pam_unix(gdm:session): session opened for user gadzooks by (uid=0)
Apr  8 02:30:45 GenericHostname gdm[5509]: gkr-pam: couldn't unlock 'login' keyring: 1
Apr  8 02:31:45 GenericHostname sudo: gadzooks : TTY=unknown ; PWD=/home/uber ; USER=root ; COMMAND=/usr/sbin/firestarter
Apr  8 03:17:01 GenericHostname CRON[6876]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 03:17:01 GenericHostname CRON[6876]: pam_unix(cron:session): session closed for user root
Apr  8 04:17:01 GenericHostname CRON[7533]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 04:17:01 GenericHostname CRON[7533]: pam_unix(cron:session): session closed for user root
Apr  8 05:17:01 GenericHostname CRON[8152]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 05:17:02 GenericHostname CRON[8152]: pam_unix(cron:session): session closed for user root
Apr  8 06:17:01 GenericHostname CRON[8748]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 06:17:01 GenericHostname CRON[8748]: pam_unix(cron:session): session closed for user root
Apr  8 06:25:02 GenericHostname CRON[8844]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 06:25:02 GenericHostname CRON[8844]: pam_unix(cron:session): session closed for user root
Apr  8 07:17:01 GenericHostname CRON[9338]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 07:17:01 GenericHostname CRON[9338]: pam_unix(cron:session): session closed for user root
Apr  8 07:30:01 GenericHostname CRON[9487]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 07:30:02 GenericHostname CRON[9487]: pam_unix(cron:session): session closed for user root
Apr  8 08:17:01 GenericHostname CRON[10036]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 08:17:01 GenericHostname CRON[10036]: pam_unix(cron:session): session closed for user root
Apr  8 09:17:01 GenericHostname CRON[10440]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 09:17:01 GenericHostname CRON[10440]: pam_unix(cron:session): session closed for user root
Apr  8 10:17:01 GenericHostname CRON[10939]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 10:17:01 GenericHostname CRON[10939]: pam_unix(cron:session): session closed for user root
Apr  8 11:17:01 GenericHostname CRON[11480]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 11:17:01 GenericHostname CRON[11480]: pam_unix(cron:session): session closed for user root
Apr  8 12:17:01 GenericHostname CRON[12032]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 12:17:01 GenericHostname CRON[12032]: pam_unix(cron:session): session closed for user root
Apr  8 13:17:01 GenericHostname CRON[12501]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 13:17:01 GenericHostname CRON[12501]: pam_unix(cron:session): session closed for user root
Apr  8 14:17:01 GenericHostname CRON[12949]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 14:17:01 GenericHostname CRON[12949]: pam_unix(cron:session): session closed for user root
Apr  8 14:20:03 GenericHostname gdm[5509]: pam_unix(gdm:session): session closed for user gadzooks
Apr  8 14:21:57 GenericHostname gdm[5512]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=gadzooks
Apr  8 14:22:33 GenericHostname gdm[5512]: pam_unix(gdm:session): session opened for user gadzooks by (uid=0)
Apr  8 14:22:33 GenericHostname gdm[5512]: gkr-pam: couldn't unlock 'login' keyring: 1
Apr  8 15:16:42 GenericHostname sudo: gadzooks : TTY=unknown ; PWD=/home/uber ; USER=root ; COMMAND=/usr/sbin/firestarter
Apr  8 15:17:01 GenericHostname CRON[6340]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 15:17:01 GenericHostname CRON[6340]: pam_unix(cron:session): session closed for user root
Apr  8 15:19:44 GenericHostname gdm[5516]: pam_unix(gdm:session): session opened for user gadzooks by (uid=0)
Apr  8 15:19:44 GenericHostname gdm[5516]: gkr-pam: couldn't unlock 'login' keyring: 1
Apr  8 15:22:17 GenericHostname sudo: gadzooks : TTY=unknown ; PWD=/home/uber ; USER=root ; COMMAND=/usr/sbin/firestarter
Apr  8 16:12:15 GenericHostname sudo: gadzooks : TTY=unknown ; PWD=/home/uber ; USER=root ; COMMAND=/usr/sbin/firestarter
Apr  8 16:14:22 GenericHostname sudo: gadzooks : TTY=unknown ; PWD=/home/uber ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 50331651 --update-at-startup
Apr  8 16:17:01 GenericHostname CRON[7153]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 16:17:01 GenericHostname CRON[7153]: pam_unix(cron:session): session closed for user root
Apr  8 16:21:47 GenericHostname sudo: gadzooks : TTY=unknown ; PWD=/home/uber ; USER=root ; COMMAND=/usr/sbin/firestarter

-----------------------------------------------------------------------------------------------------------------------------
Also recent events logged by firestarter:

Time:Apr  5 15:48:26 Direction: Unknown In:eth0 Out: Port:53479 Source:ohiggins.canonical.com Destination:192.168.123.100 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown

Time:Apr  5 15:48:26 Direction: Unknown In:eth0 Out: Port:53479 Source:ohiggins.canonical.com Destination:192.168.123.100 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown

Time:Apr  3 16:27:34 Direction: Unknown In:eth0 Out: Port:42598 Source:209.170.75.176 Destination:192.168.123.100 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown

Time:Mar 28 22:22:31 Direction: Unknown In:eth0 Out: Port:53 Source:192.168.123.254 Destination:192.168.123.101 Length:56 TOS:0x00 Protocol:ICMP Service:DNS

Time:Mar 21 23:29:05 Direction: Unknown In:eth0 Out: Port:53886 Source:od-in-f147.google.com Destination:192.168.123.100 Length:410 TOS:0x00 Protocol:TCP Service:Unknown

---

### Post by atomkarinca on 2008-04-08
Firestarter is not an application that you can start or stop. It just makes changes on your iptables. When you "start" those changes take effect and if you "stop" they don't. And the canonical address seems to be this forum :)

---

### Post by bapoumba on 2008-04-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/firestarter/+bug/120445](https://bugs.launchpad.net/firestarter/+bug/120445) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a bug in Firestarter. Please see if it is related to you issues (it crashes if you open the prefs> network settings tab).
And ohiggins.canonical.com is indeed where UF is located.

---

