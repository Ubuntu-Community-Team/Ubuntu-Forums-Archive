---
title: "[SOLVED] VOIP free incoming UK number - Ekiga / sipgate"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ugm6hr on 2007-07-22
I have successfully managed to get my headset working with skype.

I have a sipgate.co.uk account, specifically for receiving incoming calls on a UK landline number (which is free with sipgate) to my VOIP computer.  This is pretty useful in a house-share, where the main landline is always busy!

Unfortunately, I can't get Ekiga to work properly with sipgate.
I have done the following:

Set up Ekiga with my SIP-ID and password, and put the registry, proxy and STUN server as suggested in sipgate settings.

Ekiga confirms the account is registered, as does logging into my sipgate.co.uk account.

However, if I call my sipgate account (from my mobile phone), the line goes dead (failed call).  Then 30 seconds later, Ekiga puts up a notice stating that there is an incoming call (which lasts about 2 seconds).  If I accept in that time - it states that the Remote user ended call.

If I try to make an outgoing call to the 10000 test number, it tries to dial for about 40 seconds, then appears to connect (with PCMA) but I can't hear the recorded message.

I have also tried turning off the Linux firewall (with Firestarter), and forwarding all relevant ports from my router.

I am wondering whether it is the DTMF support that means sipgate won't work...  Or is it something more simple.  I gather sipgate suggests X-Lite, but I don't think that's in the repos.

Anyone got this to work?

---

### Post by YannickDefais on 2007-07-23
Hi,

Can you upgrade to Ekiga version 2.0.9 and see if you still have this problem ?

[https://help.ubuntu.com/community/Ekiga?highlight=%28ekiga%29#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c](https://help.ubuntu.com/community/Ekiga?highlight=%28ekiga%29#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c)

Regards,
Yannick

---

### Post by ugm6hr on 2007-07-23
Cheers for the link (and the great program - assuming you were involved).

As it happens, having tried to set it up at my dad's (and encountering the problems above), I have now brought my laptop to my house share, and it just works.  No port-forwarding required.  Bizarre.

I have installed the new version anyway.  I will try again at my dad's to try and work out what the problem is, if that information is useful to you, but I don't need it there anyway.  It must be an issue with the router, presumably.

For anyone trying this:
My settings for Ekiga / sipgate:

Accounts:
```
Registrar: *sipgate.co.uk:5060*
User / Password: As per sipgate.co.uk Settings page
```

Preferences:
```

Network Settings:
NAT: *STUN*
STUN server: *stun.sipgate.net:10000*

SIP Settings:
Outbound proxy: *sipgate.co.uk:5060*
DTMF: *RFC2833*

H.323 Settings:
Default gateway: *sipgate.co.uk*
Untick all "Advanced Settings"
DTMF: *String*

```

---

### Post by YannickDefais on 2007-07-23
Hi,

The settings for ekiga should be the same as x-lite, there is an official setup but I can't access it:
[http://www.sipgate.co.uk/setup/xlite](http://www.sipgate.co.uk/setup/xlite)

Regards,
Yannick

---

